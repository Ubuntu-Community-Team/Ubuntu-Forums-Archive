---
title: "what happened to my 3.2TB reiserfs partition?"
date: 2008-05-14
forum: Hardware
---

### Post by wquiles on 2008-05-14
In my prior thread I got help in creating and using a new RAID5 3.2TB partition which I formated using reiserfs as shown here:
[http://ubuntuforums.org/showthread.php?t=789728]("http://ubuntuforums.org/showthread.php?t=789728")

So after using this partition with no problems/errors whatsoever, and after writing approx. 1.5TB of data to it, I rebooted, only to get a boot error about the partition.  Here is the contents of the /var/lot/fsck/checkfs file:

> Log of fsck -C -R -A -a 
Wed May 14 20:14:19 2008

fsck 1.40.2 (12-Jul-2007)
dev/sdb1: clean, 2811/122109952 files, 17762367/244190000 blocks (check in 4 mounts)
bread: Cannot read the block (781236463): (Invalid argument).

reiserfs_open: Your partition is not big enough to contain the 
filesystem of (781236463) blocks as was specified in the found super block.
Failed to open the filesystem.

If the partition table has not been changed, and the partition is
valid  and  it really  contains  a reiserfs  partition,  then the
superblock  is corrupted and you need to run this utility with
--rebuild-sb.

/dev/sdd1: clean, 356225/36618240 files, 47896814/73236310 blocks
fsck died with exit status 8

Wed May 14 20:14:20 2008
----------------



Here is the part of the /var/log/messages file that mentions the /dev.sdc1 (which is my RAID5 3.2TB partition):

> May 14 20:15:54 workstation kernel: [  145.854801] kjournald starting.  Commit interval 5 seconds
May 14 20:15:54 workstation kernel: [  145.855421] EXT3 FS on sdb1, internal journal
May 14 20:15:54 workstation kernel: [  145.855427] EXT3-fs: mounted filesystem with writeback data mode.
May 14 20:15:54 workstation kernel: [  145.892321] ReiserFS: sdc1: found reiserfs format "3.6" with standard journal
May 14 20:15:54 workstation kernel: [  145.892367] ReiserFS: sdc1: using writeback data mode
May 14 20:15:54 workstation kernel: [  145.902798] ReiserFS: sdc1: journal params: device sdc1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
May 14 20:15:54 workstation kernel: [  145.903597] ReiserFS: sdc1: checking transaction log (sdc1)
May 14 20:15:54 workstation kernel: [  145.921731] attempt to access beyond end of device
May 14 20:15:54 workstation kernel: [  145.921734] sdc1: rw=0, want=2272790328, limit=1954924477
May 14 20:15:54 workstation kernel: [  145.921739] ReiserFS: sdc1: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [1 2 0x0 SD]
May 14 20:15:54 workstation kernel: [  145.921745] ReiserFS: sdc1: Using r5 hash to sort names
May 14 20:15:54 workstation kernel: [  145.921753] ReiserFS: sdc1: warning: xattrs/ACLs enabled and couldn't find/create .reiserfs_priv. Failing mount.
May 14 20:15:54 workstation kernel: [  145.987030] kjournald starting.  Commit interval 5 seconds
May 14 20:15:54 workstation kernel: [  145.987320] EXT3 FS on sdd1, internal journal
May 14 20:15:54 workstation kernel: [  145.987325] EXT3-fs: mounted filesystem with writeback data mode.
May 14 20:15:54 workstation kernel: [  147.793687] No dock devices found.
May 14 20:15:54 workstation kernel: [  147.886011] input: Power Button (FF) as /class/input/input5
May 14 20:15:54 workstation kernel: [  147.886030] ACPI: Power Button (FF) [PWRF]
May 14 20:15:54 workstation kernel: [  147.886066] input: Power Button (CM) as /class/input/input6
May 14 20:15:54 workstation kernel: [  147.886075] ACPI: Power Button (CM) [PWRB]
May 14 20:15:54 workstation kernel: [  148.029149] powernow-k8: Found 4 Dual Core AMD Opteron(tm) Processor 290 processors (version 2.00.00)
May 14 20:15:56 workstation kernel: [  150.511559] Failure registering capabilities with primary security module.
May 14 20:15:57 workstation kernel: [  151.587866] Failure registering capabilities with primary security module.
May 14 20:15:57 workstation kernel: [  152.314505] ppdev: user-space parallel port driver
May 14 20:15:58 workstation kernel: [  152.523125] audit(1210814158.050:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5994 profile="/usr/sbin/cupsd"
May 14 20:16:05 workstation dhcdbd: Started up.
May 14 20:16:06 workstation kernel: [  160.769152] Bluetooth: Core ver 2.11
May 14 20:16:06 workstation kernel: [  160.769205] NET: Registered protocol family 31
May 14 20:16:06 workstation kernel: [  160.769207] Bluetooth: HCI device and connection manager initialized
May 14 20:16:06 workstation kernel: [  160.769210] Bluetooth: HCI socket layer initialized
May 14 20:16:06 workstation kernel: [  160.848468] Bluetooth: L2CAP ver 2.8
May 14 20:16:06 workstation kernel: [  160.848474] Bluetooth: L2CAP socket layer initialized
May 14 20:16:06 workstation kernel: [  160.921460] Bluetooth: RFCOMM socket layer initialized
May 14 20:16:06 workstation kernel: [  160.921475] Bluetooth: RFCOMM TTY layer initialized
May 14 20:16:06 workstation kernel: [  160.921478] Bluetooth: RFCOMM ver 1.8
May 14 20:16:07 workstation dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
May 14 20:16:08 workstation kernel: [  162.665106] bridge-eth0: already up
May 14 20:16:11 workstation kernel: [  165.499871] 3dm2[7234] trap divide error rip:595d76 rsp:2ba47232b780 error:0
May 14 20:16:13 workstation dhcdbd: dhco_input_option: Value 4294967295 cannot be converted to type L 
May 14 20:16:13 workstation dhcdbd: dhco_parse_option_settings: bad option setting: new_dhcp_lease_time = 4294967295 
May 14 20:16:13 workstation dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
May 14 20:16:13 workstation dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
May 14 20:35:54 workstation -- MARK --



Note than when I run "parted", the system finds the partition properly:
> william@workstation:~$ sudo parted /dev/sdc
[sudo] password for william:
GNU Parted 1.7.1
Using /dev/sdc
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) p

Disk /dev/sdc: 3200GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name   Flags
 1      17.4kB  3200GB  3200GB  reiserfs     RAID5

(parted) quit
Information: Don't forget to update /etc/fstab, if necessary.

william@workstation:~$



but if I try to mount the partition manually, I get an error (even though this worked fine before!):

> william@workstation:~$ sudo mount -t reiserfs /dev/sdc1 /media/sdc1
mount: Operation not supported
william@workstation:~$


and here is the updated /var/messages from when I tried to mount the partition above:

> ay 14 20:43:44 workstation kernel: [ 1818.627484] ReiserFS: sdc1: found reiserfs format "3.6" with standard journal
May 14 20:43:44 workstation kernel: [ 1818.627533] ReiserFS: sdc1: using ordered data mode
May 14 20:43:44 workstation kernel: [ 1818.628215] ReiserFS: sdc1: journal params: device sdc1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
May 14 20:43:44 workstation kernel: [ 1818.629323] ReiserFS: sdc1: checking transaction log (sdc1)
May 14 20:43:44 workstation kernel: [ 1818.633058] attempt to access beyond end of device
May 14 20:43:44 workstation kernel: [ 1818.633062] sdc1: rw=0, want=2272790328, limit=1954924477
May 14 20:43:44 workstation kernel: [ 1818.633069] ReiserFS: sdc1: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [1 2 0x0 SD]
May 14 20:43:44 workstation kernel: [ 1818.633076] ReiserFS: sdc1: Using r5 hash to sort names
May 14 20:43:44 workstation kernel: [ 1818.633085] ReiserFS: sdc1: warning: xattrs/ACLs enabled and couldn't find/create .reiserfs_priv. Failing mount.


The boot message stated something about running the fsck file with the "--rebuild-sb" option, but I don't want to do anything to the array until I am sure since I am fairly convinced all of the data is still there intact.

What I was trying to do which required the reboot was to move my /home directory to a new hard drive, so I had changed the "/home" mount point in /etc/fstab.  That is all - as soon as I rebooted I got the error, so I copied the original /etc/fstab back, but the error continues now every time I reboot.

Recommendations/ideas?  What would have caused the error when I rebooted while it ran fine before the reboot?

Will

---

### Post by wquiles on 2008-05-15
Looking at when it was formated, this partition had in fact 781236464 blocks long:
> william@workstation:/media$ sudo mkreiserfs /dev/sdc1
mkreiserfs 3.6.19 (2003 [www.namesys.com](www.namesys.com))

A pair of credits:
Vladimir Saveliev started as the most junior programmer on the team, and became
the lead programmer. He is now an experienced highly productive programmer. He
wrote the extent handling code for Reiser4, plus parts of the balancing code
and file write and file read.

Vitaly Fertman wrote fsck for V3 and maintains the reiserfsprogs package now.
He wrote librepair, userspace plugins repair code, fsck for V4, and worked on
developing libreiser4 and userspace plugins with Umka.


Guessing about desired format.. Kernel 2.6.22-14-server is running.
Format 3.6 with standard journal
Count of blocks on the device: 781236464
Number of blocks consumed by mkreiserfs formatting process: 32053
Blocksize: 4096
Hash function used to sort names: "r5"
Journal Size 8193 blocks (first block 1
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


When I attempted to run "sudo reiserfsck --rebuild-sb /dev/sdc1", I get the following information/error:
> william@workstation:~$ sudo reiserfsck --rebuild-sb /dev/sdc1
reiserfsck 3.6.19 (2003 [www.namesys.com](www.namesys.com))

*************************************************************
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to [email]reiserfs-list@namesys.com[/email], **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  [www.namesys.com/support.html](www.namesys.com/support.html). **
*************************************************************

Will check superblock and rebuild it if needed
Will put log info to 'stdout'

Do you want to run this program?[N/Yes] (note need to type Yes if you do):Yes

Did you use resizer(y/n)[n]: n
rebuild-sb: wrong block count occured (781236464), fixed (244365552)
rebuild-sb: wrong bitmap number occured (23842), fixed (7458)
rebuild-sb: wrong root block occured (284098790), zeroed
rebuild-sb: wrong free block count occured (324461171), zeroed
Reiserfs super block in block 16 on 0x821 of format 3.6 with standard journal
Count of blocks on the device: 244365552
Number of bitmaps: 7458
Blocksize: 4096
Free blocks (count of blocks - used [journal, bitmaps, data, reserved] blocks): 0
Root block: 0
Filesystem is clean
Tree height: 5
Hash function used to sort names: "r5"
Objectid map size 972, max 972
Journal parameters:
        Device [0x0]
        Magic [0xc3ded65]
        Size 8193 blocks (including 1 for journal header) (first block 18)
        Max transaction length 1024 blocks
        Max batch size 900 blocks
        Max commit age 30
Blocks reserved by journal: 0
Fs state field: 0x1:
         some corruptions exist.
sb_version: 2
inode generation number: 353371
UUID: cd236b4e-a523-4f1f-9586-d26abe370525
LABEL:
Set flags in SB:
        ATTRIBUTES CLEAN
Is this ok ? (y/n)[n]: n
Super block was not written
william@workstation:~$        

Note that the reiserfsck states that there is a wrong block count (781236464) and it wants to fix it as (244365552).  Looking at the original formatting output, the larger value of 781236464 is "the" correct value:

original size: 7812366464 blocks * 4096 block size (bytes) = 3.2TB

size the utility claims is correct: 244365552 * 4096 (bytes) = 1.0TB

So the real questions are:
1) Why the utility things 1TB is the correct size when 3.2TB is the correct size?

2) How can I fix this so that the correct 3.2TB size is restored and so that I can access my partition again?

By the way, the RAID controller still says that the 3.2TB partition is perfect - no problems in any of the drives.

Will

---

### Post by wquiles on 2008-05-16
Well, after Googling for hours, I can't find anything that can explain what happened.  Since I have all of the data, nothing was really lost, so I am starting all over, but trying EXT3 this time:
> william@workstation:~$ sudo parted /dev/sdc
GNU Parted 1.7.1
Using /dev/sdc
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) p

Disk /dev/sdc: 3200GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name   Flags
 1      17.4kB  3200GB  3200GB  reiserfs     RAID5

(parted) rm 1
(parted) p

Disk /dev/sdc: 3200GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags

(parted)
(parted) mklabel gpt
(parted)
(parted) p

Disk /dev/sdc: 3200GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags

(parted) mkpart
Partition name?  []? RAID5
File system type?  [ext2]? ext3
Start? 0
End? 3200GB
(parted)
(parted) p

Disk /dev/sdc: 3200GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name   Flags
 1      17.4kB  3200GB  3200GB  reiserfs     RAID5

(parted)
(parted) q
william@workstation:~$
william@workstation:~$ sudo fdisk -l

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
william@workstation:~$ sudo mkfs.ext3 -m0 /dev/sdc1
mke2fs 1.40.2 (12-Jul-2007)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
390627328 inodes, 781236471 blocks
0 blocks (0.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
23842 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000, 214990848, 512000000, 550731776, 644972544

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 21 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
william@workstation:~$



Here is my new /etc/fstab:
> william@workstation:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6d250087-72b1-4b3e-a40a-d02036f05119 /               ext3    defaults,errors=remount-ro,noatime,data=writeback 0       1

# /dev/sda2
UUID=e488ebbc-72d3-4f71-a57f-df3b9964cc93 none            swap    sw              0       0

# /dev/sdb1
UUID=79ca7c76-03bc-4a66-bb89-7f992734c308 /home           ext3    defaults,noatime,data=writeback        0       2

# /dev/sdc1
UUID=8127b451-d090-4582-b854-3ba32108adc5 /media/sdc1     ext3    defaults,noatime,data=writeback        0        2

# /dev/sdd1
UUID=b6446c34-945c-4ef3-bd49-b13f958251aa /media/sdd1     ext3    defaults,noatime,data=writeback        0        2

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
william@workstation:~$



Here I mounted it:
> william@workstation:~$
william@workstation:~$ sudo mount -t ext3 /dev/sdc1 /media/sdc1
william@workstation:~$
william@workstation:~$ mount
/dev/sda1 on / type ext3 (rw,noatime,errors=remount-ro,data=writeback)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sdb1 on /home type ext3 (rw,noatime,data=writeback)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdc1 on /media/sdc1 type ext3 (rw)
william@workstation:~$




Lets see what happens now ...

Will

---

### Post by wquiles on 2008-05-16
Well, I have the same exact problem now with EXT3 as I did earlier with REISERFS.  It works great "before" I reboot.  After I reboot, the system keeps insisting this is really a 1TB partition instead of a 3.2TB partition (/dev/sdc1 is the RAID5 3.2TB partition):

> william@workstation:~$ sudo umount /dev/sdc1
[sudo] password for william:
william@workstation:~$
william@workstation:~$ mount
/dev/sda1 on / type ext3 (rw,noatime,errors=remount-ro,data=writeback)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sdb1 on /home type ext3 (rw,noatime,data=writeback)
/dev/sdd1 on /media/sdd1 type ext3 (rw,noatime,data=writeback)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
william@workstation:~$
william@workstation:~$ sudo fdisk -l

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
william@workstation:~$ sudo fsck /dev/sdc1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
The filesystem size (according to the superblock) is 781236471 blocks
The physical size of the device is 244365559 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? yes

william@workstation:~$



Ideas/suggestions?

Will

---

### Post by wquiles on 2008-05-16
If no-one has seen this before in this forum, are there other forums who might be a good place to post this question/problem?

Will

---

### Post by jwuorenmaa on 2008-05-17
Wquiles,
I'm having the exact same issue, and it's driving me nuts.  I'm running 64bit 7.04 on Intel Xeon with 6TB Areca raid 6.  Partioned as GPT with parted, formated ext3, mounts fine.  I then copy files to the array, a-okay.  Run fsck on unmounted array, everything still fine.  Reboot, array corrupt, fsck complains about file system being larger than partition,  can't read superblock/s, i/o errors, blah blah blah.  Another user on this forum (Yfrwlf) also had these issues,  I'd search for his/her posts.  Anyway,  most people were saying that parted 1.7.X was the proplem, that you needed to use 1.8.X.  So I installed parted 1.8.9 from Debian packages, had to update a boat load of dependancies, and had high hopes going through the whole process again. Guess what It did, the same corruption bologna on reboot. I got tired and went home,  that was tonight. Other users said that the kernel has to be compiled with gpt support, which it ought to be by default but need I need to check.  My next attempt next week is to boot from a hardy heron installation and see what happens.  All I can say is Ubuntu really is great when you get it working, but is a big ol' pain in the butt to get it there.  Don't even get me started with the whole LCD display refresh rate-resolution hell that even 8.04 puts users through, it's really silly if you think about it.  I'll let you know if I find a workable solution.
-john

---

### Post by wquiles on 2008-05-17
John,

Thanks much for your post - now I don[http://www.unixgods.org/~tilo/linux_larger_2TB.html[/IMG]"][IMG]http://www.unixgods.org/~tilo/linux_larger_2TB.html[/IMG]]("[IMG)'t feel alone on this, and I have higher hopes of figuring this stuff out :)

Besides the earlier links I found:
[http://www.unixgods.org/~tilo/linux_larger_2TB.html]("http://www.unixgods.org/~tilo/linux_larger_2TB.html")

[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html]("http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html")


now thanks to you I found yet another one:
[http://blog.interrupt3h.com/?p=27]("http://blog.interrupt3h.com/?p=27")


This one actually states (like you did above) that parted 1.7 is broken!!!.  It states again to try using parted 1.8.8, which I got, but it took some work to get running.

Here is me trying the new parted (note that I had to manually copy a file like it says in the comments on that last link above):
> william@workstation:~/Parted_1.8.8/parted-1.8.8/libparted/.libs$ sudo cp libparted-1.8.so.8 /lib
[sudo] password for william:
[email]william@workstation:~/Parted_1.8.8/parted-1.8.8/libparted/.libs[/email]$ cd ..
william@workstation:~/Parted_1.8.8/parted-1.8.8/libparted$ cd..
bash: cd..: command not found
william@workstation:~/Parted_1.8.8/parted-1.8.8/libparted$ cd ..
william@workstation:~/Parted_1.8.8/parted-1.8.8$ sudo parted
Warning: Unable to open /dev/hda read-write (Read-only file system).  /dev/hda has been opened read-only.
GNU Parted 1.8.8
Using /dev/hda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) q
william@workstation:~/Parted_1.8.8/parted-1.8.8$
william@workstation:~/Parted_1.8.8/parted-1.8.8$ sudo parted /dev/sdc
GNU Parted 1.8.8
Using /dev/sdc
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) p
Warning: /dev/sdc contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition
table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you
deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?
Yes/No? Yes
Model: AMCC 9650SE-8LP DISK (scsi)
Disk /dev/sdc: 3200GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name   Flags
 1      17.4kB  3200GB  3200GB  ext3         RAID5

(parted) rm 1
Warning: /dev/sdc contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition
table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you
deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?
parted: invalid token: 1
Yes/No? Yes
Partition number? 1
(parted) p
Model: AMCC 9650SE-8LP DISK (scsi)
Disk /dev/sdc: 3200GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags

(parted)
(parted) help
  check NUMBER                             do a simple check on the file system
  cp [FROM-DEVICE] FROM-NUMBER TO-NUMBER   copy file system to another partition
  help [COMMAND]                           print general help, or help on COMMAND
  mklabel,mktable LABEL-TYPE               create a new disklabel (partition table)
  mkfs NUMBER FS-TYPE                      make a FS-TYPE file system on partititon NUMBER
  mkpart PART-TYPE [FS-TYPE] START END     make a partition
  mkpartfs PART-TYPE FS-TYPE START END     make a partition with a file system
  move NUMBER START END                    move partition NUMBER
  name NUMBER NAME                         name partition NUMBER as NAME
  print [devices|free|list,all|NUMBER]     display the partition table, available devices, free space, all found partitions, or a
        particular partition
  quit                                     exit program
  rescue START END                         rescue a lost partition near START and END
  resize NUMBER START END                  resize partition NUMBER and its file system
  rm NUMBER                                delete partition NUMBER
  select DEVICE                            choose the device to edit
  set NUMBER FLAG STATE                    change the FLAG on partition NUMBER
  toggle [NUMBER [FLAG]]                   toggle the state of FLAG on partition NUMBER
  unit UNIT                                set the default unit to UNIT
  version                                  display the version number and copyright information of GNU Parted
(parted)
(parted) mkpart
Partition name?  []? RAID5
File system type?  [ext2]? ext3
Start? 0
End? 3200GB
(parted)
(parted) p
Model: AMCC 9650SE-8LP DISK (scsi)
Disk /dev/sdc: 3200GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name   Flags
 1      17.4kB  3200GB  3200GB  ext3         RAID5

(parted)
(parted) p
Model: AMCC 9650SE-8LP DISK (scsi)
Disk /dev/sdc: 3200GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name   Flags
 1      17.4kB  3200GB  3200GB  ext3         RAID5

(parted) q
Information: You may need to update /etc/fstab.

william@workstation:~/Parted_1.8.8/parted-1.8.8$ sudo parted /dev/sdc
GNU Parted 1.8.8
Using /dev/sdc
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) p
Model: AMCC 9650SE-8LP DISK (scsi)
Disk /dev/sdc: 3200GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name   Flags
 1      17.4kB  3200GB  3200GB  ext3         RAID5

(parted) q
william@workstation:~/Parted_1.8.8/parted-1.8.8$


---

### Post by wquiles on 2008-05-17
OK, it works!!!

So in the end, it was simply an outdated, buggy parted!

The last link I posted has the exact details how to install parted-1.8.8, including the comments by RoundSparrow about the manual copy of a lib to make it run.

I have now rebooted several times, copied files and directories in between reboots, and every time I reboot everything is there as it should ;)

Will

---

### Post by jwuorenmaa on 2008-05-19
I'm glad to hear your system is now working.  I plan on installing parted 1.8.8 today, and will report my findings.

-john

---

### Post by wquiles on 2008-05-20
Cool - good luck!

Basically, the new parted fixes the superblock and correctly creates the fake name so that the OS properly recognizes the partition as a "large" one.  If you look carefully at the output of the new parted, you will see that in fact it says that the fake name was not done right.

I did not even had to reformat the drive.  All of the data was actually still there :)

Will

---

### Post by fadetoblack82 on 2009-03-11
is anyone still having this issue? i recently setup a 3TB raid5 array and i seem to be having this issue. the worst part is that im using the new ubuntu 9.04 alpha 5 which has the new version of parted.

1. i checked the default kernel config for the one i am using (2.6.28.8-generic) and verified that it has the following:
```

CONFIG_EFI=y
CONFIG_EFI_PARTITION=y
CONFIG_EFI_VARS=y

```

2. 
```

ar@nas:~$ parted -v
parted (GNU parted) 1.8.8

```

i created a gpt partition on my raid volume using parted, and then did mkfs.ext4. everything was fine and i copied about 1TB of data onto the drive. used it with zero issues - and then reboot. after rebooting, i got the following in /var/log/fsck/checkfs:
```

Log of fsck -C3 -R -A -a
Wed Mar 11 04:40:31 2009

fsck 1.41.4 (27-Jan-2009)
/dev/sdb1: Note: if several inode or block bitmap blocks or part
of the inode table require relocation, you may wish to try
running e2fsck with the '-b 32768' option first.  The problem
may lie only with the primary block group descriptors, and
the backup block group descriptors may be OK.

/dev/sdb1: Block bitmap for group 128 is not in group.  (block 877310461)


/dev/sdb1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)
/dev/sda7: clean, 624/12214272 files, 828612/48827551 blocks
fsck died with exit status 4

Wed Mar 11 04:40:31 2009

```

i thought this was an old issue and would have been fixed by now. im even using the new verion of parted and the kernel is configured for gpt. any ideas?

---

### Post by wquiles on 2009-03-12
Yes, I had the problem, and it was solved, when I installed parted-1.8.8 !!!

Basically the parted that came with my Ubuntu was buggy :(

my steps were:

sudo parted /dev/sdc
(parted) mklabel gpt
(parted) print /*to get the sizes
(parted) mkpart primary 0 3200GB
(parted) quit

sudo mkfs.ext3 -m0 /dev/sdc1

sudo mount -t ext3 /dev/sdc1 /mount_point


I hope this helps you ;)

Will

---

### Post by HDave on 2009-05-14
Wow -- thanks for this post.  I have a 3Ware 9650SE and thought I was losing my mind!!!!  I had no idea about "GPT", let alone that "disklabel" meant "kind of partition table".  WTF???

---

