---
title: "Unable to mount /dev/hda"
date: 2005-06-01
forum: Hardware &amp; Laptops
---

### Post by Buelldozer on 2005-06-01
Okay, so my system has two drives in it. Primary drive (hda) is the windows drive (Win XP SP2, NTFS) the secondary drive (hdb) has Ubuntu installed.

Ubuntu boots okay but whenever I try and mount my windows drive I get this error message : special device hda1 does not exist.

fdisk -l reports that /dev/hda1 DOES exist but oddly it says that it is filetype SFS.

Any thoughts on what to try?

My apologies if this is a rehash question, but I did several searches and didn't find anything that matched what I'm up against.

---

### Post by jkndrkn on 2005-06-02
Try this:

[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

### Post by stizzco@gmail.com on 2006-06-08
I am having a similar issue, only its hdb giving me the greif.

```
Disk /dev/hda: 15.3 GB, 15307407360 bytes
255 heads, 63 sectors/track, 1861 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1815    14578956   83  Linux
/dev/hda2            1816        1861      369495    5  Extended
/dev/hda5            1816        1861      369463+  82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14593   117218241   42  SFS
Note: sector size is 2048 (not 512)

Disk /dev/hdc: 452 MB, 452603904 bytes
255 heads, 63 sectors/track, 13 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes

Disk /dev/hdc doesn't contain a valid partition table
root@ubuntu:~# mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I manually edited the partition table after diskmounter failed.

I know that the drive exists, as does the partition. I can only hope that my 120GB's of data remain intact. I'm doing this all through the command line since I installed the server version. I'm essentially trying to replace w2k server with ubuntu server on my samba fileserver.

WTF is a SFS? It is suppose to be Fat32.

Help!

---

