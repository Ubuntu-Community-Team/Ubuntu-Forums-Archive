---
title: "Reiserfs checked okay but volume not mountable"
date: 2008-08-22
forum: General Help
---

### Post by ubunteduser on 2008-08-22
I have a lvm volume with reiser filesystem. 

I had to recover it and rebuild superblock.

Reiserfsck indicates everything is okay, but I cannot mount.

Before recovery /lib/udev/vol_id /dev/mapper/home-myhome produced nothing, 
but now I get volume information.

root@sheridan:/mnt/foreign/home# mount -t reiserfs /dev/mapper/home-myhome /mnt/foreign/home/myhome
mount: wrong fs type, bad option, bad superblock on /dev/mapper/home-myhome, missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

> dmesg | tail gives this:

[ 2544.243981] ReiserFS: dm-2: found reiserfs format "3.6" with standard journal
[ 2544.243995] ReiserFS: dm-2: using ordered data mode
[ 2544.247326] ReiserFS: dm-2: journal params: device dm-2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[ 2544.247632] ReiserFS: dm-2: checking transaction log (dm-2)
[ 2544.267671] ReiserFS: dm-2: warning: vs-7000: search_by_entry_key: search_by_key returned item position == 0

Anyone know what I am doing wrong?

---

### Post by ubunteduser on 2008-08-22
Does it matter that I brought the hardisk in from a 64-bit system into a 32-bit system.

---

### Post by spiderbatdad on 2008-08-22
Dunno. I was reading the man pages trying to find some help for you. There is information on mounting/remounting  options for reiserfs, and a link to more information, but the site is down. There is also a link to a utility for resizing. I'm thinking try the -a -f options, or the detect option. Maybe a look at your fstab would help.

---

### Post by ubunteduser on 2008-08-23
It is a foreign mount -- from some other computer since I am trying to recover the information. There is no fstab.

I know the data is still intact. From the reiserfsck  you can see it rebuild the index listing the directories very quickly.

Thanks.

---

