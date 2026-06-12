---
title: "Problem with upgrade"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by ghonz on 2009-04-27
Hi I've recently attempted to upgrade to 9.04 from 8.10 and I am now having problems getting in to my computer.
I am using a HP Pavilion tx1138ea

After switching it on I get the following message:

usplash: setting mode 1280x1024 failed
usplash: setting mode 1152x864 failed
usplash using mode 1024x768
gave up waiting for root device. common problems:
 - Boot args (cat /prc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the sysytem wait for the right device?)
 - Missing modules (cat /proc/modules; 1s /dev)
ALERT! /dev/disk/by-auid/6888b0e4-fb16-4df6-81c2e8b546e5 does not exist.  Dropping to a shell!

Busy box v1.10.2 (ubuntu 1:1.10.2-2ubuntu7) built in shell (ash)
Enter 'help' for a list of built-in commands

(initranfs)

After this point I don't know what to do.  I've looked at the list of commands & tried a few but nothing happens.  I've tried using recovery mode and following the options there but they don't seem to help.
I've reloaded with previous ubuntu, I get to the login screen and the mouse and keyboard don't work.

Any one got any advise to help?

---

### Post by Cybie257 on 2009-04-27
There is a fix for this. I had the same problem. If I remember correctly, the kernel had to be re-installed. I am looking for the like and will post it asap. Don't give up. It *IS* fixable. :)

-Cybie

---

### Post by Cybie257 on 2009-04-27
Ok, had a problem finding a link with the answer. When I had done an update, there was a Kernel problem. I had to drop back to the older kernal and run the install command for the latest kernel. You will find that line of code within this link, along with other information. You might need to use the livecd if there are no older kernel options for you to use in your grub boot up, but here's a start. 

[http://ubuntuforums.org/showthread.php?t=1120858](http://ubuntuforums.org/showthread.php?t=1120858)

-Cybie

---

### Post by ghonz on 2009-04-27
Thanks for the swift reply:) I'll try it this evening

---

