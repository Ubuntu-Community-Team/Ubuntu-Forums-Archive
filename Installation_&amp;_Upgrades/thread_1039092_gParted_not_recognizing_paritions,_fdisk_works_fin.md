---
title: "gParted not recognizing paritions, fdisk works fine"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by mastergaurav on 2009-01-14
Hi,

I just downloaded the Ubuntu 8.10 and tried to install on my laptop (Presario v3000) with SATA hard-disk.

gParted (0.3.8) does not detect any partition table while fdisk (using live CD) works just great!

I saw in gParted forums regarding it and they ask to upgrade to 0.4.1. However, there's no deb update available for v0.4.1.

apt-get install gparted

says udpated to 0.3.8 for the first time and then it's already updated.

:mad:

What do I do now?


--
Happy Hacking,
Gaurav
[http://www.mastergaurav.com](http://www.mastergaurav.com)

---

### Post by Partyboi2 on 2009-01-14
You could always downloaded the gparted live cd iso from [[COLOR=Blue]here[/COLOR]]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779") and burn to disk and use.

---

### Post by mastergaurav on 2009-01-14
> **Partyboi2 said:**
> You could always downloaded the gparted live cd iso ... and burn to disk and use.

How? I mean... when I will go to ubuntu, it says no partitions found! Back to square one...

IMHO, I need to ensure that the Ubuntu installer is able to recognize the partition table and not gParted.

Correct me if I am wrong in my understanding...


--
Happy Hacking,
Gaurav
[www.mastergaurav.com](www.mastergaurav.com)

---

### Post by caljohnsmith on 2009-01-14
It sounds like your HDD's partition table might be slightly corrupt. How about posting the output of:
```
sudo fdisk -lu
sudo sfdisk -d
```
And we can work from there if you want.

---

### Post by mastergaurav on 2009-01-14
> **caljohnsmith said:**
> How about posting the output of

Here it goes:

```

ubuntu@ubuntu:~$ **sudo sfdisk -d**
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size= 41943667, Id= 7, bootable
/dev/sda2 : start= 41945088, size= 41946342, Id= 7
/dev/sda3 : start= 83888128, size= 56005892, Id= 7
/dev/sda4 : start=139894020, size= 16402365, Id= c

ubuntu@ubuntu:~$ **sudo fdisk -lu**

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4d384d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    41945714    20971833+   7  HPFS/NTFS
/dev/sda2        41945088    83891429    20973171    7  HPFS/NTFS
/dev/sda3        83888128   139894019    28002946    7  HPFS/NTFS
/dev/sda4       139894020   156296384     8201182+   c  W95 FAT32 (LBA)

```

Hmmm... end of /dev/sda1 is "into" the /dev/sda2 -- given by fdisk.
Can something be done?


-Gaurav

---

### Post by mastergaurav on 2009-01-14
I did one more thing... and I think there's a trouble:

```

ubuntu@ubuntu:~$ sudo parted -l /dev/sda
Error: Can't have overlapping partitions.                                 

```


-Gaurav

---

### Post by caljohnsmith on 2009-01-14
> **mastergaurav said:**
> Here it goes:
```

ubuntu@ubuntu:~$ **sudo fdisk -lu**

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4d384d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    [COLOR="Red"]41945714[/COLOR]    20971833+   7  HPFS/NTFS
/dev/sda2        [COLOR="Red"]41945088    83891429[/COLOR]    20973171    7  HPFS/NTFS
/dev/sda3        [COLOR="Red"]83888128[/COLOR]   139894019    28002946    7  HPFS/NTFS
/dev/sda4       139894020   156296384     8201182+   c  W95 FAT32 (LBA)

```

So it looks like from fdisk's output, your sda1 partition overlaps sda2, and your sda2 partition also overlaps sda3. Most likely we can get things straightened out with "testdisk" though, so how about first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
First check that the testdisk version you are using is 6.9 or higher; using 6.8 won't work well in your situation since it tends to crash when trying to list NTFS partitions. So if you don't have version 6.9, let me know and I'll send alternate instructions of how to download it and use it.

After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing. Also, please post the output of:
```
sudo sfdisk -l
```
And we can work from there. :)

---

### Post by mastergaurav on 2009-01-14
I got testdisk v6.9... great!

Here's the output:

**Analyze results (Level 0):**

```

Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0  32 33  2610 254 63   41943667 [C DRIVE]
 2 P HPFS - NTFS           2610 245  4  5221 254 63   41946342 [D DRIVE]
 3 P HPFS - NTFS           5221 202 38  8707 254 63   56005892 [PERSONAL]
 4 P FAT32 LBA             8708   0  1  9728 254 63   16402365 [PRESARIO_RP]
Space conflict between the following two partitions
 1 * HPFS - NTFS              0  32 33  2610 254 63   41943667 [C DRIVE]
 2 P HPFS - NTFS           2610 245  4  5221 254 63   41946342 [D DRIVE]
Space conflict between the following two partitions
 2 P HPFS - NTFS           2610 245  4  5221 254 63   41946342 [D DRIVE]
 3 P HPFS - NTFS           5221 202 38  8707 254 63   56005892 [PERSONAL]

```

After selecting the disk (and I don't have Vista)...

**Results (Level 1):**

```

Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  8706 254 63  139877892
P FAT32 LBA             8708   0  1  9728 254 63   16402365 [PRESARIO_RP]

```

**Here's the result of "Deeper Search" (Level 3):**

```

Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  8706 254 63  139877892
D HPFS - NTFS              0  32 33  2610 245  3   41943040 [C DRIVE]
D HPFS - NTFS           2610 245  4  5221 202 37   41943040 [D DRIVE]
D HPFS - NTFS           5221 202 38  8707 234 39   56004608 [PERSONAL]
* FAT32 LBA             8708   0  1  9728 254 63   16402365 [PRESARIO_RP]

```

**And the final set of "Files" (Level 4):**

All partitions show the file list... and all the files (at least in the root directory of the partition).


-Gaurav

---

### Post by caljohnsmith on 2009-01-14
> **mastergaurav said:**
> 
```

Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]D[/COLOR] HPFS - NTFS              0   1  1  8706 254 63  139877892
[COLOR="Red"]*[/COLOR] HPFS - NTFS              0  32 33  2610 245  3   41943040 [C DRIVE]
[COLOR="Red"]P[/COLOR] HPFS - NTFS           2610 245  4  5221 202 37   41943040 [D DRIVE]
[COLOR="Red"]P[/COLOR] HPFS - NTFS           5221 202 38  8707 234 39   56004608 [PERSONAL]
[COLOR="Red"]P[/COLOR] FAT32 LBA             8708   0  1  9728 254 63   16402365 [PRESARIO_RP]

```

That's good news, Gaurav, because it looks like it should be easy to recover your correct partition table. How about selecting each of the partitions shown above, and using the right/left arrow keys, mark them as I have highlighted in red above. Once you are sure all the partitions are marked exactly as shown above, press enter to continue, and then write the new partition table to your drive. Next reboot, and post the new output of:
```
sudo fdisk -lu
sudo sfdisk -l
sudo parted /dev/sda print
```
And we can work from there. :)

---

### Post by mastergaurav on 2009-01-14
Hey!

Things are fantastic!

```

**ubuntu@ubuntu:~$ sudo fdisk -lu**

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4d384d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    41945087    20971520    7  HPFS/NTFS
/dev/sda2        41945088    83888127    20971520    7  HPFS/NTFS
/dev/sda3        83888128   139892735    28002304    7  HPFS/NTFS
/dev/sda4       139894020   156296384     8201182+   c  W95 FAT32 (LBA)

**ubuntu@ubuntu:~$ sudo sfdisk -l**

Disk /dev/sda: 9729 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   2610-   2611-  20971520    7  HPFS/NTFS
/dev/sda2       2610+   5221-   2611-  20971520    7  HPFS/NTFS
/dev/sda3       5221+   8707-   3487-  28002304    7  HPFS/NTFS
/dev/sda4       8708    9728    1021    8201182+   c  W95 FAT32 (LBA)

**ubuntu@ubuntu:~$ sudo parted /dev/sda print**
Model: ATA FUJITSU MHV2080B (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  21.5GB  21.5GB  primary  ntfs         boot 
 2      21.5GB  43.0GB  21.5GB  primary  ntfs              
 3      43.0GB  71.6GB  28.7GB  primary  ntfs              
 4      71.6GB  80.0GB  8398MB  primary  fat32        lba  

```

***[FONT="Times New Roman"]And now, gparted also works!!![/FONT]***
Thanks a ton!


-Gaurav

---

### Post by caljohnsmith on 2009-01-14
That's great news, Gaurav; it looks like testdisk saved the day. Cheers, and I hope you don't run into any more problems installing Ubuntu. :)

---

### Post by kranny on 2009-01-14
@caljohnsmith:I couldnt install 6.9.Can you help me out?

---

### Post by caljohnsmith on 2009-01-14
Kranny, as long as you have to download testdisk anyway, how about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your Ubuntu desktop, and then do:
```
cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
Let me know how that goes.

---

### Post by kranny on 2009-01-14
```
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
```

Maybe a bad download..Strtd downloading it again

---

### Post by mastergaurav on 2009-01-14
Yes... testdisk did save my life. Fanstatic. I've digg-ed this thread :)

```
cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```

btw, I think you missed out "bunzip2" step. tar will not understand bzip2-ed contents :)


-Gaurav

---

### Post by kranny on 2009-01-14
> 

btw, I think you missed out "bunzip2" step. tar will not understand bzip2-ed contents :)


-Gaurav

No it was indeed a bad download..And the fresh download works fine..Thanks...

---

### Post by caljohnsmith on 2009-01-14
> **mastergaurav said:**
> Yes... testdisk did save my life. Fanstatic. I've digg-ed this thread :)

```
cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```

btw, I think you missed out "bunzip2" step. tar will not understand bzip2-ed contents :)


-Gaurav
I'm using tar 1.20-1, and it seems to handle the bz2 file just fine; does it not work for you?

---

### Post by mastergaurav on 2009-01-14
Hey... one point problem... IIRC, marking the partitions "*, P, P, P" ensures that there are 4 primary partitions... now that's an issue.

I need to convert one of these partitions to "logical". Can I do it now... or do I need to necessarily empty the partition, delete and recreate?


-Gaurav

---

### Post by caljohnsmith on 2009-01-14
> **mastergaurav said:**
> Hey... one point problem... IIRC, marking the partitions "*, P, P, P" ensures that there are 4 primary partitions... now that's an issue.

I need to convert one of these partitions to "logical". Can I do it now... or do I need to necessarily empty the partition, delete and recreate?


-Gaurav

According to the physical layout of your new partition table, we could easily convert your sda4 FAT32 partition into a logical partition. That partition is only ~8GB though, so if you resize that, it might not give you much room for Ubuntu. If you want more room, how about shrinking sda1, sda2 or sda3; also for whichever partition you want to convert to a logical partition, you'll need to make sure there is at least 63 sectors of space between it and the partition before it in order to make room for the EBR (Extended Boot Record) necessary for the logical partition. So if the partition before ends at the sector right before the partition you want to convert to a logical partition, practically speaking then you can use gparted to shrink the partition by the smallest increment possible, which is usually a couple of MB. How about doing that, and once you are done post the new output of:
```
sudo fdisk -lu
sudo sfdisk -d
```
Also let me know exactly which partition you want to convert to a logical partition, and we can work from there.

---

### Post by mastergaurav on 2009-01-14
/dev/sda4 is my WindowsXP recovery partition.
I would be using /dev/sda3, which was originally about 26GB.

I've resized it to 18GB (18000000 blocks), keeping about 8GB for Ubuntu.

And I'd be keeping my life simple with the following setup:

1. Swap: 512MB
2. /: 4GB
3. /home: Remainder

Here's the latest stuff after resizing...

```

**ubuntu@ubuntu:~/Desktop$ sudo fdisk -lu**

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4d384d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    41945087    20971520    7  HPFS/NTFS
/dev/sda2        41945088    83888127    20971520    7  HPFS/NTFS
/dev/sda3        83888128   119888127    18000000    7  HPFS/NTFS
/dev/sda4       139894020   156296384     8201182+   c  W95 FAT32 (LBA)

**ubuntu@ubuntu:~/Desktop$ sudo sfdisk -d**
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size= 41943040, Id= 7, bootable
/dev/sda2 : start= 41945088, size= 41943040, Id= 7
/dev/sda3 : start= 83888128, size= 36000000, Id= 7
/dev/sda4 : start=139894020, size= 16402365, Id= c

```

btw, can I use testdisk to convert P to Logical?

-Gaurav

---

### Post by caljohnsmith on 2009-01-14
OK, how about first downloading the attached "partition_table.txt" file to your Ubuntu desktop, and then do:
```
sudo sfdisk -f /dev/sda -O ~/Desktop/sda_sectors_modified.save < ~/Desktop/partition_table.txt
```
That will produce a lot of output, including some warnings, so you don't need to be alarmed; but please post the output so I can check that everything went OK. Also, the above command will create a backup of the sectors being modified as a small "sda_sectors_modified.save" file that will be created on your desktop, so that if for some reason anything were to go wrong, you can easily restore your original partition table with that file. Therefore, be sure to copy that file to a different drive, or you could for instance save it to your email account or something like that. The contents of the partition_table.txt file are as follows: 
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size= 41943040, Id= 7, bootable
/dev/sda2 : start= 41945088, size= 41943040, Id= 7
/dev/sda3 : start= 83888128, size= 36000000, Id= 7
/dev/sda4 : start=119888181, size= 36408204, Id= 5
/dev/sda5 : start=119888244, size=  1048576, Id=82
/dev/sda6 : start=120936883, size=  8388608, Id=83
/dev/sda7 : start=129325554, size= 10568404, Id=83
/dev/sda8 : start=139894020, size= 16402365, Id= c
```
So as you can see from above, we are changing your current FAT sda4 partition into the sda8 logical partition above, and then sda4 will become the extended partition. Also we are going to create logical partitions sda5, sda6, and sda7 for your swap, root, and home partitions respectively. Keep in mind that the above "size" values are the size of the partition calculated as follows:
```
partition size = stop sector - start sector + 1
```
So be careful not to confuse size with the partition sector. Next reboot, and please post the new output of:
```
sudo fdisk -lu
sudo sfdisk -d
```
And we can work from there. :)

---

### Post by mastergaurav on 2009-01-14
Hi,

```

/dev/sda3 : start= 83888128, size= 36000000, Id= 7
/dev/sda4 : start=119888181, size= 36408204, Id= 5

```

The gap is 18GB + 53bytes. Shouldn't it be 18GB + 63bytes?
```

/dev/sda4 : start=**1198881*9*1**, size= 36408204, Id= 5

```

Correct me if I am wrong in my understanding?

---

### Post by caljohnsmith on 2009-01-14
Actually, I deliberately made it 119888181 so that the extended partition would begin on a track boundary, i.e. 119888181 is divisible by 63 whereas 119888191 isn't. The discrepancy is that your sda3 partition does not end at a track boundary. And at least in my experience, actually it is not necessary for the partition to start exactly on a track boundary since all modern OSes that I'm aware of use LBA (Logical Block Addressing) rather than the old CHS (Cylinder, Heads, Sectors) values to access the HDD, because the OS has no other choice but to use LBA if the HDD is bigger than 8.4 GB anyway; so the partition doesn't have to start on a track, but in my experience it is nice to do so or fdisk/sfdisk will usually throw a warning. If you wanted you could instead have sda4 start at 119888181 + 63 = 119888244 to allow more cushion, but then you will have to move the starting position of sda5 by 63 sectors and also decrease its size by the same amount. It's up to you. :)

---

### Post by mastergaurav on 2009-01-14
Thanks!

Here's the final output:

```

**ubuntu@ubuntu:~$ sudo fdisk -lu**

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4d384d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    41945087    20971520    7  HPFS/NTFS
/dev/sda2        41945088    83888127    20971520    7  HPFS/NTFS
/dev/sda3        83888128   119888127    18000000    7  HPFS/NTFS
/dev/sda4       119888181   156296384    18204102    5  Extended
/dev/sda5       119888244   120936819      524288   82  Linux swap / Solaris
/dev/sda6       120936883   129325490     4194304   83  Linux
/dev/sda7       129325554   139893957     5284202   83  Linux
/dev/sda8       139894020   156296384     8201182+   c  W95 FAT32 (LBA)

**ubuntu@ubuntu:~$ sudo sfdisk -d**
[I]Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
[/I]# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size= 41943040, Id= 7, bootable
/dev/sda2 : start= 41945088, size= 41943040, Id= 7
/dev/sda3 : start= 83888128, size= 36000000, Id= 7
/dev/sda4 : start=119888181, size= 36408204, Id= 5
/dev/sda5 : start=119888244, size=  1048576, Id=82
/dev/sda6 : start=120936883, size=  8388608, Id=83
/dev/sda7 : start=129325554, size= 10568404, Id=83
/dev/sda8 : start=139894020, size= 16402365, Id= c

```

I've still not booted to WinXP... wishing it's all fine. ;)

btw, it looks good now (I'm familiar with fdisk results).

-Gaurav

---

### Post by caljohnsmith on 2009-01-14
I see I was wrong in thinking that making sda4 begin on a track would be enough to keep sfdisk from complaining, because sfdisk complained about it anyway--the fact that it doesn't start on a cylinder boundary. Fortunately though it shouldn't make any difference, or at least that's how it's always been in my experience, and also in my experience helping in the forums; in fact, I've found you will get the same type of "partition does not start on a cylinder boundary" warning if you use some Windows partitioning programs and then check the partition table in Linux. It seems that it all has to do with what geometry the partition program assigns to the HDD, and that's completely arbitrary for modern drives from what I've read. How about going ahead and booting your Live CD and try installing Ubuntu, because it looks like your partition table is ready for it now. Be sure to format the new partitions when you go through the installer. Let me know how it goes. :)

---

### Post by mastergaurav on 2009-01-14
Ah! I slept on the sofa while installing... it was 3am after all. :)

Ubuntu installed. Partitions working fine. Need to do a final check on WinXP boot-up... I don't think there should be any problem...


-Gaurav

---

