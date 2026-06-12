---
title: "Formatting 32GB shdc (sd4) to a linux format??? check out this crazyness"
date: 2009-04-14
forum: Hardware
---

### Post by dragonneus on 2009-04-14
Using a asus eee 1000 
2 gb ram 
Upgraded to Jaunty 9.04

I recently purchased a kingston 32 gb sdhc (sd4) card, Immediately after placing this card into my sdhc card slot I tried to partition/format this card ext2,ext3,ext4 all fail and wont format. Using my girlfriends windows pc, I was able to use the quick format function. Placing this card back into my ubuntu laptop I read the following odd partition table, but it seems to work.

Disk /dev/sdc: 33.5 GB, 33553907712 bytes
64 heads, 32 sectors/track, 31999 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?      379950      937327   570754815+  72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?       82368     1027695   968014120   65  Novell Netware 386
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?      913029     1858355   968014096   79  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?     1409025     1409052       27749+   d  Unknown
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


The help I need is to format this to a linux type format, I dont really want to use fat32.

Using plain ol fdisk it partitions but the command of mkfs fails. I tried gparted and get the following results in a log.
GParted 0.4.3

Libparted 1.8.8
Delete /dev/sdc1 (unknown, 31.25 GiB) from /dev/sdc  00:00:10    ( SUCCESS )
     	
calibrate /dev/sdc1  00:00:00    ( SUCCESS )
     	
path: /dev/sdc1
start: 32
end: 65533951
size: 65533920 (31.25 GiB)
delete partition  00:00:10    ( SUCCESS )

========================================
Create Primary Partition #1 (ext4, 31.25 GiB) on /dev/sdc  00:00:58    ( ERROR )
     	
calibrate New Partition #1  00:00:00    ( SUCCESS )
     	
path: /dev/sdc-1
start: 0
end: 65534975
size: 65534976 (31.25 GiB)
create empty partition  00:00:11    ( SUCCESS )
     	
path: /dev/sdc1
start: 63
end: 65529134
size: 65529072 (31.25 GiB)
set partition type on /dev/sdc1  00:00:11    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:00:36    ( ERROR )
     	
mkfs.ext4 -j -O extent -L "" /dev/sdc1
     	
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
2048000 inodes, 8191134 blocks
409556 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
250 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
4096000, 7962624

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 27 mounts or
180 days, whichever comes first. Use tune2fs -c or -i to override.
mke2fs 1.41.4 (27-Jan-2009)

Warning, had trouble writing out superblocks.

========================================

any help or insigt would be greatly appreciated.

Thank you for your time,

Dragonneus.


UPDATE

upon reinserting the card back into the windows pc with data on it, it ask for a reformat everytime.

---

### Post by ahbart on 2009-04-14
> **dragonneus said:**
> UPDATE
upon reinserting the card back into the windows pc with data on it, it ask for a reformat everytime.
As far as I know windows, that is a normal windows reaction on non-windows filesystems on removable media like this sdhc card. Primitive isn't it.

It sounds like a wrong sd card. I've never had trouble like this. Have you tried the website of kingston? Don't they have a forum or online support system?

---

### Post by tgalati4 on 2009-04-14
Because of the large size of the disk, you may have scrambled the cylinders, heads, and secttors count.  You need to find the factory counts and reformat.

I had this happen to me using a 4 gb sd card.  I was able to recover using the appropriate switches (which are not handy since l'm using an n800).   My  guess is the csrd's controller expects a given CHS count.  The ubuntu disk tools seem to make up a suitable count--but one that doesn't work.

---

### Post by dragonneus on 2009-04-14
Its odd,It formats fine in windows , then I try to use it by transferring files on my ubuntu pc and back, works a few times then windows asks to format the drive and ubuntu sees no valid partition. The card came to me originally as you see above labled with novel netgear partition???? Thats wwhat it comes up with too when I do the quick format in windblows.

---

### Post by ahbart on 2009-04-14
Does Kingston no have there own low format tool.

---

### Post by dragonneus on 2009-04-14
well I fouund a factory reformat tool, Ill give that a try and report back.

---

### Post by Carthorse on 2010-04-17
I'd be interested in any follow-ups, too. I'm having a similar problem. My 32gb generic SD card will format to ext2 (and of course, FAT16/32/vfat) no probs but won't format to a journalling file system, such as ext3/4. gparted seems to format it ok but then it won't mount, with an error 'invalid file type or bad super-block' etc. It would be handy to know what's going wrong before I throw more money at another card or card reader.

---

### Post by mhampson on 2010-07-30
> **Carthorse said:**
> My 32gb generic SD card will format to ext2 no probs but won't format to a journalling file system, such as ext3/4. gparted seems to format it ok but then it won't mount...

Exact same situation here, using laptop's own card reader *and* using external USB card reader. Any explanation?

---

