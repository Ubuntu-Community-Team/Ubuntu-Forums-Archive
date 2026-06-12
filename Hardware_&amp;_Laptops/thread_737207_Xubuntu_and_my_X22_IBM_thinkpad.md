---
title: "Xubuntu and my X22 IBM thinkpad"
date: 2008-03-27
forum: Hardware &amp; Laptops
---

### Post by ouwe_man on 2008-03-27
Good morning,

Imanaged to install Xubuntu on my little x22 with a P3 800 cpu and 640 ram, 20 gig HD from the most recent live disk ver 7.10

All is well but at startup I get the grub info and than the boot begins..... 3.5 minutes of blank screen before I get the login screen.

Did any one experience the same problem and what can I do to change this. It is alway nice and comforting to see something move....

thanks for any reply

John

PS any idea how to get my WiFi Linksys WPC54GS notebook adapter with speed booster card working?

---

### Post by kerry_s on 2008-03-27
you need to add a line for the screen size, it would be like vga=791(1024x768@16)
scroll down to "Linux video mode numbers"
[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions)

once you have your number, you need to add it to your menu.lst->
press alt+f2
gksu mousepad /boot/grub/menu.lst

look for this something like this line->
# kopt=root=/dev/hda1
and just add
# kopt=root=/dev/hda1 vga=?

then keep going down, look for
kernel		/boot/vmlinuz-2.6.18-6-686 root=/dev/hda1 
and add to then end of that
kernel		/boot/vmlinuz-2.6.18-6-686 root=/dev/hda1 vga=?

yours won't look exactly like mine, just similar, i use debian.

i also think i saw a thread around here, saying it's the splash that needs to be set. do a forum search.
or just remove the "quiet splash" in that menu.lst lines and dump splash altogether.

---

### Post by ouwe_man on 2008-03-27
Thanks for that fast answer. I'm going to do that now and let you know if it worked....

John

---

### Post by white_eagle-mk on 2008-03-27
> then keep going down, look for
kernel /boot/vmlinuz-2.6.18-6-686 root=/dev/hda1 
and add to then end of that
kernel /boot/vmlinuz-2.6.18-6-686 root=/dev/hda1 vga=?

I don't have anything even similar to what you are suggesting that I have....

Here's what I have in my conf file:

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
# kopt=root=UUID=18d85731-f617-41ec-ac71-6e34fb34112f ro vga=0x318

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=18d85731-f617-41ec-ac71-6e34fb34112f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=18d85731-f617-41ec-ac71-6e34fb34112f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

k### END DEBIAN AUTOMAGIC KERNELS LIST

```

***EDIT: I found it, nevermind

---

### Post by ouwe_man on 2008-03-28
Hi,

I have taken your advice under consideration but I'm not yet sure if that is the way to go. My screen is set at vga=792 and I'm now going to find out if thsi quiet splash thing is doing something special....

I do thank you and the others for your help and I hope to report on my findings in the days to come.

John

---

