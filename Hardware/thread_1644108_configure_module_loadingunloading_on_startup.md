---
title: "configure module loading/unloading on startup"
date: 2010-12-12
forum: Hardware
---

### Post by hamstersquasher on 2010-12-12
All, 

I am running Ubuntu 10.10 with a broadcom bcm4312 802.11a/b/g chipset.  I am using a patched driver in order to enable packet injection for aircrack-ng.  The patched drivers is 'b43'.  After each reboot, I have to perform the following commands in order to get any wireless working.  Once I complete these commands, I have working wireless using the patched driver I compiled. 

[B]sudo modprobe -r ssb
sudo modprobe -r mac80211
sudo modprobe b43[/B]

How can I keep from doing this each time on startup?  I have tried adding ssb and mac80211 to the /etc/modprobe.d/blacklist.conf file but they still load on startup.  Even if I could get them to stop loading, I would like to automate the loading of the b43 module.  Any help would be greatly appreciated.

---

### Post by earthwormdan on 2011-01-15
I am also having this problem with kernel 2.6.35 on ubuntu 10.10 with latest compat-wireless and negative channel patch ( I have tried a few now) and would love for a way to automate this system. any idea's?

---

