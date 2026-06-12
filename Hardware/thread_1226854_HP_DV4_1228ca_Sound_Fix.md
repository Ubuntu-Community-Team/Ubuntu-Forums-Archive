---
title: "HP DV4 1228ca Sound Fix"
date: 2009-07-30
forum: Hardware
---

### Post by nconceicao on 2009-07-30
Here is the fix on Ubuntu 9.04 64bit

gksudo gedit /etc/modprobe.d/alsa-base

add the following to the end of the file.

# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1

Reboot and enjoy!

---

