---
title: "[SOLVED] Mounting an Olympus Digital Recorder DS 2300"
date: 2007-09-29
forum: Hardware &amp; Laptops
---

### Post by Robbyx on 2007-09-29
I need help on this:

As it is a removable usb device I thought it best to use the uuid or label. However it does not show up as a device in either of the following two commands:

```
robin@robin-desktop:~$ ls /dev/disk/by-label -lah
total 0
drwxr-xr-x 2 root root 120 2007-09-29 09:58 .
drwxr-xr-x 6 root root 120 2007-09-29 09:58 ..
lrwxrwxrwx 1 root root  10 2007-09-29 09:58 F:_My_docs___Pics_disk_1 -> ../../hdb5
lrwxrwxrwx 1 root root  10 2007-09-29 09:58 G:_Downloads_disk_1 -> ../../hdb6
lrwxrwxrwx 1 root root  10 2007-09-29 09:58 H:_disk_1 -> ../../hdb7
lrwxrwxrwx 1 root root  10 2007-09-29 09:58 NEW_VOLUME -> ../../hdb1

robin@robin-desktop:~$ ls /dev/disk/by-uuid -lah
total 0
drwxr-xr-x 2 root root 220 2007-09-29 09:58 .
drwxr-xr-x 6 root root 120 2007-09-29 09:58 ..
lrwxrwxrwx 1 root root  10 2007-09-29 09:58 107E-9F7D -> ../../hdb1
lrwxrwxrwx 1 root root  10 2007-09-29 09:58 15F8E6F16E4354F3 -> ../../hdd5
lrwxrwxrwx 1 root root  10 2007-09-29 09:58 221d448e-c456-4e67-b1f4-675a654e16c8 -> ../../hda1
lrwxrwxrwx 1 root root  10 2007-09-29 09:58 26b10955-df89-4b53-ace4-e4b4e8afa042 -> ../../hdb3
lrwxrwxrwx 1 root root  10 2007-09-29 09:58 2C7049D57049A684 -> ../../hdb7
lrwxrwxrwx 1 root root  10 2007-09-29 09:58 44DC3E21DC3E0E24 -> ../../hdb5
lrwxrwxrwx 1 root root  10 2007-09-29 09:58 5abbef3f-03f4-4927-868f-93ec33fe1a6f -> ../../hda5
lrwxrwxrwx 1 root root  10 2007-09-29 09:58 7E0442D704429257 -> ../../hdb6
lrwxrwxrwx 1 root root  10 2007-09-29 09:58 ECACA26CACA230CE -> ../../hdd1


```

sdb1 does show in the following:

```
robin@robin-desktop:~$ ls /dev/disk/by-id -lah
total 0
drwxr-xr-x 2 root root 380 2007-09-29 15:47 .
drwxr-xr-x 6 root root 120 2007-09-29 09:58 ..
lrwxrwxrwx 1 root root   9 2007-09-29 09:58 ata-ExcelStor_Technology_J340_VNVB17E20SSTUA -> ../../hdb
lrwxrwxrwx 1 root root  10 2007-09-29 09:58 ata-ExcelStor_Technology_J340_VNVB17E20SSTUA-part1 -> ../../hdb1

....
lrwxrwxrwx 1 root root   9 2007-09-29 15:47 usb-OLYMPUS_DVR-0:0 -> ../../sdb
lrwxrwxrwx 1 root root  10 2007-09-29 15:47 usb-OLYMPUS_DVR-0:0-part1 -> ../../sdb1

```

1. Does anyone know how  I ensure that the recorder gets a label or a uuid?

2. How do I mount it? It is not clear to me from the searches I have made.

3. Sudo fdisk -l shows the device as attached  with a system FAT12. Will ubuntu be able to read it?

4. Is there a group somewhere that deals with removable devices?

I hope someone will be able to help me get this recorder working.


Robin

---

### Post by Robbyx on 2007-09-30
Is there more information I need to post to get an answer to this query? I would like a response please.

---

### Post by Robbyx on 2007-09-30
Delighted to say i have it working.

---

