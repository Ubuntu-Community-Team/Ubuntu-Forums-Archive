---
title: "can't use dual boot into Win 7 (Vista)"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by karembeu_ca on 2009-05-16
PC had Vista Ultimate on it, and I decided to upgrade to Windows 7 (yes, I know #-o)

anyway, Win7 kills my network adapter every 15 mins, and have always wanted to get a dual-boot with Ubuntu, so finaly did it.

GRUB shows Windows in the boot menu (as Vista though), but if I choose the Vista option it gives a "disk write error" and wont boot into Windows. I'd be happy to just format and start from scratch but I have 1 file I would like to get off the C: drive.

I have 2 external USB HDs that are showing up no problems in jaunty

> 
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc8afc89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30402   244197528+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21628b33

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60475   485765406    7  HPFS/NTFS
/dev/sdb2           60476       60801     2618595    5  Extended
/dev/sdb5           60476       60779     2441848+  83  Linux
/dev/sdb6           60780       60801      176683+  82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc226996c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001    7  HPFS/NTFS


also, when I first ran jaunty, it had NO free disk space - I had to uninstall open office to even get enough space to save my home page in Forefox!!! 

here is my fstab, for anyone that knows what that really means:

> 
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=eb977534-39ae-434f-9450-87ac3d93b670 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=012745d0-ecae-4ebb-9fd8-604badea9e7e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


I've been trying to figure out how to mount the NTFS partition to copy the file, but I havent been able to find or get ntfs-3g installed, or figure out any alternative.

I'm not a total nix-noob, but it has been a LONG time since I was running a linux box (back when I used to have to download and compile my own slackware kernel :))

any help is appreciated.

~ karembeu

p.s. more info

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=eb977534-39ae-434f-9450-87ac3d93b670 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=eb977534-39ae-434f-9450-87ac3d93b670

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
uuid        eb977534-39ae-434f-9450-87ac3d93b670
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=eb977534-39ae-434f-9450-87ac3d93b670 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        eb977534-39ae-434f-9450-87ac3d93b670
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=eb977534-39ae-434f-9450-87ac3d93b670 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        eb977534-39ae-434f-9450-87ac3d93b670
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
makeactive
chainloader    +1


---

### Post by karembeu_ca on 2009-05-16
have been able to find the files.

---

