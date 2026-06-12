---
title: "Installed Ubuntu 9.04 - Problems booting"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by JerseyJim on 2009-08-30
I installed Ubuntu on a partition with XP.  Everything seemed to be okay.  The partitions are where they should be.  Both OS are on a disk other than C.  When I boot up, the system will start to boot into Window, and then restart the computer.  I can look at everything with my rescue cd, but I'm not sure where to start.

---

### Post by oboedad55 on 2009-08-30
> **JerseyJim said:**
> I installed Ubuntu on a partition with XP.  Everything seemed to be okay.  The partitions are where they should be.  Both OS are on a disk other than C.  When I boot up, the system will start to boot into Window, and then restart the computer.  I can look at everything with my rescue cd, but I'm not sure where to start.

How did you install Ubuntu, with Wubi or as a normal install?

---

### Post by tal007 on 2009-08-30
You can not install two operating systems on the same partition. Windows Xp and Ubuntu are different. They use different file system type. Xp uses NTFS, Ubuntu ext2,etx3,ext4 etc... They can not share the same partition. You probably installed Ubuntu over XP partition. If you did that you have lost your Xp.

---

### Post by raymondh on 2009-08-30
JerseyJim,

Is this a wubi-install or not?

Boot into the liveCD and in live session (try ubuntu without any changes).  IN live session, access a terminal (applications > accessories) and type

```
sudo fdisk -l
```

small L not 1 nor I.

Kindly copy and paste results in your next post.  Let's take a look at your HD.

---

### Post by JerseyJim on 2009-08-30
It wasn't with Wubi.  I installed from the disk.  As far as I can see, XP wasn't overlaid. I split off part of the XP partition, and installed Ubuntu into the new partition.  

here is the paste of the FDISK

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa8d76f81

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1914    15374173+   7  HPFS/NTFS
/dev/sda2            1915        7297    43238947+   f  W95 Ext'd (LBA)
/dev/sda5            1915        3828    15374173+   7  HPFS/NTFS
/dev/sda6            3829        5742    15374173+   7  HPFS/NTFS
/dev/sda7            5743        7297    12490506    7  HPFS/NTFS

Disk /dev/sdb: 10.2 GB, 10200637440 bytes
145 heads, 63 sectors/track, 2180 cylinders
Units = cylinders of 9135 * 512 = 4677120 bytes
Disk identifier: 0x07310731

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2180     9953496    7  HPFS/NTFS

Disk /dev/sdc: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07470747

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2338    18779953+   7  HPFS/NTFS
/dev/sdc2            2339        4866    20306160    f  W95 Ext'd (LBA)
/dev/sdc5   *        2339        3896    12514572   83  Linux
/dev/sdc6            3897        3971      602406   82  Linux swap / Solaris
/dev/sdc7            3972        4866     7189056    7  HPFS/NTFS

Disk /dev/sdd: 100 MB, 100663296 bytes
64 heads, 32 sectors/track, 96 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x0e78014e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd4   *           1          96       98288    6  FAT16
ubuntu@ubuntu:~$

---

### Post by JerseyJim on 2009-08-30
Additional info from Boot Info.  

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => No known boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
Hibernated non-system partition, refused to mount.
Failed to mount '/dev/sdb1': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, or mount the volume read-only with the 'ro' mount option, or
mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:

            mount -t ntfs-3g -o remove_hiberfile /dev/sdb1 sdb1

Hibernated non-system partition, refused to mount.
Failed to mount '/dev/sdb1': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, or mount the volume read-only with the 'ro' mount option, or
mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:

            mount -t ntfs-3g -o remove_hiberfile /dev/sdb1 sdb1


sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdd4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa8d76f81

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    30,748,409    30,748,347   7 HPFS/NTFS
/dev/sda2          30,748,410   117,226,304    86,477,895   f W95 Ext d (LBA)
/dev/sda5          30,748,473    61,496,819    30,748,347   7 HPFS/NTFS
/dev/sda6          61,496,883    92,245,229    30,748,347   7 HPFS/NTFS
/dev/sda7          92,245,293   117,226,304    24,981,012   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 10.2 GB, 10200637440 bytes
145 heads, 63 sectors/track, 2180 cylinders, total 19923120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x07310731

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    19,907,054    19,906,992   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x07470747

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    37,559,969    37,559,907   7 HPFS/NTFS
/dev/sdc2          37,559,970    78,172,289    40,612,320   f W95 Ext d (LBA)
/dev/sdc5    *     37,560,096    62,589,239    25,029,144  83 Linux
/dev/sdc6          62,589,303    63,794,114     1,204,812  82 Linux swap / Solaris
/dev/sdc7          63,794,178    78,172,289    14,378,112   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 100 MB, 100663296 bytes
64 heads, 32 sectors/track, 96 cylinders, total 196608 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0e78014e

Partition  Boot         Start           End          Size  Id System

/dev/sdd4    *             32       196,607       196,576   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="0000000000000000" LABEL="New Volume" TYPE="ntfs" 
/dev/sda5: UUID="0000000000000000" LABEL="New Volume" TYPE="ntfs" 
/dev/sda6: UUID="0000000000000000" LABEL="New Volume" TYPE="ntfs" 
/dev/sda7: UUID="0000000000000000" LABEL="New Volume" TYPE="ntfs" 
/dev/sdb1: UUID="4CE838A3E8388CE8" LABEL="Local Disk" TYPE="ntfs" 
/dev/sdc1: UUID="0E04F11404F0FF8F" LABEL="DISK2PART01" TYPE="ntfs" 
/dev/sdc5: UUID="dd624e69-0f26-4308-ba74-c92544530b65" TYPE="ext3" 
/dev/sdc6: UUID="3e555adc-39dd-49f9-9880-a230785d8ec6" TYPE="swap" 
/dev/sdc7: UUID="12C098A4C0989019" TYPE="ntfs" 
/dev/sdd4: SEC_TYPE="msdos" LABEL="ZIP-100" UUID="34D8-1C07" TYPE="vfat" 

=============================== "mount" output: ===============================

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
/dev/sr1 on /media/RESCUE_DISK type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=999,utf8)
/dev/sdd4 on /media/ZIP-100 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda7 on /media/New Volume type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/New Volume_ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/New Volume__ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdc1 on /media/DISK2PART01 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /media/New Volume___ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=20 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="win xp"  

=========================== sdc5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=dd624e69-0f26-4308-ba74-c92544530b65 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dd624e69-0f26-4308-ba74-c92544530b65

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
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        dd624e69-0f26-4308-ba74-c92544530b65
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=dd624e69-0f26-4308-ba74-c92544530b65 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        dd624e69-0f26-4308-ba74-c92544530b65
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=dd624e69-0f26-4308-ba74-c92544530b65 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        dd624e69-0f26-4308-ba74-c92544530b65
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows NT/2000/XP (loader)
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc6 during installation
UUID=dd624e69-0f26-4308-ba74-c92544530b65 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc7 during installation
UUID=3e555adc-39dd-49f9-9880-a230785d8ec6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


  28.5GB: boot/grub/menu.lst
  28.5GB: boot/grub/stage2
  28.5GB: boot/initrd.img-2.6.28-11-generic
  28.5GB: boot/vmlinuz-2.6.28-11-generic
  28.5GB: initrd.img
  28.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdd

00000000  eb 2e 49 50 41 52 54 20  63 6f 64 65 20 30 30 39  |..IPART code 009|
00000010  20 2d 20 49 6f 6d 65 67  61 20 43 6f 72 70 6f 72  | - Iomega Corpor|
00000020  61 74 69 6f 6e 20 2d 20  31 31 2f 32 33 2f 39 30  |ation - 11/23/90|
00000030  fa fc 8c c8 8e d0 bc 00  7c 8e d8 8e c0 b9 00 02  |........|.......|
00000040  bf 00 7e be 00 7c f3 a4  e9 00 02 fb bd 00 7e 8b  |..~..|........~.|
00000050  fd be be 01 b9 04 00 80  3a 80 74 0b 83 c6 10 e2  |........:.t.....|
00000060  f6 8b b5 b2 01 eb 51 56  83 c6 10 49 e3 0b 80 3a  |......QV...I...:|
00000070  80 75 f5 8b b5 b0 01 eb  3f 5e 56 8a 12 8a 72 01  |.u......?^V...r.|
00000080  8a 4a 02 8a 6a 03 bb 00  7c be 05 00 56 b8 01 02  |.J..j...|...V...|
00000090  cd 13 73 0e 33 c0 cd 13  5e 4e 75 f0 8b b5 b4 01  |..s.3...^Nu.....|
000000a0  eb 16 5e be fe 7d 81 3c  55 aa 74 06 8b b5 b6 01  |..^..}.<U.t.....|
000000b0  eb 06 5e 03 f5 e9 48 fd  e8 1b 00 8b b5 b8 01 e8  |..^...H.........|
000000c0  14 00 b4 00 cd 16 33 c0  8e c0 26 c7 06 72 04 34  |......3...&..r.4|
000000d0  12 ea f0 ff 00 f0 03 f5  ac 3c 00 74 0b 56 b4 0e  |.........<.t.V..|
000000e0  bb 07 00 cd 10 5e eb f0  c3 49 6e 76 61 6c 69 64  |.....^...Invalid|
000000f0  20 70 61 72 74 69 74 69  6f 6e 20 74 61 62 6c 65  | partition table|
00000100  00 44 69 73 6b 20 69 73  20 6e 6f 74 20 62 6f 6f  |.Disk is not boo|
00000110  74 61 62 6c 65 00 45 72  72 6f 72 20 6c 6f 61 64  |table.Error load|
00000120  69 6e 67 20 6f 70 65 72  61 74 69 6e 67 20 73 79  |ing operating sy|
00000130  73 74 65 6d 00 4d 69 73  73 69 6e 67 20 6f 70 65  |stem.Missing ope|
00000140  72 61 74 69 6e 67 20 73  79 73 74 65 6d 00 0d 0a  |rating system...|
00000150  52 65 70 6c 61 63 65 20  61 6e 64 20 73 74 72 69  |Replace and stri|
00000160  6b 65 20 61 6e 79 20 6b  65 79 20 77 68 65 6e 20  |ke any key when |
00000170  72 65 61 64 79 0d 0a 00  00 00 00 00 00 00 00 00  |ready...........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 e9 00  |................|
000001b0  e9 00 01 01 16 01 35 01  4e 01 78 0e 13 6b 00 00  |......5.N.x..k..|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 80 01  |................|
000001f0  01 00 06 3f 20 5f 20 00  00 00 e0 ff 02 00 55 aa  |...? _ .......U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sde sdf

---

### Post by presence1960 on 2009-08-30
well it looks like you really fouled this up, there are numerous things not as they should be. First you did not install a bootloader for linux, that we can fix. But your windows on sda1 has a boot.ini file but no NTLDR. is that an actual windows installation on that partition? if it is we can maybe fix that also. You also have a major problem with windows on sdb1 which from the message in the output I suspect that is your windows installation. You left that in hibernation and did not come out of it, now the partition can not be mounted.

To sort all this out I would If I were you sort out the windows install first because reinstalling windows is a time consuming bear. I would not want to reinstall windows unless absolutely necessary. Then we can work on installing GRUB so you can boot either OS.

Is the partition sda1 a windows OS? If it is I would try to repair the bootloader there and see if we can get that to boot.

The windows on sdb1 may be a lost cause, as is the possibility that the one on sda1 is also. Once you get GRUB installed you can boot into ubuntu and try running the command given in the script for sdb1. I would not hold my breath though, if this is the case I would reinstall windows then configure GRUB to boot windows also.

---

### Post by JerseyJim on 2009-08-30
sdc1 is the main windows partition.  sdb1 was a failed install.  I should have cleaned it out a long time ago.  When was booting up into XP, it gave me two choices.  I just chose the install that was working.  I'm not sure why there is a sda1 boot flag, the os isn't located there.  That was the disk that I added to hold a bunch of misc programs.  The script should probably be sdc1 instead of sdb1.

---

### Post by presence1960 on 2009-08-30
Ok I will go by your word here that sdc1 is the windows install. it does not have any boot files/dir so you will have to try to fix that with the windows XP install disk. This what you want to do:

Put the windows install disk in the CD drive. Boot your machine & go into BIOS before trying to fix windows. In BIOS put sdc 40GB disk as first in the order of hard disk booting. This is very critical. If sdc (40 GB) is not first hard disk to boot you will have more problems. Once you set the 40 Gb disk to boot save the changes & exit BIOS. You are going to boot off the windows install disk and try to repair the bootloader for windows on sdc1 by doing [this]("http://ubuntuforums.org/showthread.php?t=1014708") (scroll down to instructions for XP)
When complete reboot and see if you boot straight into windows XP. if you do you need to do one more thing. You are now going to install GRUB to MBR of sdc so you will be able to boot Ubuntu and windows from GRUB menu. Follow this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,4)or   (hd2,4)". Use whatever your computer spits out for the following lines.
5. Type "root (hd0,4) or root (hd2,4)", or whatever your hard disk + boot  partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)" or setup (hd2), to install GRUB to MBR, depending on the output from #4 above. if (hd0,4) use setup (hd0), if (hd2,4) use setup (hd2)
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

You should be greeted by the GRUB menu when you boot. Try Ubuntu to see if it boots. If it does reboot & try windows. if windows is not an entry we can fix that easily too. Give it a whirl!

---

### Post by presence1960 on 2009-08-30
Just in case that windows fix does not work and windows still will not boot you may have to rebuild the boot.ini file. here is a how to on that 
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

if you need to do this do it before you install GRUB from the Ubuntu Live CD.

---

### Post by JerseyJim on 2009-08-31
Thanks for your note Presence. I think I know what went wrong with the install.  My machine is already dual booted.  One to Windows XP, and the other to the failed install.  I think I should have gotten rid of the second boot before starting the install of Ubuntu.  Would it be better for me to erase the Ubuntu partition, fix the problem with XP, and then reinstall Ubuntu?

---

### Post by presence1960 on 2009-08-31
> **JerseyJim said:**
> Thanks for your note Presence. I think I know what went wrong with the install.  My machine is already dual booted.  One to Windows XP, and the other to the failed install.  I think I should have gotten rid of the second boot before starting the install of Ubuntu.  Would it be better for me to erase the Ubuntu partition, fix the problem with XP, and then reinstall Ubuntu?

I would install GRUB to MBR of sdc as outlined in previous post. make sure after installing GRUB to the sdc disk set sdc to boot first in hard disk boot priority in BIOS. Reboot & see if Ubuntu runs. If Ubuntu works, leave it be. Then fix those windows partitions and reinstall Windows.

Note : if you install windows to sdc you will have to reinstall GRUB again. If you install windows to sda or sdb make sure you set the disk you are putting windows on to boot first in BIOS because windows always tries to write it's bootloader to the first disk that boots (very important). If you put windows on sda or sdb you should not have to mess with GRUB again other than to add the windows entry to menu.lst so you can boot windows. post back if you need help.

---

### Post by JerseyJim on 2009-08-31
I'm able to boot up into Ubuntu from the Grub menu.  XP gets to the Window XP screen, and shuts down.

---

### Post by presence1960 on 2009-08-31
Great JerseyJim. leave ubuntu alone! If you want to install Windows onto sdc1 all you need to do is Boot off the Ubuntu Live CD & choose "Try Ubuntu without any changes". When the desktop loads you want to use gparted to delete that bad windows install on sdb. You can access gparted by opening a terminal and typing ```
gksu gparted
``` or by going System > Administration > Partition Editor.

Then I would reboot with the windows install CD and install Windows to sdc1. You may want to make note of that partitions size while in gparted so you can tell which partition is actually sdc1 from inside the windows installer. Reinstall Windows to that sdc1 partition. When completed you are going to have to reinstall GRUB again. You are halfway there now!

---

### Post by tal007 on 2009-08-31
My friend, I don't want to sound very insensitive to your loss and pain. It looks like you have to  write an Obituary for your Xp. Boot sector on your drive is like a map that hold records containing the location of each and every file on your drive. If you have lost that there is nothing on Earth will be able to bring back what you have on your drive. Without that you will not be able to locate anything on your drive. It is like driving in a big city without a map.

---

### Post by presence1960 on 2009-08-31
> **tal007 said:**
> My friend, I don't want to sound very insensitive to your loss and pain. It looks like you have to  write an Obituary for your Xp. Boot sector on your drive is like a map that hold records containing the location of each and every file on your drive. If you have lost that there is nothing on Earth will be able to bring back what you have on your drive. Without that you will not be able to locate anything on your drive. It is like driving in a big city without a map.

I don't want to sound insensitive but have you been following the progress of this thread? Try posting something relevant to the task at hand. The OP has reinstalled GRUB to MBR of sdc & set sdc as first in hard disk booting in BIOS and has been able to boot Ubuntu. Now he wishes to scrap the failed windows install on sdb and also the one on sdc1 and reinstall windows to sdc1.

That is where we are at currently. Post something helpful to the task at hand.

P.S. he may be able to save data off sdc1 with backtrack linux or possibly even the Ubuntu live CD.

---

### Post by JerseyJim on 2009-09-04
Hey Presense, I ran into a bit of a snag.  My sister used my XP install disk to boot up her pc, and misplaced it.  She hasn't been able to locate it.  Using windows recovery is out.  I thought I had a copy of it on cd, but I can't find it.  Is there a way of unhibernating my primary disk?  Or is there a tool that would allow me to boot from my second disk?

---

### Post by presence1960 on 2009-09-05
> **JerseyJim said:**
> Hey Presense, I ran into a bit of a snag.  My sister used my XP install disk to boot up her pc, and misplaced it.  She hasn't been able to locate it.  Using windows recovery is out.  I thought I had a copy of it on cd, but I can't find it.  Is there a way of unhibernating my primary disk?  Or is there a tool that would allow me to boot from my second disk?

Boot into Ubuntu, open a terminal and run this command ```
mount -t ntfs-3g -o remove_hiberfile /dev/sdb1 sdb1
``` you may need to use sudo in front of that if it says you don't have permission. That is straight from the boot info script output for sdb1. See if it works and then we will have to edit your windows entry in menu.lst to be for sdb1. I will need to know what order in BIOS sdb boots. We know sdc is first. Well run that command and let's see what happens.

P.S. sorry about the delay, I was at my part time job tonight. I manage a pro shop inside a bowling center. Lots of hands to measure tonight for new balls.

---

### Post by JerseyJim on 2009-09-05
I'm a bowler myself.  Although I'm stuck with subbing until I find a new job.  Where do you bowl out of?

I had to fiddle with the mount command to use the label, but it seems to be mounted.  I did another BOOT INFO script.  I saw this:

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa8d76f81

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    30,748,409    30,748,347   7 HPFS/NTFS
/dev/sda2          30,748,410   117,226,304    86,477,895   f W95 Ext d (LBA)
/dev/sda5          30,748,473    61,496,819    30,748,347   7 HPFS/NTFS
/dev/sda6          61,496,883    92,245,229    30,748,347   7 HPFS/NTFS
/dev/sda7          92,245,293   117,226,304    24,981,012   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 10.2 GB, 10200637440 bytes
145 heads, 63 sectors/track, 2180 cylinders, total 19923120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x07310731

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    19,907,054    19,906,992   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x07470747

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    37,559,969    37,559,907   7 HPFS/NTFS
/dev/sdc2          37,559,970    78,172,289    40,612,320   f W95 Ext d (LBA)
/dev/sdc5          37,560,096    62,589,239    25,029,144  83 Linux
/dev/sdc6          62,589,303    63,794,114     1,204,812  82 Linux swap / Solaris
/dev/sdc7          63,794,178    78,172,289    14,378,112   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0000000000000000" LABEL="New Volume" TYPE="ntfs" 
/dev/sda5: UUID="0000000000000000" LABEL="New Volume" TYPE="ntfs" 
/dev/sda6: UUID="0000000000000000" LABEL="New Volume" TYPE="ntfs" 
/dev/sda7: UUID="0000000000000000" LABEL="New Volume" TYPE="ntfs" 
/dev/sdb1: UUID="4CE838A3E8388CE8" LABEL="Local Disk" TYPE="ntfs" 
/dev/sdc1: UUID="0E04F11404F0FF8F" LABEL="DISK2PART01" TYPE="ntfs" 
/dev/sdc5: UUID="dd624e69-0f26-4308-ba74-c92544530b65" TYPE="ext3" 
/dev/sdc6: UUID="3e555adc-39dd-49f9-9880-a230785d8ec6" TYPE="swap" 
/dev/sdc7: UUID="12C098A4C0989019" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdc5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jerseyjim/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jerseyjim)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=20 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="win xp"  

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect 

It looks to me like the boot record was written to SDA1 instead of SDC1.  I should be able to build a boot record on SDC1.  Is that correct?

---

### Post by presence1960 on 2009-09-05
what is the boot order of your hard disks in BIOS? we want sdc first as that has GRUB, but what are the other disks order?

You can see if sda Windows or sdb Windows will boot by going into Bios and putting them first to boot. Try sda, then sdb. See if either will boot. If one of them boots since you don't have the XP install disk you can use that one. We would just have to make an entry in menu.lst for that windows to appear in GRUB.

---

### Post by presence1960 on 2009-09-05
> I'm a bowler myself. Although I'm stuck with subbing until I find a new job. Where do you bowl out of?

I did not bowl last winter season, i took a year off. I am bowling this year out of Erie lanes in Philadelphia. That is where I work part time as well.

---

### Post by JerseyJim on 2009-09-05
Hey Presence, Great news, I copied the partition boot record over from SDA to SDC, left the boot order alone and was able to boot up into XP.  I'm not going to mess around with SDB.  Thanks for your help!!

---

### Post by presence1960 on 2009-09-05
> **JerseyJim said:**
> Hey Presence, Great news, I copied the partition boot record over from SDA to SDC, left the boot order alone and was able to boot up into XP.  I'm not going to mess around with SDB.  Thanks for your help!!

Excellent! Glad you got it working. When you get the time you may want to copy any files over from the other windows on sda & sdc then remove those partitions. Enjoy Ubuntu.

---

