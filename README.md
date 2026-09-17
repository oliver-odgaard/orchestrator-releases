# Orchestrator releases

This repository holds **builds of Orchestrator and the Sparkle appcast that
points at them. It holds no source.** Orchestrator itself is developed in a
private repository; this one exists so that a copy of the app on somebody
else's Mac has a public, permanent https address to ask "is there a newer
one?" — and a public address to download it from.

## What is here

| | |
|---|---|
| `appcast.xml` | The Sparkle 2 feed. One `<item>` per release, each with the zip's URL, its length, and an EdDSA signature. |
| Releases | One GitHub release per version, tagged `v<version>`, with `Orchestrator-<version>-<commit>.zip` attached. |

The app reads the feed at

```
https://raw.githubusercontent.com/oliver-odgaard/orchestrator-releases/main/appcast.xml
```

## Installing by hand

Download the newest `.zip` from [Releases](../../releases), unzip it, and drag
`Orchestrator.app` to your Applications folder. Every build is Developer ID
signed, notarized by Apple and stapled, so it opens without a right-click.

Once you are running it, you do not have to come back here: **Orchestrator ▸
Check for Updates…** does this, and it checks on its own about once a day.
It never installs anything without you clicking Install.

## What the signature means

Two independent ones, and they answer different questions.

* **Apple's notarization ticket**, stapled inside each zip, is what Gatekeeper
  checks on your Mac. It says this build came from the developer's signing
  identity and Apple scanned it. It is checked whether you downloaded the zip
  from this page or Orchestrator downloaded it for you.
* **The EdDSA signature** in `appcast.xml` is what Sparkle checks before it
  will install anything. It says the build the feed points at is the build the
  developer signed, on a machine holding the private key — which is not this
  repository and not GitHub.

Neither one is issued by GitHub, so a GitHub account compromise cannot make
Orchestrator install something the developer did not sign.

## Reporting something

Use **Orchestrator ▸ Settings ▸ Feedback** in the app. Issues are disabled
here because this repository holds no code to file them against.
