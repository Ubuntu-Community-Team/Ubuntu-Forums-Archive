---
title: "MBR issue.. Vista/Ubuntu 9.04"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by ripjames on 2009-04-26
on my other computer I have decided to dual boot Vista and linux.  Vista was installed first, than I installed Linux.  it would just boot into vista.  So I reinstalled Grub in the live session cd.  My Linux distro was installed to HD (1,2) HD (0) is my media drive, and is not set to boot.  The swap partition is i'm assuming HD (1,1) as it comes first in the partition manager before the ubuntu partition and Vista was the third one.  I have grub working and there is Vista option in it but it dosn't work, when i try to log into Vista from Grub, all it does is give me and Error 22 Ctrl ALT DEL.  That is a missing partiton error, I assume I can fix this by booting up with the vista cd and and having it repair, this will I'm guessing install over grub removing grub, is there a way I can fix grub, is it somthing as simple as changing the menu.list file in the grub folder?

---

### Post by ripjames on 2009-04-26
bump

---

### Post by Ravernomina on 2009-04-26
first off please get your Partition locations correctly :). Then after that try getting into the GRUb folder and please post you menu.lst, This will give all the users a better understand to how grub is set up :).


menu.lst Location:  Filesystem>boot>GRUB>Menu.lst :)

---

### Post by ripjames on 2009-04-27
linus is hd(1,2) here is a copy of the grub.lst how do i know which partition linux is on? will gparted tell me that?

```
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

# hiddenmenu
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
# kopt=root=UUID=efe00fcc-7d0b-45a1-8f70-2700061fe9f2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=efe00fcc-7d0b-45a1-8f70-2700061fe9f2

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		efe00fcc-7d0b-45a1-8f70-2700061fe9f2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=efe00fcc-7d0b-45a1-8f70-2700061fe9f2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		efe00fcc-7d0b-45a1-8f70-2700061fe9f2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=efe00fcc-7d0b-45a1-8f70-2700061fe9f2 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		efe00fcc-7d0b-45a1-8f70-2700061fe9f2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows Vista (loader)
rootnoverify	(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

I'm also attaching a screenshot of hd(1) in gparted

---

### Post by Ravernomina on 2009-04-27
hmm if u can do left click properties on all the partitons and take a screen shot of them and let me look at them.... so far your vista partition location looks correct. now do what i did above it looks like you vita partition has an error.

---

