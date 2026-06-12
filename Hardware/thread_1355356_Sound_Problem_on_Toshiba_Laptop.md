---
title: "Sound Problem on Toshiba Laptop"
date: 2009-12-14
forum: Hardware
---

### Post by mandoman on 2009-12-14
Hi,
I'm completely new to Ubuntu and Linux style operating systems.  I just installed it today, and so far it's working great, except that I have no sound. :(  I'm running Ubuntu 9.10 on a Toshiba Satellite A105 S4201 laptop.  Not sure how to go about fixing this, can anyone possibly help me out?  Thanks!
-Chris

---

### Post by cartisdm on 2009-12-14
Someone with a similar Toshiba laptop model in [this thread]("http://ubuntuforums.org/showthread.php?t=451011") was about to get success by running the following:

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop ubuntu-minimal
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto
sudo gedit /etc/modprobe.d/alsa-base

```

then added:
"options snd-hda-intel probe_mask=8 model=auto"

It's worth a shot but I'm not sure if you both are running the same configuration so it might not have any effect

---

### Post by mandoman on 2009-12-14
Hi, thanks for the reply!
I started entering those, but when I got to
sudo rmmod snd-hda-intel I got a message saying "ERROR: Module snd_hda_intel is in use".
Any idea what that might mean?
Thanks!

---

### Post by cartisdm on 2009-12-14
> **mandoman said:**
> Hi, thanks for the reply!
I started entering those, but when I got to
sudo rmmod snd-hda-intel I got a message saying "ERROR: Module snd_hda_intel is in use".
Any idea what that might mean?
Thanks!

There are two things that might work.

1. Try running **killall esd** before your sudo rmmod command

or

2. Try blacklisting the module in /etc/modprobe.d/blacklist

---

