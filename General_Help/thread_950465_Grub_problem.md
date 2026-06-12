---
title: "Grub problem"
date: 2008-10-17
forum: General Help
---

### Post by stereo_steve on 2008-10-17
Hi Guys,

I have a 2.5" USB hard drive that I use alot because I switch computers often and its handy having my settings always with me. I installed it from a laptop with no hard drive. I am using Hardy.

My friend saw this and wanted the same thing. He went out and bought a USB hard drive too. We formated it and installed Intrepid. ( I know its beta but its two weeks away and it seems fine).

The thing is he always gets a GRUB error 17 when he boots and has to manually change what disk he boots off. I've been editing his /boot/grub/menu.lst from my computer.

Is there a reason why mine will boot from all computers but his won't?

Thanks,
stephen

---

### Post by ajmorris on 2008-10-17
Hi there,
grub error 17 means that grub can not find the device that is specified in the grub config.
Can you please do the following from your friends computer:
post the output of ```
sudo fdisk -l
```
and the contents of his /boot/grub/menu.lst  file please.


AJ

---

### Post by stereo_steve on 2008-10-17
Thanks AJ for any help you can give.

Steve


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
timeout		2

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
# kopt=root=UUID=770cdfd8-2a62-4e5b-9e1f-7a9d9cab7513 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=770cdfd8-2a62-4e5b-9e1f-7a9d9cab7513 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-4-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=770cdfd8-2a62-4e5b-9e1f-7a9d9cab7513 ro  single
initrd		/boot/initrd.img-2.6.27-4-generic

title		Ubuntu intrepid (development branch), kernel Last successful boot
root		(hd0,0)
kernel		/boot/last-good-boot/vmlinuz root=UUID=770cdfd8-2a62-4e5b-9e1f-7a9d9cab7513 ro quiet splash  last-good-boot
quiet

title		Ubuntu intrepid (development branch), memtest86+
root		(hd0,0)
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
#root		(hd0,0)
#savedefault
#chainloader	+1
 


and sudo fdisk -l

/dev/sdc1               1       24080   193422568+   7  HPFS/NTFS
/dev/sdc2           24081       24323     1951897+  82  Linux swap / Solaris
/dev/sdc3           24324       29186    39062047+  83  Linux
/dev/sdc4   *       29187       30401     9759487+  83  Linux

---

### Post by caljohnsmith on 2008-10-17
So is the sdc drive the USB drive you are trying to boot from? And do you get the Grub error 17 before seeing a Grub menu, or after you get the Grub menu and select to boot Ubuntu? 

It is important to know which case is yours, but either way, the Intrepid entries in the menu.lst look like they are incorrect; they should use either (hd0,2) or (hd0,3). If you get the Grub menu on start up, an easy way to figure out which is the correct one is to reboot, when you get the Grub menu select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hd0,0)", press "e" to edit it, change it to "root (hd0,2)", press return to save the change, then press "b" to boot. If that doesn't work try (hd0,3), and one of those should work if you don't have any other issues. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent. Let me know how it goes or if you run into problems.

---

