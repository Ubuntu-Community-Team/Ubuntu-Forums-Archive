---
title: "grub error 17 cannot mount selected partition"
date: 2008-10-16
forum: General Help
---

### Post by dalzate0988 on 2008-10-16
Hi i was trying to dual boot xp and ubuntu and can run xp but i get a a message grub error 17 cannot mount selected partition can anyone help me??

---

### Post by caljohnsmith on 2008-10-17
So do you get the grub error 17 when you select Ubuntu from the Grub menu, or do you get it before even seeing a Grub menu? When you say you can boot Win XP, are you doing that from the Grub menu? 

Please boot your Live CD, open a terminal (applications > accessories > terminal) and post:
```
sudo fdisk -lu
```

---

### Post by dalzate0988 on 2008-10-20
after i see the grub menu and no it goes directly to xp 



   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    10442249     5221093+   7  HPFS/NTFS
/dev/sda2   *    10442250    56115044    22836397+  83  Linux
/dev/sda3        56115045    58621184     1253070    5  Extended
/dev/sda5        56115108    58621184     1253038+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by dalzate0988 on 2008-10-20
after i see the grub menu and no it goes directly to xp



Device Boot Start End Blocks Id System
/dev/sda1 63 10442249 5221093+ 7 HPFS/NTFS
/dev/sda2 * 10442250 56115044 22836397+ 83 Linux
/dev/sda3 56115045 58621184 1253070 5 Extended
/dev/sda5 56115108 58621184 1253038+ 82 Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by macheboy on 2008-10-20
I was getting this error when I had grub loader on different disk than the disk that was selected as the first boot disk in bios.
Try changing boot device priority in BIOS. That fixed problem for me.
Also, if you have message like "press F11 to enter boot popup menu" maybe you will have to do it like this becuse GRUB will only start if boot order is arranged in certain way that may not make the disk on which is GRUB installed the first boot disk.

---

### Post by caljohnsmith on 2008-10-20
OK, please post the results of:
```
sudo mount /dev/sda2 /mnt
cat /mnt/boot/grub/menu.lst
```

---

### Post by dalzate0988 on 2008-10-21
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
# kopt=root=UUID=d23a56de-e1bb-477a-91bf-0f2f612b2152 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d23a56de-e1bb-477a-91bf-0f2f612b2152 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d23a56de-e1bb-477a-91bf-0f2f612b2152 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by caljohnsmith on 2008-10-21
OK, from your Live CD, do:
```
sudo mount /dev/sda2 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And find the line that says "# groot=(hd0,0)" and change it to:
```
# groot=(hd0,1)
```
Also, replace the "root (hd0,0)" in all the Ubuntu entries with:
```
root (hd0,1)
```
And lastly, at the end of the file add:
```
title Windows XP
root (hd0,0)
chainloader +1
```
Reboot, and let me know what happens.

---

### Post by dalzate0988 on 2008-10-21
thanks man it worked i would have just reinstalled ubuntu and lost everything

---

### Post by caljohnsmith on 2008-10-21
Glad to hear everything is working. Cheers and have fun. :)

---

