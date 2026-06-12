---
title: "large ext HDD problem"
date: 2013-09-08
forum: Hardware
---

### Post by funked up on 2013-09-08
I've been through all kinds of forums for about a week now and I've found dozens of threats with similar problems but no one seems to have found a solution yet.

Problem:
I've been using my 3TB ext HDD for a couple of years now with absolutely no problem.
Since it was formated in FAT32 from the day I bought it and I couldn't use it with files bigger than 4GB, I've decided to format it in NTFS.
I wanted a one-partition disk since I only store media files on it.

1st format and the disk wouldn't mount. After googling around I find out that I had to do a GPT format for partitions over 2TB.
Ok. So I did that and formatted it as ext4. I started copying back my files and everything seemed ok. 
When I next booted my desktop, this message came up once again:
> Error mounting /dev/sdh1 at /media/george/3TB: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdh1" "/media/george/3TB"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdh1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


The output of the dmesg | tail:
george@george-MS-7091:~$ dmesg | tail
[  919.249043] sd 9:0:0:0: [sdd] 732566642 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[  919.251026] sd 9:0:0:0: [sdd] No Caching mode page present
[  919.251036] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[  919.295666]  sdd: sdd1
[  919.297016] sd 9:0:0:0: [sdd] 732566642 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[  919.299020] sd 9:0:0:0: [sdd] No Caching mode page present
[  919.299028] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[  919.299034] sd 9:0:0:0: [sdd] Attached SCSI disk
[  919.665826] EXT4-fs (sdd1): ext4_check_descriptors: Checksum for group 3968 failed (44912!=0)
[  919.665833] EXT4-fs (sdd1): group descriptors corrupted!

It's been really frustrading searching for about a week on the internet.
Please don't redirect me to other threads if there isn't really a solution to THIS problem and not to "similar" problems. I've pretty much read everything I found this week and no one seems to be able to help.

Additional info: 
- I use only ubuntu 13.04
- I did a disk check with gparted which tried to fix any problems but it failed to do that
- I use 3 other external disks with no problem for a long time now. 
  One is 400GB formated in FAT32, 2nd is a 500GB NTFS formated and 2rd is a 120GB previously NTFS formated. 
These 3 were never manual mounted or unmounted and never had any problem. I just plug them in and they just work. So did the large 3TB HDD until now. 
  I don't think I did anything wrong when formatting it since I've already formated the other 2 (NTFS formated disks) I mentioned above.

- Here is the info from gparted when I double click on the disk. (Sorry for the Greek and sorry for not having uploaded the whole pic. I just could't move it up further or drag it...)

---

### Post by CharlesA on 2013-09-08
What's with the "uhelper=udisks2,nodev,nosuid" part in the mount command?

Have you already tried running fsck on the drive? Dmesg says the file system is damaged and that is used to repair ext file systems.

```
sudo fsck -fC /dev/sdXY
```

---

### Post by carlwsnyder on 2013-09-08
First, I suggest reading the Wikipedia article [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

Second, from reading the article, your options for mounting the GPT partitioned disk seem to be incorrect, which is resulting in the error.

---

### Post by funked up on 2013-09-08
Don't know what's with the [COLOR=#000000]"uhelper=udisks2,nodev,nosuid" part in the mount command...
[/COLOR]
I've already done sudo fsck -fC /dev/sdh1 sometime the past days with no luck as I can recall.
Doing it right now once again. This is what came up so far:

george@george-MS-7091:~$ sudo fsck -fC /dev/sdh1
```
[sudo] password for george: 
fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
ext2fs_check_desc: Corrupt group descriptor: bad block for block bitmap
fsck.ext4: Group descriptors look bad... trying backup blocks...
Superblock has an invalid journal (inode 8).
Clear<y>? yes
*** ext3 journal has been deleted - filesystem is now ext2 only ***
```

and then multiple of these: (&#917;&#954;&#954;&#945;&#952;&#940;&#961;&#953;&#963;&#951; = clear, &#957;&#945;&#953; = yes)
```
Error while reading over extent tree in inode 134233537: Corrupt extent header
Clear inode<&#957;>? &#957;&#945;&#953;
Inode 134233537, i_blocks is 1606652, should be 0.  &#916;&#953;&#972;&#961;&#952;&#969;&#963;&#951;<&#957;>? &#957;&#945;&#953;
Inode 134233553 was part of the orphaned inode list.  FIXED.
Inode 134233553 has compression flag set on filesystem without compression support.  &#917;&#954;&#954;&#945;&#952;&#940;&#961;&#953;&#963;&#951;<&#957;>? &#957;&#945;&#953;

```

and that: (&#916;&#953;&#972;&#961;&#952;&#969;&#963;&#951; = Fix)
```
Error while reading over extent tree in inode 134233585: Corrupt extent header
Clear inode<&#957;>? &#957;&#945;&#953;
Inode 134233585, i_blocks is 1606655, should be 0.  &#916;&#953;&#972;&#961;&#952;&#969;&#963;&#951;<&#957;>? &#957;&#945;&#953;
Inode 134233601 was part of the orphaned inode list.  FIXED.
Error while reading over extent tree in inode 134233601: Corrupt extent header
Clear inode<&#957;>? &#957;&#945;&#953;
Inode 134233601, i_blocks is 1606656, should be 0.  &#916;&#953;&#972;&#961;&#952;&#969;&#963;&#951;<&#957;>? &#957;&#945;&#953;
yyInode 134234135 has illegal block(s).  &#917;&#954;&#954;&#945;&#952;&#940;&#961;&#953;&#963;&#951;<&#957;>? &#957;&#945;&#953;
Illegal block #397329 (1378679529) in inode 134234135.  CLEARED.
Illegal block #398353 (1378679529) in inode 134234135.  CLEARED.
Illegal block #399377 (1378679529) in inode 134234135.  CLEARED.
Illegal block #400401 (1378679529) in inode 134234135.  CLEARED.
Illegal block #401425 (1378679529) in inode 134234135.  CLEARED.
Illegal block #402449 (1378679529) in inode 134234135.  CLEARED.
Illegal block #403473 (1378679529) in inode 134234135.  CLEARED.
Illegal block #404497 (1378679529) in inode 134234135.  CLEARED.
Illegal block #405521 (1378679529) in inode 134234135.  CLEARED.
Illegal block #406545 (1378679529) in inode 134234135.  CLEARED.
Illegal block #407569 (1378679529) in inode 134234135.  CLEARED.
Too many illegal blocks in inode 134234135.
Clear inode<&#957;>? &#957;&#945;&#953;

```

and now it's doing this:
```
Recreate journal<&#957;>? &#957;&#945;&#953;                                                       
Creating journal (32768 blocks):  Done.


*** journal has been re-created - filesystem is now ext3 again ***
Restarting e2fsck from the beginning...
Resize inode not valid.  &#913;&#957;&#945;&#948;&#951;&#956;&#953;&#959;&#965;&#961;&#947;&#943;&#945;<&#957;>? &#957;&#945;&#953;
Pass 1: Checking inodes, blocks, and sizes

```

and now multiple of these:
```
Inode 19660804, i_blocks is 8388616, should be 0.  &#916;&#953;&#972;&#961;&#952;&#969;&#963;&#951;<&#957;>? &#957;&#945;&#953;
Inode 19660805 has an invalid extent node (blk 615546881, lblk 0)
&#917;&#954;&#954;&#945;&#952;&#940;&#961;&#953;&#963;&#951;<&#957;>? &#957;&#945;&#953;

```

---

### Post by funked up on 2013-09-08
> **carlwsnyder said:**
> First, I suggest reading the Wikipedia article [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

Second, from reading the article, your options for mounting the GPT partitioned disk seem to be incorrect, which is resulting in the error.

Thanx for the article but I'm not a computer genius so I can find the solution to my problem by reading the whole article.
By that I don't mean that I'm too lazy to read the whole article. I just don't understand everything it sais.
You seem to spotted the problem. Can you help me with a solution?

---

### Post by CharlesA on 2013-09-08
Either the drive is bad or something is going on with the file system that is causing the problems.

The results of the fsck show that you deleted the journal, so it's not really a ext4 file system anymore. Do you have a backup of whatever data you copied to the drive?

I would suggest running:

```
sudo badblocks -wsv /dev/sdXY
```

After backing up whatever data you can.
See here:
[https://wiki.archlinux.org/index.php/Badblocks](https://wiki.archlinux.org/index.php/Badblocks)

---

### Post by funked up on 2013-09-08
> **CharlesA said:**
> Either the drive is bad or something is going on with the file system that is causing the problems.

The results of the fsck show that you deleted the journal, so it's not really a ext4 file system anymore. Do you have a backup of whatever data you copied to the drive?

I would suggest running:

```
sudo badblocks -wsv /dev/sdXY
```

After backing up whatever data you can.
See here:
[https://wiki.archlinux.org/index.php/Badblocks](https://wiki.archlinux.org/index.php/Badblocks)


I don't think that the drive is bad cause til the format I was using it without any problems.
When I did the fsck it asked me to clear the invalid journal I think. I don't know what it means but I guessed it would be the right thing to do since it asked me.
(Keep in mind that after over 2 hours the fsck is still running!!!)

I have a backup of all my data. I don't mind doing a new format to the disk. I just want it to work properly as it did.

---

### Post by CharlesA on 2013-09-08
> **funked up said:**
> I don't think that the drive is bad cause til the format I was using it without any problems.
When I did the fsck it asked me to clear the invalid journal I think. I don't know what it means but I guessed it would be the right thing to do since it asked me.
(Keep in mind that after over 2 hours the fsck is still running!!!)

I have a backup of all my data. I don't mind doing a new format to the disk. I just want it to work properly as it did.

Cancel the fsck and run badblocks. It'll take a while, but it'll verify that the drive is ok. Then try creating the file system and see what happens.

---

### Post by funked up on 2013-09-08
> **CharlesA said:**
> Cancel the fsck and run badblocks. It'll take a while, but it'll verify that the drive is ok. Then try creating the file system and see what happens.

Ok but what file system should I use? As I told I want this 3TB external hard drive to work just as a USB stick with only one partition.
Should I go for NTFS or ext4 (I only want it for Ubuntu). And what about GPT? And why do the other ones that I formated to NTFS just work?!

---

### Post by CharlesA on 2013-09-08
I use ext4 on all my hard drives. GPT is just a special partition type, which allows partitions larger than 2TB (which is the limit of MBR partitions).

You should be able to create the partitions in gparted with little problem.

---

### Post by funked up on 2013-09-09
> **CharlesA said:**
> I use ext4 on all my hard drives. GPT is just a special partition type, which allows partitions larger than 2TB (which is the limit of MBR partitions).

You should be able to create the partitions in gparted with little problem.

Well that's exactly what I did last time. First I started to copy some of my backed up files and checked if everything was ok. I also did a restart on my desktop to see if everything was ok.

I had already copied over 100GB and I was happy that everything worked. Then I copied bigger files/data (folders with subfolfers etc) and when I was about 500GB and restarted my desktop again, I had these problems again...

Can it be that some of my files have a problem? But then again, why doesn't the problem appear on the other disks too?

---

### Post by CharlesA on 2013-09-09
Unknown but if it shows the same problems after copying data to it, I would look into RMAing it or at least not storing any data on it until it is replaced.

---

### Post by funked up on 2013-09-09
What exactly is RMAing? I have no idea.

---

### Post by CharlesA on 2013-09-09
> **funked up said:**
> What exactly is RMAing? I have no idea.

Returning it to the manufacturer. Most of the external drives I've seen carry at least a 1 year warranty, so if the drive is new, you might be able to get it replaced.

---

### Post by funked up on 2013-09-13
I've been running [COLOR=#000000][FONT=Ubuntu Mono]sudo badblocks -wsv /dev/sdXY [/FONT][/COLOR]for almost 100 hours now. 
Til now there's no error found using the first 2 patterns (0xaa and 0x55). It might take a few more days til it's done...
Do you think I should leave it ending the test or should I just do a new format? 

As I said before I think that there's nothing wrong with the drive cause I've been using it for a couple of years without any problems. 
The problems appeared as soon as I did the first format 2 weeks ago. 

Any suggestions?[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by CharlesA on 2013-09-13
Just let it finish. On the larger drives it takes a LONG time. After if finishes reformat the drive and try again.

---

### Post by funked up on 2013-09-22
It finished. NO problems were found with every 4 patterns. So I formated it again with gparted (GPT, ext4) and started to copy back files on the disk.
I also did some restart several times to my computer. Some with unmounting it and some with not unmounting it and everything worked fine. Til now!
I did a restart to my desktop (without unmounting any of my external drives). At shut down and start up I noticed a message which showed up for about 2 sec so I can't tell you what it said, but it was something like "could not........HID..." and at start up something like "wrong/bad argument.... /sdd drive...."

So the same problem is back again! Only to this drive.
Could it be that there's a problem with Ubuntu handling large partitions? 
I know there are lots of issues online similar to my problem but noone seems to have a clear solution.

Should I go back to FAT32 and back up alla other files that are not over 4GB? That's quite a joke though having a 3TB disk that can handle only 4GB files...

---

### Post by oldfred on 2013-09-22
Post these if sdd or change to your drive.

 sudo parted /dev/sdd unit s print
sudo gdisk -l /dev/sdd

---

### Post by funked up on 2013-09-22
> **oldfred said:**
> Post these if sdd or change to your drive.

 sudo parted /dev/sdd unit s print
sudo gdisk -l /dev/sdd

Here's the output of: sudo parted /dev/sdd unit s print
```
Model: Hitachi HDS5C3030ALA630 (scsi)
Disk /dev/sdh: 732566642s
Sector size (logical/physical): 4096B/4096B
Partition Table: gpt


Number  Start  End         Size        File system  Name  Flags
 1      256s   732566527s  732566272s
```

For the second there's something wrong I guess...:
```
sudo: gdisk: command not found
```

---

### Post by oldfred on 2013-09-22
If you do not have gdisk but have a large gpt drive you should install it. It is the fdisk for gpt drives as fdisk (currently) does not work with gpt drives.

sudo apt-get install gdisk

Some large drives show logical at 512 and physical at 4096B or 512B/4096B that may be part of the issue? But I have no idea how to change that.

---

### Post by funked up on 2013-09-22
Here's the outcome of "[COLOR=#000000]*sudo gdisk -l /dev/sdh"*[/COLOR] after installing gdisk
```
GPT fdisk (gdisk) version 0.8.5


Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present


Found valid GPT with protective MBR; using GPT.
Disk /dev/sdh: 732566642 sectors, 2.7 TiB
Logical sector size: 4096 bytes
Disk identifier (GUID): 5FC6DDDC-76F5-497A-9262-A0E6927E4E2E
Partition table holds up to 128 entries
First usable sector is 6, last usable sector is 732566636
Partitions will be aligned on 256-sector boundaries
Total free space is 359 sectors (1.4 MiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1             256       732566527   2.7 TiB     0700
```

---

### Post by oldfred on 2013-09-22
That looks ok I think. Unless having logical sectors of 4096 is an issue. That sometimes seems to be a work around to let MBR work with very large drives.

---

### Post by funked up on 2013-09-23
> **oldfred said:**
> That looks ok I think. Unless having logical sectors of 4096 is an issue. That sometimes seems to be a work around to let MBR work with very large drives.

If that looks ok what can I do to make the disk work properly?

---

### Post by oldfred on 2013-09-23
Does your drive have configuration settings?
Some have settings for greater compatibility.

 [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html)

---

### Post by funked up on 2013-09-23
> **oldfred said:**
> Does your drive have configuration settings?
Some have settings for greater compatibility.

 [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html)

If there are settings I surely don't know where to look for.
The disk had only one partition when I bought it a couple of years ago.
But it was with FAT32. That's the only thing I've wanted to change (cause of the 4GB per file limit), but keep only one partition.

Interesting topic about sectors and disks but it couldn't help me with my problem. Except there is something I didn't notice. I'm not an expert you know...

---

### Post by oldfred on 2013-09-23
I am out of ideas.

What is specific brand and model of drive?

---

### Post by funked up on 2013-09-23
It's a Hitachi drive.
HDD CnMemory "Spaceloop" 3TB.

Here is a info snapshot from gparted for this drive (sorry for the Greek). Maybe there's something you see that can help:
[ATTACH=CONFIG]246458[/ATTACH]

---

### Post by oldfred on 2013-09-23
What mode is BIOS in. AHCI or IDE?

But I do not think that is the issue and I do not know what else to try.
I was hoping to find some info from Hitachi, but it was only on configuring in Windows.

---

### Post by funked up on 2013-09-23
Don't know if this helps:

# dmidecode 2.11
SMBIOS 2.3 present.
38 structures occupying 1135 bytes.
Table at 0x000F0000.


Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
    Vendor: Phoenix Technologies, LTD
    Version: 6.00 PG
    Release Date: 01/27/2005
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 512 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported

---

### Post by oldfred on 2013-09-23
Is this an old system? 
Some BIOS did not support the new large drives and the drive mfg. did the work around to support some older systems. Do you have a BIOS update available?
(Notice - grasping at straws as out of real ideas.).

---

### Post by funked up on 2013-09-24
> **oldfred said:**
> Is this an old system? 
Some BIOS did not support the new large drives and the drive mfg. did the work around to support some older systems. Do you have a BIOS update available?
(Notice - grasping at straws as out of real ideas.).

Yes it is old. I bought this desktop in 2005 but really never had problems with it (except when I had windows :p).
It's just weird the problem doesn't appear right away. And how do you explain that the drive DID work before the formating when it also was only one partition but with a FAT32 file system?

Another thing I noticed is that it happend after leaving the desktop running for days but I don't think that's an issue since I have other (smaller) disks mounted too and they have no problem.

---

### Post by oldfred on 2013-09-24
It just may be with your BIOS that it only works with the emulation mode and not otherwise. Some have updated BIOS and had larger drives then work correctly but I think they were newer computers.

---

### Post by funked up on 2013-09-24
I have also a much newer lenovo thinkpad with updated bios and when I connect the HDD (after already having that problem) the same message appears (look at first post).
So does it make sense to upgrade the bios since everything else works ok?
And sorry for asking again but how is it possible that the drive worked with only one big partition with FAT32? Is it because of the FAT32?
 I don't really understand what you mean with emulation mode.

Can it be that Ubuntu has an issue with large partitions? I have found many posts with similar problems but with no clear answer yet.

---

### Post by oldfred on 2013-09-24
I think it is that drive has 4K sectors but also 4K logical sectors. The MBR partitioning may have worked. Most newer drives have 4K sectors but 512B logical sectors and have to use gpt to have a partition table with that large of a data size.
Sector size (logical/physical): 4096B/4096B

But I do not know enough of technical details to really know. Some more general info:
[https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues](https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues)

---

### Post by funked up on 2013-09-24
That's a good article but unfortunately it doesn't help me much.
Anyway, I guess I have to do a format again. Maybe I'll try it with 2 partitions each 1.5 TB and with no GPT.

Thank you for all your time and effort!

---

