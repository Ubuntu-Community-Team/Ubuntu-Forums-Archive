---
title: "x205-S9359 and sound after standby resume - Ubuntu 8.04"
date: 2008-06-25
forum: Hardware
---

### Post by hraqhraq on 2008-06-25
Here is the solution that I tested on my laptop to enable sound to come back after a system resume from a standby

open the file

/etc/modprobe.d/alsa-base

as a root and type at the end the following line

options snd-hda-intel model=toshiba

and test the sound; it will work for you.

All other devices are excellently handled by Ubuntu 8.04.

---

### Post by eClaW on 2008-08-23
Thanks man, worked for me and probably saved me lots of surfing time. ;)

---

