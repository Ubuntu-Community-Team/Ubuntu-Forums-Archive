---
title: "external hd goes crazy/inaccessible after gparted repartitioning?"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Bjoern on 2009-10-29
Hello,

some weird problems with my external hd (Western Digital My Passport, 160GB): it was formatted with NFTS, I tried to resize that partition to 30GB, rename it, and create an ext3 partition for the remaining space.

3 operations with gparted. After a while gparted said the operations where done, even though the LED on the external hd was still blinking. Since quite some time had passed, I decided to reboot the computer, hoping any pending operations would be executed before shutting down.

Since then, the hd can not be accessed (starting gparted or cfdisk just hangs, and it doesn't show up in the file system). As soon as the hd is connected, it's LED starts blinking like crazy. 

I tried to overwrite the whole disk with zeros using dd, but after 8 hours quit the process - only 3GB had been written. I suspect that it was slowed down by the other process that makes the LED blink, as the computer is supposed to have an USB 2.0 port.

Any ideas on how to make the hd usable again, and what is causing the blinking? My only guess is that it could be a process that constantly tries to mount the hd and fails, as otherwise no process should have a reason to access the hd.

Thanks!

Björn

---

### Post by Lord Landis on 2009-10-29
It sounds like the partition table got jacked.  My guess is that even though gparted said it was done, the disk was still working, so when you shut the system down, things got borked.

My best advice is to plug the disk in, figure out which /dev/sd it is (probably /dev/sdb unless you have multiple disks), and use fdisk to completely redo it as a single Fat32 volume.  By going so you'll be able to use it in both environments.

---

### Post by Bjoern on 2009-10-31
Hi,

thanks, but fdisk also hangs. Any other way?

Björn

---

