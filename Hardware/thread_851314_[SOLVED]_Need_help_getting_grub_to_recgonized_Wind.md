---
title: "[SOLVED] Need help getting grub to recgonized Windows os."
date: 2008-07-06
forum: Hardware
---

### Post by MantinoX on 2008-07-06
Hello, Just descided to do a dual boot of windows on a seperate hard drive and I was wondering what are the ways for the grub menu to recgonize it in the start up. I have one drive that is ubuntu and the other windows xp pro. Both are sata drives and i just need some pointers on how to edit the grub menu.

thanks

---

### Post by Nikitas350 on 2008-07-06
run "gedit /boot/grub/menu.lst" in terminal and post here the output

---

### Post by MantinoX on 2008-07-06
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
# kopt=root=UUID=ed518ca0-93f2-4fe9-ae26-45e15fec8508 ro

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ed518ca0-93f2-4fe9-ae26-45e15fec8508 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ed518ca0-93f2-4fe9-ae26-45e15fec8508 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=ed518ca0-93f2-4fe9-ae26-45e15fec8508 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=ed518ca0-93f2-4fe9-ae26-45e15fec8508 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ed518ca0-93f2-4fe9-ae26-45e15fec8508 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ed518ca0-93f2-4fe9-ae26-45e15fec8508 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

It looks like its only reading the first disk.

---

### Post by Nikitas350 on 2008-07-06
run "sudo gedit /boot/grub/menu.lst" and add these lines at the end of the file:

title        Microsoft Windows XP Professional
root        (hd1,0)
savedefault
makeactive
chainloader    +1

---

### Post by MantinoX on 2008-07-06
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ed518ca0-93f2-4fe9-ae26-45e15fec8508 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ed518ca0-93f2-4fe9-ae26-45e15fec8508 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=ed518ca0-93f2-4fe9-ae26-45e15fec8508 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=ed518ca0-93f2-4fe9-ae26-45e15fec8508 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ed518ca0-93f2-4fe9-ae26-45e15fec8508 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ed518ca0-93f2-4fe9-ae26-45e15fec8508 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
chainloader	+1
```

Shows up in Grub but one i hit it will not load.
am im doing this right? Could there be another hard drive number?

---

### Post by MantinoX on 2008-07-06
Is there a way to find out which hard drive is what?

---

### Post by MantinoX on 2008-07-06
K well when i look at the command to find the map of the hd this is what i get
see picture.

However when i type it in as ) and reboot i get an invald ...

Any reason why?

---

### Post by MantinoX on 2008-07-06
```
chuck@chuck-desktop:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb76a0d4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb76a0d4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       37777   303443721   83  Linux
/dev/sdb2           37778       38913     9124920    5  Extended
/dev/sdb5           37778       38913     9124888+  82  Linux swap / Solaris
chuck@chuck-desktop:~$ 

```

---

### Post by Nikitas350 on 2008-07-06
What error do you get when you try to boot to xp? Also try changing hd1,0 to sd0,0 or sd1,0

---

### Post by MantinoX on 2008-07-06
error 13, when i switch it back to hd1 it will go to the starting up but nothing will happend .

---

### Post by Nikitas350 on 2008-07-06
"when i switch it back to hd1 it will go to the starting up but nothing will happend" what do you mean? The logo of windows is appeared? If so, it's a problem of windows...

---

### Post by MantinoX on 2008-07-06
Fixed it. 
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ed518ca0-93f2-4fe9-ae26-45e15fec8508 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ed518ca0-93f2-4fe9-ae26-45e15fec8508 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=ed518ca0-93f2-4fe9-ae26-45e15fec8508 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=ed518ca0-93f2-4fe9-ae26-45e15fec8508 ro single
initrd		/boot/initrd.img-2.6.24-18-generic


title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
[COLOR="Lime"]map             (hd0) (hd1)
map             (hd1) (hd0)[/COLOR]
chainloader	+1
```

the code is green had to be added to fix it so it would boot windows or ubuntu.

I looked around and tried many things and this one worked. However i have no idea what map means.


Thank you for you help.

---

### Post by Nikitas350 on 2008-07-07
"If you have installed DOS (or Windows) on a non-first hard disk, you have to use the disk swapping technique, because that OS cannot boot from any disks but the first one. The workaround used in GRUB is the command, like this:

grub> map (hd0) (hd1)
grub> map (hd1) (hd0)

This performs a virtual swap between your first and second hard drive." ;)

---

