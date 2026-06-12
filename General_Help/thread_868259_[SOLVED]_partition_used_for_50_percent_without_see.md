---
title: "[SOLVED] partition used for 50 percent without seeing any files/folder"
date: 2008-07-23
forum: General Help
---

### Post by hydratic on 2008-07-23
Hello ppl,

i am using ubuntu 7.10 with kernel 2.6.22-15 generic. I am using an external usb 2.0 hardisk for file storage.

The usb harddisk is 300 Gig. I have partioned it in 6 partitions of 50 Gig
One of my partition is used for 49 percent. I have confirmed this with
-- nautilus
-- the command du and df
-- gparted

I have emptied my trash

I have made sure no files are hidden
-- ctrl h in nautilus
-- ls -all on shell prompt

I can ofcourse reformat the partition but i would like know the source of this issue

Can anyone tell me how to check the 49 percent of unaccounted disk space ?

thanks in advance for replies

hydratic

---

### Post by unutbu on 2008-07-23
Please post

```
sudo fdisk -l
df
sudo tune2fs -l /dev/sda3
```

changing /dev/sda3 to the partition that is 49% full.

---

### Post by hydratic on 2008-07-24
```
xxx@xxx:~$ sudo fdisk -l 

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00008c90

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3647    29294496   83  Linux
/dev/sda2            3648        4620     7815622+  82  Linux swap / Solaris
/dev/sda3            4621        7052    19535040    5  Extended
/dev/sda4            7053       18241    89875642+  83  Linux
/dev/sda5            4621        7052    19535008+  83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x072039d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6635    53295606    7  HPFS/NTFS
/dev/sdb2            6636       38913   259273035    f  W95 Ext'd (LBA)
/dev/sdb5            6636       13301    53544613+   7  HPFS/NTFS
/dev/sdb6           13302       19654    51030441    7  HPFS/NTFS
/dev/sdb7           19655       26165    52299576    b  W95 FAT32
/dev/sdb8           26166       32539    51199123+   7  HPFS/NTFS
/dev/sdb9           32540       38913    51199123+   7  HPFS/NTFS
xxx@xxx:~$ 

```

This is kinda of strange. According to fdisk i am using NTFS partition for my /dev/sdb drive. When i run: ```
sudo gparted /dev/sdb
``` gparted tells me i am using ext2 for my disks 

[IMG]http://home.telfort.nl/dumper/forum/gparted.jpg[/IMG]

```
xxx@xxx:~$ df /dev/sdb7
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb7             51475528  20992028  27868524  43% /media/diversen
xxx@xxx:~$ 
 
```

```
xxx@xxx:~$ sudo tune2fs -l /dev/sdb7
tune2fs 1.40.2 (12-Jul-2007)
Filesystem volume name:   diversen
Last mounted on:          <not available>
Filesystem UUID:          f4e4a410-91a3-4f3c-8685-5dd62658ee43
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      filetype sparse_super large_file
Default mount options:    (none)
Filesystem state:         not clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              6549984
Block count:              13074432
Reserved block count:     653744
Free blocks:              5214222
Free inodes:              6532432
First block:              0
Block size:               4096
Fragment size:            4096
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16416
Inode blocks per group:   513
Filesystem created:       Sat Feb 17 06:47:34 2007
Last mount time:          Sat Feb 17 13:58:46 2007
Last write time:          Thu Jul 24 00:04:08 2008
Mount count:              326
Maximum mount count:      24
Last checked:             Sat Feb 17 06:47:34 2007
Check interval:           15552000 (6 months)
Next check after:         Thu Aug 16 07:47:34 2007
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Default directory hash:   tea
Directory Hash Seed:      ab1a2bcd-5d6e-4bc1-9a19-dc565a38fee1

```

I see that the file system is not clean. I want to do a fsck.ext2 on this partition but i am waiting for the input from this thread

---

### Post by hydratic on 2008-07-24
unutbu thank you for replying

I did do a fsck.ext2 for the partition. It did alot of fixing 
i do see 50 Gigs available :)

however i still think to see the difference between 
```
sudo fdisk -l 
``` 

and 

```
sudo gparted
```

see my image in the previous post.

Can someone help me to clarify this ?

hydratic

---

### Post by unutbu on 2008-07-24
fdisk -l is showing the "partition type" (see [http://tldp.org/HOWTO/Partition/partition-types.html](http://tldp.org/HOWTO/Partition/partition-types.html)) while gparted is showing the filesystem type. 

According to [http://www.win.tue.nl/~aeb/partitions/partition_types-2.html](http://www.win.tue.nl/~aeb/partitions/partition_types-2.html), some operating systems like Windows will read a partition table and ignore all partitions that are of a certain type. It seems likely that you used a non-linux partition editor to create sdb* and it chose non-linux partition types by default.

I do not know if there is any problem having a partition type that does not match the filesystem type. I've never explored this. Wanting to err on the side of caution, I've always just made my partition types match the filesystem types.

---

### Post by danwood76 on 2008-07-24
This can be caused by using different partitioners to partition the disk as they all use slightly different systems.

You can change the partition types within fdisk, which I would do as its better to have them matching ;)

---

### Post by hydratic on 2008-07-24
thank you very much for the responses/help.

I will mark this thread as SOLVED

hydratic

---

### Post by unutbu on 2008-07-24
Good news, hydratic. You can change partition types without having to destroy your partitions: Here is an example, using a USB flash key:

I used fdisk to create a partition table similar to your sdb drive.
```
not@all:~/test% sudo fdisk -l /dev/sdb

Disk /dev/sdb: 2004 MB, 2004877312 bytes
191 heads, 11 sectors/track, 1863 cylinders
Units = cylinders of 2101 * 512 = 1075712 bytes
Disk identifier: 0x000961c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         300      315144+   7  HPFS/NTFS
/dev/sdb2             301        1863     1641931+   f  W95 Ext'd (LBA)
/dev/sdb5             301         600      315144+   7  HPFS/NTFS
/dev/sdb6             601        1863     1326776    b  W95 FAT32
```

However, I created ext3 filesystems in sdb1, sdb5 and sdb6:
```
not@all:~/test% mkfs.ext3 /dev/sdb1
not@all:~/test% mkfs.ext3 /dev/sdb5
not@all:~/test% mkfs.ext3 /dev/sdb6

```
So that GParted looks like the attachment (see below).

Put some data on the disk:
```
not@all:~/test% mkdir $HOME/test/sdb5
not@all:~/test% mkdir $HOME/test/sdb6
not@all:~/test% sudo mount /dev/sdb5 $HOME/test/sdb5
not@all:~/test% sudo mount /dev/sdb6 $HOME/test/sdb6
not@all:~/test% echo "This is a test, sdb5" > $HOME/test/sdb5/testfile
not@all:~/test% echo "Hello sdb6" > $HOME/test/sdb6/testfile
not@all:~/test% ls -l $HOME/test/sdb5
total 13
drwx------ 2 root   root   12288 2008-07-24 08:13 lost+found
-rw-r--r-- 1 not not    21 2008-07-24 08:18 testfile
not@all:~/test% ls -l $HOME/test/sdb6
total 20
drwx------ 2 root   root   16384 2008-07-24 08:13 lost+found
-rw-r--r-- 1 not not    11 2008-07-24 08:18 testfile
not@all:~/test% sudo umount /dev/sdb5
not@all:~/test% sudo umount /dev/sdb6
```

Ok, now we change the partition types using fdisk:
```
not@all:~/test% sudo fdisk /dev/sdb

The number of cylinders for this disk is set to 1863.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

```
Type p to print the current partition table.
Type t to change the partition type
Type w to write partition table to disk.
Type m to see all the commands available.

Changing sdb1 to type 83 (Linux):
```

Command (m for help): t
Partition number (1-6): 1
Hex code (type L to list codes): 83
Changed system type of partition 1 to 83 (Linux)

Command (m for help): t
Partition number (1-6): 5
Hex code (type L to list codes): 83
Changed system type of partition 5 to 83 (Linux)

Command (m for help): t
Partition number (1-6): 6
Hex code (type L to list codes): 83
Changed system type of partition 6 to 83 (Linux)

Write the new partition table to disk. There are warnings, but it seems to work anyway.
Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.

WARNING: If you have created or modified any DOS 6.x
partitions, please see the fdisk manual page for additional
information.
Syncing disks.
```

The new partition table has Linux partition types:
```
not@all:~/test% sudo fdisk -l /dev/sdb

Disk /dev/sdb: 2004 MB, 2004877312 bytes
191 heads, 11 sectors/track, 1863 cylinders
Units = cylinders of 2101 * 512 = 1075712 bytes
Disk identifier: 0x000961c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         300      315144+  83  Linux
/dev/sdb2             301        1863     1641931+   f  W95 Ext'd (LBA)
/dev/sdb5             301         600      315144+  83  Linux
/dev/sdb6             601        1863     1326776   83  Linux

```
And the data is still there:
```
not@all:~/test% sudo mount /dev/sdb5 $HOME/test/sdb5
not@all:~/test% sudo mount /dev/sdb6 $HOME/test/sdb6
not@all:~/test% ls -l $HOME/test/sdb5
total 13
drwx------ 2 root   root   12288 2008-07-24 08:13 lost+found
-rw-r--r-- 1 not not    21 2008-07-24 08:18 testfile
not@all:~/test% ls -l $HOME/test/sdb6
total 20
drwx------ 2 root   root   16384 2008-07-24 08:13 lost+found
-rw-r--r-- 1 not not    11 2008-07-24 08:18 testfile
not@all:~/test% cat $HOME/test/sdb5/testfile 
This is a test, sdb5
not@all:~/test% cat $HOME/test/sdb6/testfile 
Hello sdb6

```

---

