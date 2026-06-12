---
title: "Formatting usb"
date: 2015-06-19
forum: Hardware
---

### Post by Quarkrad on 2015-06-19
Not strictly a Ubuntu question but hopefully you can help - running 14.04 64bit.  I have 4GB usb stick that gparted shows as dev/sdh 3.84GB and dev/sdi 2.00 MB - somehow this stick has a ridiculous 2.00mb partition on it.  I have deleted both partitions but when I create new partitions gparted still shows me have dev/a and dev/b.  Is it possible to have a single dev/x partition?

---

### Post by sudodus on 2015-06-19
That particular USB stick is probably hard-coded like that - it contains two mass storage devices, the normal big one, and that small one with 2 MB. Maybe you can find some information about the small device - what it is intended to do - from the manufacturer.

---

### Post by efflandt on 2015-06-19
See what **dmesg** says about the partitions after you plug it in. If it is something like a SanDisk Cruzer with U3, /dev/sdi may be a pseudo-cd with Windows security software, web search "sandisk cruzer u3 linux" to see about modifying or removing the U3 partition.

Then (or otherwise) try **gparted** (on live/install, but not installed by default on installed system) to create a new msdos partition table. Then you could create whatever partitions you want on it (typically FAT32 if also using it with Windows or for Ubuntu live/install iso). If that does not work (like if you had written a cd/dvd iso directly to it) you may need to dd some /dev/zero to the beginning of it so it appears to be fresh, and return to beginning of this paragraph. If the device is /dev/sdh, the first partition in that would be /dev/sdh1.

If you want to clear the flash to appear fresh (would not clear the U3 partition) assuming that **sudo fdisk -l** (small L) shows it as /dev/sdh, make sure any partitions on it are umount'd (see if mount shows /dev/sdh1 or anything) then do following before making new msdos partition table and partition(s):```
sudo dd bs=512K count=1 if=/dev/zero of=/dev/sdh
```

---

