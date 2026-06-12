---
title: "point grub to exsisting xp hard drive"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by mulkwolf on 2009-01-26
OK... I've looked around a bit and need a little more direction... At work I've installed ubuntu 8.10 on an usb hard drive while the desktop xp hard drive was unplugged... result: grub only knows that the usb exsists. I currently change the boot order of harddrives at the start.... Problem is that it's tedious and the dell vostro 200 (desktop) is finicky in allowing me to get to the boot order.

A little help in pointing me in the right direction would be greaaaatly appreciated.

Thanks,
Greg

PS.... just spent 2 hours last night de-virusing and bringing up to speed an xp laptop....God I hate that.....Ubuntu ROCKS!

---

### Post by Pumalite on 2009-01-26
You have to edit your external HH menu.lst and add an entry for XP at the bottom.

---

### Post by mulkwolf on 2009-01-26
Thanks so much... I thought it probably was something link that... Is there a like to a few instructions....

Greg

---

### Post by caljohnsmith on 2009-01-26
How about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And then add at the bottom an entry like:
```
title       Windows XP (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Note (hd1,0) corresponds to the 1st partition on the other drive (the Windows drive), so if your Windows is on a different partition, you'll need to adjust that. If that doesn't work, then please post the output of:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

### Post by mulkwolf on 2009-01-26
> **mulkwolf said:**
> Thanks so much... I thought it probably was something link that... Is there a like to a few instructions....

Greg

I looked for joy and found only silence... I looked for silence and found joy.

---

### Post by mulkwolf on 2009-01-26
Thanks again... tried the above without really knowing what was here... Below is the fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       96389       48163+  de  Dell Utility
/dev/sda2   *       96390   488247479   244075545    7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81963515904 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160084992 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc10dbb97

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   153468944    76734441   83  Linux
/dev/sdb2       153468945   160071659     3301357+   5  Extended
/dev/sdb5       153469008   160071659     3301326   82  Linux swap / Solaris

---

### Post by caljohnsmith on 2009-01-26
OK, so your Windows partition is actually the 2nd partition, so how about trying both:
```
title       Windows XP (hd1)
rootnoverify     (hd1,1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows XP (hd0)
rootnoverify     (hd0,1)
chainloader +1
```
And let me know how that goes.

---

### Post by mulkwolf on 2009-01-26
Ok added the above.... Do I need to change the menu to provide opportunity to choose... below is the menu.... Thanks!!!!

# default num
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
# kopt=root=UUID=4b25857b-000a-41cd-9e4d-fdbd90c35fd7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4b25857b-000a-41cd-9e4d-fdbd90c35fd7

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
uuid		4b25857b-000a-41cd-9e4d-fdbd90c35fd7
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=4b25857b-000a-41cd-9e4d-fdbd90c35fd7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		4b25857b-000a-41cd-9e4d-fdbd90c35fd7
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=4b25857b-000a-41cd-9e4d-fdbd90c35fd7 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		4b25857b-000a-41cd-9e4d-fdbd90c35fd7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4b25857b-000a-41cd-9e4d-fdbd90c35fd7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		4b25857b-000a-41cd-9e4d-fdbd90c35fd7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4b25857b-000a-41cd-9e4d-fdbd90c35fd7 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		4b25857b-000a-41cd-9e4d-fdbd90c35fd7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title       Windows XP (hd1)
rootnoverify     (hd1,1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows XP (hd0)
rootnoverify     (hd0,1)
chainloader +1

---

### Post by caljohnsmith on 2009-01-26
Yes, if I were you, I would comment out the "hiddenmenu" line near the beginning so you will get the Grub menu on start up by default:
```
# hiddenmenu
```

---

### Post by mulkwolf on 2009-01-26
Ok... all set ... actuall the hd1 is the one that works... Thank you thank you....

The community is awesome!

Greg

---

