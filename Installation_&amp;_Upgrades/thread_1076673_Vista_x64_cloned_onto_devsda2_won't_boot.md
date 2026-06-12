---
title: "Vista x64 cloned onto /dev/sda2 won't boot"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by otheracco on 2009-02-21
I don't know if this will work.  My problem differs from other GRUB dual boot issues as does the way it was installed (by imaging windows partition directly, not installing from DVD).
I also need to throw in an unrelated question to SWAP space not being mounted after repartitioning it. 
I'll supply screenshots to more easily explain.

Here's my partition 
[IMG]http://www.FreeImageHut.com/view.php?file=11903-4k9l7pfg.jpg[/IMG]

The following steps are what I did.
1.) Installed Ubuntu on whole disc
2.) In Gparted, shrunk Ubuntu and deleted SWAP partition
3.) In Gparted, created NTFS partition at 'end' of drive
4.) Re-created extended and SWAP partition between Ubuntu and NTFS
5.) Used the following command to copy my Vista install from another working disc (/dev/hda) onto main disc (/dev/sda)  
      - 'dd if=\dev\hda1 of=\dev\sda2 bs=128M
      - I also created the destination partition about 3GB larger to make sure I had enough space and didn't run into a boundary.
6.) Edited 'menu.lst' to the following 

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
# kopt=root=UUID=51596bd6-fb8d-411d-a6cf-15120e7aec6f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=51596bd6-fb8d-411d-a6cf-15120e7aec6f

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		51596bd6-fb8d-411d-a6cf-15120e7aec6f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=51596bd6-fb8d-411d-a6cf-15120e7aec6f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title 		Windows Vista 64
root 		(hd0,1)
savedefault
makeactive
chainloader +1

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		51596bd6-fb8d-411d-a6cf-15120e7aec6f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=51596bd6-fb8d-411d-a6cf-15120e7aec6f ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		51596bd6-fb8d-411d-a6cf-15120e7aec6f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=51596bd6-fb8d-411d-a6cf-15120e7aec6f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		51596bd6-fb8d-411d-a6cf-15120e7aec6f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=51596bd6-fb8d-411d-a6cf-15120e7aec6f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		51596bd6-fb8d-411d-a6cf-15120e7aec6f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

When I restart the PC and press ESC to enter GRUB menu, I select 'Windows Vista' from the list, hit enter, and it hangs while displaying 'starting up' (or something very similar).

---

### Post by otheracco on 2009-02-22
This is solved.  I don't know why an exact replica with 'dd' didn't work, but I did get it working.

What I did was created a WIM image with winpe and imagex and then applied it to the partition.

Everything works now and I didn't even have to change my Windows entry in GRUB.

---

