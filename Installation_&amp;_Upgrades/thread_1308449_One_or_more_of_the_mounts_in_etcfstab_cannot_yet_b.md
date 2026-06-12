---
title: "One or more of the mounts in /etc/fstab cannot yet be mounted"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Gitykins on 2009-10-31
I get this when booting up from any kernel from GRUB after updating from Jaunty to Karmic from the update manager.

/dev/disk, /dev/sdaX, and /dev/sdbX are all missing on the Karmic partition, and fstab gives a UDID for the / partition which is supposed to be in /dev/disk/by-uuid, but is not there since /dev/disk does not exist.

I've had this system since Hoary Hedgehog and this is really pissing me off that I have always had to salvage my system after a supposedly stable upgrade. Literally every upgrade I've ever done has ****** up and I consider myself pretty good with linux, and there is usually no support for widespread errors like this. I have seen 20+ threads with this problem and almost none of them have actually been solved.

---

### Post by Wednesday on 2010-04-05
I have just had a similar problem when upgrading to Karmic. When starting after the upgrade I get the message:One or more of the mounts in /etc/fstab cannot yet me mounted: swap : waiting for UUID= (here is the number for my swap file).

I did a bit of digging and found that during the upgrade the ID of my swapfile became changed. So I used the command 
sudo blkid to find the current UUID of my swapfile and then edited fstab. It all works.

---

