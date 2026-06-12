---
title: "Ubuntu 8.10 64 bit installed but could no boot, grub was no installed."
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by sunnyDev on 2009-01-23
I tried several times to install Ubuntu_8.10_desktop_amd64 on My laptop ( dual intel(R) Core(TM) Duo 2.2Ghz cpus). I have another two existing system : 1) ubuntu 8.04.1 32 bit 2) windows xp. and grub was installed. 

I download the .iso file from Ubuntu official website, tried the live CD, made integrity check, it all worked well. I then installed the system to a new partition, the installation gave no error. But when I restart the computer, I could not boot Ubuntu 8.10, either no grub could be found or the old grub was shown (after I manually install grub) . There was no entry added by the installer, nor /grub/ folder under /boot/ folder on the partition of the new installation. 

I'm a bit desperate now, but still with the hope of 64bit power. Any hints are welcome, Thanks a lot in advance!

---

### Post by Pumalite on 2009-01-23
Install Grub to it's own partition and later edit menu.lst of original Grub to add the new entry.
Or try to reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by sunnyDev on 2009-01-24
Thanks a lot for Pumalite's reply.

Following this advice to I tried to install grub in the partition of Ubuntu 8.10 64 bit, but still failed. I got: "Could not find device for /boot: Not found or not a block device."

After some search, I found another post, the problem described is quite similar to mine:

[http://ubuntuforums.org/showthread.php?p=6606912](http://ubuntuforums.org/showthread.php?p=6606912)

---

