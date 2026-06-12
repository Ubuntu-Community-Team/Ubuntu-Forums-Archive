---
title: "Ubuntu doesn't auto mount drive E:"
date: 2008-07-22
forum: General Help
---

### Post by iampriteshdesai on 2008-07-22
I have a big problem in ubuntu. Ubuntu doesnt mount all my hard drives at booting. So if I fire up Rhythmbox during startup it doesn't play any songs. If I open that drive. E: in this case it plays those songs. Untill that point it says media/ path of that folder/ not found. What can I do?
Here are few outputs from the terminal. PLZ help me. Due to this problem I don't login to Ubuntu much.
cat /etc/fstab OUTPUT:
 Re: Mounting Problem
sudo fdisk -l
cat /etc/fstab
Output:
Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeccaecca

Device Boot Start End Blocks Id System
/dev/sda1 * 1 4487 36041796 7 HPFS/NTFS
/dev/sda2 4488 9732 42130462+ f W95 Ext'd (LBA)
/dev/sda5 4488 9732 42130431 7 HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5f4fd0a0

Device Boot Start End Blocks Id System
/dev/sdb1 1 4869 39110211 7 HPFS/NTFS
pritesh@pritesh-desktop:~$
pritesh@pritesh-desktop:~$
pritesh@pritesh-desktop:~$

pritesh@pritesh-desktop:~$ cat /etc/fstab

# /etc/fstab: static file system information.

#

# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0

/host/ubuntu/disks/root.disk / ext3 loop,errors=remount-ro 0 1

/host/ubuntu/disks/boot /boot none bind 0 0

/host/ubuntu/disks/swap.disk none swap loop,sw 0 0

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

pritesh@pritesh-desktop:~$

pritesh@pritesh-desktop:~$

pritesh@pritesh-desktop:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=0070FE7470FE7030 loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)/ubuntu/disks

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,0)/ubuntu/disks
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=0070FE7470FE7030 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,0)/ubuntu/disks
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=0070FE7470FE7030 loop=/ubuntu/disks/root.disk ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,0)/ubuntu/disks
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
chainloader +1

pritesh@pritesh-desktop:~$

---

