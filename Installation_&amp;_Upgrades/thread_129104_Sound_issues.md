---
title: "Sound issues"
date: 2006-02-12
forum: Installation &amp; Upgrades
---

### Post by CookieOrc on 2006-02-12
When I am using any of the desktop enviroments my sound works perfectly. When I play any type of game I get no sound what so ever it is driving me nuts...

---

### Post by joft on 2006-02-15
Which games do you run?

Be aware that most (non-free, non-open source) games (e.g. ET) only support OSS (Open Sound System) and that's not what you want, because Kubuntu ususally uses ALSA (Advanced Linux Sound Architecture) to drive your sound card. (Let's call OSS and ALSA a set of differently working sound card/chip drivers).
The problem is, that ALSA supports OSS through it's emulation modules, but as soon as an OSS application uses the OSS emulation, it will **block** the whole sound device or isn't even able to open the sound device, because it's used by another application.
This problem only occurs if you have a sound card/chip which **does not support mixing of several sound sources in hardware**.

A solution might be to run such OSS applications through KDE's artsd wrapper, called "artsdsp". (artsd is a "sound server" which allows more than one application to connect to it and then mixes these several sources into one stream to output it to your ALSA sound card driver.)
You could start a game through artsdsp by doing:

```
artsdsp -m <game-executable-file/script>
```

Open a console for that and cd into the directory of your game and replace the above text between the < and > with the game's executable.

---

