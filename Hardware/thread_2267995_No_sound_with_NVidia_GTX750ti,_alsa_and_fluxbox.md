---
title: "No sound with NVidia GTX750ti, alsa and fluxbox"
date: 2015-03-05
forum: Hardware
---

### Post by sveni_lee on 2015-03-05
I installed kodi on Ubuntu server 14.04.2 Efi mode and fluxbox. I use the following startscript to start fluxbox.

```
# kodi-upstart
# starts KODI on startup by using xinit.
# by default runs as kodi, to change edit below.
env USER=kodi

emits kodi-started
description     "KODI-barebones-upstart-script"
author          "Matt Filetto"

start on (filesystem and stopped udevtrigger)
stop on runlevel [016]

respawn
respawn limit 10 5
limit nice 21 21

script
exec su -c "xinit /usr/bin/startfluxbox -- /usr/bin/X -nolisten tcp :0" $USER
end script

```

Audio for kodi works fine but when I start Dolphin-emu via advanced louncher the sound in dolphin is gone...
So I checked the sound without kodi (boot without startup), but still no sound.

So I've ask google and have done the following steps:

```
kodi@mediacenter:~$ grep eld_valid /proc/asound/NVidia/eld*
/proc/asound/NVidia/eld#0.0:eld_valid           0
/proc/asound/NVidia/eld#0.1:eld_valid           1
/proc/asound/NVidia/eld#0.2:eld_valid           0
```

```
kodi@mediacenter:~$ aplay -l | grep NVidia
Karte 1: NVidia [HDA NVidia], Gerät 3: HDMI 0 [HDMI 0]
Karte 1: NVidia [HDA NVidia], Gerät 7: HDMI 1 [HDMI 1]
Karte 1: NVidia [HDA NVidia], Gerät 8: HDMI 2 [HDMI 2]
```

```
speaker-test -D plughw:1,3 -c2
```
```
speaker-test -D plughw:1,7 -c2
```

but I can't get any sound... So I think it must be related to fluxbox...

---

