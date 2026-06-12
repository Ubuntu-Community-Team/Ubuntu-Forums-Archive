---
title: "Mounting 129 gb NTFS partition"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by snakedog on 2008-12-04
Recently installed 8.04 on a Toshiba Satellite with a 160 gb HDD.  I already had XP on the first partition (FAT, 13-14 gb's), some free space in the middle for Ubuntu, and then a 129 gb NTFS partition at the end.

The installer let me mount the first partition at /windows, but I got an error trying to set a mount point on the 129 gb NTFS partition.  So I figured I could mount it manually after the install and/or set things up there.  But it didn't even make it into the fstab or mtab files.

What can I do here to be able to mount, or better yet, automount that partition?  The appropriate files are as follows:

----------------------------------

snakedog@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda4              9427328   2504868   6447340  28% /
varrun                  509204       104    509100   1% /var/run
varlock                 509204         0    509204   0% /var/lock
udev                    509204        52    509152   1% /dev
devshm                  509204         0    509204   0% /dev/shm
lrm                     509204     39788    469416   8% /lib/modules/2.6.24-22-generic/volatile
/dev/sda1             14669032   5945080   8723952  41% /windows

---------------------------------

snakedog@ubuntu:~$ sudo fdisk /dev/sda
[sudo] password for karl: 

The number of cylinders for this disk is set to 19457.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x355b355a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1828    14683378+   c  W95 FAT32 (LBA)
/dev/sda2            3136       19457   131106465    7  HPFS/NTFS
/dev/sda3            3012        3135      996030   82  Linux swap / Solaris
/dev/sda4            1829        3011     9502447+  83  Linux

Partition table entries are not in disk order

Command (m for help): q

-------------------------------------

If I try to manually mount it, I get this:

snakedog@ubuntu:~$ mount /dev/sda2
mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab
snakedog@ubuntu:~$ sudo mount /dev/sda2
mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab

I've never edited fstab and/or mtab and am unsure how to proceed.

-----fstab----------------------------

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=95594f48-4a59-4953-89ce-07a08f157dd5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=9488-18C3  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=c454435b-f66f-4747-8364-501b10041291 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

-----mtab------------------

/dev/sda4 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-22-generic/volatile tmpfs rw 0 0
/dev/sda1 /windows vfat rw,utf8,umask=007,gid=46 0 0
securityfs /sys/kernel/security securityfs rw 0 0

---------------------------

Thanks for any help.

---

### Post by Mark Phelps on 2008-12-05
That's because your mount command is incomplete.

The syntax of the mount command is mount -t <type> <device> <dir>

Since you're mounting an NTFS volume, you should use NTFS-3G to mount it.  If that package is not installed, add it through synaptic first.

Then, create a mount point using "sudo mkdir /mnt/windows" where "windows" is the name of the directory you want to contain the files.

Then, issue the following mount command "sudo mount -t ntfs-3g /dev/sda2 /mnt/windows"

The format for fstab entries is different than the mount command.

---

