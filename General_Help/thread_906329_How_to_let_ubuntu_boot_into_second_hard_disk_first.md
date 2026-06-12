---
title: "How to let ubuntu boot into second hard disk first partition (using wubi)?"
date: 2008-08-31
forum: General Help
---

### Post by eatblueorange on 2008-08-31
I am dual booting XP and ubuntu, i am still using Ubuntu Gutsy Gibbon 7.10.  I used to install it my primary master hard disk with only 1 partition but my files are getting bigger in my primary disk, my XP is installed in my primary master hard disk which is Drive C, so I moved the wubi folder to the first partition of my secondary master hard disk which is Drive D but ubuntu wont boot, I always get an error "error 17: file not found" and "finding boot/grub/menu.lst"

I already defragmented drive c and drive d, but ubuntu won't boot.  If I move the wubi folder back to drive c, ubuntu will boot so my question is what specific commands to modify in the menu.lst to make my ubuntu boot on my second drive which is drive d.  Thank you for your help!

Here are the partitions of my drives:

Primary Master Hard Disk (Drive C:)
Primary Slave  DVD-RW (Drive L:)
Secondary Master Hard Disk partitions:
Drive D: --> my wubi folder is in this partition. (D:\wubi)
Drive E:
Drive F:

Secondary Slave Hard Disk partitions:
Drive G:
Drive H:
Drive I:
Drive J:
 
Here is my menu.lst when wubi was installed in drive c:

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'boot'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		1

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
# kopt=find=/wubi/boot/linux ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=find --set-root --ignore-floppies /wubi/boot/linux

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

## should update-grub add boot to the default options
## can be true or false
# boot=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-386
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.22-14-386 find=/wubi/boot/linux ro quiet splash
initrd		/wubi/boot/initrd.img-2.6.22-14-386

title		Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.22-14-386 find=/wubi/boot/linux ro single
initrd		/wubi/boot/initrd.img-2.6.22-14-386

title		Ubuntu 7.10, kernel 2.6.22-14-generic
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.22-14-generic find=/wubi/boot/linux ro quiet splash
initrd		/wubi/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.22-14-generic find=/wubi/boot/linux ro single
initrd		/wubi/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.20-16-generic find=/wubi/boot/linux ro quiet splash
initrd		/wubi/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.20-16-generic find=/wubi/boot/linux ro single
initrd		/wubi/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, kernel 2.6.20-15-generic
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.20-15-generic find=/wubi/boot/linux ro quiet splash
initrd		/wubi/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.20-15-generic find=/wubi/boot/linux ro single
initrd		/wubi/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 7.10, memtest86+
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title Ubuntu (Original Kernel)
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=ubuntu-7.04-alternate-i386.iso quiet splash ro
initrd /wubi/boot/initrd
boot

---

