---
title: "Jaunty, windows 7 raid0"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by Panda_N_Shark on 2009-05-22
Hy there, 

I install ubuntu with raid0 very times. Always work good. However now, in one of my pcs, i want dual boot it with windows 7 (before i have windows XP and 8.10 with raid)

I format the two drives, clean everything, then make partitions with ubuntu live cd. After that i installed windows 7. Next install ubuntu. Do all the steps need, (chroot etc, to install grub in raid0, generate the menu.lst, then update-grub) everything like i do always and is explained in fakeraid howto in wiki.

The issue is when i boot the computer i don't see the grub menu, and the computer boot in windows!!! So i don't know why, but the grub isn't be installed, but it say it is, when i run setup (hd0)


This is my partition table
raid -> name of the raid disk
raid1 -> /boot -> ext4
raid5 -> windows system -> ntfs
radi6 -> windows second drive -> ntfs
raid7 -> / -> ext4
raid8 -> /home -> ext4
raid9 -> swap

Anyone can help?

Thanks

---

### Post by Panda_N_Shark on 2009-05-22
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         30

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
#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
## default grub root device
## e.g. groot=(hd0,0)
 groot=(hd0,0)

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

title           Ubuntu 9.04, kernel 2.6.28-11-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.28-11-generic root=/dev/mapper/isw_ecchaeafef_raid7 ro quiet splash
initrd          /initrd.img-2.6.28-11-generic

title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.28-11-generic root=/dev/mapper/isw_ecchaeafef_raid7 ro  single
initrd          /initrd.img-2.6.28-11-generic

title           Ubuntu 9.04, memtest86+
root            (hd0,0)
kernel          /memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
#FOR WINDOWS CODEDMIND
 title         Windows 7
 root          (hd0,4)
 makeactive
 chainloader   +1



That is my menu.lst

---

### Post by Panda_N_Shark on 2009-05-22
up!!

---

