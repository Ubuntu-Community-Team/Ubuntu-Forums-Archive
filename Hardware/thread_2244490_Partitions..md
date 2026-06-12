---
title: "Partitions."
date: 2014-09-16
forum: Hardware
---

### Post by cybuss on 2014-09-16
Hello im trying to figure out how many partitions i have. 

the first part says system record partition 1 105mb 
then a filesystem partition 2 581 gb NTFS (windows)
then i got partition 5 411 gb Ext4 (ubuntu)
then theres the swap partition 6
and extended partition 3

I think the 105mb partition does not count? also the extended partition should not count to the 4 primary partition limit.
does the swap?

so i should have 2 more primary partitions open?

thanks for any help!

---

### Post by Bashing-om on 2014-09-16
cybuss; Hello;

To see what your partitioning is:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f

```
and will show several ways of looking at the partitioning.

Is there a particular problem needing attention ?

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by cybuss on 2014-09-16
sudo fdisk -lu   

>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1134321663   567057408    7  HPFS/NTFS/exFAT
/dev/sda3      1134323710  1953523711   409600001    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5      1134323712  1936830463   401253376   83  Linux
/dev/sda6      1936832512  1953523711     8345600   82  Linux swap / Solaris


sudo parted -l
> Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   581GB   581GB   primary   ntfs
 3      581GB   1000GB  419GB   extended
 5      581GB   992GB   411GB   logical   ext4
 6      992GB   1000GB  8546MB  logical   linux-swap(v1)


sudo parted /dev/sda unit s print

> Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start        End          Size         Type      File system     Flags
 1      2048s        206847s      204800s      primary   ntfs            boot
 2      206848s      1134321663s  1134114816s  primary   ntfs
 3      1134323710s  1953523711s  819200002s   extended
 5      1134323712s  1936830463s  802506752s   logical   ext4
 6      1936832512s  1953523711s  16691200s    logical   linux-swap(v1)


lsblk -f
> NAME   FSTYPE LABEL MOUNTPOINT
sda                 
&#9500;&#9472;sda1              
&#9500;&#9472;sda2              
&#9500;&#9472;sda3              
&#9500;&#9472;sda5              /
&#9492;&#9472;sda6              [SWAP]
sr0   

im just trying to see if i have a open primary partition. im going to make a seperate partition for steam games so i dont have to redownload or restore backups everytime i reinstall ubuntu

---

### Post by cybuss on 2014-09-16
From what i've read if you go over the 4 limit bad things happen so a second more knowledgeable opinion would be the safest route for me.

---

### Post by yancek on 2014-09-16
You are only using 3 primary partitions so you might be able to create another.  You didn't post the full output of fdisk so we don't know the size of the Extended partition (sda3) or whether there is any unallocated space.  To get that info, open a terminal and type: parted
 
> GNU Parted 3.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted)

You should see the '[parted' prompt as shown above.  Type:  print free
Then post that output here.

---

### Post by cybuss on 2014-09-16
my bad. im trying to keep it as cluster free as possible. is this the 1 your asking?

> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x7928dc39

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1134321663   567057408    7  HPFS/NTFS/exFAT
/dev/sda3      1134323710  1953523711   409600001    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5      1134323712  1936830463   401253376   83  Linux
/dev/sda6      1936832512  1953523711     8345600   82  Linux swap / Solaris

---

### Post by Bashing-om on 2014-09-16
cybuss; Well, well.

All to the good. yancek does have the right of it.
You have
sda1 primary
sda2 primary
sda3 extended -> which counts a a primary partition of which :
sda5 is a logical partition that is contained within that 'extended' partition , and is NOT counted as primary
sda6 is a logical partition - swap - that is contained within that 'extended' partition , and is NOT counted as primary

So, that means indeed you can make up one more primary partition.
[https://iam.tj/kb/pc/boot/#a_bootloader](https://iam.tj/kb/pc/boot/#a_bootloader) 
TJ- has a good write up, and in it is a good explanation of that 4 primary partition limit (think addressing ).

[INDENT][INDENT]I bet this helps just a little bit
[/INDENT][/INDENT]

---

### Post by cybuss on 2014-09-16
> **Bashing-om said:**
> cybuss; Well, well.

All to the good. yancek does have the right of it.
You have
sda1 primary
sda2 primary
sda3 extended -> which counts a a primary partition of which :
sda5 is a logical partition that is contained within that 'extended' partition , and is NOT counted as primary
sda6 is a logical partition - swap - that is contained within that 'extended' partition , and is NOT counted as primary

So, that means indeed you can make up one more primary partition.
[https://iam.tj/kb/pc/boot/#a_bootloader](https://iam.tj/kb/pc/boot/#a_bootloader) 
TJ- has a good write up, and in it is a good explanation of that 4 primary partition limit (think addressing ).

[INDENT][INDENT]I bet this helps just a little bit
[/INDENT][/INDENT]


Thanks guys! ill list this as solved, have a good evening/day!

---

