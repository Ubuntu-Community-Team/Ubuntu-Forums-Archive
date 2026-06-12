---
title: "Dual boot window7 - Kubuntu 9.04 issue"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by TaseR2 on 2009-10-10
Hey guys, this is my first post but I'm not a total noob with Ubuntu (I think ;))

I've been using windows 7 for a while and decided to try out KUbuntu 9.04, so I installed KUbuntu from the disc, however I manually set up the partitions. Since doing this I can no longer access my windows partition (I don't get an option to boot into windows when I start up)

ANy help with this issue would be awesome.

Here is my menu.lst
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=0ece8f8a-f216-4d85-9671-7191c8bdeaf2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0ece8f8a-f216-4d85-9671-7191c8bdeaf2

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        0ece8f8a-f216-4d85-9671-7191c8bdeaf2
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=0ece8f8a-f216-4d85-9671-7191c8bdeaf2 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        0ece8f8a-f216-4d85-9671-7191c8bdeaf2
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=0ece8f8a-f216-4d85-9671-7191c8bdeaf2 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        0ece8f8a-f216-4d85-9671-7191c8bdeaf2
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0ece8f8a-f216-4d85-9671-7191c8bdeaf2 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        0ece8f8a-f216-4d85-9671-7191c8bdeaf2
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0ece8f8a-f216-4d85-9671-7191c8bdeaf2 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        0ece8f8a-f216-4d85-9671-7191c8bdeaf2
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```And here is my fdisk -l
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07c3275c                     

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488384504    7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0137d3ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       36482   292930560    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe7edef9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1           60046       60801     6072570   82  Linux swap / Solaris
/dev/sdc2           19123       60045   328710144    7  HPFS/NTFS
/dev/sdc3   *           1       12158    97659103+  83  Linux
/dev/sdc4           12159       19088    55665225    5  Extended
/dev/sdc5           12159       19088    55665193+  83  Linux

Partition table entries are not in disk order

```

---

### Post by Mark Phelps on 2009-10-10
You have no stanza in your menu.lst file for MS Windows.  To tell you what to code, we would have to know which of the three disks (they all have boot sectors) you're actively booting from.

---

### Post by TaseR2 on 2009-10-13
> **Mark Phelps said:**
> You have no stanza in your menu.lst file for MS Windows.  To tell you what to code, we would have to know which of the three disks (they all have boot sectors) you're actively booting from.

Cheers for the help anyway dude, I sorted it myself.

Just incase anyone is wondering, I have multiple hard disks, so I unplugged everyone apart from the one that I wanted to instal Ubuntu on. I then Manually installed Ubuntu, which cause an issue, most probably because the Windows boot area / sector / manager was on a different disk.

I added a generic boot option for windows in my menu.lst that pointed to the correct HDD Partition (in this case (HD0,1) I think.

After selecting this and trying to boot into windows it failed. So I whapped my windows 7 DVD in and used the startup repair option. (I had to do this twice for some reason)

It all works now.

I think what happened was that the repair tool moved the boot area / sector / manager onto the correct HDD for me.

TBH Setting up Ubuntu and using it is probably more trouble than its worth for me, I quite like the way windows feels and looks, plus I never really have any issues with it :D One other thing is that I like having more desktop space and Ubuntu / Kubuntu seems to hog all the screen space, even on high resolutions.

---

