---
title: "Old 240mb HD shows as 2TB, any way to set manually?"
date: 2011-03-26
forum: Hardware
---

### Post by jimbojones on 2011-03-26
I have an old 240MB Quantum ProDrive LPS HD.  I plugged it in to make a dd copy of the disk for a backup as it contains some sensitive information.  The filesystem is not in a format that Ubuntu recognizes, so I can not mount it, but really I was just looking to make a raw copy of the whole disk.  The disk is 240 MB (723 cylinders, 13 heads, 51 sectors), is there anyway I can set this manually?  If i try to dd the disk it just keeps going well past 240MB.  Any pointers would be greatly appreciated.  :)

Here's what fdisk & lshw are showing

> 

root@ubuntu:~# fdisk -l

...

Disk /dev/sdc: 2199.0 GB, 2199023255552 bytes
255 heads, 63 sectors/track, 267349 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffe1ffe1

Disk /dev/sdc doesn't contain a valid partition table



root@ubuntu:~# lshw -C disk
&#8230;

  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@7:0.0.0
       logical name: /dev/sdc
       size: 2TiB (2199GB)



---

