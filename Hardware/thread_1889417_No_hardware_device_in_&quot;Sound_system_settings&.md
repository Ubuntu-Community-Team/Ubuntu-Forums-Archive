---
title: "No hardware device in &quot;Sound system settings&quot; on X220T"
date: 2011-12-01
forum: Hardware
---

### Post by weichel on 2011-12-01
Hi everyone,

I'm running Oneiric on my Lenovo X220T. The sound itself works fine (pure ALSA, killed pulse), and so does the alsamixer (I can change the volumne using the alsamixer).

Yet, the hardware list in the sound settings remains empty, which I suspect is the reason for the Gnome audio integration not to work. Does anyone have an idea how to fix that?

Any help is appreciated,
Chris

I've also attached the alsa-info of my system (as suggested on the sound troubleshooting page [https://help.ubuntu.com/community/SoundTroubleshootingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure"))

---

### Post by MoreOrLess on 2011-12-01
It only works with pulseaudio...
You can make scripts that change the volume and bind them to your media keys, though (google it).

---

### Post by weichel on 2011-12-01
Thank you MoreOrLess for you answer :)

Unfortunately it also didn't work when pulseaudio was running.
Binding scripts to those buttons is the last resort, I'd rather have the Gnome integration working properly (good looking OSD, media menu, etc.)

The buttons themselves are recognized (they create an event in *xev*) and I can also bind them to *volume up* and *volume down* actions in the "keyboard shortcut" system settings.

So, the question remains: why doesn't Gnome see my sound device?

---

### Post by weichel on 2011-12-01
After giving pulseaudio a second try, it seems that I'm affected by this [bug]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/747838").

So maybe making pulseaudio ignoring that virtual card helps. Will give it a try.

---

### Post by weichel on 2011-12-01
I forced pulseaudio to use ALSA by adding ```
load-module module-alsa-sink
``` to /etc/pulse/deamon.conf


That did the trick.

---

