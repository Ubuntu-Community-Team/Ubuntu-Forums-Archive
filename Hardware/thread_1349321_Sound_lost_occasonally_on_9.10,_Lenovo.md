---
title: "Sound lost occasonally on 9.10, Lenovo"
date: 2009-12-08
forum: Hardware
---

### Post by inkimar on 2009-12-08
Hi!

Installed 9.10 on my Lenovo 3000 ( V100 ) and I am having problem with the sound. 
Following the advice in this [thread]("http://ubuntuforums.org/showthread.php?t=205449") , 
Following the advice until.

[INDENT](2) Reinstall those same packages
sudo apt-get install linux-sound-base alsa-base alsa-utils
[/INDENT]
and then[INDENT]
sudo apt-get install gdm ubuntu-desktop
[/INDENT]
and then[INDENT]
Saving Sound Settings
sudo alsactl store 0[/INDENT]

Now I reboot, the sound is working.

if I restart again, then all is lost.

What am I missing here ?

My file '/etc/modules' consists of the following two lines.
lp
snd-hda-intel



Regards, i

---

