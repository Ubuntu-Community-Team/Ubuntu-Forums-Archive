---
title: "Grub didn't find my sda1 at install! Can't boot! Please help!"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by Pipps on 2009-07-11
I have installed Ubuntu, with the Grub boot-loader, into my existing multi-boot system. The pre-existing operating systems are XP and Vista. Prior to installing Ubuntu, I had done some repartitioning in Gparted.

When Grub starts, I can see Ubuntu and Vista in the list, but no XP. XP was my main operating system for client work tasks. I really need to get back into it, if possible!

Currently, the menu.lst file in /boot/grub recognises my drives to the extent of the following:

[LIST]
[*]Ubuntu (hd0,2) (this drive is sda3 in Ubuntu)
[*]Vista (hd0,0) (this drive is sda2 in Ubuntu)
[/LIST]

XP is my drive sda1 in Ubuntu - but it does not appear in the Grub menu file. I don't understand why Vista is recognised as the (hd0,0). By my understanding, it should have been found and indexed by Grub as (hd0,1). 

Please help me find the (hdx,x) for XP, so that I can update the Grub menu file and boot into it from Grub! Thank you.

---

### Post by merlinus on 2009-07-11
Post results of

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by Pipps on 2009-07-11
Sir, thank you for your prompt assistance. Output of commands as follows:

```
*#sudo fdisk -l*

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedf4edf4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       56850   456647593+   7  HPFS/NTFS
/dev/sda2           57615       60801    25599577+   7  HPFS/NTFS
/dev/sda3           56851       57602     6040440   83  Linux
/dev/sda4           57603       57614       96390   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cd17c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 2004 MB, 2004877312 bytes
255 heads, 63 sectors/track, 243 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0032fcea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         243     1951866    b  W95 FAT32

```

```
*#cat /boot/grub/menu.lst*

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/ubuntu.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
##      altoptions=(single-user) single
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

title		Ubuntu, kernel 2.6.28-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda3 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
chainloader	+1

```

---

### Post by merlinus on 2009-07-11
Change this

title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1

to 

title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

and add this:

title        Windows XP
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

and restart.

Also make sure that sda is first in bios booting order.

---

### Post by Pipps on 2009-07-11
Thank you, Sir! I will do exactly this, and report back.

---

### Post by Pipps on 2009-07-11
One further question:

When I add the second section of code relating to XP, should I also copy and paste another instance of:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
```

Also, should I make any change to the 'sdax' in both instances, for Vista and XP, respectively?

---

### Post by Pipps on 2009-07-11
I have implemented the above prescribed advice, and can report my unexpected findings.

Firstly, I am delighted to say that I can boot back into XP, for my client work purposes. Thank you so much for enabling me to do this!

Secondly, however, booting into either XP or Vista appears to be rather stunted.

When I select the XP option from the Grub menu, I am taken to the Vista bootloader screen, where I am given the choice of booting in XP or Vista. Choosing either XP or Vista at this screen happens to boot either happily.

However, if I directly choose the Vista option from the Grub bootloader menu, I receive the following error message:

```
BOOTMGR is missing... Press CTRL + ALT + DEL to continue.
```

What do you think could perhaps be the problem, here?

Also, I am surprised that the inferior Vista bootloader is still in existence, and that Grub is still pointing to it, as my only route of enterting into Vista or XP.

How can I use Grub to replace the previous Vista bootloader altogether?

---

### Post by Pipps on 2009-07-11
I have made another small step forward.

I noticed [this thread]("http://ubuntuforums.org/showthread.php?t=319814") on a similar subject. The advice on moving the Vista 'boot' folder seemed useful.

I deleted the 'boot' folder on the Vista partition. I then cut and pasted the 'boot' folder from the XP partition, along with the 'bootmgr' file in the respective parent directory.

When I select Vista from Grub menu, now, it launches into the Vista bootloader, which thereby allows me to launch into Vista.

When I select XP from the Grub menu, I launch straight into XP, as desired.

Now, if I could only get rid of the useless Vista sub-bootloader menu, it would all be perfect!

Further advice would be much appreciated!

---

### Post by merlinus on 2009-07-11
Good work!  I am very glad to hear that you can access all three operating systems.

I do not know anything about vista's boot manager.

---

### Post by Pipps on 2009-07-11
I think I have got there!

I booted into Vista and downloaded [EasyBCD]("http://neosmart.net/dl.php?id=1").

I used this to change the Vista bootloader settings so that the timeout is zero.

This means that when Grub boots into the Vista bootloader, I don't actually see the Vista bootloader at all, or even know that it's there. Grub now satisfactorily appears to just boot straight into Vista. Much neater!

Thank you so much for your help!:)

---

### Post by merlinus on 2009-07-11
Excellent!  And you learned a great deal in the process as well, and hopefully can help others in future.

---

