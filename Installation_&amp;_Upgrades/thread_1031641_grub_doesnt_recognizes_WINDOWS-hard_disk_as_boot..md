---
title: "grub doesnt recognizes WINDOWS-hard disk as boot."
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by amonsul on 2009-01-05
hi!

I have 3 hard disks
the first with a completely new ubuntuinstalaltion
the second with a windows xp
and the third data only

Grub can recognize only Ubuntu as bootsystem and i cant start windows
here my fstab:

> amonsul@amonsul:~$ sudo fdisk -l 
[sudo] password for amonsul: 

Platte /dev/sda: 320.0 GByte, 320072933376 Byte
255 Köpfe, 63 Sektoren/Spuren, 38913 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xd3f7cb70

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda2   *           1       38913   312568641    5  Erweiterte
/dev/sda5            1825        2067     1951866   82  Linux Swap / Solaris
/dev/sda6            2068       38913   295965463+  83  Linux
/dev/sda7               1        1824    14651185+  83  Linux

Partitionstabelleneinträge sind nicht in Platten-Reihenfolge

Platte /dev/sdb: 320.0 GByte, 320072933376 Byte
255 Köpfe, 63 Sektoren/Spuren, 38913 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x0004e545

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1               1       38912   312560608+   7  HPFS/NTFS

Platte /dev/sdc: 320.0 GByte, 320072933376 Byte
255 Köpfe, 63 Sektoren/Spuren, 38913 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x000d6a26

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdc1               1       38912   312560608+  83  Linux
amonsul@amonsul:~$ 


and here my menu.lst

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
# kopt=root=UUID=be7038b3-7263-4f6d-85b1-270bf92f8b4a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=be7038b3-7263-4f6d-85b1-270bf92f8b4a

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
uuid		be7038b3-7263-4f6d-85b1-270bf92f8b4a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=be7038b3-7263-4f6d-85b1-270bf92f8b4a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		be7038b3-7263-4f6d-85b1-270bf92f8b4a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=be7038b3-7263-4f6d-85b1-270bf92f8b4a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		be7038b3-7263-4f6d-85b1-270bf92f8b4a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


I tried to add manually a windows option in menu.lst but it doesnt work... :(
Whats wrong?

Thank you

---

### Post by logos34 on 2009-01-05
add a windows entry to the bottom of menu.lst [like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk") (i.e. mapping).

(if 'hd1,0' doesn't work, try 'hd2,0')

also, might want to change this

> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

to this:
> 
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"]#[/COLOR]hiddenmenu

---

