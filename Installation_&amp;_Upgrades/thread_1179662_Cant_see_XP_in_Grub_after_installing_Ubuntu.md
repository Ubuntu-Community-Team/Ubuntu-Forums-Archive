---
title: "Cant see XP in Grub after installing Ubuntu"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by sapple on 2009-06-05
Hi all,
I just installed ubuntu 9.04 to my laptop. It had XP previously. Now when i start the computer, the Grub page comes but there is no XP listed there.

I know XP is still there because I can see it from ubuntu. I installed Ubuntu on a seperate partition that i created while installing ubuntu.


How can I get XP on GRUB menu. Here is the snapshot from gparted: 

[ATTACH]116566[/ATTACH]



sda5 has XP,  sda6 has ubuntu swap, sda2 has ubuntu, sda3 is HP recovery partition, and unallocated is free.

---

### Post by VMC on 2009-06-05
It looks like it's on sda5. print out menu.lst:

```
cat/boot/grub/menu.lst
```

---

### Post by merlinus on 2009-06-05
Did you have xp in a logical partition to begin with?

---

### Post by sapple on 2009-06-05
My fstab file is below.

The laptop originally had vista in it. I installed XP using the windows CD. I just formatted the disk and installed XP. 

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=dc7a0282-3170-4a7f-95bf-b122cfe823b8 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=26987202-2809-4741-a61b-5f6098741f05 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0

---

### Post by sapple on 2009-06-05
> **merlinus said:**
> Did you have xp in a logical partition to begin with?

I dont know.. but while partitioning the disk during ubuntu installation, there was a 1 gb partition saying XP.  I deleted it because i knew XP wasnt there.

---

### Post by sapple on 2009-06-05
> **VMC said:**
> It looks like it's on sda5. print out menu.lst:

```
cat/boot/grub/menu.lst
```

here is the file:

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
# kopt=root=UUID=dc7a0282-3170-4a7f-95bf-b122cfe823b8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dc7a0282-3170-4a7f-95bf-b122cfe823b8

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
uuid		dc7a0282-3170-4a7f-95bf-b122cfe823b8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dc7a0282-3170-4a7f-95bf-b122cfe823b8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		dc7a0282-3170-4a7f-95bf-b122cfe823b8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dc7a0282-3170-4a7f-95bf-b122cfe823b8 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		dc7a0282-3170-4a7f-95bf-b122cfe823b8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista (loader)
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1

---

### Post by merlinus on 2009-06-05
If indeed windows is on sda5, then change this line

rootnoverify	(hd0,2)

to 

rootnoverify	(hd0,4)

---

### Post by sapple on 2009-06-05
> **merlinus said:**
> If indeed windows is on sda5, then change this line

rootnoverify	(hd0,2)

to 

rootnoverify	(hd0,4)

no it didnt work. after the change i restrated and selected windows but grub gave an error  (invalid device) and went back to grub menu.

---

### Post by sapple on 2009-06-05
any ideas? i dont want to reinstall xp and ubuntu and all the drivers...

---

### Post by theProdiKalson on 2009-06-06
> **sapple said:**
> any ideas? i dont want to reinstall xp and ubuntu and all the drivers...
so i have the same problem too WinXP is installed on a logical partition... i think(really new at this) that an HDD can only have 4 primary partitions sda1 thru sda4.. after that... sda 5 and over are extended logical partitions... your winXP seems to be installed on that... 


you should start with editing the menu.lst file to trick that choosy lover windows into thinking it is booting from a primary partition... at least this is what i think i have been reading... its going on like 4 hours and been trying to get inside windows but she wont open her legs...

change the menu.lst to

map (hd0,0) (hd0,4)
map (hd0,4) (hd0,0)
rootnoverify (hd0,4)
chainloader    +1

i am new to buntu world so this might not work for u... hope it does thou
bless

---

### Post by sapple on 2009-06-06
> **theProdiKalson said:**
> 

change the menu.lst to

map (hd0,0) (hd0,4)
map (hd0,4) (hd0,0)
rootnoverify (hd0,4)
chainloader    +1

i am new to buntu world so this might not work for u... hope it does thou
bless

thanks but it didn't work.

---

### Post by merlinus on 2009-06-06
IMFFHO, often it is better to bite the bullet, so to speak, and start over.

Back up important data, and this time install windows in a primary partition that is first on the disk.  Then create an extended partition for all remaining space, and install ubuntu into logical partitions within that.

OTOH, you can continue to tear your hair out and gnash your teeth in hopes of learning something in the process.

---

### Post by sapple on 2009-06-07
I reinstalled XP and Ubuntu, deleted me recovery partition, and i am fine now..

---

### Post by merlinus on 2009-06-07
Excellent news!  Happy ubuntuing, and post back if you run into any more difficulties.

---

