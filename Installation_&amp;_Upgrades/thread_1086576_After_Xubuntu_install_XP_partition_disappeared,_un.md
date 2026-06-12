---
title: "After Xubuntu install XP partition disappeared, unable to boot into Xubuntu. Help!"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by Roob on 2009-03-04
I started a [thread]("http://ubuntuforums.org/showthread.php?t=1084528") on this earlier, but because it was getting a bit messy, I start a new one.

System:
- Abit BX133 (with integrated Highpoint 370 RAID controller)
- Intel P3 1 GHz CPU
- 768 kB Mem
- CDrom drive on IDE-1 as prim. master
- 2 HDD's connected to Highpoint370 RAID-controller:
   * HDD 1: 160 GB, part. 1: 10 GB with WinXP, 2: 150 GB Data
   * HDD 2: 20 GB, empty (-> Xubuntu)

Operator:
- Totally new to Linux

This is what I did:
I booted from the Xubuntu CD, and chose install. In the partitioning menu I chose option 2 (use entire disk), and chose the empty HDD2. Install went just fine w/o any errors.

After this I couldn't boot into either OS though. I tried booting from both HDD's.
- When booting from HDD 2 the system rebooted just after displaying "Verifying DMI pool data"
- When booting from HDD 1 system hanged right there, w/o displaying any errors

So, I booted into the live CD and ran the Boot Info Script:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader? is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 24595578. But according to the info from 
                       fdisk, sdb1 starts at sector 16128.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9e369e36

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    37,383,254    37,383,192  83 Linux
/dev/sda2          37,383,255    39,102,209     1,718,955   5 Extended
/dev/sda5          37,383,318    39,102,209     1,718,892  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbd5a7964

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *         16,128   312,576,704   312,560,577   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8019 MB, 8019509248 bytes
16 heads, 32 sectors/track, 30592 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdfa4a156

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  32    15,663,103    15,663,072   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="d7414e7f-58fb-4d29-b93b-a6ad9a7033e4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="4d062ec7-7f94-4665-88eb-cad3b870a043" 
/dev/sdb1: UUID="4E64F5EC64F5D725" LABEL="DATA" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/sdc1: LABEL="USB" UUID="8E35-50FE" TYPE="vfat" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sdc1 on /media/USB type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=999)


=========================== sda1/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=d7414e7f-58fb-4d29-b93b-a6ad9a7033e4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d7414e7f-58fb-4d29-b93b-a6ad9a7033e4

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d7414e7f-58fb-4d29-b93b-a6ad9a7033e4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d7414e7f-58fb-4d29-b93b-a6ad9a7033e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d7414e7f-58fb-4d29-b93b-a6ad9a7033e4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d7414e7f-58fb-4d29-b93b-a6ad9a7033e4 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d7414e7f-58fb-4d29-b93b-a6ad9a7033e4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d7414e7f-58fb-4d29-b93b-a6ad9a7033e4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4d062ec7-7f94-4665-88eb-cad3b870a043 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  18.4GB: boot/grub/menu.lst
  18.4GB: boot/grub/stage2
  18.4GB: boot/initrd.img-2.6.27-7-generic
  18.4GB: boot/vmlinuz-2.6.27-7-generic
  18.4GB: initrd.img
  18.4GB: vmlinuz
```

"Fdisk -l" rendered these results:
```
Cannot open /dev/sda
Cannot open /dev/sdb

Disk /dev/sdc: 8019 MB, 8019509248 bytes
16 heads, 32 sectors/track, 30592 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xdfa4a156

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30592     7831536    b  W95 FAT32
```

(sdc must be my 8 GB USB stick)

I then booted into O&O Rescuebox, which saw - this is getting weirder and weirder - my hard drive like this:

"WDC 1600JD-00HBB0(149.0 .... (rest out of screen)
  C: NTFS, 40 GB
  D: NTFS, 40 GB
  E: NTFS, 69,04 GB

Then I booted into the super-GRUB-CD

When trying loading Linux ("booting Ubuntu 8.10....") it hang, WinXP and Memtest returned error 13 ("Invalid or unsupported executable format"). Trying to fix mbr's resulted into hanging of the machine.

It listed the following partitions:
```
Natural Linux-IDE Linux SCSI Grub Hurd Size
   1        hda     sda (hd0) hd0 18 GB
   2        hdb     sdb (hd1) hd1 149 GB
```

(every app seems to have its own, unique opinion about the partitions of my HDD).

I then booted into the WinXP-CD again, "F6" and loaded Highpoint-drivers. I executed fixmbr in the recovery console.

After this I was still not able to boot into either OS. "Results.txt" now looks like this:
```
============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader? is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 24595578. But according to the info from 
                       fdisk, sdb1 starts at sector 16128.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9e369e36

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    37,383,254    37,383,192  83 Linux
/dev/sda2          37,383,255    39,102,209     1,718,955   5 Extended
/dev/sda5          37,383,318    39,102,209     1,718,892  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbd5a7964

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *         16,128   312,576,704   312,560,577   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8019 MB, 8019509248 bytes
16 heads, 32 sectors/track, 30592 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdfa4a156

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  32    15,663,103    15,663,072   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="d7414e7f-58fb-4d29-b93b-a6ad9a7033e4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="4d062ec7-7f94-4665-88eb-cad3b870a043" 
/dev/sdb1: UUID="4E64F5EC64F5D725" LABEL="DATA" TYPE="ntfs" 
/dev/sdc1: LABEL="USB" UUID="8E35-50FE" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sdb1 on /media/DATA type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/USB type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=999)


=========================== sda1/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=d7414e7f-58fb-4d29-b93b-a6ad9a7033e4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d7414e7f-58fb-4d29-b93b-a6ad9a7033e4

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d7414e7f-58fb-4d29-b93b-a6ad9a7033e4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d7414e7f-58fb-4d29-b93b-a6ad9a7033e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d7414e7f-58fb-4d29-b93b-a6ad9a7033e4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d7414e7f-58fb-4d29-b93b-a6ad9a7033e4 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d7414e7f-58fb-4d29-b93b-a6ad9a7033e4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d7414e7f-58fb-4d29-b93b-a6ad9a7033e4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4d062ec7-7f94-4665-88eb-cad3b870a043 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  18.4GB: boot/grub/menu.lst
  18.4GB: boot/grub/stage2
  18.4GB: boot/initrd.img-2.6.27-7-generic
  18.4GB: boot/vmlinuz-2.6.27-7-generic
  18.4GB: initrd.img
  18.4GB: vmlinuz
```

As far as I can see, the only differences 'fixing' the mbr has let to in "Result.txt" are these:

```
1. In Boot Info Summary:
" => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst."

is now replaced by

" => Syslinux is installed in the MBR of /dev/sda"

2. New entry in "mount" output:
"/dev/sdb1 on /media/DATA type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)"
```


Booting into Paragon partition manager, and executing "View mounted partitions" renders these results:
```

Basic disk 0:
N L Type      FS     Size     Label    Device      Mount
0 C Primary  Ext3FS 17.8 Gb          /dev/hde1   mnt/disk/hde1
1   Extended        839.3 Mb         /dev/hde2
2   Logical  LSWAP2 839.3 Mb         /dev/hde5

Basic disk 1:
N L Type      FS     Size     Label    Device      Mount
0   Primary  Free   7.9 Mb
1 D Primary  NTFS   149.0 Gb  DATA   /dev/hdf1   mnt/disk/hdf1

Basic disk 2:
N L Type      FS     Size     Label    Device      Mount
0 E Primary  FAT32    7.5 Gb  USB    /dev/sda1   mnt/disk/sda1


```

Finally, booting into Windows XP, I get this is the partitioning section (translated from dutch):
```

Disk of 7641 MB on disk [MBR]
D: partition 1 (USB) [FAT32]   7648 MB

Disk of 19093 MB, 0 with ID0 at bus 0 (hpt3xx) [MBR]
F: partition 1 [Unknown]     18254 MB (18254 MB free)
G: partition 2 [Unknown]       839 MB (839 MB free)

Disk of 152626 MB, 0 with ID1 at bus 0 (hpt3xx) [MBR]
   Not partitioned space              8 MB
C: partition 1 (DATA) [NTFS]     152617 MB (30924 MB free)

```

Quite sure all of this has got something to do with the Highpoint RAID adapter not properly recognized by Xubuntu. Question is: how can I restore things? Most important thing right now is getting XP to work again and to keep my data (in the "DATA"-partition) in tact.

---

### Post by overdrank on 2009-03-04
Please do not create duplicate threads on the same issue. [Duplicate here]("http://ubuntuforums.org/showthread.php?t=1084528")

---

