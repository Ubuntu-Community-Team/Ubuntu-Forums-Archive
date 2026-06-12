---
title: "Multiboot UbuntuStudio and 2 Vista Installs"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by otheracco on 2009-04-21
Hi, I have a need for 2 Vista installs with all functionality alongside my UbuntuStudio Install.

UbuntuStudio and Vista #1 are working great, but I just 'dd' installed Vista onto another partition, and while I incremented the 'hd' number in 'menu.lst', my Grub loader seems to be pointing at just the 1 install no matter which option I choose.

Here's a breakdown of how Ubuntu is reading my partitions.
/dev/sda1   -Ubuntu
/dev/sda2   -Vista (the original that works)
/dev/sda3   -Vista (the copied one)

Here is my 'menu.lst'

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

title		Windows Vista 64 Copy
root		(hd0,2)
savedefault
makeactive
chainloader +1

title 		Windows Vista 64 Original
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

---

### Post by lemming465 on 2009-04-23
You are probably running into a couple of issues.  First, I don't think you can safely relocate NTFS partition using dd; they contain too many embedded pointers to specific disk addresses buried in the metadata structures.  You need one of the filesystem-aware tools like "ghost".  Second, the vista boot loader is reading a binary file that says what to load, just like the grub boot loader reads a text file to pick what to load.  If the vista loader is even reading the clone copy menu DB, rather than the original (which I doubt), the clone still **says** to load the original.  So what I think is happening is that your grub entries are working perfectly, but Vista doesn't realize you are trying to pick between two installs, and always loads the original one.

You should be able to use Vista's *bcdedit* tool in the original vista to add the secondary one as a boot option.

---

