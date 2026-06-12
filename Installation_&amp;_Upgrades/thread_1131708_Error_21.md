---
title: "Error 21"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by MikRose on 2009-04-21
I had XP Home on first HD and Hardy on 2nd, dual boot with grub on #1 drive.  I had trouble with XP, so unhooked drive with XP on it and want to only use Linux hard drive now.  When I start up I still get the Grub screen listing my Linux kernels (2) and the XP Home listed in Other OS.  However, when I click on Linux, the screen reads Error 21 "Selected Disk Does Not Exist".  If I click on the XP Home entry, the screen says Error 13.  

I have used all the techniques for restoring/repairing/installing the Grub, but each time I reboot the original Grub screen yields the above results.  I've used Super Grub Disk, trying almost all possibilities, with no luck.  

If I use a Live CD (8.04), I see /boot/grub/stage1 is at (hd0,0).
  
If I use Sudo Fdisk -l, I get:
 /dev/sda1 = linux
 /dev/sda2 = Extended
 /dev/sda5 = linux Swap/Solaris

If I try to do an Install of Hardy, I can see that my original installation is using 84% of my 80g drive, with 18% left.  But I can't boot the drive.  I think there is a way to do an install and install the grub again at the first of this drive from the CD, but I'm afraid I'll lose the info on the drive from before I started this experiment.  Any suggestions?

---

### Post by Elfy on 2009-04-21
Can you reboot the livecd - then run these commands

```
sudo mkdir /mnt/test
sudo mount -t ext3 /dev/sda1 /mnt/test
```

Assuming that completed without error, please run these and post the results

```
ls -al /dev/disk/by-uuid/
sudo fdisk -l
cat /mnt/test/boot/grub/menu.lst

```

Please use [noparse]```
[/noparse] and [noparse]
```[/noparse] codes at the beginning and end of each part.

---

### Post by MikRose on 2009-04-21
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mkdir /mnt/test
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt/test
ubuntu@ubuntu:~$ ls -al /dev/disk/by-uuid/
total 0
drwxr-xr-x 2 root root  80 2009-04-21 12:33 .
drwxr-xr-x 5 root root 100 2009-04-21 12:33 ..
lrwxrwxrwx 1 root root  10 2009-04-21 12:33 2b1b7cb9-971b-4a88-b861-f878d3b7b362 -> ../../sda1
lrwxrwxrwx 1 root root  10 2009-04-21 12:33 6301e7cd-6354-469f-8c5c-20ef8f7d80cd -> ../../sda5
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x417c6ff7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9447    75882996   83  Linux
/dev/sda2            9448        9729     2265165    5  Extended
/dev/sda5            9448        9729     2265133+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ cat /mnt/test/boot/grub/menu.lst
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
timeout		15

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
# kopt=root=UUID=2b1b7cb9-971b-4a88-b861-f878d3b7b362 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# howmany=2

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2b1b7cb9-971b-4a88-b861-f878d3b7b362 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2b1b7cb9-971b-4a88-b861-f878d3b7b362 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2b1b7cb9-971b-4a88-b861-f878d3b7b362 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2b1b7cb9-971b-4a88-b861-f878d3b7b362 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$

---

### Post by Elfy on 2009-04-21
```
gksudo gedit /mnt/test/boot/grub/menu.lst
```

Find
# groot=(hd1,0)

it should be # groot=(hd[COLOR="Red"]0[/COLOR],0)

Then go to the boot lines, the root lines 
root (hd1,0)

should also be 
root (hd[COLOR="Red"]0[/COLOR],0)

Try that

---

### Post by MikRose on 2009-04-21
I'm still weeping tears of joy...thank you so much.  I wondered if it would boil down to a binary coin flip of "0's" and "1's"!  I'm still learning and have stored this information safely away, hopefully to help someone else in the future,or me!  Thanks again.

---

