---
title: "testdisk doesn't seem to write partition structure to disk"
date: 2010-01-04
forum: Hardware
---

### Post by 1branchonthevine on 2010-01-04
I have a drive that shows as unallocated space... but when I use sudo testdisk to restore the partition structure (which gets detected correctly) and then reboot, gparted still reports entire drive as unallocated.

The BIOS still detects the drive's MBR with the installed GRUB on it. This latest version of grub is awesome and still loads my linux partition on my drive (from the current unallocated mess), so I'm still able to use the drive just fine. palimpsest (drive SMART reporter and checker) says the drive is healthy. Windows no longer loads from the grub menu, gofig ;)

I have tried testdisk with the currently installed 64bit ubuntu, and even tried the 32bit & 64bit live cd versions of testdisk... no effect!
I have tried removing dmraid, as I have had similar issues with a karmic install before... no effect!
-------------------------------------------------------------------------------
Results from: sudo fdisk -l 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49028545

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1306    10490413+   7  HPFS/NTFS
/dev/sda2            1307        8955    61440592+   7  HPFS/NTFS
/dev/sda3            8956       11505    20482872   83  Linux
/dev/sda4           11506       30402   151790152+   f  W95 Ext'd (LBA)
/dev/sda5           11506       29352   143354880    7  HPFS/NTFS
/dev/sda6           29353       30401     8426084   82  Linux swap / Solaris
-------------------------------------------------------------------------------
Results from QUICK partition detection in testdisk:

Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS          0 1  1      1305 254 63     20980827 [PQSERVICE]
 2 P HPFS - NTFS     1306   0   1     8954 254 63  122881185 [Win7]
 3 P Linux               8955   0   1   11504 254 57     40965744 [Karmic]
 4 E extended LBA 11505   0   1   30401 254 63  303580305
 5 L HPFS - NTFS   11505   1 17   29351 219 52  286709760 [Data Backup]
 6 L Linux Swap     29352   0   1   30400 254 46    16852168
-------------------------------------------------------------------------------
Results from DEEPER partition detection in testdisk:

Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
Partition                  Start        End    Size in sectors
  HPFS - NTFS              0    1   1    1305 254 63    20980827 [PQSERVICE]
  HPFS - NTFS              0    1   1    1305 254 63    20980827 [PQSERVICE]
  HPFS - NTFS         1306    0   1    8954 254 63  122881185
  HPFS - NTFS         1306   13 52    8954 249 63  122880000 [System Reserved]
  HPFS - NTFS         1318 204 39    6418   22  4    81920000
  HPFS - NTFS         1306   13 52    8954 249 63  122880000 [System Reserved]
  HPFS - NTFS         1306    0   1     8954 254 63  122881185
  Linux                   8955     0   1   11504 254 57   40965744
  HPFS - NTFS       11505     1 17   29351 219 52  286709760
  HPFS - NTFS         1306   13 52   15853 204 31  233709568
  HPFS - NTFS       15853 204 32    30401  42  41  233703424 [DATA]
  HPFS - NTFS         8967 185 51   16633   25 32  123144192
  HPFS - NTFS         8967 185 51   22752   61 29  221448192
  HPFS - NTFS       11505     1 17   29351 219 52  286709760
  HPFS - NTFS       11505     2  1    29351 254 63  286711929
  Linux Swap         29352     0  1   30400 254 46    16852168
-------------------------------------------------------------------------------


I notice there is a shift in start and end, they are off by 1 on each partition... not familiar with testdisk enough to know what is going on here. Nobody seems to have tried testdisk and ended up with an unallocated drive when they were done writing a partition table to their drive... only the opposite!

How it all started: Win 7 seemed to be the culprit as it was running fine until the OS somehow corrupted and lost my [data backup] partition and left it showing as free space. Once I tried to recover the lost partition and rewrite the drive structure with testdisk, the entire drive resulted as unallocated. Now I can't get any partition structure back. Is this a permission issue with win7? How do I take ownership of a drive that is unallocated?

---

### Post by 1branchonthevine on 2010-01-19
bump... anyone????????

---

### Post by warfacegod on 2010-01-19
Don't put too much faith in Palimpset. Its got a habit of throwing false positives.

```
sudo apt-get install gsmartcontrol
```

It's much more reliable.

Try reinstalling Gparted for your drive space issue, I've seen it do that when it doesn't have support for the filesystem.

---

### Post by rockofclay on 2010-01-23
I've had the exact same issue.

It started when I installed windows 7. It killed my first partition (EXT3 with karmic installed).

As soon as I ran testdisk on the gparted live disk, the whole drive came up as unallocated in gparted.

Testdisk still sees the right structure though.

I'll let you know if I have any luck.

---

### Post by 1branchonthevine on 2010-01-25
Reinstalling gparted had no effect... Thanks though!

I was told that win7 partitioning tool creates a sector offset in some way or something of the matter... maybe this is why testdisk thought the shift was in error and tried to "correct" it, thus breaking it further? Anyone heard of this? I will try and find the website again... 

Ahh.. I think this is it...
[http://www.multibooters.co.uk/partitions.html](http://www.multibooters.co.uk/partitions.html)
And, maybe this would be useful? 
[http://www.dcr.net/~w-clayton/Vista/DisappearingPartitions/DisappearingPartitions.htm](http://www.dcr.net/~w-clayton/Vista/DisappearingPartitions/DisappearingPartitions.htm)

Again if anyone can provide support on this issue, that would be more than totally awesome!

---

### Post by ibuclaw on 2010-01-25
I can't see a problem, lol. :)

Which drive is missing again?

---

### Post by 1branchonthevine on 2010-01-25
Here is what MICROSCRUFF told me... but I never went any further because they did not answer my second Q.

[http://social.answers.microsoft.com/Forums/en-US/w7install/thread/c512ffb7-aa0a-4368-914d-08932f43f9e1](http://social.answers.microsoft.com/Forums/en-US/w7install/thread/c512ffb7-aa0a-4368-914d-08932f43f9e1)

---

### Post by ibuclaw on 2010-01-25
I still can't see anything wrong. :)

Then again, fdisk is a low level partitioner and doesn't usually show what there really is, such as whether or not the partition has been formatted properly.


When you run testdisk, I take it you ran a deep scan?
When you see the partition list, you can press **P** to list the contents of the partition it finds.

---

### Post by oldfred on 2010-01-25
If you do 

sudo fdisk -lu 

You will see sectors not the usual cylinders. This normally will show the Vista and 7 partitions starting at 2048 instead of the normal 63.

My XP partition starts at 63 & on my desktop all the linux partitions start at 63 for each drive. 
fred@fred-laptop:~$ sudo fdisk -lu

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   113595614    56797776    7  HPFS/NTFS

---

### Post by 1branchonthevine on 2010-02-02
~tiny v...~
The problem is that in every drive reporting tool I use from gparted, to windows install disk part tool, etc., reports the entire disk as unallocated. Obviously the drive structure is still on the disk, but somewhere something is messed up. The MBR containing Grub bootloader still works, plus it still locates and boots the linux partition just fine. Windows partition is toast, since grub can't load it anymore, and my data backup drive is messed up because every time I run photorec file recovery, I get old files from long ago, not my recent files from when it got messed up in the first place. I'm guessing this is because when I installed win7, I quick formated over the older data backup partition with the win7 installer, so maybe the default cluster size in win7 was different than the previous ntfs format. So maybe photorec is automatically assuming the previous format over the later??? I was just hoping that I could restore the drive structure first though, and make sure it isn't because of some sector offset issue. After that, then I'll see if I can play with cluster deviations in photorec.

Ultimately, I just want to get my partition structure working correctly so that I can get windows working/reinstalled again, and restore what I can from my NTFS data backup partition. But, as I stated earlier, when I use testdisk to restore the drive structure (as it sees it), the drive still shows up as unallocated in the end! It is like testdist is not writing the structure to the disk, or that it is incorrectly reporting something... maybe this is because of the mysterious sector shift that win7 partitioning may have done..... read link in previous post.

---

### Post by 1branchonthevine on 2010-02-02
~oldfred~
That's interesting.... not sure what happened/changed since I last did this but now when I use fdisk I get the following....

$ sudo fdisk -lu
Error: Can't have a partition outside the disk!

$ sudo fdisk -l
Error: Can't have a partition outside the disk!

OH JOY, another unexpected variable!!!
Looking it up now....

UPDATE:...
okay I found out that I installed gnu-fdisk a while back hoping that it might have more support than standard fdisk... well it sucked on this issue! now that it is uninstalled, I get ....
------------------------------------------------------------------------------------
$ sudo fdisk -lu /dev/sda

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x49028545

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    20980889    10490413+   7  HPFS/NTFS
/dev/sda2        20980890   143862074    61440592+   7  HPFS/NTFS
/dev/sda3       143862075   184827818    20482872   83  Linux
/dev/sda4       184827825   488408129   151790152+   f  W95 Ext'd (LBA)
/dev/sda5       184827904   471537663   143354880    7  HPFS/NTFS
/dev/sda6       471539880   488392047     8426084   82  Linux swap / Solaris

--------------------------------------------------------------------------------------------

$ sudo fdisk -l /dev/sda

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49028545

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1306    10490413+   7  HPFS/NTFS
/dev/sda2            1307        8955    61440592+   7  HPFS/NTFS
/dev/sda3            8956       11505    20482872   83  Linux
/dev/sda4           11506       30402   151790152+   f  W95 Ext'd (LBA)
/dev/sda5           11506       29352   143354880    7  HPFS/NTFS
/dev/sda6           29353       30401     8426084   82  Linux swap / Solaris
---------------------------------------------------------------------------------------------

---

### Post by oldfred on 2010-02-02
Very advanced partition table repair. (over my head unless I had to repair my own then I might try it)

[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

---

### Post by 1branchonthevine on 2010-02-02
~tinivole~
I updated the partition table list (on the first post...) using the deeper testdisk search like you  asked. I also notice that fdisk reports sda's max cylinders as 30401 but testdisk reports 30402. Not sure how the drive popped up with another cylinder...

I thought the following deviations were worth noting... not sure which one testdisk wrote under the basic quick search.... since fdisk -lu doesn't work anymore, I can't tell what was written to the partition table under head/sector. My guess is 0 1, not 13 52. I wonder if this head/sector deviation is the nonstandard offset that is described in the [http://www.multibooters.co.uk/partitions.html](http://www.multibooters.co.uk/partitions.html) page! Interestingly the NTFS partitions are the only ones that have this head/sector deviation too!

Win7
HPFS - NTFS         1306    0   1    8954 254 63  122881185
  HPFS - NTFS         1306   13 52    8954 249 63  122880000 [System Reserved]

Data backup partition
HPFS - NTFS       11505     1 17   29351 219 52  286709760
  HPFS - NTFS       11505     2  1    29351 254 63  286711929

I do know that when/if I get this fixed, I am writting zeros to every partition, because testdisk deeper search had way too much old partition crap in the list!

I think I'm on a role here... I'm guessing I will be asked to chose the deviated partitions next, but I do worry about the cylinder difference being reported by fdisk/testdisk, and the fact that both gparted and fdisk mention: Error: Can't have a partition outside the disk! Because as far as I can tell neither of the lists show a partition out side of the disk! They are all slightly smaller looking to me by 1 or more cylinders.

Thanks for suggesting the deeper search... my right brain didn't want to wait that long for the results. ;)

---

### Post by 1branchonthevine on 2010-02-02
Allright so I wrote the following to the partition table after using deeper search with testdisk (note, testdisk wouldn't let me add the swap partition contained in cylinder 29352 to 30401, so I ignored it and figured it will show this as freespace instead, no biggie):

Disk /dev/sda - 250 GB / 232 GiB (RO) - ATA ST9250827AS

     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  1305 254 63   20980827 [PQSERVICE]
 2 P HPFS - NTFS           1306  13 52  8954 249 63  122880000 [System Reserved]
 3 P Linux                 8955   0  1 11504 254 57   40965744
 4 E extended LBA         11505   0  1 30401 254 63  303580305
 5 L HPFS - NTFS          11505   2  1 29351 254 63  286711929

But, when I rebooted and ran fdisk I got:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49028545

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1306    10490413+   7  HPFS/NTFS
/dev/sda2            1307        8955    61440000    7  HPFS/NTFS
/dev/sda3            8956       11505    20482872   83  Linux
/dev/sda4           11506       30402   151790152+   f  W95 Ext'd (LBA)
/dev/sda5           11506       29352   143355964+   7  HPFS/NTFS

What the heck... the report shows everything is off by one cylinder! Note the extended (W95 Ext'd (LBA)) partition ends on 30402 not 30401! Testdisk was supposed to write 30401, but when all is done fdisk shows 30402.... so let me guess what happens when I try gparted again...???

 $ sudo gparted
======================
libparted : 1.8.8.1.159-1e0e
======================
Can't have a partition outside the disk!

Duh! that's not what I selected to have written.... 

Still lost!

---

### Post by 1branchonthevine on 2010-02-08
THANKS FOR ALL THE HELP, I decided it isn't worth the time and frustration. For some reason photorec is seeing old files; before I resized my ntfs data partition and started putting my photos on it. They are not showing up in the now corrupt partition at all, only old crap. I loose all my pictures, my acer image partition, my win7, and soon my linux. Since I can't get this partitioning stuff figured out, it's time to write zeros and start over! This time I'll format ntfs in gparted and screw winblows way of doing it. Again, thanks for trying!

---

