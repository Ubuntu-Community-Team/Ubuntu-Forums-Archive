---
title: "Ubuntu 9.04 FakeRaid Issue"
date: 2009-06-28
forum: Installation &amp; Upgrades
---

### Post by siliond on 2009-06-28
I followed instructions posted here, but got stuck in the same place as with 8.10, step **9.l.ii.** :
> grub> find /boot/grub/stage1

**returns**
```
find /boot/grub/stage1

Error 15: File not found
```

**/dev/mapper**
```
root@ubuntu:/dev/mapper# ls
control            isw_dfeffeagbe_Volume01  isw_dfeffeagbe_Volume06
isw_dfeffeagbe_Volume0    isw_dfeffeagbe_Volume05  isw_dfeffeagbe_Volume07
```

**/boot/grub files, in target**
```
root@ubuntu:/boot/grub# ls
e2fs_stage1_5  jfs_stage1_5    reiserfs_stage1_5  stage2       xfs_stage1_5
fat_stage1_5   minix_stage1_5  stage1          stage2_eltorito
```

**grub command sequence**
```
root@ubuntu:/# grub --no-curses
Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature
Unknown partition table signature
Unknown partition table signature

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> device (hd0) /dev/mapper/isw_dfeffeagbe_Volume0
device (hd0) /dev/mapper/isw_dfeffeagbe_Volume0
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
```

---

### Post by P3P on 2009-06-28
Which tool have you used for partitioning?

Grub tells you "Unknown partition table signature".
I experienced some problems with partitions in the same step.

Usually "cfdisk" and "parted" make different partition tables in which "partition type" is not the same.

I would try a couple of partition tools and gather some information about "partition type" field.

---

### Post by ronparent on 2009-06-28
Your list of /boot/grub clearly indicates a stage1 file is present! Are you running the command from the live cd?

---

### Post by siliond on 2009-06-29
> **P3P said:**
> Which tool have you used for partitioning?

Grub tells you "Unknown partition table signature".
I experienced some problems with partitions in the same step.

Usually "cfdisk" and "parted" make different partition tables in which "partition type" is not the same.

I would try a couple of partition tools and gather some information about "partition type" field.
I used cfdisk to make a 108 GB ext 3 partition, bootable.

---

### Post by siliond on 2009-06-29
> **ronparent said:**
> Your list of /boot/grub clearly indicates a stage1 file is present! Are you running the command from the live cd?
No.
In previous steps I ran "sudo chroot /target/", the command prompt changed from "ubuntu@ubuntu:~$" to "root@ubuntu:/#".

---

### Post by ronparent on 2009-06-29
Try the grub setup from a live cd session. I forget the reason why. Once setup, everything should work.

---

### Post by siliond on 2009-06-30
**I tried again using target as root**, still no luck:
```
ubuntu@ubuntu:~$ sudo mount --bind /dev /target/dev/
ubuntu@ubuntu:~$ sudo mount -t proc proc /target/proc/
ubuntu@ubuntu:~$ sudo mount -t sysfs sys /target/sys/
ubuntu@ubuntu:~$ sudo chroot /target/
root@ubuntu:/# ls -l /dev/mapper/
total 0
crw-rw---- 1 root root  10, 61 2009-06-30 00:48 control
brw-rw---- 1 root disk 252,  0 2009-06-30 04:52 isw_dfeffeagbe_Volume0
brw-rw---- 1 root disk 252,  1 2009-06-30 04:52 isw_dfeffeagbe_Volume01
brw-rw---- 1 root disk 252,  3 2009-06-30 04:52 isw_dfeffeagbe_Volume05
brw-rw---- 1 root disk 252,  4 2009-06-30 04:52 isw_dfeffeagbe_Volume06
brw-rw---- 1 root disk 252,  5 2009-06-30 04:52 isw_dfeffeagbe_Volume07
root@ubuntu:/# grub --no-curses
Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature
Unknown partition table signature
Unknown partition table signature

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> device (hd0) /dev/mapper/isw_dfeffeagbe_Volume0
device (hd0) /dev/mapper/isw_dfeffeagbe_Volume0
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
```

**And then w/o chroot command**, no luck:
```
ubuntu@ubuntu:~$ grub --no-curses
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> device (hd0) /dev/mapper/isw_dfeffeagbe_Volume0
device (hd0) /dev/mapper/isw_dfeffeagbe_Volume0

Error 15: File not found
grub> device (hd0) /target/dev/mapper/isw_dfeffeagbe_Volume0
device (hd0) /target/dev/mapper/isw_dfeffeagbe_Volume0

Error 15: File not found
```

---

### Post by siliond on 2009-06-30
I have 4 disks in RAID 0 and 1 as JBOD. How does the Linux partition in the RAID look?
```
ubuntu@ubuntu:~$ sudo fdisk -l
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0xe581 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x944f944f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12749   102406311    7  HPFS/NTFS
/dev/sda2           12750      155652  1147868347+   f  W95 Ext'd (LBA)
/dev/sda5   ?       52931      193979  1132971556+  a5  FreeBSD

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000012

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000101

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2852ebaf

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94a294a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       38912   312560608+   7  HPFS/NTFS
```

---

### Post by diraol on 2009-06-30
I'm not an expert on this subject, but I'd no problems installing ubuntu in a FakeRaid Computer.

I've made this tutorial: [http://diraolinux.blogspot.com/2009/01/instalar-o-ubuntu-num-equipamento-com.html]("http://diraolinux.blogspot.com/2009/01/instalar-o-ubuntu-num-equipamento-com.html")

I know that this is in portuguese, but i think it would be easy to understand.

I've been successful in installing the Ubuntu 9.04 with a FakeRaid on my desktop, but i'd problems with my VGA (ATI Radeon), so that's why i still have the ubuntu 8.10 on my PC.

Anyway, this tutorial has worked pretty fine for me.

---

### Post by Little Girl on 2009-06-30
You pasted the contents of **/boot/grub**, so I take it you found where GRUB should be. ;)

**Your /boot/grub**:

```

e2fs_stage1_5  jfs_stage1_5    reiserfs_stage1_5  stage2       xfs_stage1_5
fat_stage1_5   minix_stage1_5  stage1          stage2_eltorito

```**M****y /boot/grub**:

```

default  e2fs_stage1_5  installed-version  menu.lst  menu.lst~
reiserfs_stage1_5  stage2 device.map  fat_stage1_5  jfs_stage1_5
minix_stage1_5  stage1  xfs_stage1_5

```Yours is missing some files, so GRUB doesn't know what to do. :icon_frown:

First, some questions:


[LIST]
[*] Did you make a backup of what was on the original partition(s) before adding the new partition?
[*] What did you put on the new partition you created?
[*] What kind of access do you have to the machine? Can you only access it with a Live CD?
[*]Which partition did you find **/boot/grub** on?
[*] Have you taken a look at [http://ubuntuforums.org/showthread.php?t=297261](http://ubuntuforums.org/showthread.php?t=297261) and tried the suggestion by Ralphie?
[/LIST]

What worries me the most is your partition errors on[FONT=monospace] **/dev/sdb**, **/dev/sdc**, and **/dev/sdd**. [/FONT][FONT=monospace]I don't know anything about raids, but if this is a known glitch where raids report as not having valid partition tables, then maybe your data is still safe. Otherwise, I would think that those three partitions will have to be formatted properly to be used again. Hopefully that's not the case.


[/FONT][FONT=monospace]
[/FONT]

---

### Post by siliond on 2009-06-30
Thank you for the reply.

> Did you make a backup of what was on the original partition(s) before adding the new partition?
[INDENT]Yes.
I had 108GB free unpartitioned space on a 4 disk RAID 0. I created 108 GB ext 3 partition, bootable. I also have around 900 GB worth of Windows partitions on the same RAID, working fine.[/INDENT]

> What did you put on the new partition you created?
[INDENT]I installed Ubuntu 9.04 using instructions posted here [https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto").[/INDENT]

> What kind of access do you have to the machine? Can you only access it with a Live CD?
[INDENT]Windows boots from hdd fine.
Ubuntu only through Live CD.[/INDENT]


> Which partition did you find /boot/grub on?
[INDENT]I'm a little bit unclear how to answer this.
But it's isw_dfeffeagbe_Volume07 in /dev/mapper or
/dev/sda5 as listed by fdisk.[/INDENT]

> Have you taken a look at [http://ubuntuforums.org/showthread.php?t=297261](http://ubuntuforums.org/showthread.php?t=297261) and tried the suggestion by Ralphie?
[INDENT]I'll check it out tonight, together with checking diraol's instructions.[/INDENT]

Thank you.

---

### Post by P3P on 2009-06-30
**siliond** I had the same problem hundred of times. I solved it, but I can not remember exactly what was the problem.

I think that it was "partition type" related.

Please be sure partition type has the same value in parted and in cfdisk.

Can you paste the output of
```
sudo fdisk -l /dev/mapper/isw_dfeffeagbe_Volume0
```(or change the name of the correct volume name)


You can also try running grub with the option --device-map=/dev/null.

Good luck ;)

---

### Post by ronparent on 2009-06-30
Hey guys, you're getting too complicated for me. Little Girl is correct that if grub had been installed correctly you would see at least /boot/grub/menu.lst. Are you perchance installed on the raid0? Did you do the install following the procedure explained here: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) 

To sweep away the extraneous, if you partitioned with dmraid active it is likey normal that fdisk -l will show valid partiotions on only the first disk of a raid0 set.

Regardless of the state of the grub install in the target OS, the find command should find /boot/grub/stage1 which is present on the drive when you do a ls. Keep it simple. From a live cd open a terminal and enter only the commands as follows:

[B]sudo grub
find /boot/grub/stage1[/B]
 from the output of find
[B]root (hdx,y)
setup (hdx)[/B]

No more, no less. If an error on the last step, grub will have to be reinstalled to the target.

PS I correct myself. If your MB has an older bios, the grub install may be to deep on the disk for the protion of grub on the mbr to find the grub stage files. It that were the case, you would need to install grub probably within the 1st130 GB or so of the boot disk. This can be done in a separate small boot partition or for that matter any partition with a compatible fs (not ntfs).

---

### Post by siliond on 2009-07-01
ronparent,

Thank you for the reply.

> Did you do the install following the procedure explained here: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[INDENT]Yes[/INDENT]

> Little Girl is correct that if grub had been installed correctly you would see at least /boot/grub/menu.lst.
[INDENT]I did not do GUI installation of grub as per instruction 8.b. I did it manually by instructions 9.i - 9.k. 9.l failed due to find not finding.[/INDENT]

> Are you perchance installed on the raid0?
[INDENT]Yes. But I don't have grub set up yet, so in order to have access to it I boot from Live CD, I choose the Leave system unchanged option during boot.[/INDENT]

**Here is the output when trying with chroot to target from the Live CD**, I choose the Leave system unchanged option during boot, as installation got completed on the RAID 0:
```
ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_dfeffeagbe_Volume07 /target
ubuntu@ubuntu:~$ sudo mount --bind /dev /target/dev/
ubuntu@ubuntu:~$ sudo mount -t proc proc /target/proc/
ubuntu@ubuntu:~$ sudo mount -t sysfs sys /target/sys/
ubuntu@ubuntu:~$ sudo chroot /target/
root@ubuntu:/# sudo grub
sudo: unable to resolve host ubuntu
Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature
Unknown partition table signature
Unknown partition table signature

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
```

**Here is the output w/o chroot**:
```
ubuntu@ubuntu:/$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature
Unknown partition table signature
Unknown partition table signature

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /target/boot/grub/stage1          
find /target/boot/grub/stage1

Error 15: File not found
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
```

---

### Post by siliond on 2009-07-01
> **P3P said:**
> **siliond** I had the same problem hundred of times. I solved it, but I can not remember exactly what was the problem.

I think that it was "partition type" related.

Please be sure partition type has the same value in parted and in cfdisk.

Can you paste the output of
```
sudo fdisk -l /dev/mapper/isw_dfeffeagbe_Volume0
```(or change the name of the correct volume name)


You can also try running grub with the option --device-map=/dev/null.

Good luck ;)

Thank you for the reply.

Here it is:
```
root@ubuntu:/# sudo fdisk -l /dev/mapper/isw_dfeffeagbe_Volume0
sudo: unable to resolve host ubuntu

Disk /dev/mapper/isw_dfeffeagbe_Volume0: 1280.2 GB, 1280282460160 bytes
255 heads, 63 sectors/track, 155652 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x944f944f

                              Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_dfeffeagbe_Volume0p1   *           1       12749   102406311    7  HPFS/NTFS
/dev/mapper/isw_dfeffeagbe_Volume0p2           12750      155652  1147868347+   f  W95 Ext'd (LBA)
/dev/mapper/isw_dfeffeagbe_Volume0p5           12750      140231  1023999133+   7  HPFS/NTFS
/dev/mapper/isw_dfeffeagbe_Volume0p6          154680      155652     7815591   82  Linux swap / Solaris
/dev/mapper/isw_dfeffeagbe_Volume0p7          140232      154679   116053528+  83  Linux

Partition table entries are not in disk order
root@ubuntu:/# 
```

---

### Post by siliond on 2009-07-01
> **P3P said:**
> **siliond** I had the same problem hundred of times. I solved it, but I can not remember exactly what was the problem.

I think that it was "partition type" related.

Please be sure partition type has the same value in parted and in cfdisk.

Can you paste the output of
```
sudo fdisk -l /dev/mapper/isw_dfeffeagbe_Volume0
```(or change the name of the correct volume name)


You can also try running grub with the option --device-map=/dev/null.

Good luck ;)

**cfdisk**:
```
ubuntu@ubuntu:~$ sudo apt-get install -y dmraid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdmraid1.0.0.rc15
The following NEW packages will be installed:
  dmraid libdmraid1.0.0.rc15
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 140kB of archives.
After this operation, 459kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com jaunty/main libdmraid1.0.0.rc15 1.0.0.rc15-6ubuntu2 [105kB]
Get:2 http://archive.ubuntu.com jaunty/main dmraid 1.0.0.rc15-6ubuntu2 [35.1kB]
Fetched 140kB in 11s (12.5kB/s)
Selecting previously deselected package libdmraid1.0.0.rc15.
(Reading database ... 103503 files and directories currently installed.)
Unpacking libdmraid1.0.0.rc15 (from .../libdmraid1.0.0.rc15_1.0.0.rc15-6ubuntu2_amd64.deb) ...
Selecting previously deselected package dmraid.
Unpacking dmraid (from .../dmraid_1.0.0.rc15-6ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Setting up libdmraid1.0.0.rc15 (1.0.0.rc15-6ubuntu2) ...

Setting up dmraid (1.0.0.rc15-6ubuntu2) ...
update-initramfs is disabled since running on read-only media
update-initramfs is disabled since running on read-only media

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
ubuntu@ubuntu:~$ sudo swapoff -a
ubuntu@ubuntu:~$ sudo dmraid -ay 
RAID set "isw_dfeffeagbe_Volume0" already active
RAID set "isw_dfeffeagbe_Volume01" already active
RAID set "isw_dfeffeagbe_Volume05" already active
RAID set "isw_dfeffeagbe_Volume06" already active
RAID set "isw_dfeffeagbe_Volume07" already active
ubuntu@ubuntu:~$ ls -l /dev/mapper/
total 0
crw-rw---- 1 root root  10, 61 2009-07-01 05:50 control
brw-rw---- 1 root disk 252,  0 2009-07-01 09:56 isw_dfeffeagbe_Volume0
brw-rw---- 1 root disk 252,  1 2009-07-01 09:56 isw_dfeffeagbe_Volume01
brw-rw---- 1 root disk 252,  2 2009-07-01 09:56 isw_dfeffeagbe_Volume05
brw-rw---- 1 root disk 252,  5 2009-07-01 09:56 isw_dfeffeagbe_Volume06
brw-rw---- 1 root disk 252,  6 2009-07-01 09:56 isw_dfeffeagbe_Volume07
ubuntu@ubuntu:~$ sudo cfdisk /dev/mapper/isw_dfeffeagbe_Volume0

FATAL ERROR: Cannot seek on disk drive
Press any key to exit cfdisk
```

**parted**
```
ubuntu@ubuntu:~$ sudo parted /dev/mapper/isw_dfeffeagbe_Volume0
GNU Parted 1.8.8
Using /dev/mapper/isw_dfeffeagbe_Volume0
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print all                                                        
Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/isw_dfeffeagbe_Volume0: 1280GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  105GB   105GB   primary   ntfs         boot 
 2      105GB   1280GB  1175GB  extended               lba  
 5      105GB   1153GB  1049GB  logical   ntfs              
 7      1153GB  1272GB  119GB   logical   ext3              
 6      1272GB  1280GB  8003MB  logical   linux-swap        


Error: Can't have a partition outside the disk!                           

Error: /dev/sdb: unrecognised disk label                                  

Error: /dev/sdc: unrecognised disk label                                  

Error: /dev/sdd: unrecognised disk label                                  

Model: ATA ST3320620AS (scsi)
Disk /dev/sde: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  320GB  320GB  primary  ntfs              


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

(parted) 
```

---

### Post by ronparent on 2009-07-01
Based on your last post, so far so good. And apparently dmraid activates the array on install from the live cd session. The contents of /dev/mapper appear correct. I wouldn't expect cfdisk to successfully act on vol 0. This is a symbolic link for the entire disk and I don't beleive cfdisk is designed to handle it. Once dmraid is installed gparted will recognize the array as one drive with it's partitions. 

Also a simple mount command should mount vol 7 (the partition to which ubuntu is installed). After mounting, of course, a ls /root/grub should list the contents of that local. From your prior listing that will show stage1. If at that point the find command from the gubb prompt doesn't find it then I am at a complete loss!

---

### Post by siliond on 2009-07-01
> **ronparent said:**
> Based on your last post, so far so good. And apparently dmraid activates the array on install from the live cd session. The contents of /dev/mapper appear correct. I wouldn't expect cfdisk to successfully act on vol 0. This is a symbolic link for the entire disk and I don't beleive cfdisk is designed to handle it. Once dmraid is installed gparted will recognize the array as one drive with it's partitions. 

Also a simple mount command should mount vol 7 (the partition to which ubuntu is installed). After mounting, of course, a ls /root/grub should list the contents of that local. From your prior listing that will show stage1. If at that point the find command from the gubb prompt doesn't find it then I am at a complete loss!
It is exactly what is happening, somehow find does not know how to find, maybe I should try finding something else, outside of the /boot/grub folder, maybe those files are locked or something?

---

### Post by ronparent on 2009-07-01
Try a couple of files (not on a ntfs partition) that you know are there and see what you get.

---

### Post by Little Girl on 2009-07-01
This might help, since the original problem was that you got stuck while installing GRUB:

[http://en.gentoo-wiki.com/wiki/Software_RAID_Install#Installing_Grub_onto_both_MBRs](http://en.gentoo-wiki.com/wiki/Software_RAID_Install#Installing_Grub_onto_both_MBRs)

No, then again - probably not, since it specifically mentions Raid 1. But I'll leave the link there as food for thought or inspiration.

Have you tried Ralphie's suggestion at the link I sent earlier? I'm curious what output you get when you try **find /grub/stage1** instead of **find /boot/grub/stage1**.

---

### Post by siliond on 2009-07-01
> **Little Girl said:**
> This might help, since the original problem was that you got stuck while installing GRUB:

[http://en.gentoo-wiki.com/wiki/Software_RAID_Install#Installing_Grub_onto_both_MBRs](http://en.gentoo-wiki.com/wiki/Software_RAID_Install#Installing_Grub_onto_both_MBRs)

No, then again - probably not, since it specifically mentions Raid 1. But I'll leave the link there as food for thought or inspiration.

Have you tried Ralphie's suggestion at the link I sent earlier? I'm curious what output you get when you try **find /grub/stage1** instead of **find /boot/grub/stage1**.

I've tried a bunch of other combinations in previous attempts.

```
grub> find stage1
find stage1

Error 15: File not found
grub> find boot/grub/stage1             
find boot/grub/stage1

Error 15: File not found
grub> find /grub/stage1
find /grub/stage1

Error 15: File not found
grub> find /stage1
find /stage1

Error 15: File not found
grub> find /boot/stage1
find /boot/stage1

Error 15: File not found
```

---

### Post by siliond on 2009-07-01
Looking back at my partition information, see below, I see Bootable is unchecked even though I set it to true in cfdisk.

**Does this mean I should have said**
```
# mkdir /grub
# cp /usr/lib/grub/x86_64-pc/* /grub/
```

**instead of**

```
# mkdir /boot/grub
# cp /usr/lib/grub/x86_64-pc/* /boot/grub/
```

at **step 9.j** in [https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")?

**Partition information**
```
                              Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_dfeffeagbe_Volume0p1   *           1       12749   102406311    7  HPFS/NTFS
/dev/mapper/isw_dfeffeagbe_Volume0p2           12750      155652  1147868347+   f  W95 Ext'd (LBA)
/dev/mapper/isw_dfeffeagbe_Volume0p5           12750      140231  1023999133+   7  HPFS/NTFS
/dev/mapper/isw_dfeffeagbe_Volume0p6          154680      155652     7815591   82  Linux swap / Solaris
/dev/mapper/isw_dfeffeagbe_Volume0p7          140232      154679   116053528+  83  Linux
```

---

### Post by Little Girl on 2009-07-01
> **siliond said:**
> Looking back at my partition information, see below, I see Bootable is unchecked even though I set it to true in cfdisk.

**Does this mean I should have said**
```
# mkdir /grub
# cp /usr/lib/grub/x86_64-pc/* /grub/
```

**instead of**

```
# mkdir /boot/grub
# cp /usr/lib/grub/x86_64-pc/* /boot/grub/
```

at **step 9.j** in [https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")?


I'm not sure, but I don't think it would make any difference since you're getting the Error 15 no matter which find command you run. The problem is in the partition setup and not in GRUB. If the partitions had been set up properly, you would have been able to continue with the instructions in the guide you followed and finished installing GRUB, in which case it would have the files it needs. What, exactly, went wrong is a mystery. O:)

You could probably use a partition editor to make the partition bootable, although you'd probably lose the data on it. If you don't lose the data, you could try installing GRUB again. If you do lose it, you could go through all the steps again and this time not get stuck at step 9.l.i. of the instructions you originally followed.

I'm curious about one additional thing, though. You had mentioned that you use Raid 0 and JBOD. I don't know anything about raids, so I did a bit of Googling on both of those. They seem to be different "creatures," so I'm wondering why you use both, and which you use for Linux and which for Windows, or if it's an even more confusing set-up that uses both for both operating systems.

---

### Post by heaths on 2009-07-01
Hi thanks for your replies:guitar:
  [[color=#FFFFFF]_simulationcredit_[/color]](http://simulationcredit1.com)

---

### Post by siliond on 2009-07-02
Little Girl,

I'm going to try making the partition bootable and let you know on the output.

The standalone, JBOD, has no involvement in the Linux install. I only mentioned because it got listed by fdisk (as /dev/sde) and wanted to avoid any confusion.

Thank you.

---

### Post by siliond on 2009-07-02
If previous fails I'll give LILO a try.

---

### Post by P3P on 2009-07-02
Remember to try with the option --device-map=/dev/null in grub

```
grub --device-map=/dev/null
```

---

### Post by siliond on 2009-07-03
> **P3P said:**
> Remember to try with the option --device-map=/dev/null in grub

```
grub --device-map=/dev/null
```

**First I flagged the Linux partition as bootable**:
```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/mapper/isw_dfeffeagbe_Volume0

Disk /dev/mapper/isw_dfeffeagbe_Volume0: 1280.2 GB, 1280282460160 bytes
255 heads, 63 sectors/track, 155652 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x944f944f

                              Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_dfeffeagbe_Volume0p1               1       12749   102406311    7  HPFS/NTFS
/dev/mapper/isw_dfeffeagbe_Volume0p2           12750      155652  1147868347+   f  W95 Ext'd (LBA)
/dev/mapper/isw_dfeffeagbe_Volume0p5           12750      140231  1023999133+   7  HPFS/NTFS
/dev/mapper/isw_dfeffeagbe_Volume0p6          154680      155652     7815591   82  Linux swap / Solaris
/dev/mapper/isw_dfeffeagbe_Volume0p7   *      140232      154679   116053528+  83  Linux

Partition table entries are not in disk order
```

**Then I tried grub --device-map=/dev/null**:
```
root@ubuntu:/# sudo grub --device-map=/dev/null
sudo: unable to resolve host ubuntu

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> device (hd0) /dev/mapper/isw_dfeffeagbe_Volume0
device (hd0) /dev/mapper/isw_dfeffeagbe_Volume0
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub> find /grub/stage1    
find /grub/stage1

Error 15: File not found
```

**Next I'll try moving the partition closer to the beginning as per ronparent's suggestion**:
> PS I correct myself. If your MB has an older bios, the grub install may be to deep on the disk for the protion of grub on the mbr to find the grub stage files. It that were the case, you would need to install grub probably within the 1st130 GB or so of the boot disk. This can be done in a separate small boot partition or for that matter any partition with a compatible fs (not ntfs).

---

### Post by siliond on 2009-07-03
**I must be getting closer**:

1. **I added a 200 MB boot partition** at the beginning of the RAID, as per suggestion here: [http://ubuntuforums.org/showthread.php?t=88299]("http://ubuntuforums.org/showthread.php?t=88299")
```
root@ubuntu:/# sudo parted /dev/mapper/isw_dfeffeagbe_Volume0
sudo: unable to resolve host ubuntu
GNU Parted 1.8.8
Using /dev/mapper/isw_dfeffeagbe_Volume0
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print all                                                        
Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/isw_dfeffeagbe_Volume0: 1280GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 3      32.3kB  214MB   214MB   primary   ext3         boot 
 1      214MB   105GB   105GB   primary   ntfs              
 2      105GB   1280GB  1175GB  extended               lba  
 5      105GB   1153GB  1049GB  logical   ntfs              
 7      1153GB  1272GB  119GB   logical   ext3              
 6      1272GB  1280GB  8003MB  logical   linux-swap        


Error: Can't have a partition outside the disk!                           

Error: /dev/sdb: unrecognised disk label                                  

Error: /dev/sdc: unrecognised disk label                                  

Error: /dev/sdd: unrecognised disk label                                  

Model: ATA ST3320620AS (scsi)
Disk /dev/sde: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  320GB  320GB  primary  ntfs              


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been
opened read-only.
Error: /dev/sr0: unrecognised disk label 
```

2. **I set up grub**, find still did not return anything but i ran root (hd0,2) and then the rest of the steps anyway.

3. **Now, when I boot a get the grub prompt, not a menu**.

---

### Post by ronparent on 2009-07-03
menu.lst must be present to get a menu. In your original post you didn't have a menu.lst with the stage1 etc. files. I presume you have the grub staging files present in that dedicated grub directory since that is what appears to have produced the grub prompt. Is there a menu.lst there also? It does appear you are getting somewhere.

I still don't understand why the find command is not finding stage1. That step is not essential to the setup if you know the grub coordinates to assign root to, merely a convenience to verify the root location!

---

### Post by manola on 2009-07-05
It does appear you are getting somewhere.
[[color=#F5F5FF]_sonnerie portable gratuite_[/color]](http://sonneriegratuite.org)

---

