---
title: "New install, GRUB error 17"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by andyl1980 on 2009-08-27
I am trying to become a new user of Ubuntu, but so far am not having any luck.
I installed Ubuntu 9.04 x64 over my XP installation and after the installation completed cannot get past GRUB error 17.

Here is relevant info that was requested in every topic about this error.


```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #7 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde
 => Windows is installed in the MBR of /dev/sdf
 => Grub0.97 is installed in the MBR of /dev/sdg and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdh
 => Windows is installed in the MBR of /dev/sdi
 => Windows is installed in the MBR of /dev/sdj
 => Windows is installed in the MBR of /dev/sdk

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdg1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdg2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdg5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdh1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdi1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdj1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdk1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2b793bed

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5d5a18bb

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2b793bee

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5d5a18b8

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaaf283c3

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaaf283c4

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x18cf18ce

Partition  Boot         Start           End          Size  Id System

/dev/sdg1                  63   149,838,254   149,838,192  83 Linux
/dev/sdg2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdg5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaaf283c5

Partition  Boot         Start           End          Size  Id System

/dev/sdh1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdi ___________________ _____________________________________________________

Disk /dev/sdi: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x706c7cb8

Partition  Boot         Start           End          Size  Id System

/dev/sdi1                  63   781,417,664   781,417,602   7 HPFS/NTFS


Drive: sdj ___________________ _____________________________________________________

Disk /dev/sdj: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaa66d0ab

Partition  Boot         Start           End          Size  Id System

/dev/sdj1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdk ___________________ _____________________________________________________

Disk /dev/sdk: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x228e94bd

Partition  Boot         Start           End          Size  Id System

/dev/sdk1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="AA041031040FFECF" LABEL="320" TYPE="ntfs" 
/dev/sdb1: UUID="F4301BFC301BC490" LABEL="Empty 320" TYPE="ntfs" 
/dev/sdc1: UUID="F8884D18884CD6B2" LABEL="Squeeze 500" TYPE="ntfs" 
/dev/sdd1: UUID="6C385A85385A4E68" LABEL="Torrent Movies 500" TYPE="ntfs" 
/dev/sde1: UUID="967093DA7093C003" LABEL="Movies 1000" TYPE="ntfs" 
/dev/sdf1: UUID="4C9C9E7A9C9E5DF0" LABEL="TV 1000" TYPE="ntfs" 
/dev/sdg1: UUID="9db40bfc-4515-4ce9-aa76-5a522adf19fc" TYPE="ext3" 
/dev/sdg5: UUID="66761010-bdd7-4c18-943f-c51a4a5a7213" TYPE="swap" 
/dev/sdh1: UUID="D0FCAAC4FCAAA466" LABEL="Ripped 1000" TYPE="ntfs" 
/dev/sdi1: UUID="4AEC6F13EC6EF919" LABEL="Downloading 400" TYPE="ntfs" 
/dev/sdj1: UUID="E488F55D88F52EA4" LABEL="Record U 1000" TYPE="ntfs" 
/dev/sdk1: UUID="D404B46304B449EE" LABEL="Torrent TV 500" TYPE="ntfs" 

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
/dev/sdg1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdf1 on /media/TV 1000 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/Squeeze 500 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sde1 on /media/Movies 1000 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdh1 on /media/Ripped 1000 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdk1 on /media/Torrent TV 500 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/Empty 320 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1 on /media/Torrent Movies 500 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdi1 on /media/Downloading 400 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/320 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdj1 on /media/Record U 1000 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sdg1/boot/grub/menu.lst: ===========================

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
timeout        3

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
# kopt=root=UUID=9db40bfc-4515-4ce9-aa76-5a522adf19fc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9db40bfc-4515-4ce9-aa76-5a522adf19fc

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
uuid        9db40bfc-4515-4ce9-aa76-5a522adf19fc
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9db40bfc-4515-4ce9-aa76-5a522adf19fc ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        9db40bfc-4515-4ce9-aa76-5a522adf19fc
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9db40bfc-4515-4ce9-aa76-5a522adf19fc ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        9db40bfc-4515-4ce9-aa76-5a522adf19fc
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdg1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdg1 during installation
UUID=9db40bfc-4515-4ce9-aa76-5a522adf19fc /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdg5 during installation
UUID=66761010-bdd7-4c18-943f-c51a4a5a7213 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdg1: Location of files loaded by Grub: ===================


   9.5GB: boot/grub/menu.lst
   9.6GB: boot/grub/stage2
   9.5GB: boot/initrd.img-2.6.28-11-generic
   9.5GB: boot/vmlinuz-2.6.28-11-generic
   9.5GB: initrd.img
   9.5GB: vmlinuz

```Any help would be appreciated.

---

### Post by ronparent on 2009-08-27
You do love challanges :)

The script file is helpful. Which drive is set first in the bios boot order? You should be able to boot with either sda or sdg set first in the boot order. If for some reason it is not working from sda, can you check to see if it would boot with sdg first in the boot order?

---

### Post by presence1960 on 2009-08-27
Ron is absolutely correct. Either your sda (320 GB) or sdg (80 GB) should boot first in BIOS hard disk order. Either one will get you to boot Ubuntu, but you may have to edit the windows entry in menu.lst to get windows to boot. What that entry will read will depend on which hard disk boots first in BIOS. report back.

P.S. nevermind about windows, I see you don't have it installed. breezing through all those entries I misinterpreted some of the info.

---

