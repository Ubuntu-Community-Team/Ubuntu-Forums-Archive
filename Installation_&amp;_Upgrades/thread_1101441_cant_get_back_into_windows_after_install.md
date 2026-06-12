---
title: "cant get back into windows after install"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by th347 on 2009-03-20
Hi,

I was trying to install ubuntu on my laptop. It had an installation of Vista on 40GB partition. During the installation I installed Ubuntu to a 10GB partition and made a 2GB swap area. It all worked fine however now when i boot my computer it goes straight into ubuntu... I cant get back into windows

When it loads i can go into the grub menu by pressing esc at the right time. from there i only have 3 options:

-Ubuntu 8.10
-Ubuntu recovery mode
-memort test

nothing to get me into vista


What do i need to do to add windows vista to that list of options so that vista is on that list and i can choose whether to boot into vista or ubuntu at start up?

Thanks very much, I will need step by step instructions, this is all very new to me!

Regards

Tim
What

---

### Post by taurus on 2009-03-20
Let's see if your windows is still on your harddrive first.  Open a terminal and post the output of this command here.

```
sudo fdisk -l
```

---

### Post by th347 on 2009-03-20
It prints out this:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x186992ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530        7986    51857408    7  HPFS/NTFS
/dev/sda3            7986        8241     2046976+   f  W95 Ext'd (LBA)
/dev/sda4            8241        9730    11955200   83  Linux
/dev/sda5            7986        8241     2046976   82  Linux swap / Solaris


END PRINT OUT

thanks for the help

I think sda2 is the partition with the majority of my windows stuff and windows system files...

regards

 tim

---

### Post by taurus on 2009-03-20
Can you post your /boot/grub/menu.lst?

```
cat /boot/grub/menu.lst
```

---

### Post by th347 on 2009-03-20
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
# kopt=root=UUID=555c029f-a568-4660-a3b1-7aacad72309a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=555c029f-a568-4660-a3b1-7aacad72309a

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		555c029f-a568-4660-a3b1-7aacad72309a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=555c029f-a568-4660-a3b1-7aacad72309a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		555c029f-a568-4660-a3b1-7aacad72309a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=555c029f-a568-4660-a3b1-7aacad72309a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		555c029f-a568-4660-a3b1-7aacad72309a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by taurus on 2009-03-20
Edit /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
and add these lines to the end of it.

```

title Windows Vista
root (hd0,1)
makeactive
chainloader +1

```
Save it and reboot.  See if you can boot your windows now.

---

### Post by th347 on 2009-03-20
thanks that works! Only one other problem now with my wireless connection which i will post in appropriate section

Regards

Tim

---

