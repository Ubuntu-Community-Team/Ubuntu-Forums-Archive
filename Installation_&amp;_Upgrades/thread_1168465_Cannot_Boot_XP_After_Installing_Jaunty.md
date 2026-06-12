---
title: "Cannot Boot XP After Installing Jaunty"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by groovybloke on 2009-05-24
Hi all I've been using Ubuntu since Hardy Heron always dual booting with XP Pro on a separate drive. I upgraded from Intrepid to Jaunty but that did not go too well and so installed again from scratch. I yesterday I tried to boot into XP and got Grub error code 13. I checked the grub menu list and changed it to the below - now I can get it to start booing XP but system justs hangs with 'starting up' and a flashing cursor on the screen. Have I trashed my XP MBR ? Any help greatly appreciated.

PS I am pretty sure that I did get int XP AFTER the Jaunty reinstall but cannot be 100%.

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=4014e1ee-61e7-44d3-a74b-20c1f6b6fd9f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4014e1ee-61e7-44d3-a74b-20c1f6b6fd9f

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

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		4014e1ee-61e7-44d3-a74b-20c1f6b6fd9f
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=4014e1ee-61e7-44d3-a74b-20c1f6b6fd9f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		4014e1ee-61e7-44d3-a74b-20c1f6b6fd9f
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=4014e1ee-61e7-44d3-a74b-20c1f6b6fd9f ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		4014e1ee-61e7-44d3-a74b-20c1f6b6fd9f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4014e1ee-61e7-44d3-a74b-20c1f6b6fd9f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		4014e1ee-61e7-44d3-a74b-20c1f6b6fd9f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4014e1ee-61e7-44d3-a74b-20c1f6b6fd9f ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		4014e1ee-61e7-44d3-a74b-20c1f6b6fd9f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root               (hd0,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

---

### Post by presence1960 on 2009-05-24
Suggestion: next time you paste text like that in here highlight all text and click # (hash sign) on the toolbar to place code tags around the text It will make it easier to read and fit better.

Why don't you open a terminal and run >  sudo fdisk -l and post the output here. BTW that is a lowercase L

---

### Post by groovybloke on 2009-05-24
Thanks for the advice presence1960 here's the output what do you reckon ?
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc151c151

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8c24e08a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9331    74951226   83  Linux
/dev/sdb2            9332        9733     3229065    5  Extended
/dev/sdb5            9332        9733     3229033+  82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47c1da15

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14593   117218241    7  HPFS/NTFS

```

---

### Post by presence1960 on 2009-05-24
```
title		Microsoft Windows XP Professional
rootnoverify    (hd0,0)
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

You need the map lines in there because Windows needs to think it is on the first boot device. Currently you have your Ubuntu disk as first boot. Give that a whirl and see what happens

---

### Post by groovybloke on 2009-05-24
No joy - XP still hangs at 'starting up'.

---

### Post by presence1960 on 2009-05-24
> **groovybloke said:**
> No joy - XP still hangs at 'starting up'.

well it looks like the problem is with XP. I would try this : [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Use the instructions for XP obviously.

---

### Post by groovybloke on 2009-05-24
I thank you ! After a bit of huffing and puffing got it sorted thanks to your advice.

---

### Post by presence1960 on 2009-05-24
> **groovybloke said:**
> I thank you ! After a bit of huffing and puffing got it sorted thanks to your advice.

Glad you got it working. Enjoy!

---

