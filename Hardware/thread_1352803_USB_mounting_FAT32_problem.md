---
title: "USB mounting FAT32 problem"
date: 2009-12-12
forum: Hardware
---

### Post by aero528 on 2009-12-12
I've had Ubuntu on my IBM X31 laptop for quite a while now.  Its been going great, and I just upgraded to 9.10.  This has gotten me thinking how I can fix some of the little problems I've been having.  A couple distros back(I think 7.04) I messed with something relating to the USB.  Now When I plug my hard drive in(Two partitions, one is NTFS, and the other is FAT32), the NTFS mounts just fine, but it never mounts the FAT32 partition.  This also comes up in an error message(STORAGE is the name of the partiton, btw), 

Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I go to terminal and type, 

sudo mount -t vfat /dev/sdb1 /mnt/usb

This mounts it just fine, and its all dandy from there on, until I restart the computer, then I have to do it all over again.  I have to do this whenever I plug in any FAT32 device, BTW.  Do you guys have any idea what I might of done, and how I can correct it?  I can't remember for the life of me what I did.  Any and all help is greatly appreciated!

---

### Post by aero528 on 2009-12-14
No one has any suggestions?

---

### Post by Chesamo on 2009-12-14
Post the output of dmesg | tail after the failed mount.

---

### Post by srfito on 2009-12-16
I have a similar problem (see [http://ubuntuforums.org/showthread.php?p=8499544#post8499544](http://ubuntuforums.org/showthread.php?p=8499544#post8499544))

This is my output to dmesg | tail:

[  137.970741] sd 3:0:0:0: [sdf] Write Protect is off
[  137.970744] sd 3:0:0:0: [sdf] Mode Sense: 23 00 00 00
[  137.970747] sd 3:0:0:0: [sdf] Assuming drive cache: write through
[  137.987580] sd 3:0:0:0: [sdf] 62734336 512-byte hardware sectors: (32.1 GB/29.9 GiB)
[  137.988464] sd 3:0:0:0: [sdf] Write Protect is off
[  137.988468] sd 3:0:0:0: [sdf] Mode Sense: 23 00 00 00
[  137.988471] sd 3:0:0:0: [sdf] Assuming drive cache: write through
[  137.988476]  sdf: sdf1
[  138.210280] sd 3:0:0:0: [sdf] Attached SCSI removable disk
[  138.210357] sd 3:0:0:0: Attached scsi generic sg6 type 0

Thanks very much.

---

### Post by srfito on 2009-12-16
I found the solution just after writing my previous post:

1. I manually mounted the usb key (via terminal)
2. I right-clicked on the icon on the desktop and went to the drive tab.
3. There I found the wrong options I had previously written.
4. I manually unmounted the usb key (via terminal)
5. I unplugged and replugged the usb key and it automounted perfectly, as before.

I hope this is useful for aero528.

---

### Post by aero528 on 2009-12-18
I will test this and post when I do, but this week i've been busy.  Thanks for the help.

---

