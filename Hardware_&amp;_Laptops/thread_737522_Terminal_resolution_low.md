---
title: "Terminal resolution low"
date: 2008-03-27
forum: Hardware &amp; Laptops
---

### Post by white_eagle-mk on 2008-03-27
When I go into terminal with ctrl-alt-f1 the letters are too big and when I type something sometimes it barely even shows up, and I guess thats because the resolution is too low, and I need to make it bigger...
Anyone knows how to do that?

***EDIT: I'm the dumbest guy in the world because I put this post in Apple Intel Users and the question is about a Toshiba Laptop PC.... I hope it will be moved to another section, thank you!

---

### Post by kerry_s on 2008-03-27
see my thread here-> [http://ubuntuforums.org/showthread.php?t=737207](http://ubuntuforums.org/showthread.php?t=737207)
to set your resolution.

---

### Post by cyberdork33 on 2008-03-27
I hope you can get the vga or video lines working as they do not work on my Mac at all.

---

### Post by white_eagle-mk on 2008-03-28
> **kerry_s said:**
> see my thread here-> [http://ubuntuforums.org/showthread.php?t=737207](http://ubuntuforums.org/showthread.php?t=737207)
to set your resolution.
Hello, I saw your post there, I did what you told me ( example, vga=791 ) but nothing happened, everything is as it was before!

It looks like this now...

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
## e.g. kopt=root=/dev/hda1 ro vga=791
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=18d85731-f617-41ec-ac71-6e34fb34112f ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=18d85731-f617-41ec-ac71-6e34fb34112f ro quiet splash vga=791
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

---

### Post by Perfect Storm on 2008-03-28
Thread moved

---

### Post by white_eagle-mk on 2008-03-28
> **kerry_s said:**
> see my thread here-> [http://ubuntuforums.org/showthread.php?t=737207](http://ubuntuforums.org/showthread.php?t=737207)
to set your resolution.
So, as I said, I need to fix my terminal resolution and that post didn't help, as you can see in my menu.lst file I did everything as you told me, but I still get 5 mins boot time and a crappy terminal resolution when I do Ctrl-Alt-F1....

Any other pointers out there?

---

