---
title: "HP dv7-3085dx internal mic issue"
date: 2009-12-02
forum: Hardware
---

### Post by Veratyr9 on 2009-12-02
Have an HP dv7-3085dx laptop, has stero internal mics that do not function.  the mic port on the front works just fine, but in sound preferences there is only one device listed in the device list (my front plug).  anybody know where to start to get the internal mic's recognized?

---

### Post by anton_vila on 2010-04-10
Hi,

I have a similar problem with the internal mike on a HP dv7-3085dx. With 'sound recorder' I see the level bar moving while recording but the only thing that gets recorded is static noise. I have tried all kinds of things that I have seen posted but none has worked. I hope somebody comes up with a solution to this.

Anton

---

### Post by lidex on 2010-04-11
What version of ubuntu are you using? Karmic? Go to this page and follow instructions to install alsa-backports:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

Then open a terminal="Applications>Accessories>Terminal" and enter this command:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
``` to open the file for editing. Paste in these lines at the bottom.
```
options snd-hda-intel enable_msi=1
options snd-hda-intel model=hp-dv5

```
 Save. Close. Reboot.

---

