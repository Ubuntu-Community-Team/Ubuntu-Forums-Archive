---
title: "Can not boot XP"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by Rodney9 on 2009-03-04
Hello I installed XP home edition on my spare drive after Ubuntu 8.10, but whatever I try in grub I can't get xp to boot.

I thought 

title windows xp (Loader)
root (hd2,1)
savedefault
makeactive
chainloader +1

would work, but no.
I have tried- (hd2) (hd2,0) (hd2,1 and 2 and 3)

 cat /boot/grub/device.map
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd

sudo fdisk -lu
shows -

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41570539

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   299805029   149902483+  83  Linux
/dev/sda2       299805030   312576704     6385837+   5  Extended
/dev/sda5       299805093   312576704     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders, total 20005650 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f8000b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    19984859     9992398+   7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x52bf52bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   156280319    78140128+   7  HPFS/NTFS

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cc9e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   625142447   312571192+   b  W95 FAT32
```




sdc is the xp drive

sudo bash ~/Desktop/boot_info_script*.sh
gives me the following

```
> ============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41570539

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   299,805,029   299,804,967  83 Linux
/dev/sda2         299,805,030   312,576,704    12,771,675   5 Extended
/dev/sda5         299,805,093   312,576,704    12,771,612  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders, total 20005650 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f8000b1

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    19,984,859    19,984,797   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x52bf52bf

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cc9e9

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   625,142,447   625,142,385   b W95 FAT32

/dev/sdd1 ends after the last cylinder of /dev/sdd

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="66836617-a725-48d2-9a30-b7bd47189a37" TYPE="ext3" 
/dev/sda5: UUID="ec671497-3cc4-4d85-a12d-51496fc64467" TYPE="swap" 
/dev/sdc1: UUID="5B0DA49D78E0C68E" TYPE="ntfs" 
/dev/sdd1: LABEL="WD320" UUID="491E-97AD" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rodney/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rodney)
/dev/sdd1 on /media/WD320 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


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
# kopt=root=UUID=66836617-a725-48d2-9a30-b7bd47189a37 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=66836617-a725-48d2-9a30-b7bd47189a37

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		66836617-a725-48d2-9a30-b7bd47189a37
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=66836617-a725-48d2-9a30-b7bd47189a37 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		66836617-a725-48d2-9a30-b7bd47189a37
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=66836617-a725-48d2-9a30-b7bd47189a37 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		66836617-a725-48d2-9a30-b7bd47189a37
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=66836617-a725-48d2-9a30-b7bd47189a37 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		66836617-a725-48d2-9a30-b7bd47189a37
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=66836617-a725-48d2-9a30-b7bd47189a37 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		66836617-a725-48d2-9a30-b7bd47189a37
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=66836617-a725-48d2-9a30-b7bd47189a37 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		66836617-a725-48d2-9a30-b7bd47189a37
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=66836617-a725-48d2-9a30-b7bd47189a37 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		66836617-a725-48d2-9a30-b7bd47189a37
kernel		/boot/memtest86+.bin
quiet

title windows xp (Loader)
root (hd2,1)
savedefault
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

========================== sda1/boot/grub/grub.conf: ==========================

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
# kopt=root=UUID=66836617-a725-48d2-9a30-b7bd47189a37 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=66836617-a725-48d2-9a30-b7bd47189a37

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		66836617-a725-48d2-9a30-b7bd47189a37
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=66836617-a725-48d2-9a30-b7bd47189a37 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		66836617-a725-48d2-9a30-b7bd47189a37
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=66836617-a725-48d2-9a30-b7bd47189a37 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		66836617-a725-48d2-9a30-b7bd47189a37
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=66836617-a725-48d2-9a30-b7bd47189a37 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		66836617-a725-48d2-9a30-b7bd47189a37
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=66836617-a725-48d2-9a30-b7bd47189a37 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		66836617-a725-48d2-9a30-b7bd47189a37
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=66836617-a725-48d2-9a30-b7bd47189a37 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		66836617-a725-48d2-9a30-b7bd47189a37
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=66836617-a725-48d2-9a30-b7bd47189a37 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		66836617-a725-48d2-9a30-b7bd47189a37
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=66836617-a725-48d2-9a30-b7bd47189a37 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=ec671497-3cc4-4d85-a12d-51496fc64467 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

=================== sda1: Location of files loaded by Grub: ===================


 121.5GB: boot/grub/grub.conf
 121.3GB: boot/grub/menu.lst
 121.5GB: boot/grub/stage2
 122.1GB: boot/initrd.img-2.6.27-11-generic
 122.1GB: boot/initrd.img-2.6.27-7-generic
 122.1GB: boot/initrd.img-2.6.27-9-generic
 121.7GB: boot/vmlinuz-2.6.27-11-generic
 122.1GB: boot/vmlinuz-2.6.27-7-generic
 122.1GB: boot/vmlinuz-2.6.27-9-generic
 122.1GB: initrd.img
 122.1GB: initrd.img.old
 121.7GB: vmlinuz
 122.1GB: vmlinuz.old

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

```

 Can anyone help me please ?

Rodney

---

### Post by Rodney9 on 2009-03-05
I just tried - 

title Windows XP Home
rootnoverify (hd2,1)
map (hd1) (hd2)
map (hd2) (hd1)
chainloader +1

It does not work either.

Any clues ?

---

### Post by Rodney9 on 2009-03-05
Solved with the code below, usually one or the other works.

```
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```

Rodney

---

