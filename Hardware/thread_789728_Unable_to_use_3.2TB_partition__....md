---
title: "Unable to use 3.2TB partition  ..."
date: 2008-05-10
forum: Hardware
---

### Post by wquiles on 2008-05-10
Hi there folks - first time posting!

I am running Ubunto 7.10 Server (using Kubuntu for the GUI), and I have a Tyan S2895 Workstation with 8GB of RAM, and two Opteron 290  Dual-Core Processors.  I am running an Nvidia 7600 256MB Video card on the PCI-E slot 1.  This MB supports 4 native SATA drives, and I have 2 of them being used:
- Raptor 10K SATA for the "/" partition and SWAP
- 1TB 7200 SATA for "/home" partition

I just installed a 3Ware 9650SE-8LPML RAID controller in the PCI-E slot 2.  On this Raid controller I have defined two containers:
- Container 1: 6x WD640GB drives in a RAID 5 Array (Raw 3.2TB array)
=> Note this is the array I can't use!

- Container 2: 2x WD 150GB 10K Raptors in a RAID 0 Array (Raw 300GB array)
=> Everything is fine on this one :-)

I compiled the latest source code for the 3Ware Raid and everything is working great from the controller side.  The 3Ware utilitiy within Ubuntu (./TW_CLI) reports that both arrays are healthy (I also get an OK at the BIOS when I reboot the machine).  Basically the drives and the two arrays are perfect.

Since the RAID5 array is larger than 2TB, I found via Google that I needed to use "parted" to work with this device.  These are the two main sites that I used:
[http://portal.itauth.com/2008/01/17/creating-large-2tb-linux-partitions]("http://portal.itauth.com/2008/01/17/creating-large-2tb-linux-partitions")

and

[http://www.unixgods.org/~tilo/linux_larger_2TB.html]("http://www.unixgods.org/~tilo/linux_larger_2TB.html")

I followed those steps, and got the drive formated as ext3 at the end.  I got no errors, and I can mount the drive to "/media/sdc1".

Here is my "/etc/fstab":
> william@workstation:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6d250087-72b1-4b3e-a40a-d02036f05119 /               ext3    defaults,errors=remount-ro,noatime,data=writeback 0       1

# /dev/sdb1
dev/sdb1        /home           ext3    defaults,noatime,data=writeback        0       2

# /dev/sdc1 (RAID5 3.2T array)
/dev/sdc1       /media/sdc1     ext3    defaults,user,noatime,data=writeback     0       2

# /dev/sdd1 (RAID0 300GB array)
/dev/sdd1       /media/sdd1     ext3    defaults,user,noatime,data=writeback     0       2

# /dev/sda2
UUID=e488ebbc-72d3-4f71-a57f-df3b9964cc93 none            swap    sw              0       0

# CD-ROM and floppy
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
william@workstation:~$ 


Here is the output of the "mount" command:
> william@workstation:/$ mount
/dev/sda1 on / type ext3 (rw,noatime,errors=remount-ro,data=writeback)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sdb1 on /home type ext3 (rw,noatime,data=writeback)
/dev/sdd1 on /media/sdd1 type ext3 (rw,noexec,nosuid,nodev,noatime,data=writeback)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
william@workstation:/$


Here is the output of the "fdisk" command, of course, the 3.2T partition being of type GTP does not print properly, but you get the idea:
> sudo fdisk -l
[sudo] password for william:

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03770376

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14346   115234213+  83  Linux
/dev/sda2           14347       18241    31286587+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00008954

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 3199.9 GB, 3199944622080 bytes
255 heads, 63 sectors/track, 389037 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005ae0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121689   977462238+  83  Linux

Disk /dev/sdd: 299.9 GB, 299978719232 bytes
255 heads, 63 sectors/track, 36470 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dbed3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       36470   292945243+  83  Linux
william@workstation:~$                         


So here is the problem.  Everytime I reboot I get an error stating that "fsck" found some problem since the filesystem size is not the same as the physical size.  I continue the boot sequence, and when I try to run this command, I get the following:
> william@workstation:/media$ cd ..
william@workstation:/$ sudo umount /dev/sdc1
william@workstation:/$ sudo fsck /dev/sdc1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
The filesystem size (according to the superblock) is 781236471 blocks
The physical size of the device is 244365559 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? yes

william@workstation:/$        

I have been "afraid" of running it since I don't know if this will make things worst since some utlities just can't handle the GTP partitions.

Now, if I try to do anything on that 3.2TB partition, I can't.  I always get this "input/output error:
> william@workstation:~$ cd /media/sdc1
william@workstation:/media/sdc1$ ls -la
total 24
drwxr-xr-x 3 root root  4096 2008-05-09 22:46 .
drwxr-xr-x 7 root root  4096 2008-05-10 18:43 ..
drwx------ 2 root root 16384 2008-05-09 22:46 lost+found
william@workstation:/media/sdc1$ sudo mkdir delme_later
mkdir: cannot create directory `delme_later': Input/output error
william@workstation:/media/sdc1$            

Ideas, suggestions?  I feel as if I am "really" close to making this work, but it eludes me ... probably something "really" simple/stupid that I am doing wrong ...

Will

---

### Post by Frak on 2008-05-10
I may be wrong, but I think you have over the amount of space that ext3 is able to use. You may want to try ext4 (possibly requires a new kernel compilation, also not stable but it supports somewhere up to about 1EB).

EDIT
I forgot that ReiserFS also supports up to around 8 TB, so you may try that instead (no recompilation, no kernel issues)

---

### Post by PilotJLR on 2008-05-10
ext3 may or may not work, depending on the block size you used... you can exceed a 2 TB partition on ext3, but only if the block size is appropriate. this link has good info on this:
[http://www.howtoadvice.com/Ext3Max/](http://www.howtoadvice.com/Ext3Max/)

---

### Post by wquiles on 2008-05-10
Thank you both.  Now things make more sense - it had to do not with an intrinsic limitation of ext3, but more with the block size (I was using defaults, so I was limited to 2TB).

Since reiserfs sounds like a really good idea in my case (lots and lots of files will go here), I went ahead and reformated the Raid5 container as a reiserfs.  Now things work!

Here is the output:
> william@workstation:/$ sudo mkreiserfs /dev/sdc1
mkreiserfs 3.6.19 (2003 [www.namesys.com](www.namesys.com))

A pair of credits:
Joshua Macdonald wrote the first draft of the transaction manager. Yuri Rupasov
did testing  and benchmarking,  plus he invented the r5 hash  (also used by the
dcache  code).  Yura  Rupasov,  Anatoly Pinchuk,  Igor Krasheninnikov,  Grigory
Zaigralin,  Mikhail  Gilula,   Igor  Zagorovsky,  Roman  Pozlevich,  Konstantin
Shvachko, and Joshua MacDonald are former contributors to the project.

Chris Mason wrote the journaling code for V3,  which was enormously more useful
to users than just waiting until  we could create a wandering log filesystem as
Hans would have unwisely done without him.
Jeff Mahoney optimized the bitmap  scanning code for V3,  and performed the big
endian cleanups.


Guessing about desired format.. Kernel 2.6.22-14-server is running.
Format 3.6 with standard journal
Count of blocks on the device: 244365552
Number of blocks consumed by mkreiserfs formatting process: 15669
Blocksize: 4096
Hash function used to sort names: "r5"
Journal Size 8193 blocks (first block 18)
Journal Max transaction length 1024
inode generation number: 0
UUID: 36c0c103-acca-4627-ad94-de6325f92a01
ATTENTION: YOU SHOULD REBOOT AFTER FDISK!
        ALL DATA WILL BE LOST ON '/dev/sdc1'!
Continue (y/n):y
Initializing journal - 0%....20%....40%....60%....80%....100%
Syncing..ok

Tell your friends to use a kernel based on 2.4.18 or later, and especially not a
kernel based on 2.4.9, when you use reiserFS. Have fun.

ReiserFS is successfully created on /dev/sdc1.
william@workstation:/$
william@workstation:/$ sudo mount -t reiserfs /dev/sdc1 /media/sdc1
[sudo] password for william:
william@workstation:/$
william@workstation:/$ cd /media/sdc1
william@workstation:/media/sdc1$ ls -la
total 4
drwxr-xr-x 4 root root   80 2008-05-10 21:03 .
drwxr-xr-x 7 root root 4096 2008-05-10 18:43 ..
william@workstation:/media/sdc1$ sudo mkdir delme_later
william@workstation:/media/sdc1$ ls -la
total 4
drwxr-xr-x 5 root root  112 2008-05-10 21:04 .
drwxr-xr-x 7 root root 4096 2008-05-10 18:43 ..
drwxr-xr-x 2 root root   48 2008-05-10 21:04 delme_later
william@workstation:/media/sdc1$      


and here is my updated "/etc/fstab" file:
> william@workstation:/media/sdc1$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6d250087-72b1-4b3e-a40a-d02036f05119 /               ext3    defaults,errors=remount-ro,noatime,data=writeback 0       1

# /dev/sdb1
dev/sdb1        /home           ext3            defaults,noatime,data=writeback        0       2

# /dev/sdc1 (RAID5 3.2T array)
/dev/sdc1       /media/sdc1     reiserfs        defaults,user,noatime,data=writeback     0       2

# /dev/sdd1 (RAID0 300GB array)
/dev/sdd1       /media/sdd1     ext3            defaults,user,noatime,data=writeback     0       2

# /dev/sda2
UUID=e488ebbc-72d3-4f71-a57f-df3b9964cc93 none            swap    sw              0       0

# CD-ROM and floppy
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
william@workstation:/media/sdc1$       


Thanks much!!!

Will

---

### Post by wquiles on 2008-05-10
Actually, I claimed victory too quickly, the resulting partition is only 1TB big, instead of 3.2TB:
> william@workstation:/media/sdc1$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6d250087-72b1-4b3e-a40a-d02036f05119 /               ext3    defaults,errors=remount-ro,noatime,data=writeback 0       1

# /dev/sdb1
dev/sdb1        /home           ext3            defaults,noatime,data=writeback        0       2

# /dev/sdc1 (RAID5 3.2T array)
/dev/sdc1       /media/sdc1     reiserfs        defaults,user,noatime,data=writeback     0       2

# /dev/sdd1 (RAID0 300GB array)
/dev/sdd1       /media/sdd1     ext3            defaults,user,noatime,data=writeback     0       2

# /dev/sda2
UUID=e488ebbc-72d3-4f71-a57f-df3b9964cc93 none            swap    sw              0       0

# CD-ROM and floppy
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
william@workstation:/media/sdc1$       

So I am going to try again to use parted to whipe everything from the start again ...  

I first tried to run "parted" again, but it looks like I first have to delete the whole thing first:
> william@workstation:/media/sdc1$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6d250087-72b1-4b3e-a40a-d02036f05119 /               ext3    defaults,errors=remount-ro,noatime,data=writeback 0       1

# /dev/sdb1
dev/sdb1        /home           ext3            defaults,noatime,data=writeback        0       2

# /dev/sdc1 (RAID5 3.2T array)
/dev/sdc1       /media/sdc1     reiserfs        defaults,user,noatime,data=writeback     0       2

# /dev/sdd1 (RAID0 300GB array)
/dev/sdd1       /media/sdd1     ext3            defaults,user,noatime,data=writeback     0       2

# /dev/sda2
UUID=e488ebbc-72d3-4f71-a57f-df3b9964cc93 none            swap    sw              0       0

# CD-ROM and floppy
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
william@workstation:/media/sdc1$       


So I opened "gparted" just to delete the existing partition, and then went into "parted" once more:
> william@workstation:/media$ sudo parted /dev/sdc
GNU Parted 1.7.1
Using /dev/sdc
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) help
  check NUMBER                             do a simple check on the file system
  cp [FROM-DEVICE] FROM-NUMBER TO-NUMBER   copy file system to another partition
  help [COMMAND]                           prints general help, or help on COMMAND
  mklabel LABEL-TYPE                       create a new disklabel (partition table)
  mkfs NUMBER FS-TYPE                      make a FS-TYPE file system on partititon NUMBER
  mkpart PART-TYPE [FS-TYPE] START END     make a partition
  mkpartfs PART-TYPE FS-TYPE START END     make a partition with a file system
  move NUMBER START END                    move partition NUMBER
  name NUMBER NAME                         name partition NUMBER as NAME
  print [free|NUMBER|all]                  display the partition table, a partition, or all devices
  quit                                     exit program
  rescue START END                         rescue a lost partition near START and END
  resize NUMBER START END                  resize partition NUMBER and its file system
  rm NUMBER                                delete partition NUMBER
  select DEVICE                            choose the device to edit
  set NUMBER FLAG STATE                    change the FLAG on partition NUMBER
  toggle [NUMBER [FLAG]]                   toggle the state of FLAG on partition NUMBER
  unit UNIT                                set the default unit to UNIT
  version                                  displays the current version of GNU Parted and copyright information
(parted) mklabel gpt
(parted) p

Disk /dev/sdc: 3200GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags

(parted) mkpartfs
Partition name?  []? RAID5
File system type?  [ext2]? reiserfs
Start? 0
End? 3200GB
(parted) p

Disk /dev/sdc: 3200GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags

(parted) mkpart
Partition name?  []? RAID5
File system type?  [ext2]? reiserfs
Start? 0
End? 3200GB
(parted) p

Disk /dev/sdc: 3200GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name   Flags
 1      17.4kB  3200GB  3200GB  reiserfs     RAID5

(parted) quit
william@workstation:/media$



Once I had the partition created, I formated it once more:
> william@workstation:/media$ sudo mkreiserfs /dev/sdc1
mkreiserfs 3.6.19 (2003 [www.namesys.com](www.namesys.com))

A pair of credits:
Vladimir Saveliev started as the most junior programmer on the team, and became
the lead programmer.  He is now an experienced highly productive programmer. He
wrote the extent  handling code for Reiser4,  plus parts of  the balancing code
and file write and file read.

Vitaly Fertman wrote  fsck for V3 and  maintains the reiserfsprogs package now.
He wrote librepair,  userspace plugins repair code, fsck for V4,  and worked on
developing libreiser4 and userspace plugins with Umka.


Guessing about desired format.. Kernel 2.6.22-14-server is running.
Format 3.6 with standard journal
Count of blocks on the device: 781236464
Number of blocks consumed by mkreiserfs formatting process: 32053
Blocksize: 4096
Hash function used to sort names: "r5"
Journal Size 8193 blocks (first block 18)
Journal Max transaction length 1024
inode generation number: 0
UUID: cd236b4e-a523-4f1f-9586-d26abe370525
ATTENTION: YOU SHOULD REBOOT AFTER FDISK!
        ALL DATA WILL BE LOST ON '/dev/sdc1'!
Continue (y/n):y
Initializing journal - 0%....20%....40%....60%....80%....100%
Syncing..ok

Tell your friends to use a kernel based on 2.4.18 or later, and especially not a
kernel based on 2.4.9, when you use reiserFS. Have fun.

ReiserFS is successfully created on /dev/sdc1.
william@workstation:/media$
william@workstation:/media$
william@workstation:/media$ sudo mount -t reiserfs /dev/sdc1 /media/sdc1
william@workstation:/media$
william@workstation:/media$ cd /media/sdc1
william@workstation:/media/sdc1$ ls -la
total 4
drwxr-xr-x 4 root root   80 2008-05-10 21:46 .
drwxr-xr-x 7 root root 4096 2008-05-10 18:43 ..
william@workstation:/media/sdc1$
william@workstation:/media/sdc1$ sudo mkdir delme_later
william@workstation:/media/sdc1$ ls -la
total 4
drwxr-xr-x 5 root root  112 2008-05-10 21:48 .
drwxr-xr-x 7 root root 4096 2008-05-10 18:43 ..
drwxr-xr-x 2 root root   48 2008-05-10 21:48 delme_later
william@workstation:/media/sdc1$

As you can see above, I can still write to it, now lets check the size problem:
> william@workstation:/media/sdc1$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            113424452   5027916 102634828   5% /
varrun                 4091920       336   4091584   1% /var/run
varlock                4091920         0   4091920   0% /var/lock
udev                   4091920        84   4091836   1% /dev
devshm                 4091920         0   4091920   0% /dev/shm
/dev/sdb1            961432072 662038212 250555860  73% /home
/dev/sdd1            288348864    195616 273505988   1% /media/sdd1
/dev/sdc1            3124850484     32840 3124817644   1% /media/sdc1
william@workstation:/media/sdc1$


Now I "truly" have the 3.2TB partition running!

Thanks again ;)

Will

---

