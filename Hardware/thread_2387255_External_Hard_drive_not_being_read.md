---
title: "External Hard drive not being read"
date: 2018-03-16
forum: Hardware
---

### Post by powerslavez on 2018-03-16
Hello all, 

My Western Digital WDBAAA2500ABK external hard drive is not mounted automatically. 
I run

```
sudo fdisk -l
``` and it shows it at [B]/dev/sdc1

[/B]When I try to mount the FAT32 partition 

```
mount -t msdos /dev/sdc1 /media/wd
```

it takes about 5 minutes to give me a superblock error. 

Putting in the command 
```
dosfsck -r /dev/sdc1
```
throws out
```
read 512 bytes at 0:Input/output error
```


To be honest I don't know what else I can do. Does it look like a controller error? or a hard drive failure?

The drive is mounted on Windows and I can see the folders, but cannot access them. Any ideas?

Thanks in advance
Cheers

---

### Post by TheFu on 2018-03-17
I didn't think that "msdos" was a valid type for a mount. Try exfat, vfat, or ntfs.
Also, manual mounts probably should be somewhere other than /media/ - where the OS tries to put things.

From the mount manpage:```

       -t, --types fstype
              The argument following the -t is used to indicate the filesystem
              type.  The filesystem types which are currently supported depend
              on  the  running  kernel.   See  /proc/filesystems and /lib/modâ
              ules/$(uname -r)/kernel/fs for a complete list of  the  filesysâ
              tems.   The  most common are ext2, ext3, ext4, xfs, btrfs, vfat,
              sysfs, proc, nfs and cifs.
```

Best to always know the exact file system type.  Partition table information doesn't guaranty anything - they are just labels.  The actual file system can easily be something different.

---

### Post by powerslavez on 2018-03-17
Sorry, my mistake - i meant to say I was mounting it with sudo mount -t vfat /dev/sdc1 /mnt/folder, since it's a FAT32 partition

In which case it gives me the superblock error. Any ideas?

---

### Post by TheFu on 2018-03-17
It would be helpful if you posted the exact commands with output. We are used to seeing that stuff.  It avoid misunderstandings.

Sometimes the only fix is to wipe the whole disk with /dev/zero, create a fresh partition table, and create new partitions.

Wouldn't hurt to look at SMART data too.

---

### Post by powerslavez on 2018-03-18
Hello! First of all thanks for all the help. 

Secondly, my purpose is to save the data off the external HDD. This is  why I'd rather not wipe the partitions, since I'm afraid of losing the  data.  
Here is the code I'm using. 

1. I first want to list all block devices. In this case the /dev/sdc is  my external hard drive I'm trying to rescue the data from. sdc1 is a  FAT32 partition while sdc2 is an Apple timecapsule. 
```

vlad@Phaedrus:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 298,1G  0 disk 
&#9500;&#9472;sda1   8:1    0   285M  0 part /boot
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9500;&#9472;sda5   8:5    0   7,6G  0 part [SWAP]
&#9500;&#9472;sda6   8:6    0  38,2G  0 part /
&#9492;&#9472;sda7   8:7    0   252G  0 part /home
sdc      8:32   0 232,9G  0 disk 
&#9500;&#9472;sdc1   8:33   0    17G  0 part 
&#9492;&#9472;sdc2   8:34   0 215,8G  0 part 
sr0     11:0    1  1024M  0 rom 

```


2. Doing blkid gives me for the sdc drive

```

vlad@Phaedrus:~$ sudo blkid
/dev/sdc1: LABEL="NATI NORMAL" UUID="8613-1C09" TYPE="vfat" 
/dev/sdc2: UUID="9e235f7f-b785-36b2-a414-1da0f17c129f" LABEL="Timemachine" TYPE="hfsplus"

```

3. Doing fdisk -l gives me back for sdc 
```

vlad@Phaedrus:~$ sudo fdisk -l
Disk /dev/sdc: 250.0 GB, 250030850048 bytes
255 heads, 63 sectors/track, 30397 cylinders, total 488341504 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe6a454f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2    35732313    17866156    b  W95 FAT32
/dev/sdc2   *    35732315   488341503   226304594+  af  HFS / HFS+

```


4. Trying to fsck the first partition gives back
```

vlad@Phaedrus:~$ sudo fsck -t vfat /dev/sdc1 -p -v
fsck from util-linux 2.20.1
fsck.fat 3.0.26 (2014-03-07)
fsck.fat 3.0.26 (2014-03-07)
Checking we can access the last sector of the filesystem
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
 Automatically removing dirty bit.
There are differences between boot sector and its backup.
This is mostly harmless. Differences: (offset:original/backup)
  71:4e/4f, 72:41/48, 73:54/4e, 74:49/45, 76:4e/54, 77:4f/49, 78:52/54
  , 79:4d/45, 80:41/4c, 81:4c/20
  Not automatically fixing this.
Boot sector contents:
System ID "BSD  4.4"
Media byte 0xf8 (hard disk)
       512 bytes per logical sector
     16384 bytes per cluster
        32 reserved sectors
First FAT starts at byte 16384 (sector 32)
         2 FATs, 32 bit entries
   4464640 bytes per FAT (= 8720 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 8945664 (sector 17472)
   1116088 data clusters (18285985792 bytes)
32 sectors/track, 255 heads
         2 hidden sectors
  35732312 sectors total
Got 397312 bytes instead of 4464360 at 16384

```


5. Trying to mount the first partition it is successful
```

vlad@Phaedrus:~$ sudo mkdir /mnt/natalie
vlad@Phaedrus:~$ sudo mount -t vfat /dev/sdc1 /mnt/natalie

```

I can open the folder and see the contents of the first partition. But  when I try to copy the contents onto my local hard drive it doesn't do  anything - I waited for about an hour
```

vlad@Phaedrus:~$ cp -v -R /mnt/natalie/Bilder /home/vlad/Desktop/Bilder
‘/mnt/natalie/Bilder’ -> ‘/home/vlad/Desktop/Bilder’
- nothing -

```



6. Trying to mount the second partition fails
```

vlad@Phaedrus:~$ sudo mkdir /mnt/natalie2
vlad@Phaedrus:~$ sudo mount -t hfsplus -o force,rw /dev/sdc2 /mnt/natalie2
mount: /dev/sdc2: can't read superblock

```


7. fsck on the second partition doesn't throw out anything
```

vlad@Phaedrus:~$ sudo fsck.hfsplus -f /dev/sdc2
[sudo] password for vlad: 
** /dev/sdc2
vlad@Phaedrus:~$

```


So, do you happen to have an idea of what I can do to save the data?

---

### Post by TheFu on 2018-03-18
Did the SMART data show that everything was fine with the disk?

I cannot help with anything HPFS related. Know nothing.  

At this stage with the vfat stuff, I'd seek out a Windows machine and use Windows tools to fix it.  It is best to use the tools for the OS that created the file system.  Every once in a while, I have a disk that uses vfat/ntfs that is required for some specialized hardware and it becomes corrupted. The only solution is to wipe it, recreate the partition table, then the partitions. I loose that data, unless there is a backup.

That applies to HPFS too - connect it to an Apple computer and use those tools.

It wouldn't hurt to use a disk imaging tool to copy the data, bit-for-bit, to new storage, then try to recover off that disk. I'd use ddrescue to make the copy.

There is a data recovery how-to here:  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)  [https://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](https://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/) might also help.

---

### Post by powerslavez on 2018-03-18
Again many thanks for your support. 
I seem to have had a stroke of luck - i was about to mount at least the FAT32 partition and I'm copying the files to my local drive as we speak. 
The Timecapsule partition looks good as well - but I'll take care of it later, the copying process is ardously slow, perhaps a sign of a failing HDD or controller. 

Enjoy your Sunday

---

### Post by TheFu on 2018-03-18
I missed that this was a USB disk.   Try a different port, different cables.  USB doesn't use the same storage commands like eSATA or regular SATA.  USB command set is limited.

After you get everything off - please check the SMART data for issues.  That is cross platform.  If everything there is fine, just wipe and reformat.  Recall that the partition wasn't un-mounted cleanly. Try not to do that anymore.

---

