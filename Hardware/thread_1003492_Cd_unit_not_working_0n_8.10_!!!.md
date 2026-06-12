---
title: "Cd unit not working 0n 8.10 !!!"
date: 2008-12-06
forum: Hardware
---

### Post by miche11 on 2008-12-06
Hi, 
i can't really give up... it's a month these configuration go on...
and now, as i inserted a cd on my drive (combo drive on an acer aspire 3023), it can't be read.
fine, dvds works, as well dvd r and rw, but as soon as i give a cd, audio or data, it won't even be read !!!
something for you:
```
miche@3023:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=46cfab58-e9ab-4096-b840-7ef75f6fe905 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/hda5
UUID=fd4b9eeb-72ed-4484-a237-099b994eb16a /home           ext3    defaults,relatime  0       2
# /dev/hda1
UUID=A0989D92989D6814 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda6
UUID=4737-3E63  /windows        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=1d49f986-303e-434e-bc94-a056dfa7a861 none            swap    sw              0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto 0       0

```

and

```
miche@3023:~$ dmesg | tail
[44701.190819] Buffer I/O error on device sr0, logical block 5
[44701.190822] Buffer I/O error on device sr0, logical block 6
[44701.190825] Buffer I/O error on device sr0, logical block 7
[44701.216475] end_request: I/O error, dev sr0, sector 0
[44701.216489] Buffer I/O error on device sr0, logical block 0
[44701.216494] Buffer I/O error on device sr0, logical block 1
[44789.913461] end_request: I/O error, dev sr0, sector 64
[44789.913504] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[44935.844861] ISO 9660 Extensions: Microsoft Joliet Level 3
[44935.938878] ISOFS: changing to secondary root

```

i tried to mount it normally, but a strange number 11 came out:

```
miche@3023:~$ ls -l /dev/scd*
brw-rw----+ 1 root cdrom 11, 0 2008-11-29 02:08 /dev/scd0

```

please help !!!

---

### Post by miche11 on 2008-12-06
edit: audio cds are opened and played by VLC, but the system doesn't recognize any CD "insertion"

help !!!

---

### Post by LeakyInkPen on 2009-02-18
I am having this problem as well, Not very sure where to start

kubuntu 8.10

---

