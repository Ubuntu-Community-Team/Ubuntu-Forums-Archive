---
title: "Partition Trouble"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by davkasayres on 2007-07-12
Hi all,

My drive is partitioned into 2 parts. 

60gb - Linux
60gb - Used to have vista on.

Ive supposedly sorted the old windows part out by using fdisk /dev/hda and i changed the type to linux too. But when ever i try and mount it i get:

raven@AMD2100:~$ sudo mount /dev/hda1 /mnt/win/
Password:
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

i dont understand. This is what is in my fstab:

  GNU nano 2.0.2              File: /etc/fstab                                  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=89aea73e-b9d8-45fe-aef7-e18977167aa0 /               ext3    defaults,erro$
# /dev/hda1
UUID=302898082897CB6C /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=4$
# /dev/hda2
UUID=20365dad-52f2-41c3-a0b0-4fa8dc56c2b2 none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,auto     0       0

Im stumped, as im pretty new to linux (about 6 months).

Can anyone help me please.

---

### Post by merlinus on 2007-07-12
From what I can see, /etc/fstab is still referencing hda1:

# /dev/hda1
UUID=302898082897CB6C /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=4$

so that is part of the problem, since it is no longer ntfs.

Also, with the reformat, the UUID may have changed.

What is the output of:

```

sudo fdisk -l
blkid

```

-merlin

---

