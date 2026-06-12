---
title: "Grub problem after installing 9.04 on a new partition"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by oshmoz on 2009-04-25
Hello,

I installed Ubuntu 64bit on a new ext3 partition (I installed the bootloader on the same partition so I would have the menu.lst file to copy to my menu.lst). I copied the menu.lst options but I get an error message (error 2) when I try to load Ubuntu. My other grub options (Windows XP and Ubuntu 8.10) work fine.

My configuration:
sda1 - Windows XP
sda5 - Ubuntu 8.10
sda6 - Ubuntu 9.04 (Which I can't load)
sda7 - Swap
sda8 - /Boot - Contains stage2 and menu.lst

Here's my menu.lst (The relevant part):

```

title        Ubuntu 9.04, kernel 2.6.28-11-generic, Original
uuid        f32edf36-09c1-4754-9cae-43be4a289fac
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f32edf36-09c1-4754-9cae-43be4a289fac ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic, Chained
root        (hd0,5)
makeactive
chainloader    +1

title        Ubuntu 9.04, kernel 2.6.28-11-generic
savedefault
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda6 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic
savedefault
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=f188d396-78af-4552-a782-a49ba919490f ro quiet splash
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=f188d396-78af-4552-a782-a49ba919490f ro single
initrd        /boot/initrd.img-2.6.27-11-generic

# Windows XP
title        Windows XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1

```As you can see, I tried using the original code, using direct partition reference (/dev/sda6) and chain loading. Each option gives me a different error code (Error 2, 15 and 17).

And before you ask, boot_info_script:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #8 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #3 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda6 and 
                       looks at sector 282593027 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb247b247

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   143,364,059   143,363,997   7 HPFS/NTFS
/dev/sda3         204,828,750   312,576,704   107,747,955   f W95 Ext d (LBA)
/dev/sda5         204,828,813   245,794,499    40,965,687  83 Linux
/dev/sda6         245,794,563   286,760,249    40,965,687  83 Linux
/dev/sda7         286,760,313   290,969,279     4,208,967  82 Linux swap / Solaris
/dev/sda8         290,969,343   312,576,704    21,607,362  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf8997767

Partition  Boot         Start           End          Size  Id System

/dev/sdb1         377,495,370   488,392,064   110,896,695  83 Linux
/dev/sdb2                  63   377,495,369   377,495,307   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="AA3496A034966ED7" LABEL="XP" TYPE="ntfs" 
/dev/sda5: LABEL="ubuntu" UUID="f188d396-78af-4552-a782-a49ba919490f" TYPE="ext3" 
/dev/sda6: UUID="f32edf36-09c1-4754-9cae-43be4a289fac" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="7c17fd8c-db57-4bd4-9360-c63701c75003" 
/dev/sda8: LABEL="bootdisk" UUID="97defc4a-1a98-4906-811d-a2102d721525" TYPE="ext3" 
/dev/sdb1: LABEL="linstore" UUID="fa8e378f-5f3a-42aa-9d64-1bb4c35b0803" TYPE="ext3" 
/dev/sdb2: UUID="3F1A0E392E0E58FD" LABEL="Storage" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda8 on /bootdisk type ext3 (rw,relatime)
/dev/sdb1 on /linstore type ext3 (rw,relatime)
/dev/sdb2 on /storage type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/osh/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=osh)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT


=========================== sda5/boot/grub/menu.lst: ===========================

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
default        saved

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=f188d396-78af-4552-a782-a49ba919490f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title        Ubuntu 8.10, kernel 2.6.27-11-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=f188d396-78af-4552-a782-a49ba919490f ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=f188d396-78af-4552-a782-a49ba919490f ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=f188d396-78af-4552-a782-a49ba919490f ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=f188d396-78af-4552-a782-a49ba919490f ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, kernel 2.6.22-14-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=f188d396-78af-4552-a782-a49ba919490f ro quiet splash 
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 8.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=f188d396-78af-4552-a782-a49ba919490f ro  single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 8.10, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=f188d396-78af-4552-a782-a49ba919490f /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda1
#UUID=AA3496A034966ED7 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
#UUID=4EE638784EC18FE4 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
#UUID=aac3b01e-5ddc-4b68-a4d3-dc6225074ce9 none            swap    sw              0       0

/dev/sda8    /bootdisk    ext3    defaults,relatime            0    2
/dev/sdb1    /linstore    ext3    defaults,relatime            0    2
/dev/sdb2    /storage    ntfs    defaults,umask=007,gid=46    0    2
/dev/sda7    none        swap    sw                0    0

#/dev/sda6    /media/sda6     ext3    defaults            0    2
#/dev/sdb2    /storage    ntfs-3g    defaults,umask=007,gid=46    0    2

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec        0    0

=================== sda5: Location of files loaded by Grub: ===================


 124.4GB: boot/grub/menu.lst
 124.3GB: boot/grub/stage2
 124.4GB: boot/initrd.img-2.6.22-14-generic
 124.3GB: boot/initrd.img-2.6.22-14-generic.bak
 124.4GB: boot/initrd.img-2.6.27-11-generic
 124.4GB: boot/initrd.img-2.6.27-7-generic
 124.4GB: boot/vmlinuz-2.6.22-14-generic
 124.3GB: boot/vmlinuz-2.6.27-11-generic
 124.3GB: boot/vmlinuz-2.6.27-7-generic
 124.4GB: initrd.img
 124.4GB: initrd.img.old
 124.3GB: vmlinuz
 124.3GB: vmlinuz.old

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=f32edf36-09c1-4754-9cae-43be4a289fac ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f32edf36-09c1-4754-9cae-43be4a289fac

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
uuid        f32edf36-09c1-4754-9cae-43be4a289fac
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f32edf36-09c1-4754-9cae-43be4a289fac ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f32edf36-09c1-4754-9cae-43be4a289fac
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f32edf36-09c1-4754-9cae-43be4a289fac ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f32edf36-09c1-4754-9cae-43be4a289fac
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=f188d396-78af-4552-a782-a49ba919490f ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=f188d396-78af-4552-a782-a49ba919490f ro single 
initrd        /boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=f188d396-78af-4552-a782-a49ba919490f ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=f188d396-78af-4552-a782-a49ba919490f ro single 
initrd        /boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.10, kernel 2.6.22-14-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=f188d396-78af-4552-a782-a49ba919490f ro quiet splash 
initrd        /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=f188d396-78af-4552-a782-a49ba919490f ro single 
initrd        /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.10, memtest86+ (on /dev/sda5)
root        (hd0,4)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=f32edf36-09c1-4754-9cae-43be4a289fac /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=7c17fd8c-db57-4bd4-9360-c63701c75003 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 144.6GB: boot/grub/menu.lst
 144.6GB: boot/grub/stage2
 144.7GB: boot/initrd.img-2.6.28-11-generic
 144.7GB: boot/vmlinuz-2.6.28-11-generic
 144.7GB: initrd.img
 144.7GB: vmlinuz

=========================== sda8/boot/grub/menu.lst: ===========================

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
default        saved

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
# kopt=root=UUID=f188d396-78af-4552-a782-a49ba919490f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
# howmany=1

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

#title PC-BSD 7.0
#root (hd0,1)
#savedefault
#makeactive
#chainloader +1

#title        Debian - Lenny
#savedefault
#root        (hd0,5)
#kernel        /boot/vmlinuz-2.6.24-1-686 root=/dev/sda6 ro
#initrd        /boot/initrd.img-2.6.24-1-686

#title        Arch Linux X11
#savedefault
#root        (hd0,5)
#kernel        /boot/vmlinuz26 root=/dev/sda6 ro
#initrd        /boot/kernel26.img

#title        Arch Linux console
#root        (hd0,5)
#kernel        /boot/vmlinuz26 root=/dev/sda6 ro 3
#initrd        /boot/kernel26.img

#title        Arch Linux Fallback
#root        (hd0,5)
#kernel        /boot/vmlinuz26 root=/dev/sda6 ro
#initrd        /boot/kernel26-fallback.img
    
title        Ubuntu 9.04, kernel 2.6.28-11-generic, Original
uuid        f32edf36-09c1-4754-9cae-43be4a289fac
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f32edf36-09c1-4754-9cae-43be4a289fac ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic, Chained
root        (hd0,5)
makeactive
chainloader    +1

title        Ubuntu 9.04, kernel 2.6.28-11-generic
savedefault
root        (hd0,5)
#uuid        d6c35057-54be-47f5-9bd7-63a3a0e09df4
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda6 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic, Noisy
savedefault
root        (hd0,5)
#uuid        d6c35057-54be-47f5-9bd7-63a3a0e09df4
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda6 ro
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,5)
#uuid        d6c35057-54be-47f5-9bd7-63a3a0e09df4
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda6 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 8.10, kernel 2.6.27-11-generic
savedefault
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=f188d396-78af-4552-a782-a49ba919490f ro quiet splash
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic, Noisy
savedefault
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=f188d396-78af-4552-a782-a49ba919490f ro
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=f188d396-78af-4552-a782-a49ba919490f ro single
initrd        /boot/initrd.img-2.6.27-11-generic

#title        Ubuntu 8.10, memtest86+
#root        (hd0,4)
#kernel        /boot/memtest86+.bin


# Windows XP
title        Windows XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1

# Windows Vista
#title        Windows Vista
#root        (hd0,1)
#savedefault
#makeactive
#map        (hd0,1) (hd0,0)
#map        (hd0,0) (hd0,1)
#chainloader    +1


=================== sda8: Location of files loaded by Grub: ===================


 159.4GB: boot/grub/menu.lst
 159.5GB: boot/grub/stage2
=============================== StdErr Messages: ===============================

sed: can't read /linstore/etc/issue: No such file or directory

```
The menu.lst on /sda8 is the relevant one.

Any ideas would be great.
Thanks for your help,
Osh.

---

### Post by meierfra. on 2009-04-25
Try

title        Ubuntu 9.04, kernel 2.6.28-11-generic, Chained
root        (hd0,5)
chainloader    +1

(so remove "makeactive" from your "chained" entry)

---

### Post by oshmoz on 2009-04-25
meierfra, It works!

But now the question is why does it work from the chained grub and not from the original MBR grub. I copied the lines for the ubuntu 9.04 option into the MBR grub menu.lst and yet I can only start ubuntu from the chained version (I'm getting error 15: File not found). Any ideas?

Thanks again,
Osh.

---

### Post by meierfra. on 2009-04-25
> But now the question is why does it work from the chained grub and not from the original MBR grub.

I would guess it is caused by the "256bs/inode ext3" file system used by Ubuntu 9.04.

Type

```
sudo tune2fs -l /dev/sda6 |grep "Inode size"
sudo tune2fs -l /dev/sda8 |grep "Inode size"
```

I would guess that the first command returns 256 and the second 128.

Did you upgrade Ubuntu 8.10 from 8.04? The versions of  grub which comes with Ubuntu 8.10  should be able handle 256 inodes, but if you  upgraded from 8.04 you are still using the 8.04  stage2 file.

Try this. Boot into Ubuntu 8.10. Then

```
sudo grub-install /dev/sda
```

Reboot and see whether your other Ubuntu 9.04 entries now work.

---

### Post by oshmoz on 2009-04-25
meierfra, you are right again. It is indeed the problem and grub-install solved the problem. But after I did grub-install, grub is using the menu.lst from /dev/sda6 (The new ubuntu) and I want it to use menu.lst from /dev/sda8 (My boot disk).
So I:
sudo grub (From ubuntu 9.04)
root (hd0,7)
setup (hd0)

and I'm with the original problem again.
Any ideas how to make your solution work with a different boot disk?

Thanks again,
Osh.

---

### Post by meierfra. on 2009-04-25
> But after I did grub-install, grub is using the menu.lst from /dev/sda6

Did you run "grub-install" from Ubuntu 8.10? or from Ubuntu 9.04?

Try this: Boot into Ubuntu 9.04


```
sudo mount /dev/sda8 /mnt
cd /mnt/boot
sudo mv grub grub.backup
sudo cp -r /boot/grub grub 
sudo cp grub.backup/menu.lst grub/
sudo grub
root (hd0,7)
setup (hd0)
quit
```

---

### Post by oshmoz on 2009-04-25
Everything is working.

Thanks again,
Osh.

---

### Post by meierfra. on 2009-04-25
> Everything is working.

Great. Have fun  with all your OSs.

---

