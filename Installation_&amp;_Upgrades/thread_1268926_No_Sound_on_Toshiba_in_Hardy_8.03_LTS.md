---
title: "No Sound on Toshiba in Hardy 8.03 LTS"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by Daniel09 on 2009-09-17
Dear all,

I'm having some problems with my sound on a Toshiba Satellite A200.

I got it working in a previous system by reinstalling alsa and changing a line in /etc/modprobe.d/alsa-base but when I upgraded to hardy 8.03 LTS I lost it.

I tried to follow the thread:

[http://ubuntuforums.org/showthread.php?t=568463&page=3](http://ubuntuforums.org/showthread.php?t=568463&page=3)

However installing alsa-driver is problematic.

sudo ./configure works fine but when doing:
sudo KBUILD_NOPEDANTIC=1 make I get the following error:


make[1]: Entering directory `/usr/src/linux-headers-2.6.24-24-generic'
  CC [M]  /home/daniel/Documents/alsasrc/alsa-driver-1.0.15/acore/hwdep.o
In file included from /home/daniel/Documents/alsasrc/alsa-driver-1.0.15/acore/hwdep.c:22:
include/sound/driver.h:26:20: error: config.h: No such file or directory
include/sound/driver.h:46:21: error: adriver.h: No such file or directory
make[3]: *** [/home/daniel/Documents/alsasrc/alsa-driver-1.0.15/acore/hwdep.o] Error 1
make[2]: *** [/home/daniel/Documents/alsasrc/alsa-driver-1.0.15/acore] Error 2
make[1]: *** [_module_/home/daniel/Documents/alsasrc/alsa-driver-1.0.15] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-24-generic'
make: *** [compile] Error 2

Any suggestions?

For additional info the sound card is:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

I know others have had the problem but I don't see why I can't get this to work on hardy.

Many thanks

---

### Post by Daniel09 on 2009-09-17
Here is some progress:

I was able to install alsa using the latest version i.e. 1.0.21 however when opening alsa I got:

alsamixer: function snd_ctl_open failed for default: No such device

So following the thread:

[http://ubuntuforums.org/showthread.php?t=337276](http://ubuntuforums.org/showthread.php?t=337276)

I tired 

asoundconf list

which did not show any sound cards. I can detect the sound card using lspci but somehow alsa does not seem to pick up on it. Any ideas?

---

