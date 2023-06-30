<div align="center">

# example-tauri-e2e

A little example on how to do e2e testing with Tauri.

</div>

## Getting started

### Testing locally

To test things locally I'm running inside WSL.

```bash
cd crates/backend
pnpm i -r
pnpm tauri dev
```

This should show you the base application the official guide is talking about.

Now lets add testing. I simply followed the official guides and made very minor adjustments based on our needs. Primarily, in wdio.conf.js, make sure you have the correct path to your resulting binary.

```bash
cargo install tauri-driver
pnpm test
```

You should now see your app pop up and the tests succeed!

### Testing in Docker

This is a bit easier honestly since you don't need to take care of the setup. Especially easier for me because I don't have to give you any instructions on how to set up your dev environment properly, I've done that for you inside the docker image.

Building the image **the first time** takes a lot of time. After the first build it's smooth sailing if you wanna use this as an alternative to running locally.

Make sure the CRATE argument at the top in the dockerfile matches the folder name of your app inside the `crates/` folder.

> If you run it and it complains that it couldn't connect to some debian servers just rerun the command a bunch of times, it's networking related, the file isn't broken

```bash
docker build -f docker/test.dockerfile -t throwaway .
```

## It's not working for me :(

If this project isn't working then the issue **should** be on your system, but it can be that some dependencies somewhere are broken and you might need to fix something.

Hit me up on the Tauri discord server if you want support.
