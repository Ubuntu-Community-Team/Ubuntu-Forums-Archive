---
title: "Initramfs problems"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by [z]er0 HP on 2009-02-02
This is an old problem i've been putting up with but i'm finally sick of it and would like it fixed. Here is the description from my other thread i posted that I was unable to get the information from to fix the problem. 

I'm having trouble after I used the Update manager to upgrade. It prompted me to restart, so I did. It was starting up normally, BIOS, GRUB, then it came up with an error message on a black terminal screen.
```

usplash: no usable theme found for 1280x1024
screen init failed

gave up waiting for root device. common problems:
-boot args (cat /proc/cmdline)
-check rootdelay=(did the system wait long enough?)
-check root=(did the system wait for the right device?) 
-missing modules (cat /proc/modules; is dev)

ALERT! /dev/disk/by-uuid/07cdf0c-25f1-4db1-a213-d44bcd3efbdd does not exist. dropping to shell!


Busybox v1.10.2 (ubuntu 1:1.10.2-1ubuntu6) built in shell (ash)
Enter 'help' for a list of built in commands.
(initramfs) [  61.156011] ata6: SRST failed (errno=-16)
(initramfs)

```

I have tried adding rootdelay=120 on to the end of the kernel line in the grub configuration and that has not fixed the problem


I managed to get it to boot by typing 'exit' or pressing ctrl+d at the prompt.

Output from fdisk -l
```

sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe454e454

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59573   478520091   83  Linux
/dev/sda2           59574       60801     9863910    5  Extended
/dev/sda5           59574       60801     9863878+  82  Linux swap / Solaris

```

/boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		0

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=070cdf0c-25f1-4db1-a213-d44bcd3efbdd ro

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
# defoptions=quiet splash vga=795

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
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=070cdf0c-25f1-4db1-a213-d44bcd3efbdd ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=070cdf0c-25f1-4db1-a213-d44bcd3efbdd ro  single
initrd		/boot/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Hopefully someone can help me fix this problem because I really don't want to have to reinstall.
Thanks

---

### Post by [z]er0 HP on 2009-02-03
Bump!

---

### Post by Mrs Twaddle on 2009-02-05
I'm having the same trouble after a kernel update.
rootdelay doesn't fix it for me either, i'm having to go into grub and use an older version

---

### Post by zer0max713 on 2009-02-05
I also have the same issue. I think mine has to do with the way my partitions are setup. 

Maybe you need to change your boot sequence from the bios.....

---

### Post by 2scott on 2009-02-05
Hi - I have also had the SAME problem installing 8.10 and 8.40 - sure hope someone can help us!!

---

### Post by jooshbro on 2009-02-18
I have the same issue - only typing "exit" or hitting ctrl-d don't work for me, meaning that I can't get into the Ubuntu GUI at all.  Is there a solution for this issue?

---

### Post by The Tornado on 2009-02-20
> **jooshbro said:**
> I have the same issue - only typing "exit" or hitting ctrl-d don't work for me, meaning that I can't get into the Ubuntu GUI at all.  Is there a solution for this issue?

I have the same problem now
plz any help???

---

### Post by iwm on 2009-02-22
if at busybox shell you type these 2 commands:

dmraid -ay 
and 
ctrl+d (or exit)

it should start...

It seems it's a 2.6.27 kernel problem, i've solved installing the hardy's one 2.6.24-23-server

---

### Post by abn91c on 2009-02-22
if first booting at the initramfs prompt wait about 5 seconds before typing **exit**

---

### Post by [z]er0 HP on 2009-02-22
I fixed it by fiddling in the BIOS settings and replugging in the cables between my hard drives and the motherboard

I fixed the other part of the problem by removing the settings stored in /home/username/.gconf/
I removed them, rebooted and then re-added the ones I needed and reconfigured a few different things.

---

