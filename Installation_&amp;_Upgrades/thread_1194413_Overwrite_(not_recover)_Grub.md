---
title: "Overwrite (not recover) Grub"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by bennis on 2009-06-22
Okay, so what has happened is this. I was using my ubuntu peacefully and just installed what i assume was a kernel update. There was a little thing that popped up to see if i wanted to overwrite some database, i wasn't really paying attention. I said, no, i didn't. Next a window requesting that i reboot pops up, and i say okay. And click the reboot button. I boot into my grub, allow it to time out on my ubuntu partition, and get a grub error. It's not a valid executable or something. 

Here is what i want to know: How do i overwrite the grub from a live disk? I've found how to **restore it** but that's not what i want. Thanks for any help.

---

### Post by dstew on 2009-06-22
What probably happened, when you updated the kernel, is that the old kernel was removed, but you did not allow the update-grub program to create a new menu.lst file with the new kernel. If you re-install grub from a Live CD, you will still have the defective menu.lst file there, and it won't help.

I think you need to fix your menu.lst file. Boot a Live CD, and mount the Ubuntu hard disk partition. Post to the forum the contents of the /boot directory, and the /boot/grub/menu.lst file:```
cd /boot
ls -l
cat /boot/grub/menu.lst
``` We should then have the information we need to edit the menu.lst file to make it work again.

You could also try running the update-grub program from the Live CD. You have to make the hard-disk /boot directory your current working directory first:```
cd /media/disk/boot (or whatever the mount point of the Ubuntu hard disk is)
sudo update-grub
```

---

### Post by bennis on 2009-06-22
So my menu.lst:
> 
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
default		saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
#password --md5 $1$QZIG2/$bguVXejASn6tYYDpuOC6s/
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
# kopt=root=UUID=9244830f-36b1-4b3c-a6a1-a62c9c58edcc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9244830f-36b1-4b3c-a6a1-a62c9c58edcc

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=true

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash vga=786

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		9244830f-36b1-4b3c-a6a1-a62c9c58edcc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9244830f-36b1-4b3c-a6a1-a62c9c58edcc ro
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

titletitle		Windows (Gaming)
rootnoverify		(hd0,0)
makeactive
chainloader	+1

		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		9244830f-36b1-4b3c-a6a1-a62c9c58edcc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9244830f-36b1-4b3c-a6a1-a62c9c58edcc ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		9244830f-36b1-4b3c-a6a1-a62c9c58edcc
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title		Microsoft Windows XP Professional
#rootnoverify	(hd0,0)
#savedefault
#chainloader	+1


And the second thing you posted didn't work. I'm not sure why, but it made no changes to my /media/disk/boot/grub/menu.lst even though i cd'd to /media/disk. I even tried appending /media/disk/boot/grub/menu.lst to the command.

I'm also about to remove the second title from the Windows entry.

---

### Post by dstew on 2009-06-23
> I'm also about to remove the second title from the Windows entry.Yes, you need to do that, and *add* "title" to the first line of the Ubuntu Recovery Mode entry. That should fix it.

---

