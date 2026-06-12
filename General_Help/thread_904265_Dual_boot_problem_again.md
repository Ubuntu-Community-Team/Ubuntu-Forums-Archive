---
title: "Dual boot problem again"
date: 2008-08-29
forum: General Help
---

### Post by eggibm on 2008-08-29
Hi again, I posted few days ago about dual boot problem, fixed by reinstall of Vista and Ubuntu, and now I have a new problem.

First things first.
I have 4 HHD, 3x500GB and one 250GB.

When I reinstalled Vista and Ubuntu I unplugged 2 of the 500GB HDD and installed Vista on one 500GB, witch is I splitted in 2 partition, one 160GB and one is the rest, and then I installed Ubuntu on the 250GB HDD.

Now when I plugged the 2 other to 500GB HDD I decided to change where the Vista HDD is plugged on the motherboard and then I plugged the other HDD.

And now when I choose the Vista in GRUB I get "NTLDR is missing".

Here is /boot/grub/menu.lst:

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
# kopt=root=UUID=8613d3f9-995d-423b-876a-8f82b74f812a ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8613d3f9-995d-423b-876a-8f82b74f812a ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8613d3f9-995d-423b-876a-8f82b74f812a ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by amedac on 2008-08-29
you need to change map option in grub to proper hard disk

---

### Post by eggibm on 2008-08-29
Hi, thanks for the reply.
I'm a total newbie here in linux, how do I change map option in grub?

---

### Post by amedac on 2008-08-29
First i need to ask you: Did you properly set your hard drive boot priotity in bios? (hdd0,hdd1,hdd2...)
If this is ok, go to System -> Administration -> Synaptic Package manager 
and install QGrubEditor. It is simple and great program for grub editing.

After installation, you will open it from Applications -> System Tools -> QGrubEditor
First edit **root** line to proper disk and partition where vista is installed, and then edit **map**

---

### Post by caljohnsmith on 2008-08-29
Eggibm, an easy way to figure out which HDD Grub thinks Vista is on is by editing the Grub menu on start up. When you start up and get the Grub menu, select the Vista entry and hit "e" to edit it. It should show:
```
title		Windows Vista/Longhorn (loader)
root		[COLOR="Blue"](hd1,0)[/COLOR]
savedefault
makeactive
map		(hd0) [COLOR="Blue"](hd1)[/COLOR]
map		[COLOR="Blue"](hd1)[/COLOR] (hd0)
chainloader	+1
```
The blue-highlighted entries above are what you need to modify. Using the arrow keys, select the "root (hd1,0)", hit "e" to edit it, change it to "root (hd2,0)", and hit return to save that change. Do the same for those other map entries, changing the (hd1) to (hd2). When you are finished, hit "b" to boot it. If that doesn't work, try (hd3,0) and (hd3) for those entries. One of those should work. When you find what works, you can make the changes permanent by editing your menu.lst to include the changes. Let me know how it goes, and whether you need more details/info.

---

### Post by eggibm on 2008-08-29
> **amedac said:**
> First i need to ask you: Did you properly set your hard drive boot priotity in bios? (hdd0,hdd1,hdd2...)
If this is ok, go to System -> Administration -> Synaptic Package manager 
and install QGrubEditor. It is simple and great program for grub editing.

After installation, you will open it from Applications -> System Tools -> QGrubEditor
First edit **root** line to proper disk and partition where vista is installed, and then edit **map**

Hi
In the bios the hdd oreder is:
Vista is Master 0
Cd drive is Slave 0
Ubuntu is Master 1
Then the other to hdd come after that.

The boot order on the hdd is:
1. Ubuntu
2. Vista
3. & 4. Other hdd

---

### Post by eggibm on 2008-08-30
> **caljohnsmith said:**
> Eggibm, an easy way to figure out which HDD Grub thinks Vista is on is by editing the Grub menu on start up. When you start up and get the Grub menu, select the Vista entry and hit "e" to edit it. It should show:
```
title		Windows Vista/Longhorn (loader)
root		[COLOR="Blue"](hd1,0)[/COLOR]
savedefault
makeactive
map		(hd0) [COLOR="Blue"](hd1)[/COLOR]
map		[COLOR="Blue"](hd1)[/COLOR] (hd0)
chainloader	+1
```
The blue-highlighted entries above are what you need to modify. Using the arrow keys, select the "root (hd1,0)", hit "e" to edit it, change it to "root (hd2,0)", and hit return to save that change. Do the same for those other map entries, changing the (hd1) to (hd2). When you are finished, hit "b" to boot it. If that doesn't work, try (hd3,0) and (hd3) for those entries. One of those should work. When you find what works, you can make the changes permanent by editing your menu.lst to include the changes. Let me know how it goes, and whether you need more details/info.

Hi, again.
I fixed it I just did like you said, and begun to change 1 to 2 and it worked, everything is up now, both OS's

Thanx guy for the help. :)

---

