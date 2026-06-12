---
title: "Installing Ubuntu with xp on first :o"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by rhyz on 2009-09-09
Hello i have been off ubuntu for half a year and back to xp but i am wierdly missing ubuntu. 

i currently have a 20gb hdd with xp on all. FAT32 format.

I like using gparted to partition the disk as i understand it. but i only have 250 mb ram so ubuntu struggles to run on my laptop in live mode. So i need to get some swap space before i try and install ubuntu.

Is there a way to do it on xp (for free)?

just another question how many mb of updates have got to be done from fresh install???

---

### Post by presence1960 on 2009-09-09
> **rhyz said:**
> Hello i have been off ubuntu for half a year and back to xp but i am wierdly missing ubuntu. 

i currently have a 20gb hdd with xp on all. FAT32 format.

I like using gparted to partition the disk as i understand it. but i only have 250 mb ram so ubuntu struggles to run on my laptop in live mode. So i need to get some swap space before i try and install ubuntu.

Is there a way to do it on xp (for free)?

just another question how many mb of updates have got to be done from fresh install???
 you might want to use the alternate text based installer. get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").
The Live CD will definitely struggle with that amount of RAM, if it will even run at all.

I would recommend at minimum 7-8 GB for Ubuntu root partition. This way you have enough space to install software & Updates.

You can't install a swap partition from windows. First off there is not an OS installed to use swap even if you could do it from windows. The Live CD does not use swap.

I would back up any data you don't want to lose. Then defrag XP at least once or twice prior to resizing the XP partition. I would also turn off system restore until after Ubuntu is installed.

I would recommend using [Gparted Live Cd ]("http://gparted.sourceforge.net/livecd.php")to shrink XP partition and then create two partitions for Ubuntu. One as ext 3 and the other as swap(linux-swap). or just use the install side by side option in Ubuntu installer without creating partitions beforehand. Either way will work. be sure to move the slider to allot correct space for Ubuntu on the side by side install.

Depending on how much data you have on XP you are really going to be cutting it close. You don't want to take away from XP so the partition is close to capacity. You may not be able to install Ubuntu if this is the case. You may need to add a hard disk. it all depends on the size of your XP install & data on XP.

---

### Post by jerrrys on 2009-09-09
[https://help.ubuntu.com/9.04/installation-guide/i386/minimum-hardware-reqts.html](https://help.ubuntu.com/9.04/installation-guide/i386/minimum-hardware-reqts.html)

---

### Post by rhyz on 2009-09-09
ok i installed it i managed to do it with live cd WOWness and i just made a swap space asap and turned it on and everything went smooth from there i have 150 mb worth of updates which is lovley compared to windows and finally i have one problem and it was using gparted to remove a small swapspace and make a ext3 extend heres what gparted saved...

```

GParted 0.4.3

Libparted 1.8.8
Delete Logical Partition (linux-swap, 243.14 MiB) from /dev/sda  00:00:14    ( SUCCESS )
     	
calibrate /dev/sda7  00:00:01    ( SUCCESS )
     	
path: /dev/sda7
start: 38572128
end: 39070079
size: 497952 (243.14 MiB)
delete partition  00:00:13    ( SUCCESS )

========================================
Grow /dev/sda6 from 3.98 GiB to 4.21 GiB  00:04:00    ( ERROR )
     	
calibrate /dev/sda6  00:00:00    ( SUCCESS )
     	
path: /dev/sda6
start: 30234393
end: 38572064
size: 8337672 (3.98 GiB)
calculate new size and position of /dev/sda6  00:00:00    ( SUCCESS )
     	
requested start: 30234393
requested end: 39070079
requested size: 8835687 (4.21 GiB)
new start: 30234393
new end: 39070079
new size: 8835687 (4.21 GiB)
check file system on /dev/sda6 for errors and (if possible) fix them  00:01:58    ( SUCCESS )
     	
e2fsck -f -y -v /dev/sda6
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

97802 inodes used (37.53%)
48 non-contiguous files (0.0%)
71 non-contiguous directories (0.1%)
# of inodes with ind/dind/tind blocks: 4030/33/0
545132 blocks used (52.31%)
0 bad blocks
1 large file

82653 regular files
9743 directories
69 character device files
26 block device files
2 fifos
0 links
5299 symbolic links (4841 fast symbolic links)
1 socket
--------
97793 files
e2fsck 1.41.4 (27-Jan-2009)
grow partition from 3.98 GiB to 4.21 GiB  00:00:13    ( SUCCESS )
     	
old start: 30234393
old end: 38572064
old size: 8337672 (3.98 GiB)
new start: 30234393
new end: 39070079
new size: 8835687 (4.21 GiB)
check file system on /dev/sda6 for errors and (if possible) fix them  00:01:48    ( SUCCESS )
     	
e2fsck -f -y -v /dev/sda6
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

97802 inodes used (37.53%)
48 non-contiguous files (0.0%)
71 non-contiguous directories (0.1%)
# of inodes with ind/dind/tind blocks: 4030/33/0
545132 blocks used (52.31%)
0 bad blocks
1 large file

82653 regular files
9743 directories
69 character device files
26 block device files
2 fifos
0 links
5299 symbolic links (4841 fast symbolic links)
1 socket
--------
97793 files
e2fsck 1.41.4 (27-Jan-2009)
grow file system to fill the partition  00:00:01    ( ERROR )
     	
resize2fs /dev/sda6
     	
resize2fs 1.41.4 (27-Jan-2009)
Please run 'e2fsck -f /dev/sda6' first.

========================================

```

any ideas running what it asks gives ...

```

sudo e2fsck -f /dev/sda6
e2fsck 1.41.4 (27-Jan-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda6: 97802/260608 files (0.1% non-contiguous), 545132/1042209 blocks

```

---

