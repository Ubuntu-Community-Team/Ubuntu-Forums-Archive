---
title: "Accidently Over Vista with Ubuntu"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by Snyder1 on 2009-10-17
I was wanting to have a dual boot first of all. I made a 32mb partition because i was just wanting to fidel around with it, nothing serious.  I installed it and everything in the 32mb, i was pretty of it. I resarted my computer and when boot manager comes up it only shows Ubuntu and no other operating system.  I have no installation cd of vista because the disc did not come with the laptop.  I am at college and need to resolve this issue fast. Please help!

---

### Post by stlsaint on 2009-10-17
it sounds like you have deleted your windows but just to be over 100% sure please post the output of your menu.lst. Go to a terminal and enter this:

```
gksudo gedit /boot/grub/menu.lst
```

post the txt file here or just copy and paste it. Then we will be able to tell you for sure whether you deleted it or not!

---

### Post by Snyder1 on 2009-10-17
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
# kopt=root=UUID=6d8dd0c4-2b51-43f6-9618-5a33af8e384a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6d8dd0c4-2b51-43f6-9618-5a33af8e384a

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        6d8dd0c4-2b51-43f6-9618-5a33af8e384a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6d8dd0c4-2b51-43f6-9618-5a33af8e384a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        6d8dd0c4-2b51-43f6-9618-5a33af8e384a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6d8dd0c4-2b51-43f6-9618-5a33af8e384a ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        6d8dd0c4-2b51-43f6-9618-5a33af8e384a
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by stlsaint on 2009-10-17
im afraid that grub is not seeing your windows meaning that you probably have erased it...maybe if some strange way you still have the windows partition you may be able to add a stanza to your menu.lst to boot into windows...please post the results of the following cmd from your terminal:

```
sudo fdisk -l
```

---

### Post by oldfred on 2009-10-17
Just because menu.lst does not show a boot for windows does not necessarily mean it is gone. 
to see partitions:

sudo fdisk -l   #that is small el not 1 or i

---

### Post by lindsay7 on 2009-10-17
Also type  the following in the terminal and post the results, it will show what is on your computer,

sudo fdisk -l  (that is the lower case letter L)

---

### Post by Snyder1 on 2009-10-17
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x678b1560

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       37699       38913     9759487+  83  Linux

---

### Post by stlsaint on 2009-10-17
> **oldfred said:**
> Just because menu.lst does not show a boot for windows does not necessarily mean it is gone. 
to see partitions:

sudo fdisk -l   #that is small el not 1 or i

i know...that is why i posted to do fdisk -l right about you!! =)

---

### Post by stlsaint on 2009-10-17
> **Snyder1 said:**
> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x678b1560

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       37699       38913     9759487+  83  Linux


if that is all you have than yes you have erased your windows...some recovvery software might be able to assist you in getting some stuff back.

---

### Post by Snyder1 on 2009-10-17
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x678b1560

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       37699       38913     9759487+  83  Linux

---

### Post by Snyder1 on 2009-10-17
what recovery software is there to get my windows back?

---

### Post by oldfred on 2009-10-17
There may be some hope since the linux partition starts at 37699. IF you look at it with Gparted does it show more than one partition?

There is a program called testdisk that is usually on most liveCD, it can recover partitions if they are not too damaged, but may not fix your windows back to working order. Testdisk and photorec can recover files but not with their original names.

testdisk
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by Snyder1 on 2009-10-17
okay...i downloaded testdisk but how do i install it?

---

### Post by falconindy on 2009-10-17
> **Snyder1 said:**
> okay...i downloaded testdisk but how do i install it?
You're better off installing it from the repositories.
```
sudo apt-get install testdisk
```

---

### Post by Snyder1 on 2009-10-17
okay i did the above command...now what?

---

### Post by lindsay7 on 2009-10-17
Type   testdisk in the terminal and run the program. If you go to the Testdisk web site you can get the documentation on how to run it.

---

### Post by Snyder1 on 2009-10-17
TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
TestDisk need 25 lines to work.
Please enlarge the terminal and restart TestDisk.

---

### Post by lindsay7 on 2009-10-17
Enlarge the terminal with the maximize button so that it fills the screen and type testdisk again.

---

