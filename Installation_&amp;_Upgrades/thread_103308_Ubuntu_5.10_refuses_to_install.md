---
title: "Ubuntu 5.10 refuses to install"
date: 2005-12-13
forum: Installation &amp; Upgrades
---

### Post by minet on 2005-12-13
Despite several attempts I found it impossible to install Ubuntu 5.10.

It seems due to a bug in either the install program itself or the parting
software. It goes into an infinite circle, refusing to go past the partitioning.

I have several SuSE versions installed as well as Fedora Core 4,
windows XP French Canadian and PC Dos.

I have two 50G partitions in Reiserfs and 2 partitions in ext2 that
I can use. One pair on disk2 and one pair on disk3.
The partitioning programs gives some ridiculous message saying that
there is an error in the ext2 partitions.
Seeing that I figured that it may be stupid enough to want to reformat
a perfectly well formatted partition so I allowed it to. It then give me
an error on the other ext2 partition where it has no business even looking
at them as I mark them to be ignored.
The basic menu starts with all of the partition to be mounted as
for example /media/hdc2 /media/hda2
On my first attempt it was giving me an error on one of the ext2 partitions
on the first drive so I told it not to use it. I did the same with all the
other partitions that I don't want the install to touch.
Since that failed I thought that it may be so buggy as not being able
to use Reiserfs so I allowed it to reformat the 50G partition on the
second drive as ext3 despite the fact that I don't like the idea.
It still didn't work. After several hours of different attempts I gave up.

Can someone explain to me what could be the problem with that
buggy installer? What is the name of the script that does those
ridiculous decisions? Perhaps there could be a way to completely
bypass the partitioning bullshit since I don't want it to mess with the
partitions anyhow.

My PC is an AMD64 with close to 400G of IDE hard disk space.
I have installations of 32 bits and 64 bits Linux versions.

I have tried to install both 32 bits and 64 bits versions of Ubuntu.

---

### Post by minet on 2005-12-14
[QUOTE=minet]Despite several attempts I found it impossible to install Ubuntu 5.10.

It seems due to a bug in either the install program itself or the parting
software. It goes into an infinite circle, refusing to go past the partitioning.

I have several SuSE versions installed as well as Fedora Core 4,
windows XP French Canadian and PC Dos.

I have two 50G partitions in Reiserfs and 2 partitions in ext2 that
I can use. One pair on disk2 and one pair on disk3.
The partitioning programs gives some ridiculous message saying that
there is an error in the ext2 partitions.
Seeing that I figured that it may be stupid enough to want to reformat
a perfectly well formatted partition so I allowed it to. It then give me
an error on the other ext2 partition where it has no business even looking
at them as I mark them to be ignored.
The basic menu starts with all of the partition to be mounted as
for example /media/hdc2 /media/hda2
On my first attempt it was giving me an error on one of the ext2 partitions
on the first drive so I told it not to use it. I did the same with all the
other partitions that I don't want the install to touch.
Since that failed I thought that it may be so buggy as not being able
to use Reiserfs so I allowed it to reformat the 50G partition on the
second drive as ext3 despite the fact that I don't like the idea.
It still didn't work. After several hours of different attempts I gave up.

Can someone explain to me what could be the problem with that
buggy installer? What is the name of the script that does those
ridiculous decisions? Perhaps there could be a way to completely
bypass the partitioning bullshit since I don't want it to mess with the
partitions anyhow.

My PC is an AMD64 with close to 400G of IDE hard disk space.
I have installations of 32 bits and 64 bits Linux versions.

I have tried to install both 32 bits and 64 bits versions of Ubuntu.[/QUOTE]



To complement the information on my PC, here is the map of the hard disks 

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           1        8001   78  Unknown
/dev/hda2               2         261     2088450    6  FAT16
/dev/hda3             262       24321   193261950    f  W95 Ext'd (LBA)
/dev/hda5             262         266       40131   83  Linux
/dev/hda6   *         267         271       40131   83  Linux
/dev/hda7             272         398     1020096   82  Linux swap / Solaris
/dev/hda8             399       10597    81923436   83  Linux
/dev/hda9           10598       24321   110237998+  83  Linux


Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         795     6385806    7  HPFS/NTFS
/dev/hdb2             796       14946   113667907+   f  W95 Ext'd (LBA)
/dev/hdb5             796         803       64228+  83  Linux
/dev/hdb6             804         811       64228+  83  Linux
/dev/hdb7             812         819       64228+  83  Linux
/dev/hdb8             820        4800    31977351   83  Linux
/dev/hdb9            4801        8800    32129968+  83  Linux
/dev/hdb10           8801       14946    49367713+  83  Linux

Disk /dev/hdc: 80.0 GB, 80026361856 bytes

255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1           1        8001   78  Unknown
/dev/hdc2               2         132     1052257+   6  FAT16
/dev/hdc3             133         387     2048287+   b  W95 FAT32
/dev/hdc4             388        9729    75039615    5  Extended
/dev/hdc5             388         393       48163+  83  Linux
/dev/hdc6             394        3000    20940696    c  W95 FAT32 (LBA)
/dev/hdc7            3001        9729    54050661   83  Linux



/dev/hda1 has the xols bootloader.

The /boot partitions I have tried are
/dev/hc5 and /dev/hdb7
The / partitions were
/dev/hdc7 and /dev/hdb10

The different operation systems are booted using the xols boot loader
and Grub is always installed on the small ext2 partitions.
It works beautifully with Fedora and SuSE.

I have a pc dos on the first and 3rd drive and windows XP on the second
drive. All boot with xols boot loader.

---

### Post by roelofs on 2005-12-28
I believe Ubuntu/Debian's partition manager is incapable of understanding "W95 Extended" partitions correctly.  In my case it couldn't see the logical partitions at all, despite Slackware 9 and Slackware 10 having no trouble.  This is just a hypothesis so far, however; I have not yet found anyone who's truly knowledgable about the Ubuntu partitioner (beyond the ntfsresize author's identification of it as "partman").

Still digging...

---

