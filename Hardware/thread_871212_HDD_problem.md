---
title: "HDD problem"
date: 2008-07-26
forum: Hardware
---

### Post by entereczek on 2008-07-26
Hi,

I've got a problem with my harddisk. After last reboot my system hangs with kernel panic about xfs problems. I tried accessing my xfs partitions using live cd but I get:
```
[ 2567.872000] hda: drive not ready for command
[ 2567.888000] hda: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
[ 2567.888000] hda: status error: error=0x40 { UncorrectableError }, LBAsect=23695938, high=1, low=6918722, sector=23695938
[ 2567.888000] ide: failed opcode was: unknown
[ 2567.888000] end_request: I/O error, dev hda, sector 23695938
[ 2567.888000] hda: drive not ready for command
[ 2567.892000] hda: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
[ 2567.892000] hda: status error: error=0x40 { UncorrectableError }, LBAsect=23695938, high=1, low=6918722, sector=23695942
[ 2567.892000] ide: failed opcode was: unknown
[ 2567.892000] end_request: I/O error, dev hda, sector 23695942
[ 2567.892000] hda: drive not ready for command
[ 2567.928000] hda: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
[ 2567.928000] hda: status error: error=0x40 { UncorrectableError }, LBAsect=23695938, high=1, low=6918722, sector=0
[ 2567.928000] ide: failed opcode was: 0xea
[ 2567.928000] hda: drive not ready for command
[ 2567.928000] hda: wcache flush failed!

```
The weirdest thing is that I can boot that disk and in command line grub after trying:
>root (hd0,[press TAB]
I get list of 3 first paritions and instead of last 3 I get: ```
Error 18: Selected cylinder exceeds maximum supported by BIOS
```
I tried >root (hd0,5) which was my home directory and I didn't get any errors. So i tried: 
>kernel /myusername/[TAB]
and I got list of my dirs&files. I can list files and dirs from that partition using grub, but I can't do it using live cd.
So I deeply investigated it using livecd:
```
>fdisk -l /dev/hda
>ls /dev/hda*
/dev/hda  /dev/hda1  /dev/hda2  /dev/hda3  /dev/hda4  /dev/hda5  /dev/hda6
>xfs_admin -l /dev/hda5
xfs_admin: /dev/hda1 is invalid (cannot read first 512 bytes)
>dd if=/dev/hda of=temp
dd: reading `/dev/hda': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.0301734 seconds, 0.0 kB/s
>dd if=/dev/hda5 of=temp
dd: reading `/dev/hda5': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.0619014 seconds, 0.0 kB/s


```

and in dmesg I get lots of errors as above.
So, fdisk doesn't see any partitions but block devices are good.
I get in&out error in linux, but grub can access that xfs partition.
So here is the deal:
1. Is there any chance of forcing linux to get access to this drive?
2. Is there any way of getting a mirror clone of this drive so I can try for example replacing first 512 bytes from another xfs partition or any other way without disturbing the orginal one?
3. Is there any way of cloning content of this xfs in grub-level or use grub-implementation of xfs client to get access to this data?
4. Is there any other working way of getting access to my data?

PS: I almost forgot, I tried connecting this HDD to PC running M$ Win and when I accessed partition manager in computer management it hang :P

---

### Post by logos34 on 2008-07-26
> **entereczek said:**
> 
[/code]The weirdest thing is that I can boot that disk and in command line grub after trying:

...but grub can access that xfs partition.


I didn't know you could boot from an xfs partition using grub.  I've always heard that if you're using xfs for / to make a separate ext2 /boot.

---

### Post by cariboo on 2008-07-26
I'd go to your hard drives manufacturers web site and download thier diagnostic tools and check the drive it could be going bad.

Jim

---

### Post by entereczek on 2008-07-27
Hey,

Case is closed. HDD is no longer recognized by BIOS so I can't do anything ;p

Regards,
Entereczek

---

