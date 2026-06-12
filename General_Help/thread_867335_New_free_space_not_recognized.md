---
title: "New free space not recognized"
date: 2008-07-22
forum: General Help
---

### Post by ahmedh on 2008-07-22
Hi all, I just deleted my swap partition because the system monitor would  always show that around .5% of its 8GB was in use (the default Ubuntu install created it that large). I have 3GB of ram, of which on average only 350MB was ever used, so I figured I needed 8GB of hard drive space more urgently than I need 8GB of never-used swap space.

I deleted the swap and extended my "/" partition into the free space using the GParted live cd. However, when I booted back into Ubuntu, the file browser is still displaying the "old" amount of free space, 119GB, rather than the actual amount of free space, 128GB. Right clicking on filesystem and then checking properties also displays the wrong number. However,  when GParted (run from within Ubuntu) scans my drives, it displays the correct amount. Also, running df from the terminal says that 39% of the partition is used (this is the old number; it should now say 37% used). Any ideas why it's not updated, or how to fix it? Thanks!

---

### Post by ibuclaw on 2008-07-22
What does this command say?
```
df -hT | grep sd
```
Also, for your information, I would recommend keeping at least a 128 or 256MB swap, just incase.

May I also note that if you, at any time, wish to hibernate your PC. It would not be possible.

Regards
Iain

---

### Post by unutbu on 2008-07-22
It appears GParted does not resize the filesystem; it only resizes the partition. If the partition is, say, /dev/sda5, then type```


sudo resize2fs /dev/sda5
```

This will resize an ext3 filesystem to occupy the maximum available space in the partition.

---

### Post by ahmedh on 2008-07-22
```
/dev/sda5     ext3    203G   75G  120G  39% /

```

is the output of ```
df -hT | grep sd
```

However, the output of the resize command is

```
resize2fs 1.40.8 (13-Mar-2008)
The filesystem is already 53541802 blocks long.  Nothing to do!

```

The file system still does not recognize the space...

Edit: after some googling, I found this: [http://osdir.com/ml/gnu.parted.bugs/2005-02/msg00087.html](http://osdir.com/ml/gnu.parted.bugs/2005-02/msg00087.html)
This person had the exact same problem and gives instructions on how to fix it, but I don't understand these directions:
"Boot the Debian sarge installation / rescue disk
When the disk drivers are loaded ALT F2 to start a root console"
Also, I don't know which of his values I need to replace with my values (like partition names etc)

---

### Post by unutbu on 2008-07-23
Please post
```

sudo fdisk -l
df
sudo tune2fs -l /dev/sda5
```

---

### Post by ahmedh on 2008-07-23
Thank you. Here it is:

sudo fdisk -l:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18d85e3e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         808     6482944   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         808        3738    23540039+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            3739       30401   214167240    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5            3739       30401   214167208+  83  Linux

```

df:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5            212480080  74275284 129638108  37% /
varrun                 1545188       116   1545072   1% /var/run
varlock                1545188         0   1545188   0% /var/lock
udev                   1545188        52   1545136   1% /dev
devshm                 1545188       384   1544804   1% /dev/shm
lrm                    1545188     39760   1505428   3% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon     212480080  74275284 129638108  37% /home/ahmed/.gvfs

```

tune2fs -l /dev/sda5:

```
tune2fs 1.40.8 (13-Mar-2008)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          9133aabc-4495-4e20-8515-4e03ebb1bb3c
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              13385728
Block count:              53541802
Reserved block count:     2141672
Free blocks:              34551199
Free inodes:              13229711
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1011
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   256
Filesystem created:       Tue Jul  8 15:32:59 2008
Last mount time:          Wed Jul 23 09:31:27 2008
Last write time:          Wed Jul 23 09:31:27 2008
Mount count:              2
Maximum mount count:      35
Last checked:             Tue Jul 22 12:33:42 2008
Check interval:           15552000 (6 months)
Next check after:         Sun Jan 18 11:33:42 2009
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:		  128
Journal inode:            8
First orphan inode:       6644306
Default directory hash:   tea
Directory Hash Seed:      01812e12-a74e-441b-a841-6ca14bc300d1
Journal backup:           inode blocks

```

Thank you once again!

---

### Post by unutbu on 2008-07-24
ahmedh,

From the data you posted (df reports sizes in 1K-blocks, tune2fs reports sizes in 4K-blocks):
```
/dev/sda5:
	   4K-blocks	1K-blocks     (4 1K-blocks = 1 4K-block. 1 1K-block = 1024 bytes.)
Total	   53120020     212480080
Used       18568821     74275284
Available  32409527     129638108
Reserved   2141672	535418   
```

Used+Available+Reserved=74275284+129638108+535418=204448810 1K-blocks.
When things are working properly, Total=Used+Available+Reserved.
But in your case 
Total = 212480080 1K-blocks, while 
Used+Available+Reserved = 204448810 1K-blocks

This leaves 212480080-204448810=8031270 1K-blocks unaccounted for!
And indeed, 8031270 1K-blocks is about 8GB.
I thought the resize2fs command should have fixed this problem, but since it didn't, I really don't know the solution.

Here is a "translation" of Dell Sanders' commands from [http://osdir.com/ml/gnu.parted.bugs/2005-02/msg00087.html](http://osdir.com/ml/gnu.parted.bugs/2005-02/msg00087.html). I'm not confident his method will work for you; I have a feeling your partition table as reported by parted's print command is going to look like all the disk space is being occupied. But I could be wrong, so for what it's worth, here are Dell Sander's instructions translated for Ubuntu:

(Please note -- I haven't checked if the Ubuntu LiveCD has parted already on it. If it does, you can skip all the way down to the parted command).

Boot from the Ubuntu LiveCD.
Open a terminal
Type 

```

sudo -i               # to enter a root shell
mount /dev/sda5 /mnt  # The following commands are simply to get parted working from the Live CD.
cd /mnt/sbin
cp parted /sbin       # copying parted
cd /mnt/lib
cp -i * /lib          # copying supporting libraries
                      # Answer N to all overwrites
umount /mnt
parted
print
```

The output will look something like 
```

Disk /dev/sdb: 2049MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2048MB  2048MB  primary  ext2   
```           

(Your numbers will be different.)
```

resize 5 32.3 2048
```

Change 32.3 and 2048 to the start and end numbers appropriate for you. If you are unsure, post the output of the print command.

---

### Post by ahmedh on 2008-07-24
Alright, thank you very much. I will try this tomorrow--It's late here. I really appreciate your help.

---

### Post by ahmedh on 2008-07-24
Yes, I am a bit unsure. (Everything worked perfectly though--no errors here!)

Here is the output of the print command: 

```

Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  6640MB  6639MB  primary   ntfs              
 2      6640MB  30.7GB  24.1GB  primary   ntfs         boot 
 3      30.7GB  250GB   219GB   extended                    
 5      30.7GB  250GB   219GB   logical   ext3              

```

So should my resize command be...?

```

resize 5 30.7 250

```

What is throwing me off is that in your example, the units are different from mine (and in your resize command, the units are mixed).
Also, does parted operate in base 10 mode? Because the disk is 250GB base 10, 232GB base 2.

---

### Post by unutbu on 2008-07-24
It is as I feared -- your partition table is correct :)
Well, to put it a bit more seriously, the Start and End points of the partitions abut nicely, so there is no room to expand sda5. It is a partition of size 219GB. I believe in parted's units 1GB equals 10^9 bytes =~ 976563 1K-blocks. So 219GB =~ 219*10^9/1024 = 213867188 1K-blocks.

You undoubtedly have noticed that df claims sda5 is 212480080 1K-blocks. Why the discrepancy? This much I can tell you with certainty: parted is reporting the size of the partition, while df is reporting the size of the filesystem within the partition.

A filesystem needs some space to record its structure (FAT for Windows, superblocks+journal for ext3). These superblocks+journal occupies space in the partition that is not counted by df as part of the filesystem.

So the apparent discrepancy between 213867188 and 212480080 is illusory. The difference is merely the space being utilized by the ext3 filesystem to maintain itself.

The problem is not in the partition table -- it looks okay.

I still agree there are 8GB of space missing, but the problem lies within the filesystem, not in the partition table.

I wish I knew the answer to help you, but right now I'm stumped.

---

### Post by ahmedh on 2008-07-25
So weird. What do you suggest I do? Maybe I will create a 7 gig partition at the end of the current large one, and then 1 gig of swap?

---

### Post by unutbu on 2008-07-25
Yes, I think that is a good idea. 
Not only will you gain a small swap partition, but it will also give us an opportunity to see if you can grow(?)/shrink(?) the filesystem to a new size.

---

