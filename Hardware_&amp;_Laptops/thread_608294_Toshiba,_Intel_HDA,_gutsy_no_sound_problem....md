---
title: "Toshiba, Intel HDA, gutsy no sound problem..."
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by crazychopsticks on 2007-11-09
Hello,

I am having the Toshiba, Intel HDA sound problem in gutsy and I just can't get it fixed like everyone else on the forum. I am certain the problem is with something that has changed with either the kernel or alsa since feisty. I really appreciate all the work the developers have done in gutsy and from what I can see it is a very nice OS but I sadly (along with many other users) can no longer use it because of the lack of sound. Is there any idea on when there will be a kernel update that may solve this issue? It is one of utmost importance for many users like me. 

PS. I had feisty working perfectly with sound and so forth using the DSDT fix and using the latest BIOS version. Sadly none of this makes gutsy play sweet music for me. Any ideas on when a fix may be available.

David

---

### Post by toutatis on 2007-11-10
You're not alone in this. I also have a Toshiba laptop, upgraded to Gutsy and lost my sound.
Until now I found no fix for it.

---

### Post by toutatis on 2007-11-10
I've got sound now!!!
There are a lot of posts that advise you to change /etc/modprobe.d/alsa-base adding a line
```
options snd-hda-intel model=...
``` 
to it.
I filled in the dots with **toshiba** according to the intructions from ALSA-configuration.txt. That seems a mistake!

According to bug 138322 ([https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/138322](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/138322)) the model should be auto or 3stack. I filled in auto and it works!

So:
```
sudo gedit /etc/modprobe.d/alsa-base
```

Change the line with 
   options snd-hda-intel model=toshiba 
to 
   options snd-hda-intel model=auto
(or add this line).

Reboot your computer. 

Hope this works for you too.

Roel

---

### Post by msanifu on 2007-11-10
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

go to the section"Getting the ALSA drivers from a *fresh* kernel"

i did the purge thingy,reistalled the packages as per instructions,rebooted,I HAVE SOUND! on my toshiba


Getting the ALSA drivers from a *fresh* kernel

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

A faster way, is to just remove the problematic packages and reinstall them cleanly.

(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils

[list][*]
VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm ubuntu-desktop


(3) Reboot
[*][left]
VERY IMPORTANT NOTE: Xubuntu (XFCE) users have reported that packages 'gdm' and 'xubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm xubuntu-desktop


(3) Reboot
Now you may ask "I already had the packages, so why did I go through the trouble of removing them, then installing them". The answer lies in the --purge option which removes all the extra information that accumulated from tinkering and upgrading. After doing a purge then install, the packages are unpackaged as if it they are brand new.
(4) At this point, try using
Code:

 aplay -l

you should get your soundcard listed.

    * Success - Your soundcard is detected. Go onto the Using alsamixer section, then try playing something on your music or media player.
    * Failure - Your card was not detected. You should try compiling your driver, so go onto ALSA drive Compilation.

---

### Post by john17 on 2008-01-25
Thanks to toutatis.

Added "options snd-hda-intel model=auto" at the end of /etc/modprobe.d/alsa-base, Rebooted and now sound works! =D>

 (I have a Toshiba Satellite A100).

---

