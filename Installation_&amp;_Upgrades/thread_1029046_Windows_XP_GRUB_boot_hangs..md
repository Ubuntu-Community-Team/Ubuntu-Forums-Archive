---
title: "Windows XP GRUB boot hangs."
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by Dvorakis on 2009-01-03
Hi,I just recently reinstalled both windows and linux(Getting rid of old windows vista and replacing it with XP,and freeing up space on my linux hard drive for when i get my new camera)
And Im having some trouble.

Im booting them on separate hard drives, the Linux being the bigger and the master(On the IDE cable) And the windows being the smaller hard drive, and the slave.

When I had my old linux install,everything booted just fine...but after a fresh install, booting windows XP from grub hangs on the line.
Starting up_

And won't switch screens.

It should also be known that when i remove the Ubuntu disk, and make the windows disk the master,everything works out perfectly.

Heres my grub menu.lst file.

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
# kopt=root=UUID=1b98b51d-93df-4aa1-a621-bad4f287710d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1b98b51d-93df-4aa1-a621-bad4f287710d

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		1b98b51d-93df-4aa1-a621-bad4f287710d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1b98b51d-93df-4aa1-a621-bad4f287710d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		1b98b51d-93df-4aa1-a621-bad4f287710d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1b98b51d-93df-4aa1-a621-bad4f287710d ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title Windows XP
root (hd1,0)
savedefault
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Please help!

---

### Post by confused57 on 2009-01-03
Your Windows entry probably needs map lines:
```
title Windows XP
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

---

