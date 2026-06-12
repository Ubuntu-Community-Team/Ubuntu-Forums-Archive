---
title: "&quot;No root file system is defined&quot;"
date: 2008-10-14
forum: General Help
---

### Post by Sonic011 on 2008-10-14
Right after installing Ubuntu through Wubi and it boots up for the first time, after doing the first part of the system check I get this error.
"No root file system is defined
Please correct this from the partitioning menu"
and won't let me go anywhere from there. I've reinstalled about 6 times and still nothing. I'm running Windows Vista home premium SP1 on an AMD dual core processor.

---

### Post by ago on 2008-10-15
Known bug, already fixed, you can use wubi 511+ for that 

[http://wubi-installer.org/devel/minefield](http://wubi-installer.org/devel/minefield)

Note that there will be another issue after second reboot ([https://bugs.edge.launchpad.net/ubuntu/+source/grub-installer/+bug/283520/](https://bugs.edge.launchpad.net/ubuntu/+source/grub-installer/+bug/283520/)).
You have to add

root ()/ubuntu/disks

before the kernel lines in /ubuntu/disks/boot/grub/menu.lst
and also edit 
# groot=...

---

### Post by Sonic011 on 2008-10-15
> **ago said:**
> Known bug, already fixed, you can use wubi 511+ for that 

[http://wubi-installer.org/devel/minefield](http://wubi-installer.org/devel/minefield)

Note that there will be another issue after second reboot ([https://bugs.edge.launchpad.net/ubuntu/+source/grub-installer/+bug/283520/](https://bugs.edge.launchpad.net/ubuntu/+source/grub-installer/+bug/283520/)).
You have to add

root ()/ubuntu/disks

before the kernel lines in /ubuntu/disks/boot/grub/menu.lst
and also edit 
# groot=... How would I add the root ()/ubuntu/disks?

---

### Post by ago on 2008-10-15
Edit the file in notepad, also change 

# groot=()/ubuntu/disks

---

### Post by Sonic011 on 2008-10-15
> **ago said:**
> Edit the file in notepad, also change 

# groot=()/ubuntu/disks

Even after adding the stuff to the file I get Error 15 when trying to boot.

---

### Post by ago on 2008-10-16
You also have to add

root ()/ubuntu/disks

before each line that starts with "kernel"

---

### Post by dlowerre on 2008-11-07
If this is a known bug, why is it still on the 8.10 ISO that I just downloaded?

---

### Post by Sonic011 on 2008-11-14
I'm sorry, I cant figure this out at all. I dont where to add the stuff, if I could get like a video or something on how to do this
[http://www.filesavr.com/menu_1](http://www.filesavr.com/menu_1)
I uploaded my menu.lst if someone wants to like do it for me because I'm a complete idiot with this stuff and I dont want to mess anything up.

---

### Post by Marius Derekus on 2008-11-15
Sonic011 I'll try my best to help you if someone else hasn't already, but ago needs to clarify himself a little. Most people i see on these forums try to give an example of what they mean or something.(No offense ago, I understand you are helping a lot people)

---

### Post by Marius Derekus on 2008-11-15
It looks like he means(the bold words represent the added text):

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
# root ()/ubuntu/disks	(hd0,1)
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
# kopt=root=UUID=7AE8BB0CE8BAC5A3 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks should update-grub create alternative automagic boot options
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

title		Ubuntu intrepid (development branch), kernel 2.6.27-7-generic
uuid		7AE8BB0CE8BAC5A3
kernel		**root ()/ubuntu/disks**/boot/vmlinuz-2.6.27-7-generic root=UUID=7AE8BB0CE8BAC5A3 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu intrepid (development branch), kernel 2.6.27-7-generic (recovery mode)
uuid		7AE8BB0CE8BAC5A3
kernel		**root ()/ubuntu/disks**/boot/vmlinuz-2.6.27-7-generic root=UUID=7AE8BB0CE8BAC5A3 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu intrepid (development branch), memtest86+
uuid		7AE8BB0CE8BAC5A3
kernel		**root ()/ubuntu/disks**/boot/memtest86+.bin

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
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
chainloader	+1


Ask if you need more help, I'm trying to help the best i can.

You could maybe try copying (not cutting) menu.1st, placing it in another directory, and then edit the original one as i have shown above. Then if it doesn't work, put the old menu.1st back where it was and overwrite the edited one.

---

### Post by Marius Derekus on 2008-11-15
You could maybe try copying menu.1st, placing it in another directory, and then edit as i have shown on page 1. Then if it doesn't work,put the old menu.1st back where it was and overwrite the edited one.

---

### Post by Sonic011 on 2008-11-17
> **Marius Derekus said:**
> You could maybe try copying menu.1st, placing it in another directory, and then edit as i have shown on page 1. Then if it doesn't work,put the old menu.1st back where it was and overwrite the edited one.

Well it seemed to work but now I get Error 1, This is so frustrating :(

---

### Post by Marius Derekus on 2008-11-17
Try this, first you are going to want to backup the edited file the same way you backed up the original, (we are going to edit more of the already edited file). I think inside the parenthesis you need put something like **hd0,1** or **hd0,0**. First try **hd0,1**. if neither work, then tell me. (i've made the parenthesis i'm talking about **bold**.
```
 
title Ubuntu intrepid (development branch), kernel 2.6.27-7-generic
uuid 7AE8BB0CE8BAC5A3
kernel root **()**/ubuntu/disks/boot/vmlinuz-2.6.27-7-generic root=UUID=7AE8BB0CE8BAC5A3 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu intrepid (development branch), kernel 2.6.27-7-generic (recovery mode)
uuid 7AE8BB0CE8BAC5A3
kernel root **()**/ubuntu/disks/boot/vmlinuz-2.6.27-7-generic root=UUID=7AE8BB0CE8BAC5A3 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu intrepid (development branch), memtest86+
uuid 7AE8BB0CE8BAC5A3
kernel root **()**/ubuntu/disks/boot/memtest86+.bin
```

---

### Post by Marius Derekus on 2008-11-18
Next time you want to backup your file, don't do the tedious process i showed you earlier, do this instead. (Type this in terminal of course) ```
sudo cp */pathname/filename /pathname/filename_WhatEverYouWantHere*
``` then you will have a backup of the file

---

### Post by falconeray on 2008-11-20
Im having a similar problem, when trying to re-install the program.

---

### Post by Sonic011 on 2008-12-19
Forget it, I cant get this to work. I'm always having some sort of problem and recently (which is why I haven't been on) my vista got corrupt and I had to send my PC in so they could reinstall windows. All this is just frustrating and I pretty much give up. I thank you for all the help though.

---

