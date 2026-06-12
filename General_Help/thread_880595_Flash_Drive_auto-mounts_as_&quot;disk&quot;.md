---
title: "Flash Drive auto-mounts as &quot;disk&quot;"
date: 2008-08-05
forum: General Help
---

### Post by Altay_H on 2008-08-05
I noticed that when I plug my flash drive in, Ubuntu auto-mounts its first partition as "disk" and its second one as "disk-1". I find this behaviour rather obnoxious and would much prefer it to mount them as "sda0" and "sda1", but I don't see any auto-mounting options. Is there a way to change this? Thanks.

---

### Post by ibuclaw on 2008-08-05
I think changing/giving the USB drive partition a Label should fix it.

[Read this howto here.]("https://help.ubuntu.com/community/RenameUSBDrive")

Regards
Iain

---

### Post by prshah on 2008-08-05
> **Altay_H said:**
> 
 would much prefer it to mount them as "sda0" and "sda1", but I don't see any auto-mounting options.

You can continue to refer to them as /dev/sdx0 and /dev/sdx1 if you like (sdx being your pendrive's device id, as reported in dmesg after plugging in the pen), instead of disk-1 and disk-0. btw, if you manually mount them, you can mount them into any directory name you like.

You can try blanking out the volume name for each partition on the pen drive.

I don't believe changing the volume name as suggested by the previous poster will work; you can rename the partitions to sda0 and sda1 (volume name only); but when it is mounted in /media, but if the sda1 and sda0 mountpoints already exist, it will end up being named as sda0_ and sda1_.

---

### Post by Altay_H on 2008-08-06
I was looking for a more permanent solution, so that whenever I plug a USB drive into my computer it will be automounted as sdx, rather than disk. One reason is that I'm using Conky and would like to display the remaining capacity of the drive. When I try to use /dev/sdb via the following code:
```
sdb:  ${fs_free_perc /dev/sdb}%   ${fs_bar 6 /dev/sdb}
```
It shows up as 99% free, despite the fact that it's only 44% free. Perhaps I made a mistake in the code I put in Conky. Whether or not I did, I'd still much prefer it mounts to /media/sdx than /media/disk.

What program does Ubuntu use to automount drives? Isn't there some way to configure it via the Terminal? Thanks for your help.

---

