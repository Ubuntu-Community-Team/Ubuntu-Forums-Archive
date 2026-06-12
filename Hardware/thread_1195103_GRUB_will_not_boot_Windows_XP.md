---
title: "GRUB will not boot Windows XP"
date: 2009-06-23
forum: Hardware
---

### Post by mcdjork on 2009-06-23
I know there have been a thousand posts like this, but none of them have fixed my problem. 

I have a Dell Latitude D630. I prefer to use Ubuntu for personal use, but need Windows XP Pro for work. Ubuntu is installed on a separate hard disk that I insert into the modular bay when needed
(sda1 below). My BIOS is setup to boot the modular disk first, then the internal drive where Windows is installed (sdb1).

I want to add Windows to GRUB so that even when the modular disk is in, I can choose to boot Windows without having to do F12 in BIOS. Everything I've tried, however, returns the Error 13. Note that Windows does boot just fine when I boot the internal drive directly from BIOS.

Any suggestions?

My menu.lst:

[I]# menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout        30

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
# kopt=root=UUID=b13d0daf-7bfd-4e61-aee0-2943e137d8d8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b13d0daf-7bfd-4e61-aee0-2943e137d8d8

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        b13d0daf-7bfd-4e61-aee0-2943e137d8d8
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=b13d0daf-7bfd-4e61-aee0-2943e137d8d8 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        b13d0daf-7bfd-4e61-aee0-2943e137d8d8
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=b13d0daf-7bfd-4e61-aee0-2943e137d8d8 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        b13d0daf-7bfd-4e61-aee0-2943e137d8d8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b13d0daf-7bfd-4e61-aee0-2943e137d8d8 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        b13d0daf-7bfd-4e61-aee0-2943e137d8d8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b13d0daf-7bfd-4e61-aee0-2943e137d8d8 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        b13d0daf-7bfd-4e61-aee0-2943e137d8d8
kernel        /boot/memtest86+.bin
quietq    

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Windows XP Professional
root            (hd1,0)
savedefault
makeactive
chainloader     +1
map (hd0) (hd1)
map (hd1) (hd0)
[/I]



My fdisk:

[I]Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x521fe134

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24316   195318238+   7  HPFS/NTFS
/dev/sda2           24317       25289     7815622+  82  Linux swap / Solaris
/dev/sda3           25290       26505     9767520   83  Linux
/dev/sda4           26506       30401    31294620   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf3d99547

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS
[/I]

---

### Post by IcarusR on 2009-06-23
I have dual boot Ubuntu 8.10 & XP. My laptop only has one HDD.
The end of my menu.1st is as below

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc423cc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3825    30724281    7  HPFS/NTFS
/dev/sda2            3826       18414   117186142+  83  Linux
/dev/sda3           18415       18657     1951897+   5  Extended
/dev/sda5           18415       18657     1951866   82  Linux swap / Solaris

I think you need to change 
```
root (hd1,0)
```
to
```
root (hd0,0)
```

I'm not sure about the 
```
map (hd0) (hd1)
map (hd1) (hd0)
``` 
at the end

---

### Post by mcdjork on 2009-06-23
That's not the solution.

---

