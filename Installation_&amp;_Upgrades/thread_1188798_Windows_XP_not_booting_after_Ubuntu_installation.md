---
title: "Windows XP not booting after Ubuntu installation"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by sivamec on 2009-06-16
Hi Ubuntu Experts,

I am new to Linux, So please help me in fixing the below issue.

My PC is already a dual booting system(Windows XP and Fedora).
Yesterday, I have installed Ubuntu 9.04, After I coudln't able to boot Window-XP but i can boot Fedora and Ubuntu without any failure. Through Ubuntu, I can see NTFS datas. 

The only issue is windows XP is not booting. Please let me know how to fix the same at earliest.

FYI, I am attaching menu.lst and fdisk -ul logs.




# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default	 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout	 5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title	 Windows 95/98/NT/2000
# root	 (hd0,0)
# makeactive
# chainloader	+1
#
# title	 Linux
# root	 (hd0,1)
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2c7433f3-df58-482d-8218-b89d162df888 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2c7433f3-df58-482d-8218-b89d162df888

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
## indomU=true
## indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title	 Ubuntu
uuid	 2c7433f3-df58-482d-8218-b89d162df888
kernel	 /boot/vmlinuz-2.6.28-11-generic root=UUID=2c7433f3-df58-482d-8218-b89d162df888 ro quiet splash 
initrd	 /boot/initrd.img-2.6.28-11-generic
quiet

#title	 Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid	 2c7433f3-df58-482d-8218-b89d162df888
#kernel	 /boot/vmlinuz-2.6.28-11-generic root=UUID=2c7433f3-df58-482d-8218-b89d162df888 ro single
#initrd	 /boot/initrd.img-2.6.28-11-generic

#title	 Ubuntu 9.04, memtest86+
#uuid	 2c7433f3-df58-482d-8218-b89d162df888
#kernel	 /boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title	 Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title	 Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title	 Fedora (2.6.23.1-42.fc (on /dev/sda3)
root	 (hd0,2)
kernel	 /boot/vmlinuz-2.6.23.1-42.fc8 ro root=LABEL=/1 rhgb quiet 
initrd	 /boot/initrd-2.6.23.1-42.fc8.img
savedefault
boot
================================================== ==========================

root@shankar-desktop:/home/shankar# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34ba34b9

Device Boot Start End Blocks Id System
/dev/sda1 * 1 2785 22370481 7 HPFS/NTFS
/dev/sda2 2786 28893 209712510 f W95 Ext'd (LBA)
/dev/sda3 28894 29403 4096575 83 Linux
/dev/sda4 29404 29671 2152710 82 Linux swap / Solaris
/dev/sda5 2786 9312 52428096 7 HPFS/NTFS
/dev/sda6 9313 12619 26563446 7 HPFS/NTFS
/dev/sda7 15840 22366 52428096 7 HPFS/NTFS
/dev/sda8 22367 28893 52428096 7 HPFS/NTFS
/dev/sda9 15170 15194 200781 83 Linux
/dev/sda10 15462 15839 3036253+ 83 Linux
/dev/sda11 12620 12984 2931831 83 Linux
/dev/sda12 12985 13227 1951866 82 Linux swap / Solaris

Partition table entries are not in disk order
root@shankar-desktop:/home/shankar#

---

