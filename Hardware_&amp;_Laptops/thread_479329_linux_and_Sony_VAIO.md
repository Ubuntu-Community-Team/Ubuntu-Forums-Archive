---
title: "linux and Sony VAIO"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by Twiggy003 on 2007-06-20
Ive looked around for solutions and what ive tried doesnt seem to work.  Basically on my Sony VAIO VGN-AR21S whenever i install any linux when it reboots GRUB will give me an error 21.  there were some threads i found on reinstalling GRUB through the Ubuntu liveCD and whatnot.  but after doing that it gave me a GRUB error 17 then i tried the SuperGRUB liveCD to repair GRUB, after that i got a GRUB error 2.  any ideas? 

cheers.

---

### Post by ukripper on 2007-06-20
Sounds like your grub is corrupted. 

Can you post output for eachof the  following  so that we can identify where things have gone wrong:
[LIST=1]
[*]fdisk -l
[*]/boot/grub/menu.lst
[*]/boot/grub/device.map
[*] /etc/fstab
[/LIST]

---

### Post by Twiggy003 on 2007-06-20
Ok, im just installing Ubuntu again.  How would it get corrupted if it does that straight after I install and reboot it with no other OS on there?

---

### Post by ukripper on 2007-06-20
Are you dual booting with windows XP on different HDDs?

---

### Post by Twiggy003 on 2007-06-20
Just Ubuntu on the first harddrive, nothing else.  I reinstalled it, it gave a GRUB error 2. so im booting into the liveCD, i shall post the output shortly.

---

### Post by Twiggy003 on 2007-06-20
sudo fdisk -l :

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10946    87923713+  83  Linux
/dev/sda2           10947       12161     9759487+  82  Linux swap / Solaris

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

/boot/grub/menu.lst :

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=cb390d8c-ba4d-4cff-82b8-bdfb7c0aa826 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cb390d8c-ba4d-4cff-82b8-bdfb7c0aa826 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cb390d8c-ba4d-4cff-82b8-bdfb7c0aa826 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

/boot/grub/device.map :

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc


and finally fstab :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cb390d8c-ba4d-4cff-82b8-bdfb7c0aa826 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=56a0f1cc-0c36-4b44-9bcc-2d549b54ad4a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

Thank you for your time.

---

### Post by IntuitiveNipple on 2007-06-20
> **Twiggy003 said:**
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10946    87923713+  83  Linux

That appears to be the problem - /dev/sda1 is incorrect if this is where Linux should be booting from:
[list]
[*]It should start at sector 63, not sector 1
[/list]
Grub installs some of its boot-loader in the 'spare' sectors on track 1. The convention is that the first partition should start at sector 63 (or more accurately, the 1st sector of track 2). 

On your system there is no space for the Grub stage-2 boot-loader.

Are you allowing Feisty to automatically create the partitions or are you doing it manually? You should intervene when it gets to the Partitioning Disk stage, go the manual route, and set this up correctly yourself.

---

### Post by Twiggy003 on 2007-06-20
When installed it i went to manual, then I made a ext3 partition then a swap, set the ext3 to / then simply let it install.  what do i need to do to it?

---

### Post by ukripper on 2007-06-20
Looking at your information provided above i see nothing wrong in those four output.

Can you post output of following commands 

1. ```
dmesg
```

2.```
ls -al  /dev/disk/by-uuid
```

---

### Post by IntuitiveNipple on 2007-06-20
> **Twiggy003 said:**
> When installed it i went to manual, then I made a ext3 partition then a swap, set the ext3 to / then simply let it install.  what do i need to do to it?
Make the first partition start at sector 63, not sector 1.

---

### Post by Twiggy003 on 2007-06-20
[ 1367.796000] end_request: I/O error, dev mmcblk0, sector 0
[ 1367.796000] mmcblk0: error 1 sending read/write command
[ 1367.796000] end_request: I/O error, dev mmcblk0, sector 0
[ 1367.796000] mmcblk0: error 1 sending read/write command
[ 1367.796000] end_request: I/O error, dev mmcblk0, sector 0
[ 1367.796000] mmcblk0: error 1 sending read/write command
[ 1367.796000] end_request: I/O error, dev mmcblk0, sector 0
[ 1367.796000] mmcblk0: error 1 sending read/write command
[ 1367.796000] end_request: I/O error, dev mmcblk0, sector 0
[ 1367.796000] mmcblk0: error 1 sending read/write command
[ 1367.796000] end_request: I/O error, dev mmcblk0, sector 0
[ 1367.796000] mmcblk0: error 1 sending read/write command
[ 1367.796000] end_request: I/O error, dev mmcblk0, sector 0
[ 1367.796000] mmcblk0: error 1 sending read/write command
[ 1367.796000] end_request: I/O error, dev mmcblk0, sector 0
[ 1368.840000] tifm_7xx1: sd card detected in socket 1
[ 1369.192000] mmcblk0: mmc0:2165 SD128 125440KiB 
[ 1369.192000]  mmcblk0:
[ 1370.228000] tifm_sd: card failed to respond for a long period of time<6>tifm_7xx1: demand removing card from socket 1
[ 1370.228000] mmcblk0: error 1 sending read/write command
[ 1370.228000] end_request: I/O error, dev mmcblk0, sector 250816
[ 1370.228000] mmcblk0: error 1 sending read/write command
[ 1370.228000] end_request: I/O error, dev mmcblk0, sector 250816
[ 1370.228000] mmcblk0: error 1 sending read/write command
[ 1370.228000] end_request: I/O error, dev mmcblk0, sector 250864
[ 1370.228000] mmcblk0: error 1 sending read/write command
[ 1370.228000] end_request: I/O error, dev mmcblk0, sector 250864
[ 1370.228000] mmcblk0: error 1 sending read/write command
[ 1370.228000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.228000] mmcblk0: error 1 sending read/write command
[ 1370.228000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.228000] mmcblk0: error 1 sending read/write command
[ 1370.228000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.228000] mmcblk0: error 1 sending read/write command
[ 1370.228000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.228000] mmcblk0: error 1 sending read/write command
[ 1370.228000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.228000] mmcblk0: error 1 sending read/write command
[ 1370.228000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.232000] mmcblk0: error 1 sending read/write command
[ 1370.232000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.256000] mmcblk0: error 1 sending read/write command
[ 1370.256000] end_request: I/O error, dev mmcblk0, sector 250752
[ 1370.256000] mmcblk0: error 1 sending read/write command
[ 1370.256000] end_request: I/O error, dev mmcblk0, sector 250752
[ 1370.256000] mmcblk0: error 1 sending read/write command
[ 1370.256000] end_request: I/O error, dev mmcblk0, sector 250872
[ 1370.256000] mmcblk0: error 1 sending read/write command
[ 1370.256000] end_request: I/O error, dev mmcblk0, sector 250872
[ 1370.260000] mmcblk0: error 1 sending read/write command
[ 1370.260000] end_request: I/O error, dev mmcblk0, sector 250872
[ 1370.260000] mmcblk0: error 1 sending read/write command
[ 1370.260000] end_request: I/O error, dev mmcblk0, sector 250872
[ 1370.260000] mmcblk0: error 1 sending read/write command
[ 1370.260000] end_request: I/O error, dev mmcblk0, sector 250872
[ 1370.260000] mmcblk0: error 1 sending read/write command
[ 1370.260000] end_request: I/O error, dev mmcblk0, sector 250872
[ 1370.260000] mmcblk0: error 1 sending read/write command
[ 1370.260000] end_request: I/O error, dev mmcblk0, sector 250816
[ 1370.260000] mmcblk0: error 1 sending read/write command
[ 1370.260000] end_request: I/O error, dev mmcblk0, sector 250864
[ 1370.260000] mmcblk0: error 1 sending read/write command
[ 1370.260000] end_request: I/O error, dev mmcblk0, sector 250872
[ 1370.264000] mmcblk0: error 1 sending read/write command
[ 1370.264000] end_request: I/O error, dev mmcblk0, sector 250872
[ 1370.264000] mmcblk0: error 1 sending read/write command
[ 1370.264000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.264000] mmcblk0: error 1 sending read/write command
[ 1370.264000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.264000] mmcblk0: error 1 sending read/write command
[ 1370.264000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.264000] mmcblk0: error 1 sending read/write command
[ 1370.264000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.264000] mmcblk0: error 1 sending read/write command
[ 1370.264000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.264000] mmcblk0: error 1 sending read/write command
[ 1370.264000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.264000] mmcblk0: error 1 sending read/write command
[ 1370.264000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.264000] mmcblk0: error 1 sending read/write command
[ 1370.264000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.268000] mmcblk0: error 1 sending read/write command
[ 1370.268000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.268000] mmcblk0: error 1 sending read/write command
[ 1370.268000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.268000] mmcblk0: error 1 sending read/write command
[ 1370.268000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.268000] mmcblk0: error 1 sending read/write command
[ 1370.268000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.268000] mmcblk0: error 1 sending read/write command
[ 1370.268000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.268000] mmcblk0: error 1 sending read/write command
[ 1370.268000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.268000] mmcblk0: error 1 sending read/write command
[ 1370.268000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.268000] mmcblk0: error 1 sending read/write command
[ 1370.268000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.268000] mmcblk0: error 1 sending read/write command
[ 1370.268000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.268000] mmcblk0: error 1 sending read/write command
[ 1370.268000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.268000] mmcblk0: error 1 sending read/write command
[ 1370.268000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.268000] mmcblk0: error 1 sending read/write command
[ 1370.268000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.268000] mmcblk0: error 1 sending read/write command
[ 1370.268000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.268000] mmcblk0: error 1 sending read/write command
[ 1370.268000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.268000] mmcblk0: error 1 sending read/write command
[ 1370.268000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.268000] mmcblk0: error 1 sending read/write command
[ 1370.268000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.268000] mmcblk0: error 1 sending read/write command
[ 1370.268000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.268000] mmcblk0: error 1 sending read/write command
[ 1370.268000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.268000] mmcblk0: error 1 sending read/write command
[ 1370.268000] end_request: I/O error, dev mmcblk0, sector 0
[ 1370.268000] mmcblk0: error 1 sending read/write command
[ 1370.268000] end_request: I/O error, dev mmcblk0, sector 0
[ 1371.276000] tifm_7xx1: sd card detected in socket 1
[ 1371.612000] mmcblk0: mmc0:2165 SD128 125440KiB 
[ 1371.612000]  mmcblk0:
[ 1372.644000] tifm_sd: card failed to respond for a long period of time<6>tifm_7xx1: demand removing card from socket 1
[ 1372.644000] mmcblk0: error 1 sending read/write command
[ 1372.644000] end_request: I/O error, dev mmcblk0, sector 250816
[ 1372.644000] mmcblk0: error 1 sending read/write command
[ 1372.644000] end_request: I/O error, dev mmcblk0, sector 250816
[ 1372.644000] mmcblk0: error 1 sending read/write command
[ 1372.644000] end_request: I/O error, dev mmcblk0, sector 250864
[ 1372.644000] mmcblk0: error 1 sending read/write command
[ 1372.644000] end_request: I/O error, dev mmcblk0, sector 250864
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.648000] mmcblk0: error 1 sending read/write command
[ 1372.648000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.672000] mmcblk0: error 1 sending read/write command
[ 1372.672000] end_request: I/O error, dev mmcblk0, sector 250752
[ 1372.672000] mmcblk0: error 1 sending read/write command
[ 1372.672000] end_request: I/O error, dev mmcblk0, sector 250752
[ 1372.672000] mmcblk0: error 1 sending read/write command
[ 1372.672000] end_request: I/O error, dev mmcblk0, sector 250872
[ 1372.672000] mmcblk0: error 1 sending read/write command
[ 1372.672000] end_request: I/O error, dev mmcblk0, sector 250872
[ 1372.676000] mmcblk0: error 1 sending read/write command
[ 1372.676000] end_request: I/O error, dev mmcblk0, sector 250872
[ 1372.676000] mmcblk0: error 1 sending read/write command
[ 1372.676000] end_request: I/O error, dev mmcblk0, sector 250872
[ 1372.676000] mmcblk0: error 1 sending read/write command
[ 1372.676000] end_request: I/O error, dev mmcblk0, sector 250872
[ 1372.676000] mmcblk0: error 1 sending read/write command
[ 1372.676000] end_request: I/O error, dev mmcblk0, sector 250872
[ 1372.676000] mmcblk0: error 1 sending read/write command
[ 1372.676000] end_request: I/O error, dev mmcblk0, sector 250816
[ 1372.676000] mmcblk0: error 1 sending read/write command
[ 1372.676000] end_request: I/O error, dev mmcblk0, sector 250864
[ 1372.676000] mmcblk0: error 1 sending read/write command
[ 1372.676000] end_request: I/O error, dev mmcblk0, sector 250872
[ 1372.676000] mmcblk0: error 1 sending read/write command
[ 1372.676000] end_request: I/O error, dev mmcblk0, sector 250872
[ 1372.680000] mmcblk0: error 1 sending read/write command
[ 1372.680000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.680000] mmcblk0: error 1 sending read/write command
[ 1372.680000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.680000] mmcblk0: error 1 sending read/write command
[ 1372.680000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.680000] mmcblk0: error 1 sending read/write command
[ 1372.680000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.680000] mmcblk0: error 1 sending read/write command
[ 1372.680000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.680000] mmcblk0: error 1 sending read/write command
[ 1372.680000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.680000] mmcblk0: error 1 sending read/write command
[ 1372.680000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.680000] mmcblk0: error 1 sending read/write command
[ 1372.680000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.684000] mmcblk0: error 1 sending read/write command
[ 1372.684000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.684000] mmcblk0: error 1 sending read/write command
[ 1372.684000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.684000] mmcblk0: error 1 sending read/write command
[ 1372.684000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.684000] mmcblk0: error 1 sending read/write command
[ 1372.684000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.684000] mmcblk0: error 1 sending read/write command
[ 1372.684000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.684000] mmcblk0: error 1 sending read/write command
[ 1372.684000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.684000] mmcblk0: error 1 sending read/write command
[ 1372.684000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.684000] mmcblk0: error 1 sending read/write command
[ 1372.684000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.684000] mmcblk0: error 1 sending read/write command
[ 1372.684000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.688000] mmcblk0: error 1 sending read/write command
[ 1372.688000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.688000] mmcblk0: error 1 sending read/write command
[ 1372.688000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.688000] mmcblk0: error 1 sending read/write command
[ 1372.688000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.688000] mmcblk0: error 1 sending read/write command
[ 1372.688000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.688000] mmcblk0: error 1 sending read/write command
[ 1372.688000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.688000] mmcblk0: error 1 sending read/write command
[ 1372.688000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.688000] mmcblk0: error 1 sending read/write command
[ 1372.688000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.688000] mmcblk0: error 1 sending read/write command
[ 1372.688000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.688000] mmcblk0: error 1 sending read/write command
[ 1372.688000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.692000] mmcblk0: error 1 sending read/write command
[ 1372.692000] end_request: I/O error, dev mmcblk0, sector 0
[ 1372.692000] mmcblk0: error 1 sending read/write command
[ 1372.692000] end_request: I/O error, dev mmcblk0, sector 0
[ 1373.692000] tifm_7xx1: sd card detected in socket 1
[ 1374.044000] mmcblk0: mmc0:2165 SD128 125440KiB 
[ 1374.044000]  mmcblk0:
[ 1375.116000] tifm_sd: card failed to respond for a long period of time<6>tifm_7xx1: demand removing card from socket 1
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 250816
[ 1375.116000] printk: 169 messages suppressed.
[ 1375.116000] Buffer I/O error on device mmcblk0, logical block 31352
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 250816
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 250864
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 250864
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1375.116000] mmcblk0: error 1 sending read/write command
[ 1375.116000] end_request: I/O error, dev mmcblk0, sector 0
[ 1376.164000] tifm_7xx1: sd card detected in socket 1
[ 1376.500000] mmcblk0: mmc0:2165 SD128 125440KiB 
[ 1376.500000]  mmcblk0:
[ 1377.572000] tifm_sd: card failed to respond for a long period of time<6>tifm_7xx1: demand removing card from socket 1
[ 1377.572000] mmcblk0: error 1 sending read/write command
[ 1377.572000] end_request: I/O error, dev mmcblk0, sector 250816
[ 1377.572000] mmcblk0: error 1 sending read/write command
[ 1377.572000] end_request: I/O error, dev mmcblk0, sector 250816
[ 1377.576000] mmcblk0: error 1 sending read/write command
[ 1377.576000] end_request: I/O error, dev mmcblk0, sector 250864
[ 1377.576000] mmcblk0: error 1 sending read/write command
[ 1377.576000] end_request: I/O error, dev mmcblk0, sector 250864
[ 1377.576000] mmcblk0: error 1 sending read/write command
[ 1377.576000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.576000] mmcblk0: error 1 sending read/write command
[ 1377.576000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.576000] mmcblk0: error 1 sending read/write command
[ 1377.576000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.576000] mmcblk0: error 1 sending read/write command
[ 1377.576000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.576000] mmcblk0: error 1 sending read/write command
[ 1377.576000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.576000] mmcblk0: error 1 sending read/write command
[ 1377.576000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.576000] mmcblk0: error 1 sending read/write command
[ 1377.576000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.580000] mmcblk0: error 1 sending read/write command
[ 1377.580000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.580000] mmcblk0: error 1 sending read/write command
[ 1377.580000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.580000] mmcblk0: error 1 sending read/write command
[ 1377.580000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.580000] mmcblk0: error 1 sending read/write command
[ 1377.580000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.580000] mmcblk0: error 1 sending read/write command
[ 1377.580000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.580000] mmcblk0: error 1 sending read/write command
[ 1377.580000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.580000] mmcblk0: error 1 sending read/write command
[ 1377.580000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.580000] mmcblk0: error 1 sending read/write command
[ 1377.580000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.580000] mmcblk0: error 1 sending read/write command
[ 1377.580000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.584000] mmcblk0: error 1 sending read/write command
[ 1377.584000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.584000] mmcblk0: error 1 sending read/write command
[ 1377.584000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.584000] mmcblk0: error 1 sending read/write command
[ 1377.584000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.584000] mmcblk0: error 1 sending read/write command
[ 1377.584000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.584000] mmcblk0: error 1 sending read/write command
[ 1377.584000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.584000] mmcblk0: error 1 sending read/write command
[ 1377.584000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.584000] mmcblk0: error 1 sending read/write command
[ 1377.584000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.584000] mmcblk0: error 1 sending read/write command
[ 1377.584000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.584000] mmcblk0: error 1 sending read/write command
[ 1377.584000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.584000] mmcblk0: error 1 sending read/write command
[ 1377.584000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.584000] mmcblk0: error 1 sending read/write command
[ 1377.584000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.584000] mmcblk0: error 1 sending read/write command
[ 1377.584000] end_request: I/O error, dev mmcblk0, sector 0
[ 1377.584000] mmcblk0: error 1 sending read/write command
[ 1377.584000] end_request: I/O error, dev mmcblk0, sector 0
[ 1378.620000] tifm_7xx1: sd card detected in socket 1
[ 1378.956000] mmcblk0: mmc0:2165 SD128 125440KiB 
[ 1378.956000]  mmcblk0:
[ 1394.848000] tifm_7xx1: demand removing card from socket 1
[ 3383.660000] usb 5-1: new high speed USB device using ehci_hcd and address 7
[ 3383.796000] usb 5-1: configuration #1 chosen from 1 choice
[ 3383.796000] scsi8 : SCSI emulation for USB Mass Storage devices
[ 3383.796000] usb-storage: device found at 7
[ 3383.796000] usb-storage: waiting for device to settle before scanning
[ 3388.796000] usb-storage: device scan complete
[ 3389.832000] scsi 8:0:0:0: Direct-Access              Audio Player          PQ: 0 ANSI: 0 CCS
[ 3389.832000] SCSI device sdc: 2036736 512-byte hdwr sectors (1043 MB)
[ 3389.836000] sdc: Write Protect is off
[ 3389.836000] sdc: Mode Sense: 03 00 00 00
[ 3389.836000] sdc: assuming drive cache: write through
[ 3389.836000] SCSI device sdc: 2036736 512-byte hdwr sectors (1043 MB)
[ 3389.836000] sdc: Write Protect is off
[ 3389.836000] sdc: Mode Sense: 03 00 00 00
[ 3389.836000] sdc: assuming drive cache: write through
[ 3389.836000]  sdc: sdc1
[ 3389.836000] sd 8:0:0:0: Attached scsi removable disk sdc
[ 3389.836000] sd 8:0:0:0: Attached scsi generic sg3 type 0
[ 3392.816000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[ 3392.880000] usb 3-1.2: new full speed USB device using uhci_hcd and address 12
[ 3393.080000] usb 3-1.2: configuration #1 chosen from 1 choice
[ 3393.160000] usb 3-1.3: new full speed USB device using uhci_hcd and address 13
[ 3393.240000] usb 3-1.3: device descriptor read/64, error -71
[ 3393.428000] usb 3-1.3: device descriptor read/64, error -71
[ 3393.608000] usb 3-1.3: new full speed USB device using uhci_hcd and address 14
[ 3393.696000] usb 3-1.3: device descriptor read/64, error -71
[ 3393.884000] usb 3-1.3: device descriptor read/64, error -71
[ 3394.064000] usb 3-1.3: new full speed USB device using uhci_hcd and address 15
[ 3394.480000] usb 3-1.3: device not accepting address 15, error -71
[ 3394.560000] usb 3-1.3: new full speed USB device using uhci_hcd and address 16
[ 3394.976000] usb 3-1.3: device not accepting address 16, error -71
[ 3419.000000] ieee80211_crypt: registered algorithm 'WEP'
[ 3419.244000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 3437.336000] eth1: no IPv6 routers present


and


total 0
drwxr-xr-x 2 root root 100 2007-06-20 13:59 .
drwxr-xr-x 6 root root 120 2007-06-20 13:59 ..
lrwxrwxrwx 1 root root  10 2007-06-20 13:59 460D-5972 -> ../../sdc1
lrwxrwxrwx 1 root root  10 2007-06-20 13:02 56a0f1cc-0c36-4b44-9bcc-2d549b54ad4a -> ../../sda2
lrwxrwxrwx 1 root root  10 2007-06-20 13:02 cb390d8c-ba4d-4cff-82b8-bdfb7c0aa826 -> ../../sda1

---

### Post by Twiggy003 on 2007-06-20
How do I make the first partition start at sector 63, not sector 1?

---

### Post by ukripper on 2007-06-20
Rather doing manually let ubuntu decide how to partition at during installation, it will do it for you.

---

### Post by Twiggy003 on 2007-06-20
Ok i did that, it gave a GRUB error and i looked on gparted it said it started at 63.  any ideas?

---

### Post by Twiggy003 on 2007-06-20
Shall i try the SuperGRUB CD and try to repair it? or try reinstalling GRUB from the ubunru live CD?

---

### Post by ukripper on 2007-06-20
reinstall grub from the ubuntu live cd, follow the link to related thread:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Twiggy003 on 2007-06-20
argh, i still get Error 2.  maybe i should try a different part of that guide, either way this is most annoying.  Thank you again for your help so far

---

### Post by Twiggy003 on 2007-06-20
By the way, when i did the first method while it was installing it said everything was fine. it found stage1, it went fine, im not sure where to go from here.

---

### Post by Twiggy003 on 2007-06-22
Is there any output i can give? reinstalling GRUB? any ideas at all?

---

### Post by ukripper on 2007-06-22
Can you post output of this -

```
gedit /boot/grub/menu.lst
```

---

### Post by Twiggy003 on 2007-06-22
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=f86d234a-5aa7-40a9-8fcc-84dc333aba7b ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f86d234a-5aa7-40a9-8fcc-84dc333aba7b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f86d234a-5aa7-40a9-8fcc-84dc333aba7b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Twiggy003 on 2007-06-24
Sorry to be a bother, but im really stuck on what to do i dont want to tinker or anything just incase i go back to square one, any ideas on what's wrong now that it starts on sector 63 and what to do from here? thank you

---

