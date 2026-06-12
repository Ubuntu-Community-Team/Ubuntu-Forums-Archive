---
title: "fixing usb after pendrivelinux?"
date: 2008-08-30
forum: Hardware
---

### Post by Garratt on 2008-08-30
hey recently stumbled across [http://www.pendrivelinux.com/]("http://www.pendrivelinux.com/")

after looking for ways to troubleshoot, fedora live USB...

I was trying to use it as a customised live OS...!

and this site does exactly what i wanted. only problem was i went through a few different methods and none seem to work.

I tried the ubuntu persistant 8.04 from ubuntu, i seemed to get some errors towards the last step (16), anyway turns out it did not work because it wouldn't bootup, and now i need to format my usb so i can xfer some files from my g/f's computer (win xp) as she has killed it with too many viruses, and spyware, adware, just about anything you can think of she has it!.



so i goto reformat her machine but before i do i need to copy all her music etc, or she will have my nuts.


this is the last method i used, and is still kinda in that format:
[http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/]("http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/")


i tried this to my usb to fix it:

```
garratt@ubuntu:~$ sudo su
root@ubuntu:/home/garratt# fdisk /dev/sdc

The number of cylinders for this disk is set to 61503.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sdc: 8061 MB, 8061451776 bytes
8 heads, 32 sectors/track, 61503 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Disk identifier: 0x7ace97ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        5723      732528    6  FAT16
/dev/sdc2            5724       61503     7139840   83  Linux

Command (m for help): d
Partition number (1-4): 1

Command (m for help): p

Disk /dev/sdc: 8061 MB, 8061451776 bytes
8 heads, 32 sectors/track, 61503 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Disk identifier: 0x7ace97ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2            5724       61503     7139840   83  Linux

Command (m for help): d
Selected partition 2

Command (m for help): p

Disk /dev/sdc: 8061 MB, 8061451776 bytes
8 heads, 32 sectors/track, 61503 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Disk identifier: 0x7ace97ea

   Device Boot      Start         End      Blocks   Id  System

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-61503, default 1): 
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-61503, default 61503): 
Using default value 61503

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
root@ubuntu:/home/garratt# 

```

i was really unsure of the format it needs to be in, that step boggled me.
so anyway i ripped it out and chucked it back in and the casper partition and files where gone but the ubuntu files were all still there so i jsut delted them, the thumbstick is still showing up with a HDD icon and called ubuntu8.... so i'm not sure if that matters or not?

i assume after that last step creating the partitions but not naming the new format may have defaulted to linux format.
basically i jsut need to know if what i have done to the usb is going to work or do i need to format it differently, to be able to read/write files from windows systems to linux systems.
thanks for any input that may help.

---

### Post by Garratt on 2008-08-30
anyone know differences between linux, fat 16, F 32 file systems?

---

### Post by Garratt on 2008-08-30
woops, i thought i had fixed it but it's only showing the original boot sector of 750mb, its 8g thumbstick.

[[IMG]http://img401.imageshack.us/img401/7128/screenshotfq4.th.jpg[/IMG]](http://img401.imageshack.us/my.php?image=screenshotfq4.jpg)

---

### Post by Garratt on 2008-08-30
hmm ill try to format on windows hopefully ill have more luck

---

### Post by az on 2008-08-30
> **Garratt said:**
> anyone know differences between linux, fat 16, F 32 file systems?

The partition type and the filesystem are two different things.  The partition type is just an attribute assigned to a partition in the partition table.  The filesystem is the method of organizing data on the disk.

You need to delete the other partition too and then create a single one you will use (as it was when you first got the usb drive).

Once you create the partition, you still have to format it - that means to create a filesystem on it.

You can create a fat ntfs or ext3 filesystem on any kind of partition.  It's just that some operating system will ignore partition other than their's.  Ubutnu will recognize them all.

To create a fat filesystem, run

sudo mkdosfs -F 16 /dev/sdc1

---

### Post by Garratt on 2008-08-30
the problem was hitting P to show the partitions would only show the 1 partition, you should be able to see that from my code... I can see it, but yea, even hitting D when there was no partitions showing i would get an error no partitions exsist...
i think i may have seriously roooted it.

I ended up using a usb formatter on windows, and now it is showing up as 7.45gb when it should be 8.1gb

so it is not seeing that 715mb or so that is on it...which is the opposite to what linux was seeing.

EDIT: sorry i did have some extra code up there of me reformatting again and again, basically it shows up as one partition sdc1, i hit delete, show partition again, no partitions, hit new partition, make it, and it throws out an error that the current partition is already in use. but will revert it on next reboot or whatever... theres something wrong with the 750mb "boot" partition, for some reason linix can't repartition it, and windows can't see it.

i'M guessing that after fixing the end partition on windows linux will now see it, and i may be able to partition the WHOLE thumstick as 1 part. but i can't do that at the moment because i've been stuffing around all day and need to copy 7g off my g/f's comp which is what im doing right now...

---

### Post by Garratt on 2008-08-30
oh AZ,

I just re-read that warning: it says the kernel will continue using the old table until i reboot, is that talking about rebooting the OS or the thumbstick? cause obviously rebooting thumbstick didn't work.

---

### Post by Garratt on 2008-09-02
ok, so yea i still get the same errors whenever I try to format, am i doing something wrong?,
 should i just right click and delete files?

 this is output. scroll down to the bottom if you want quick overview.

```
garratt@ubuntu:~$ fdisk -l
garratt@ubuntu:~$ sudo su
[sudo] password for garratt: 
root@ubuntu:/home/garratt# fdisk -l

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7bf97bf9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9331    74951226   83  Linux
/dev/sda2            9332        9733     3229065    5  Extended
/dev/sda5            9332        9733     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x87fd86ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       77826   625129472    7  HPFS/NTFS

Disk /dev/sdg: 8061 MB, 8061451776 bytes
255 heads, 63 sectors/track, 980 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06292d14

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1         980     7871818+  83  Linux
root@ubuntu:/home/garratt# fdisk /dev/sdg

Command (m for help): d
Selected partition 1

Command (m for help): p

Disk /dev/sdg: 8061 MB, 8061451776 bytes
255 heads, 63 sectors/track, 980 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06292d14

   Device Boot      Start         End      Blocks   Id  System

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-980, default 1): 
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-980, default 980): 
Using default value 980

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
root@ubuntu:/home/garratt# umount /dev/sdg
umount: /dev/sdg: not mounted
root@ubuntu:/home/garratt# fdisk --man
fdisk: invalid option -- -

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
root@ubuntu:/home/garratt# mkfs --man
mkfs.ext2: invalid option -- -
Usage: mkfs.ext2 [-c|-l filename] [-b block-size] [-f fragment-size]
	[-i bytes-per-inode] [-I inode-size] [-J journal-options]
	[-N number-of-inodes] [-m reserved-blocks-percentage] [-o creator-os]
	[-g blocks-per-group] [-L volume-label] [-M last-mounted-directory]
	[-O feature[,...]] [-r fs-revision] [-E extended-option[,...]]
	[-T fs-type] [-jnqvFSV] device [blocks-count]
root@ubuntu:/home/garratt# mkfs.vfat -F 16 -L Usb-8g /dev/sdg1
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: invalid option -- L
Unknown option: ?
Usage: mkdosfs [-A] [-c] [-C] [-v] [-I] [-l bad-block-file] [-b backup-boot-sector]
       [-m boot-msg-file] [-n volume-name] [-i volume-id]
       [-s sectors-per-cluster] [-S logical-sector-size] [-f number-of-FATs]
       [-h hidden-sectors] [-F fat-size] [-r root-dir-entries] [-R reserved-sectors]
       /dev/name [blocks]
root@ubuntu:/home/garratt# mkfs.vfat -F 16 Usb-8g /dev/sdg1
mkfs.vfat 2.11 (12 Mar 2005)
Usb-8g: No such file or directory
root@ubuntu:/home/garratt# mkfs.vfat -F 16 /dev/sdg1
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: /dev/sdg1 contains a mounted file system.
root@ubuntu:/home/garratt# mkfs.vfat -F 16 /dev/sdg1
mkfs.vfat 2.11 (12 Mar 2005)
WARNING: Not enough clusters for a 16 bit FAT! The filesystem will be
misinterpreted as having a 12 bit FAT without mount option "fat=16".
mkfs.vfat: Attempting to create a too large file system
root@ubuntu:/home/garratt# mkfs.vfat -Fat=16 /dev/sdg1
mkfs.vfat 2.11 (12 Mar 2005)
Bad FAT type : at=16
Usage: mkdosfs [-A] [-c] [-C] [-v] [-I] [-l bad-block-file] [-b backup-boot-sector]
       [-m boot-msg-file] [-n volume-name] [-i volume-id]
       [-s sectors-per-cluster] [-S logical-sector-size] [-f number-of-FATs]
       [-h hidden-sectors] [-F fat-size] [-r root-dir-entries] [-R reserved-sectors]
       /dev/name [blocks]
root@ubuntu:/home/garratt# mkfs.vfat -F16 /dev/sdg1
mkfs.vfat 2.11 (12 Mar 2005)
WARNING: Not enough clusters for a 16 bit FAT! The filesystem will be
misinterpreted as having a 12 bit FAT without mount option "fat=16".
mkfs.vfat: Attempting to create a too large file system
root@ubuntu:/home/garratt# 

```

---

### Post by Garratt on 2008-09-02
ok nevermind i used goooieee  (gui).
problem was it would not let me make fat16 due to the size of it, for some reason the fat 16 need 4088 mb blocks and the second block is too small as you can see from the pic. was able to make fat32 easy with gparted and it automatically gave it back the correct msdos name. "8.1G Media" 



[[IMG]http://img390.imageshack.us/img390/2864/screenshotcreatenewpartey2.th.png[/IMG]](http://img390.imageshack.us/my.php?image=screenshotcreatenewpartey2.png)

---

