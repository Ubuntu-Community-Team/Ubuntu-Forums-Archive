---
title: "howto mount external usb hard drive when you don't know what it is"
date: 2009-05-03
forum: Hardware
---

### Post by Preserved Killick on 2009-05-03
Hi.  I hope you can help me figure this out.

I'm running Hardy Heron Ubuntu 8.04.  I have used this system to mount an ntfs-3g drive that was attached via USB in an external drive case.

I have put a different hard drive into this same case and it doesn't mount.

gparted shows my two internal drives, sda and sdb, but not the external drive.
lsusb reveals my USB card reader and USB mouse, but not the external.
fsdisk -l reported: 
workstation:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00081d81

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29645   238123431   83  Linux
/dev/sda2           29646       30401     6072570    5  Extended
/dev/sda5           29646       30401     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00003efc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401   83  Linux


No icon popped up on my desktop.

I suspect this external drive is ext3, but it might be reiserfs or even ntfs-3g.  The only reason I want to mount it is so that I can wipe it clean and start using it.  I'm not worried about preserving what is on the disk.

I plugged this same external drive into my Windows XP machine and it never 'saw' it either.  

I could try to use the mount command but what /dev name would I use?

Suggestions are welcome!  Thank you,

killick

---

### Post by mikedep333 on 2009-05-03
> **Preserved Killick said:**
> 
I plugged this same external drive into my Windows XP machine and it never 'saw' it either.  


If your Windows XP machine won't see it either, it likely has a hardware problem.

You can check to see if windows sees the device by:
-right clicking on my computer
-manage
-disk management

---

### Post by Preserved Killick on 2009-05-03
Thanks mikedep.  I can't get windows to see it either so it's probably borked.  

pk

---

### Post by mikedep333 on 2009-05-04
Oh well, best of luck. I hope it is under warranty, so you can do an RMA.
I also hope you didn't have valuable data on it.

---

