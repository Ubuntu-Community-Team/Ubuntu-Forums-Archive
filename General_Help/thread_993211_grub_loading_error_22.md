---
title: "grub loading error 22"
date: 2008-11-25
forum: General Help
---

### Post by fakost on 2008-11-25
I participated one of my 160Gb hard drives in two partitions!then I put ubuntu 8.10 and I installed it!

now when the laptop is booting shows me: "GRUB Loading stage 1.5"
"GRUB loading, please wait ERROR 22"

please someone help me!I am new in ubuntu community!

thanks

---

### Post by caljohnsmith on 2008-11-25
Welcome to the forums. :) How about booting your Live CD (the CD you used to install Ubuntu), open a terminal (applications > accessories > terminal), and please post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by nazrysamaratin on 2008-11-25
same problem here

```
sudo fdisk -lu
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf024f024

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    42331274    21165606    7  HPFS/NTFS
/dev/sda2       103763835   171590264    33913215    f  W95 Ext'd (LBA)
/dev/sda3       207527670   208523699      498015   82  Linux swap / Solaris
/dev/sda4       208523700   312576704    52026502+  83  Linux
/dev/sda5       103763898   148135364    22185733+   7  HPFS/NTFS

Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```

GRUB 

So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```

ff06

And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.[/QUOTE]

newbie here 
replace "sda" above with each of your drives ??

---

### Post by caljohnsmith on 2008-11-25
Nazrysamaratin, according to that second "dd" command you ran, Grub is looking in sda7 for its boot files, and sda7 does not exist according to your fdisk output. That would explain your Grub error 22:
[QUOTE=Official Grub Manual]**Grub Error 22**: No such partition
This error is returned if a partition is requested in the device part of a device or full file name which isn't on the selected disk.
[/QUOTE]
So fixing your problem should hopefully be as simple as reinstalling Grub to the MBR (Master Boot Record) and have it point to sda4 (your linux partition) for its boot files. From your Live CD, how about posting the output of the following commands :
```
sudo grub
grub> root (hd0,3)
grub> setup (hd0)
grub> quit
```
Reboot, and let me know exactly what happens on start up. :)

---

### Post by nazrysamaratin on 2008-11-25
bad english not mother tongue
my menu.1st

splashimage=(hd0,3)/home/nazry/Documents/themes/HumanUbuntu.xpm.gz
default 0
timeout 10

title Ubuntu 8.04.1, kernel 2.6.24-21-generic
root (hd0,3)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=791cab7f-00ab-4a10-9bfa-6b77323195ae ro quiet splash
initrd /boot/initrd.img-2.6.24-21-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root (hd0,3)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=791cab7f-00ab-4a10-9bfa-6b77323195ae ro single
initrd /boot/initrd.img-2.6.24-21-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,3)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1
savedefault
makeactive
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
# kopt=root=UUID=791cab7f-00ab-4a10-9bfa-6b77323195ae ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

in my menu.1st.backup
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
# kopt=root=UUID=791cab7f-00ab-4a10-9bfa-6b77323195ae ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=791cab7f-00ab-4a10-9bfa-6b77323195ae ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=791cab7f-00ab-4a10-9bfa-6b77323195ae ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,3)
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
root		(hd0,0)
savedefault
makeactive
chainloader	+1

in my menu.1st no ## ## End Default Options ## & ### END DEBIAN AUTOMAGIC KERNELS LIST that is made my grub problem,

---

### Post by nazrysamaratin on 2008-11-25
So fixing your problem should hopefully be as simple as reinstalling Grub to the MBR (Master Boot Record) and have it point to sda4 (your linux partition) for its boot files. From your Live CD, how about posting the output of the following commands :
```
sudo grub
grub> root (hd0,3)
grub> setup (hd0)
grub> quit
```
Reboot, and let me know exactly what happens on start up. :)[/QUOTE]


caljohnsmith ty so much my problem SOLVE now ty again :):)

---

### Post by caljohnsmith on 2008-11-25
I'm glad it turned out to be such a simple problem, nazrysamaratin. Cheers and have fun with Ubuntu. :)

---

