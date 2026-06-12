---
title: "cannot boot ubuntu properly"
date: 2008-09-21
forum: General Help
---

### Post by betawarrior on 2008-09-21
so, i've been having quite a few computer problems lately.
all of my sata ports burned out, leaving me with two old ide drives.
because my os was on the sata drive, i had to go to my nearest public library to obtain a copy of hardy. after i installed it, i always get wierd  errors (grub read error, cannot load os, etc)
but when i use my ide to usb adapter, it boots perfectly

any help is appreciated, thanks in advance

---

### Post by Jonie on 2008-09-22
The order of drives that installer sees is not always the same as when the computer is started from HDD. I suspect that you put the second disk in the USB enclosure and it becomes hd0 then, the other one being hd1. Write, whether this is the case. 

Perhaps it will do just to change the boot sequence in BIOS, If not, post the output of sudo fdisk -l and the contents of your /boot/grub/menu.lst.

---

### Post by Uchiha_madara on 2008-09-22
> **betawarrior said:**
> so, i've been having quite a few computer problems lately.
all of my sata ports burned out, leaving me with two old ide drives.
because my os was on the sata drive, i had to go to my nearest public library to obtain a copy of hardy. after i installed it, i always get wierd  errors (grub read error, cannot load os, etc)
but when i use my ide to usb adapter, it boots perfectly

any help is appreciated, thanks in advance


My be the sata drive is the master drive so after it is Corrupted you the ubuntu is failed too , so you need to fix the error of the hard drive then install ubuntu again ...

 i hope that works.....

---

### Post by betawarrior on 2008-09-22
Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e934a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7165    57552831   83  Linux
/dev/sda2            7166        7476     2498107+   5  Extended
/dev/sda5            7166        7476     2498076   82  Linux swap / Solaris


and menu.lst
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
# kopt=root=UUID=eb24b892-0d1f-45fd-8a7c-eaddfe681511 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=eb24b892-0d1f-45fd-8a7c-eaddfe681511 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=eb24b892-0d1f-45fd-8a7c-eaddfe681511 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Jonie on 2008-09-25
In your report I see that the disk with Hardy is the one and only in your computer, so it should work without a glitch. But you wrote before, that you were left with two old ata drives - are the two connected when you boot from the internal controller? Are there any card readers, something that might get a higher priority at bootup? If this is not the case, then your hardware may be dead. However, you did get your Hardy installed, didn't you?

---

### Post by betawarrior on 2008-10-01
no, no, and no.
the hardy drive is the only one thats connected. top of the boot tree.
i get grub errors when connected via ide, but no errors when connected through usb.
i would upgrade the bios, but im afraid of bricking it...

---

