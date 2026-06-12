---
title: "Installing DVD cause UUID does not exist error"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by rfpeake on 2009-09-28
PROBLEM: Installing SATA DVD altered drive assignments causing boot error <uuid of root drive> does not exist.

SUMMARY: After installing SATA DVD burner, boot terminates with error: "UUID=1dd77d8e-23cb-43fc-8082-8776783e8781 does not exist” and drops to Busy Box shell.  This UUID identifies /dev/sdb3 according to /etc/fstab. It appears that drive assignments sda and sdb have been swapped after SATA DVD was installed.

THIS ERROR IS PRECEDED BY:
(dm_validate_partition_table): disk read failed
Dev sdb: unable to read RDB block0
Dev sdb: unable to read partition table
sd 5:0:0:0 [sdb] Attached SCSI disk
sd 5:0:0:0: Attached scsi generic sg2 type0

THIS ERROR IS BUG 221677 in Linux (Ubuntu): “unable to read IDE partition table under 8.0.4” It seems the kernel is highly sensitive to IDE cabling problems and IDE disk jumper settings. See: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221677](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221677).

EDUCATED GUESS:
After over a month of head scratching, this is what I come up with as a diagnosis.  GRUB boots from the boot sector of sdb1, which it designates hd0 in menu.lst but is designated hd1 in device.map and in the output of fdisk -l.  It would appear that when the boot starts, GRUB does not detect /dev/sda (750GB HDD) and sees /dev/sdb (80 GB EIDE HDD) as hd0.  Later, the 750GB SATA drive is assigned /dev/sda, but is not mounted.  So by the time GRUB looks for the root in what it designates hd0,2 (or /dev/sdb3), it is actually trying to access /dev/sda3, a nonexistent device.

Apparently, I have installed a 40-pin, 40-connector IDE cable, not an 80-connector cable that the kernel needs.

TEMPORARY SOLUTION: added "all_generic_ide" boot option until I could install the required cable.
SOLUTION: Installing 80-connector IDE cable solved the problem.  I was able to delete the all_generic_ide boot flag with full access to the EIDE drive.

Edited Command in menu.lst:
kernel /vmlinuz-2.6.24-24-generic root=UUID=1dd77d8e-23cb-43fc-8082-8776783e8781 ro single all_generic_ide


************Additional Information Follows****************

CONFIGURATION:
Mythbuntu 8.04.1 (Hardy Heron)
Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic 
Asus M2N-SLI Mobo
Phoenix Award BIOS version 1002 (May 2009)
AMD Athlon 64 X2 5000+ AM2 Black Edition
OCZ Platinum Rev2 2048MB PC 6400 DDR2 800MHz


ORIGINAL DRIVE CONFIGURATION:
/dev/sda  [80G EIDE]
	/dev/sda1	/boot			  526MB	ext3
	/dev/sda2	swap			 2097MB	swap	
	/dev/sda3	/			12584MB	ext3
	/dev/sda4	/home			64815MB	ext3
/dev/sdb  [750G SATA]
	/dev/sdb1	/mythtv/recordings	    750GB	jfs
/dev/sdc [250.0 GB external]				fat32

AFTER INSTALLING SATA DVD DRIVE [sda and sdb assignments been switched]:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ed5fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       91201   732572001   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006d326

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          64      514048+  83  Linux
/dev/sdb2              65         319     2048287+  82  Linux swap / Solaris
/dev/sdb3             320        1849    12289725   83  Linux
/dev/sdb4            1850        9729    63296100   83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    c  W95 FAT32 (LBA)
 on a drive that hasn't been mounted.  Nothing I have tried has solved the problem.

BOOTING FROM LIVE CD--Ubuntu 9.04
Booting from live CD, trying to open dev/sda from file browser yields the error “Cannot mount volume.”

TO MOUNT 750GB HDD:
ubuntu@ubuntu:~$ sudo fsck -t jfs /dev/sda1 
fsck 1.41.4 (27-Jan-2009) 
fsck.jfs version 1.1.12, 24-Aug-2007 
processing started: 9/28/2009 14.36.48 
Using default parameter: -p 
The current device is:  /dev/sda1 
Block size in bytes:  4096 
Filesystem size in blocks:  183143000 
**Phase 0 - Replay Journal Log 
Filesystem is clean. 

THERE ARE NO APPARENT ERRORS ON EIDE HDD:
ubuntu@ubuntu:~$ umount /dev/sdb1 
umount: /dev/sdb1 is not mounted (according to mtab) 
ubuntu@ubuntu:~$ sudo fsck -t ext3 /dev/sdb1 
fsck 1.41.4 (27-Jan-2009) 
e2fsck 1.41.4 (27-Jan-2009) 
/dev/sdb1: recovering journal 
/dev/sdb1: clean, 59/128520 files, 120860/514048 blocks 

ubuntu@ubuntu:~$ umount /dev/sdb3 
umount: /dev/sdb3 is not mounted (according to mtab) 
ubuntu@ubuntu:~$ sudo fsck -t ext3 /dev/sdb3 
fsck 1.41.4 (27-Jan-2009) 
e2fsck 1.41.4 (27-Jan-2009) 
/dev/sdb3: recovering journal 
/dev/sdb3: clean, 205350/770048 files, 1285283/3072431 blocks 

ubuntu@ubuntu:~$ sudo fsck -t ext3 /dev/sdb4 
fsck 1.41.4 (27-Jan-2009) 
e2fsck 1.41.4 (27-Jan-2009) 
/dev/sdb4: recovering journal 
/dev/sdb4: clean, 10192/3956736 files, 1786141/15824025 blocks 

ROOT:
ubuntu@ubuntu:~$ root=bootarg cat /proc/cmdline 
BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash -- 

DEVICE.MAP
(fd0)	/dev/fd0 
(hd0)	/dev/sda 
(hd1)	/dev/sdb 
(hd2)	/dev/sdc

FSTAB:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sdb3
UUID=1dd77d8e-23cb-43fc-8082-8776783e8781 / ext3 nouser,relatime,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sdb1
UUID=8099340c-8a96-4eb6-bf98-6b8d17932577 /boot ext3 nouser,relatime,atime,auto,rw,dev,exec,suid 0 2
# /dev/sdb4
UUID=62ae8371-d91f-4e33-9800-9dc40e148906 /home ext3 nouser,relatime,atime,auto,rw,dev,exec,suid 0 2
# /dev/sda1
UUID=67f24998-83f8-4c11-8d77-c1558638a8f9 /mythtv/recordings jfs nouser,relatime,atime,auto,rw,dev,exec,suid 0 2
# /dev/sdb2
UUID=5577a803-57d3-473a-b9ff-9f2e16b490c4 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,utf8,atime,noauto,rw,dev,exec,suid 0 0


I HAVE TRIED RELOADING GRUB, TO NO AVAIL:
grub> find /boot/grub/stage1
 (hd1,0)

grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+17 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
 
grub> quit

RESULTS FILE (from boot_info_script*.sh)
=========================== Boot Info Summary:==========================

 => No boot loader is installed in the MBR of /dev/sda 
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst. 
 => Windows is installed in the MBR of /dev/sdc 

sda1: _________________________________________________________________________ 

    File system:       jfs 
    Boot sector type:  Grub 
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 64 on boot drive #1 for the stage2 
                       file. A stage2 file is at this location on /dev/sda. 
                       Stage2 looks on partition #1 for /boot/grub/stage2. 
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________ 

    File system:       ext3 
    Boot sector type:  - 
    Boot sector info:  
    Boot file info:     Grub0.97 in the file /stage1 looks at sector 1 of the 
                       same hard drive for the stage2 file. A stage2 file is 
                       at this location on /dev/sdb. Stage2 looks on the same 
                       partition for /boot/grub/stage2. 
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst 

sdb2: _________________________________________________________________________ 

    File system:       swap 
    Boot sector type:  Unknown 
    Boot sector info:  

sdb3: _________________________________________________________________________ 

    File system:       ext3 
    Boot sector type:  - 
    Boot sector info:  
    Operating System:  Ubuntu 8.04.3 LTS 
    Boot files/dirs:   /etc/fstab 

sdb4: _________________________________________________________________________ 

    File system:       ext3 
    Boot sector type:  - 
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________ 

    File system:       vfat 
    Boot sector type:  MSWIN4.1: Fat 32 
    Boot sector info:  No errors found in the Boot Parameter Block. 
    Operating System:  
    Boot files/dirs:   

======================== Drive/Partition Info: =========================== 

Drive: sda _______________ _________________________________________________

Disk /dev/sda: 750.1 GB, 750156374016 bytes 
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0x000ed5fd 

Partition  Boot         Start           End          Size  Id System 

/dev/sda1    *             63 1,465,144,064 1,465,144,002  83 Linux 


Drive: sdb ________________________________________________________________ 

Disk /dev/sdb: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0x0006d326 

Partition  Boot         Start           End          Size  Id System 

/dev/sdb1    *             63     1,028,159     1,028,097  83 Linux 
/dev/sdb2           1,028,160     5,124,734     4,096,575  82 Linux swap / Solaris 
/dev/sdb3           5,124,735    29,704,184    24,579,450  83 Linux 
/dev/sdb4          29,704,185   156,296,384   126,592,200  83 Linux 

 
Drive: sdc _________________________________________________________________ 

Disk /dev/sdc: 250.0 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0x5b6ac646 

Partition  Boot         Start           End          Size  Id System 

/dev/sdc1    *             63   488,392,064   488,392,002   c W95 FAT32 (LBA) 


blkid -c /dev/null: ____________________________________________________________ 

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="67f24998-83f8-4c11-8d77-c1558638a8f9" TYPE="jfs" 
/dev/sdb1: UUID="8099340c-8a96-4eb6-bf98-6b8d17932577" TYPE="ext3" 
/dev/sdb2: LABEL="swap" UUID="5577a803-57d3-473a-b9ff-9f2e16b490c4" TYPE="swap" 
/dev/sdb3: UUID="1dd77d8e-23cb-43fc-8082-8776783e8781" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb4: UUID="62ae8371-d91f-4e33-9800-9dc40e148906" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: LABEL="My Passport" UUID="3215-4A9D" TYPE="vfat" 

============================= "mount" output: ============================ 

proc on /proc type proc (rw) 
sysfs on /sys type sysfs (rw) 
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755) 
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755) 
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755) 
varrun on /var/run type tmpfs (rw,nosuid,mode=0755) 
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777) 
udev on /dev type tmpfs (rw,mode=0755) 
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev) 
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620) 
rootfs on / type rootfs (rw) 
/dev/sr0 on /cdrom type iso9660 (ro,noatime) 
/dev/loop0 on /rofs type squashfs (ro,noatime) 
fusectl on /sys/fs/fuse/connections type fusectl (rw) 
tmpfs on /tmp type tmpfs (rw,nosuid,nodev) 
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev) 
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu) 
/dev/sdc1 on /media/My Passport type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush) 
/dev/sda1 on /media/disk type jfs (rw,nosuid,nodev,uhelper=hal) 
/dev/sdb1 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal) 


======================== sdb1/boot/grub/menu.lst: ========================== 

# menu.lst - See: grub[8], info grub, update-grub[8] 
#            grub-install[8], grub-floppy[8], 
#            grub-md5-crypt, /usr/share/doc/grub 
#            and /usr/share/doc/grub-doc/. 

## default num 
# Set the default entry to the entry number NUM. Numbering starts from 0, and 
# the entry number 0 is the default if the command is not used. 
# 
# You can specify 'saved' instead of a number. In this case, the default entry 
# is the entry saved with the command 'savedefault'. 
# WARNING: If you are using dmraid do not use 'savedefault' or your 
# array will desync and will not let you boot your system. 
default		0 

## timeout sec 
# Set a timeout, in SEC seconds, before automatically booting the default entry 
# (normally the first entry defined). 
timeout		8 

## hiddenmenu 
# Hides the menu by default (press ESC to see the menu) 
#hiddenmenu 

# Pretty colours 
#color cyan/blue white/blue 

## password ['--md5'] passwd 
# If used in the first section of a menu file, disable all interactive editing 
# control (menu entry editor and command-line)  and entries protected by the 
# command 'lock' 
# e.g. password topsecret 
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/ 
# password topsecret 

# 
# examples 
# 
# title		Windows 95/98/NT/2000 
# root		(hd0,0) 
# makeactive 
# chainloader	+1 
# 
# title		Linux 
# root		(hd0,1) 
# kernel	/vmlinuz root=/dev/hda2 ro 
# 

# 
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST 

### BEGIN AUTOMAGIC KERNELS LIST 
## lines between the AUTOMAGIC KERNELS LIST markers will be modified 
## by the debian update-grub script except for the default options below 

## DO NOT UNCOMMENT THEM, Just edit them to your needs 

## ## Start Default Options ## 
## default kernel options 
## default kernel options for automagic boot options 
## If you want special options for specific kernels use kopt_x_y_z 
## where x.y.z is kernel version. Minor versions can be omitted. 
## e.g. kopt=root=/dev/hda1 ro 
##      kopt_2_6_8=root=/dev/hdc1 ro 
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro 
# kopt=root=UUID=1dd77d8e-23cb-43fc-8082-8776783e8781 ro 

## Setup crashdump menu entries 
## e.g. crashdump=1 
# crashdump=0 

## default grub root device 
## e.g. groot=(hd0,0) 
# groot=(hd0,0) 

## should update-grub create alternative automagic boot options 
## e.g. alternative=true 
##      alternative=false 
# alternative=true 

## should update-grub lock alternative automagic boot options 
## e.g. lockalternative=true 
##      lockalternative=false 
# lockalternative=false 

## additional options to use with the default boot option, but not with the 
## alternatives 
## e.g. defoptions=vga=791 resume=/dev/hda5 
# defoptions=quiet splash 

## should update-grub lock old automagic boot options 
## e.g. lockold=false 
##      lockold=true 
# lockold=false 

## Xen hypervisor options to use with the default Xen boot option 
# xenhopt= 

## Xen Linux kernel options to use with the default Xen boot option 
# xenkopt=console=tty0 

## altoption boot targets option 
## multiple altoptions lines are allowed 
## e.g. altoptions=(extra menu suffix) extra boot options 
##      altoptions=(recovery) single 
# altoptions=(recovery mode) single 

## controls how many kernels should be put into the menu.lst 
## only counts the first occurence of a kernel, not the 
## alternative kernel options 
## e.g. howmany=all 
##      howmany=7 
# howmany=4 

## should update-grub create memtest86 boot option 
## e.g. memtest86=true 
##      memtest86=false 
# memtest86=true 

## should update-grub adjust the value of the default booted system 
## can be true or false 
# updatedefaultentry=false 

## should update-grub add savedefault to the default options 
## can be true or false 
# savedefault=false 

## ## End Default Options ## 

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic 
root		(hd0,0) 
kernel		/vmlinuz-2.6.24-24-generic root=UUID=1dd77d8e-23cb-43fc-8082-8776783e8781 ro quiet splash 
initrd		/initrd.img-2.6.24-24-generic 
quiet 

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode) 
root		(hd0,0) 
kernel		/vmlinuz-2.6.24-24-generic root=UUID=1dd77d8e-23cb-43fc-8082-8776783e8781 ro single 
initrd		/initrd.img-2.6.24-24-generic 

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic 
root		(hd0,0) 
kernel		/vmlinuz-2.6.24-23-generic root=UUID=1dd77d8e-23cb-43fc-8082-8776783e8781 ro quiet splash 
initrd		/initrd.img-2.6.24-23-generic 
quiet 

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode) 
root		(hd0,0) 
kernel		/vmlinuz-2.6.24-23-generic root=UUID=1dd77d8e-23cb-43fc-8082-8776783e8781 ro single 
initrd		/initrd.img-2.6.24-23-generic 

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic 
root		(hd0,0) 
kernel		/vmlinuz-2.6.24-22-generic root=UUID=1dd77d8e-23cb-43fc-8082-8776783e8781 ro quiet splash 
initrd		/initrd.img-2.6.24-22-generic 
quiet 

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic (recovery mode) 
root		(hd0,0) 
kernel		/vmlinuz-2.6.24-22-generic root=UUID=1dd77d8e-23cb-43fc-8082-8776783e8781 ro single 
initrd		/initrd.img-2.6.24-22-generic 

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic 
root		(hd0,0) 
kernel		/vmlinuz-2.6.24-21-generic root=UUID=1dd77d8e-23cb-43fc-8082-8776783e8781 ro quiet splash 
initrd		/initrd.img-2.6.24-21-generic 
quiet 

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic (recovery mode) 
root		(hd0,0) 
kernel		/vmlinuz-2.6.24-21-generic root=UUID=1dd77d8e-23cb-43fc-8082-8776783e8781 ro single 
initrd		/initrd.img-2.6.24-21-generic 

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic 
root		(hd0,0) 
kernel		/vmlinuz-2.6.24-19-generic root=UUID=1dd77d8e-23cb-43fc-8082-8776783e8781 ro quiet splash 
initrd		/initrd.img-2.6.24-19-generic 
quiet 

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic (recovery mode) 
root		(hd0,0) 
kernel		/vmlinuz-2.6.24-19-generic root=UUID=1dd77d8e-23cb-43fc-8082-8776783e8781 ro single 
initrd		/initrd.img-2.6.24-19-generic 

title		Ubuntu 8.04.3 LTS, memtest86+ 
root		(hd0,0) 
kernel		/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST 

=================== sdb1: Location of files loaded by Grub: =================== 


    .1GB: boot/grub/menu.lst 
    .1GB: boot/grub/stage2 
    .0GB: initrd.img-2.6.24-19-generic 
    .0GB: initrd.img-2.6.24-19-generic.bak 
    .0GB: initrd.img-2.6.24-21-generic 
    .0GB: initrd.img-2.6.24-21-generic.bak 
    .0GB: initrd.img-2.6.24-22-generic 
    .0GB: initrd.img-2.6.24-22-generic.bak 
    .0GB: initrd.img-2.6.24-23-generic 
    .1GB: initrd.img-2.6.24-23-generic.bak 
    .1GB: initrd.img-2.6.24-24-generic 
    .1GB: initrd.img-2.6.24-24-generic.bak 
    .1GB: stage2 
    .0GB: vmlinuz-2.6.24-19-generic 
    .0GB: vmlinuz-2.6.24-21-generic 
    .0GB: vmlinuz-2.6.24-22-generic 
    .1GB: vmlinuz-2.6.24-23-generic 
    .1GB: vmlinuz-2.6.24-24-generic 

============================ sdb3/etc/fstab: ============================= 

# /etc/fstab: static file system information. 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc /proc proc defaults 0 0 
# /dev/sdb3 
UUID=1dd77d8e-23cb-43fc-8082-8776783e8781 / ext3 nouser,relatime,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1 
# /dev/sdb1 
UUID=8099340c-8a96-4eb6-bf98-6b8d17932577 /boot ext3 nouser,relatime,atime,auto,rw,dev,exec,suid 0 2 
# /dev/sdb4 
UUID=62ae8371-d91f-4e33-9800-9dc40e148906 /home ext3 nouser,relatime,atime,auto,rw,dev,exec,suid 0 2 
# /dev/sda1 
UUID=67f24998-83f8-4c11-8d77-c1558638a8f9 /mythtv/recordings jfs nouser,relatime,atime,auto,rw,dev,exec,suid 0 2 
# /dev/sdb2 
UUID=5577a803-57d3-473a-b9ff-9f2e16b490c4 none swap sw 0 0 
/dev/scd0 /media/cdrom0 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0 
/dev/fd0 /media/floppy0 auto user,utf8,atime,noauto,rw,dev,exec,suid 0 0 

======================== Unknown MBRs/Boot Sectors/etc ==================== 

Unknown BootLoader  on sdb2 

00000000  42 ae e6 20 71 91 f8 57  91 19 27 4d 25 ab ec 7a  |B.. q..W..'M%..z| 
00000010  7a c5 a8 c4 fa 5f 4c 86  0b c8 d8 49 73 22 6c 88  |z...._L....Is"l.| 
00000020  aa 8f 2f e5 6c 0c 0e bc  8a e8 74 ab 29 a5 b7 86  |../.l.....t.)...| 
00000030  37 90 b3 c4 de 5e ed d9  50 39 ae 4a ba e9 0e a7  |7....^..P9.J....| 
00000040  a1 4d c9 c1 73 6e 64 6a  e5 9e ed 6c 24 1f 36 e3  |.M..sndj...l$.6.| 
00000050  0c 0b 18 e6 5f 73 eb cf  7a ee 67 d2 a0 d1 3c 3b  |...._s..z.g...<;| 
00000060  65 63 10 68 24 f2 3f d2  81 01 47 98 49 3d bf 0e  |ec.h$.?...G.I=..| 
00000070  b5 e7 4a ac 9d 47 4e 5a  d8 72 8d 3e 68 46 28 e9  |..J..GNZ.r.>hF(.| 
00000080  7c 39 1d d3 f8 76 d2 17  6d a3 ed 2d 36 4b 95 31  ||9...v..m..-6K.1| 
00000090  91 c1 04 7b 80 39 ab 97  8c 6f a1 92 d6 05 85 23  |...{.9...o.....#| 
000000a0  47 e4 ac 07 71 e3 19 27  f3 ac fd 95 9b 73 ea 69  |G...q..'.....s.i| 
000000b0  26 b5 49 1c 36 a1 68 f7  3a ee 9b a5 c4 f1 bd bc  |&.I.6.h.:.......| 
000000c0  30 8b 8b a3 2c 98 00 82  7e 51 f8 76 f7 ae 27 e2  |0...,...~Q.v..'.| 
000000d0  1f 86 96 6b e7 5b 25 8e  48 1d 10 46 36 b0 11 9e  |...k.[%.H..F6...| 
000000e0  41 ed f4 ad 29 c5 42 1c  ad 91 66 ee 99 e0 5a 9f  |A...).B...f...Z.| 
000000f0  80 ad f4 5b 6d 5b 53 77  78 5e 14 2b f6 b9 10 65  |...[m[Swx^.+...e| 
00000100  5c 8f f5 7c fb 64 02 2b  c7 fc 05 a1 db 69 fa fc  |\..|.d.+.....i..| 
00000110  da fc ae 9e 64 12 19 e2  78 f9 36 ce bd 30 3a e4  |....d...x.6..0:.| 
00000120  e4 74 ae a5 08 b5 18 dc  e2 ac fd 9c de 9a 1f 26  |.t.............&| 
00000130  7e d1 d6 e5 75 4b 4d 4a  de 79 56 e6 ef 50 91 5a  |~...uKMJ.yV..P.Z| 
00000140  35 61 fe a8 65 b3 cf 4c  96 15 f2 7d bd d3 0f 14  |5a..e..L...}....| 
00000150  e9 d7 f1 c9 75 6d 15 b3  ae c7 dc ac e1 ba 30 da  |....um........0.| 
00000160  3a 7d 47 5a ef a3 ec f0  f4 a4 e2 b5 64 50 a1 39  |:}GZ........dP.9| 
00000170  ce 75 14 ac 91 f5 15 a7  8c 06 8f aa 47 0b 4c d3  |.u..........G.L.| 
00000180  a5 d2 27 98 db 36 ac 64  9c 60 a9 ef 9c 71 5f 44  |..'..6.d.`...q_D| 
00000190  68 56 b7 d2 58 3d e9 4c  db b6 d9 93 07 01 64 ec  |hV..X=.L......d.| 
000001a0  3d b8 e7 8f 4a 31 2a 1f  55 4a 5b a6 44 25 cc a5  |=...J1*.UJ[.D%..| 
000001b0  04 f5 47 d1 3e 1c bc b4  b0 b1 49 58 a3 4e f1 02  |..G.>.....IX.N..| 
000001c0  15 81 39 f7 e6 bd eb c2  3a ac d7 76 2d 31 9d b7  |..9.....:..v-1..| 
000001d0  34 26 57 8a 34 20 47 80  4d 79 b5 7d db 25 d4 ea  |4&W.4 G.My.}.%..| 
000001e0  c3 d4 9c 5f 2d 83 52 13  5e c0 eb f2 ed b8 cf 32  |..._-.R.^......2| 
000001f0  9d bb 90 1e a3 d7 e6 af  92 fe 22 dd c9 e1 d3 ac  |..........".....| 
00000200

---

