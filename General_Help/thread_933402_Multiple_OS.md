---
title: "Multiple OS"
date: 2008-09-29
forum: General Help
---

### Post by aliboy on 2008-09-29
Good day!
I have a question, if your hard disk happen to have a multiple OS, Windows XP, Windows Vista, Fedora 8 and Ubuntu 8 respectively and the default of then is Ubuntu. How will you change the default OS to the other OS? :confused:


Thanks!:guitar:

---

### Post by bodhi.zazen on 2008-09-29
Depends on what boot loader you are using.

Assuming you are using Grub, you set the default in /boot/grub/menu.lst 

The relevant section looks like this :

> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
[default        0]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc")

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by aliboy on 2008-09-29
here it is.... is it possible to edit this code and just overwrite the original??



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
timeout		10

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
# kopt=root=UUID=ee8b08a7-1bf9-4bde-9ee7-ace63a829982 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ee8b08a7-1bf9-4bde-9ee7-ace63a829982 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ee8b08a7-1bf9-4bde-9ee7-ace63a829982 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Fedora (2.6.25-14.fc9.x86_64) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.25-14.fc9.x86_64 ro root=UUID=58a6e0aa-ca15-4253-aa55-f11ccccd7794 rhgb quiet 
initrd		/boot/initrd-2.6.25-14.fc9.x86_64.img
savedefault
boot

---

### Post by aliboy on 2008-09-29
when i try to save it, it says 


Could not save the file /boot/grub/menu.lst.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

---

### Post by Idefix82 on 2008-09-29
Open it with the command
```
gksudo gedit /boot/grub/menu.lst
```
and enter your Ubuntu password when prompted. Then you will be able to save it.

---

### Post by aliboy on 2008-09-29
ok done, ill try to restart pc now. thanks...

---

### Post by aliboy on 2008-09-29
after restarting, the menu for the different OS is still default on UBUNTU. after booting on ubuntu and check on the modified file, it was modified but nothings change. ^^
is there a command that i can do to change the default to windows? the menu for the diff OS should appear but the default is windows.

---

### Post by Idefix82 on 2008-09-29
So you changed it to 
```
default 4
```
and Ubuntu was still selected? Note that the option does not change the order in which the OSs are listed, it only changes, which OS is pre-selected.

---

### Post by aliboy on 2008-09-29
thanks! youve help me a lot!

---

