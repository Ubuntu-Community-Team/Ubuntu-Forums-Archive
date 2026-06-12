---
title: "Disk space problem."
date: 2011-03-31
forum: Hardware
---

### Post by Vejineer on 2011-03-31
Hey Ubuntu users.
I am new to Ubuntu, so take care.
I am having a little problem with my diskspace. 
I am using 2 operating systems, which is ofcourse Linux, and Windows 7. I used Windows to create a new partition on my HDD, and that partition is on app. 150 gigs.
 
But now, out of now where, Ubuntu has started to say that i only have about 90 MB space left.
It is like the folders has a limit, and the system folder is full now. How can i make Ubuntu use all of the 150 GB of space?

Thanks

Vej.:D

---

### Post by garvinrick4 on 2011-03-31
What does:
```
sudo parted -l
``` (lower case L)
```
sudo fdisk -l
``` (lower case L)
post the outcome here;

---

### Post by Vejineer on 2011-03-31
I maybe should have posted this in the beginner forum, but i typed that into the Terminal, and here is the outcome:
> fdisk: ugyldigt flag -- 1

Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track

vej@ubuntu:~$ sudo parted -1
parted: ugyldigt flag -- 1
Usage: parted [-hlmsv] [-a<align>] [DEVICE [COMMAND [PARAMETERS]]...]
vej@ubuntu:~$ sudo parted -1^C
vej@ubuntu:~$


---

### Post by garvinrick4 on 2011-03-31
That is suppose to be a (lower case L) not a 1
sudo parted -l
sudo fdisk -l

---

### Post by Daxst on 2011-03-31
Im also a new Ubuntu user, loving it and i plan on making it work. But Im having similar issues to the op, i think.  have Ubuntu duelboot with windows on the C drive with a 1TB external harddrive storing all my files except both OS and a few other things i wanted to keep running if i lost power.

Disk Usage Analyzer says that / is 100% full, media is 96.5% full, Ex HD is 65.9% full, OS 34.1%.  

what i got from those commands is attached below:

```
Model: ATA ST9500325AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  9757MB  9756MB  primary   fat32           hidden, lba
 3      9758MB  15.7GB  5968MB  extended
 5      9758MB  15.4GB  5654MB  logical   ext4
 6      15.4GB  15.7GB  314MB   logical   linux-swap(v1)
 2      15.7GB  500GB   484GB   primary   ntfs            boot


Model: WD 10EAVS External (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary  fat32        lba
```[COLOR=Red]and the next one:[/COLOR]

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd9b3496e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1187     9527385+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        1912       60802   473027608    7  HPFS/NTFS
/dev/sda3            1187        1912     5828609    5  Extended
/dev/sda5            1187        1874     5521408   83  Linux
/dev/sda6            1874        1912      306176   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    c  W95 FAT32 (LBA)
```

---

### Post by Vejineer on 2011-03-31
Ok... Here is what mine says:
```
vej@ubuntu:~$ sudo parted -l
[sudo] password for vej: 
Model: ATA WDC WD6400BEVT-2 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flag
 1      1049kB  16,8GB  16,8GB  primary   ntfs         diag
 2      16,8GB  16,9GB  105MB   primary   ntfs         start
 3      16,9GB  483GB   466GB   primary   ntfs
 4      483GB   640GB   157GB   extended               lba
 5      483GB   640GB   157GB   logical   ntfs


```

and:
```
vej@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 640.1 Gb, 640135028736 byte
255 heads, 63 sectors/track, 77825 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x58b6f323

    Enhed Opstart   Start         ****     Blokke   Id  System
/dev/sda1               1        2040    16384000   27  Ukendt
/dev/sda2   *        2040        2053      102400    7  HPFS/NTFS
/dev/sda3            2053       58703   455042048    7  HPFS/NTFS
/dev/sda4           58703       77826   153601024    f  w95 udvidet (LBA)
/dev/sda5           58703       77826   153600000    7  HPFS/NTFS
vej@ubuntu:~$ 

```

---

### Post by garvinrick4 on 2011-03-31
Vejineer:

It is 157 gig but should be formatted in ext4 and it is NTFS.
sda4 is extended and sda5 is the logical and housed by extended 
sda5 is it's partition # for linux

---

### Post by garvinrick4 on 2011-03-31
Daxst;

Yours looks right starts extended at 9.7 gig and ends at 15.6 gig or so. A difference
of 5.9 gig and that is what your linux and swap are using in the logical partitions.
You got 484 gig in Windows maybe should have made a bit more room than 5.9 gig
for Linux install. 
Not to late install gparted and it is a partitioning tool. You can shrink one and make another
larger. Defrag windows a couple of times: Go to Ubuntu and open a terminal and copy and paste.
```
sudo apt-get install gparted
```Here are some sites I had bookmarked at one time or another some might
be a little old most likely but still have value.
Gparted sites: Remember can not work on any partition that is mounted (in use) use a Live CD
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted) 

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html) 

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) 

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) 

[https://help.ubuntu.com/community/Ho...sAndPartitions](https://help.ubuntu.com/community/Ho...sAndPartitions)

[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by Daxst on 2011-03-31
Thanks so much for the quck response but ill have to find a way to use it... Little after posting i walked away, comp went to sleep and now it wont make it past the login screen. Saw a post about the same thing somewhere else just haven't had a chance to try anything yet. If i end up reinstalling. ill go ahead and put more into linux!

---

### Post by suryaworldedu on 2011-04-01
me too also new to ubuntu so need help on the same topic.

---

### Post by Vejineer on 2011-04-01
So i have to reform it?
Is there any software there can reform it into ext4?

Because Windows can't

---

### Post by garvinrick4 on 2011-04-01
Can be done with a Ubuntu install CD using Try Ubuntu in gparted. But if you were to reinstall in the same partition you can format in ext4 at same time.
Here is a Show me How link.
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")

---

