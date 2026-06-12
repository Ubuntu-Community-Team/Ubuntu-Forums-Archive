---
title: "[SOLVED] 8.10 boot problems"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by sdb2028 on 2008-12-04
Installed Ubuntu 8.10 on neew HD from CD (after old HD went T-UP), wont boot without the CD in. Have to boot to Install menu- choose "boot from first HD" in menu list and boots fine to the installed kernel otherwise, it looks for CD to boot and gives error. What may be the fix for this issue?

---

### Post by pennacook on 2008-12-04
I would suggest looking at your partition table to make sure that the boot partition is marked as bootable and that grub is installed on the MBR.

---

### Post by sdb2028 on 2008-12-04
Partition is bootable and grub is installed. Near as I can figure there must be something wrong with the configuration. Everything worked fine when I installed 8.10 as upgrade on my other (now defunct) HD. This problem occured from installing from the CD.
Here are the screenshots of partitions and grub.

[ATTACH]95320[/ATTACH]

[ATTACH]95321[/ATTACH]

---

### Post by sdb2028 on 2008-12-04
Partition screenshot got clipped, here it is again,
[ATTACH]95322[/ATTACH]

---

### Post by sdb2028 on 2008-12-07
any ideas?
Wont boot to Ubuntu 8.10, kernel 2.6.27-9-generic without the live cd in the drive.
Found out the system boots fine to Ubuntu 8.10, kernel 2.6.27-7-generic (the older kernel in menu.lst) without the cd in the drive
uuid's seem to be identical...??
For now I'm setting the older kernel as default untill I find a fix.

---

### Post by sdb2028 on 2008-12-07
new development...
Wont boot automatically to anything except recovery in grub.

When selecting from the list at boot (using esc to get the menu) Ubuntu 8.10, kernel 2.6.27-9-generic still wont boot without the cd in the drive.

When selecting Ubuntu 8.10, kernel 2.6.27-7-generic it boots fine. 
This is a strange problem. Help please....

Here is my menu.lst file:

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
default        2

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
# kopt=root=UUID=29fda627-cddd-41df-aba8-843b087f9cfa ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=29fda627-cddd-41df-aba8-843b087f9cfa

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

title        Ubuntu 8.10, kernel 2.6.27-9-generic
uuid        29fda627-cddd-41df-aba8-843b087f9cfa
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=29fda627-cddd-41df-aba8-843b087f9cfa ro quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid        29fda627-cddd-41df-aba8-843b087f9cfa
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=29fda627-cddd-41df-aba8-843b087f9cfa ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        29fda627-cddd-41df-aba8-843b087f9cfa
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=29fda627-cddd-41df-aba8-843b087f9cfa ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        29fda627-cddd-41df-aba8-843b087f9cfa
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=29fda627-cddd-41df-aba8-843b087f9cfa ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        29fda627-cddd-41df-aba8-843b087f9cfa
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by henrik65 on 2008-12-07
Not sure, but sounds similair to my problem over in
[http://ubuntuforums.org/showthread.php?p=6325225](http://ubuntuforums.org/showthread.php?p=6325225)

---

### Post by sdb2028 on 2008-12-11
Fixed it.
Went to synaptic and marked the newest kernel for re-installation.
Everything is fine now.

---

