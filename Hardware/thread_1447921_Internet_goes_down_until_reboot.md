---
title: "Internet goes down until reboot?"
date: 2010-04-06
forum: Hardware
---

### Post by UnresponsiveBeeVictim on 2010-04-06
What would cause my box to drop off the LAN until I reboot it whenever I try to transfer at high speeds to/from it?  I've tried two nics - same problem, tried WinXP and it was fine, so I know it's a config or something problem.  The install is fresh from today.  It's CLI only and wired - no wifi.   If I leave the computer alone it will eventually drop off, and I can make it happen pretty quickly by transferring data to/from it.  It was fine during the installer (I used the mini.iso) so it has to be a problem with ubuntu.

---

### Post by UnresponsiveBeeVictim on 2010-04-06
This was my issue:
[http://ohioloco.ubuntuforums.org/showthread.php?t=1311112&highlight=power+management](http://ohioloco.ubuntuforums.org/showthread.php?t=1311112&highlight=power+management)

First, In /etc/default/grub, Change this line (sudoedit or whatever you like) :
Code:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
for
Code:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
then run
Code:
sudo update-grub

---

