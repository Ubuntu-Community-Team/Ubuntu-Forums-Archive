---
title: "Dual boot: Ubunto and Centos"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by mearturo on 2009-10-10
Dear all, 

I apologize for this basic question.

I had a Centos 5.3 x64 working but I needed a lighter Linux OS for some activities, so I installed Ubuntu 9.4, and now I can't boot Centos, but I can boot XP. 

It seems to be a problem in the Kernel line.

Any help will be extremely appreciated.

This is my Ubuntu menu.lst:

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
timeout        10

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
# kopt=root=UUID=73c45dff-e869-4cc8-a7cf-56822b50f057 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=73c45dff-e869-4cc8-a7cf-56822b50f057

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
uuid        73c45dff-e869-4cc8-a7cf-56822b50f057
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=73c45dff-e869-4cc8-a7cf-56822b50f057 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        73c45dff-e869-4cc8-a7cf-56822b50f057
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=73c45dff-e869-4cc8-a7cf-56822b50f057 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        73c45dff-e869-4cc8-a7cf-56822b50f057
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=73c45dff-e869-4cc8-a7cf-56822b50f057 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        73c45dff-e869-4cc8-a7cf-56822b50f057
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=73c45dff-e869-4cc8-a7cf-56822b50f057 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        73c45dff-e869-4cc8-a7cf-56822b50f057
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Professional
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title        CentOS release 5.3 (Final) (on /dev/sda3)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.18-128.4.1.el5xen root=/dev/sda3 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title        CentOS release 5.3 (Final) (on /dev/sda3)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.18-128.el5xen root=/dev/sda3 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title        CentOS release 5.3 (Final) (on /dev/sda3)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.18-164.el5xen root=/dev/sda3 
savedefault
boot

---

### Post by tomo75 on 2009-10-10
You are right that it is a problem in the kernel line, GRUB does not use the same naming conventions as linux for identifying Disks and Partitions. so where it says root=/dev/sda3 it needs to be changed to something like root=hd0,3 (hd0=1st hard disk, 3=2nd partition) or you could find the UUID of your centos partition with GParted from within ubuntu and use that as is the case with your ubuntu partitions

---

### Post by oldfred on 2009-10-10
If you are only doing one additional operating system you can do what you are doing, but I like chainbooting. With chainbooting you only need one simple stanza that never has to change, no manual updating with every kernel update.

You have to install Grub to the partition and the chainboot entry links to the grub in the partition as if it was booted. You then get a second menu that would be you standard Centos grub menu.

boot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

You can chainboot from an existing menu or create a chainboot only menu in its own partition:
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

---

### Post by mearturo on 2009-10-11
Thanks a lot gents, I'll try today and I'll post the result.

I really appreciate the help

---

