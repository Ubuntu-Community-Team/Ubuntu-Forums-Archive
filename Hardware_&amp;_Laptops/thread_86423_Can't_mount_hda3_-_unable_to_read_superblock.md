---
title: "Can't mount hda3 - unable to read superblock?"
date: 2005-11-05
forum: Hardware &amp; Laptops
---

### Post by Beej on 2005-11-05
I managed to break my breezy installation the other day and had to reinstall. I previously had my home folder mounted as a seperate partition. I now want to remount hda3 as my home folder. So I did the following

mkdir /mnt/home
mount -t ext3 /dev/hda3 /mnt/home

I then get the following message

mount: wrong fs type, bad option, bad superblock on /dev/hda3,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg | tail dives the following output,

cs: IO port probe 0x0c00-0x0cf7: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
longhaul: VIA C3 'Nehemiah C' [C5N] CPU detected.  Powersaver supported.
eth0: no IPv6 routers present
attempt to access beyond end of device
hda3: rw=0, want=4, limit=2
EXT3-fs: unable to read superblock
attempt to access beyond end of device
hda3: rw=0, want=4, limit=2
EXT3-fs: unable to read superblock

Can anybody help? I have alot of mp3's on this partition!

Ta,

Beej

---

### Post by poptones on 2005-11-05
Did you change any other partitions when you reinstalled? Maybe add a partition or remove one?

do "sudo fdisk" and hit "p" (for print), then q (quit).

Are you certain it was formatted ext3 and not something like reiser? It wasn't encrypted?

---

### Post by Beej on 2005-11-05
When I reinstalled I deleted the swap and bootable partitions and got the partition manager to install on the frr space.

Output from  fdisk for /dev/hda follows:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1            1218        7296    48829567+  83  Linux
/dev/hda2   *           1        1163     9341766   83  Linux
/dev/hda3            1164        1217      433755    5  Extended
/dev/hda5            1164        1217      433723+  82  Linux swap / Solaris

Partition table entries are not in disk order

The partition for my home folder was about 50GB, so from looking at the table I'm assuming that the partion manager has renamed the partions, naming the existing partion (my home folder) hda1?

So mounting hda1 as home rather than hda3 should do the trick? (just want to double check my understanding). 

Thanks,

 Beej

---

### Post by poptones on 2005-11-05
Yep, that's the ticket.

If you have more than three partitions they can get renamed.

---

