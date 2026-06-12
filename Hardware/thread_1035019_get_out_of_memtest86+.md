---
title: "get out of memtest86+"
date: 2009-01-09
forum: Hardware
---

### Post by 80aless on 2009-01-09
Hi,
my ubuntu machine cannot boot normally anymore. In the grub I can only select Memtest86+ ! I am running it, but it starts over again. 
Hope somebody can help
Regards
Alex

---

### Post by 80aless on 2009-01-26
nobody nobody dy dy dy

---

### Post by jespdj on 2009-01-26
Is the problem that you can't use the keyboard at all in GRUB? Do you have an USB keyboard? If yes, then try to enable "Legacy USB support" in the BIOS settings of your computer.

Otherwise, try booting from an Ubuntu live CD. Mount your harddisk while booted with the CD, and look at the file /boot/grub/menu.lst. Make sure that it's correct.

---

### Post by 80aless on 2009-01-26
hi, thanks for your answer, there are some developments with my problem though. Now I can boot with a Super Grub USB/CD, but I cannot without. Here below the working menu.lst . If I choose it with the Super Grub USB everything goeas all right, otherwise I get an error.
Cheers,
alessandro

```

less /boot/grub/menu.lst
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
# kopt=root=UUID=0ebda0d2-112d-4645-bae3-1df95201cbdf ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0ebda0d2-112d-4645-bae3-1df95201cbdf ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=0ebda0d2-112d-4645-bae3-1df95201cbdf ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0ebda0d2-112d-4645-bae3-1df95201cbdf ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0ebda0d2-112d-4645-bae3-1df95201cbdf ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0ebda0d2-112d-4645-bae3-1df95201cbdf ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0ebda0d2-112d-4645-bae3-1df95201cbdf ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


```
```



less /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0ebda0d2-112d-4645-bae3-1df95201cbdf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=feef9251-27c9-4e34-9141-1cb313eb92bf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/etc/fstab
```

---

### Post by Yashiro on 2009-01-26
What did you do that could have caused this?

---

### Post by Hobgoblin on 2009-01-26
> **80aless said:**
> Hi,
my ubuntu machine cannot boot normally anymore. In the grub I can only select Memtest86+ ! 

What do you mean you can only select Memtest?

When you press the up and down arrows on your keyboard does the selection change?

Booting to Memtest should run memtest until you press escape then reboot, that's how it is intended.  Rebooting will bring back the Grub menu.

What type of keyboard are you using?

Can you try a different keyboard?

---

### Post by 80aless on 2009-01-27
Hi people, thank you very much for your interest but I solved it. 
Here a description of my problem, for completeness.
Basically after an update I could not boot anymore: evidently the grub was looking in the wrong partition or the partition was unmounted and it was reading some standard menu.lst files. I do not know if this makes sense, but with the ubuntu live cd in /boot/ there was only memtest86+ and no vmlinuz-*-generic or initrd* file, so the system could only make a memorytest.

With a Super Grub USB I could chose the right menu.lst (which was a menu.lst~ ) and log in. To make the booting settings stable I had to use 
grub (hd0,0)
setup (hd0)

Easy, if one knows what to do. 
The keyboard was ok (never had any problem with it), the cause was an ubuntu update I think because this happened after a reboot.

---

### Post by Yashiro on 2009-01-27
Nice work.

---

### Post by oldyoda on 2010-04-26
ok so i have the same problem but i dont have a live CD and i dont know what grub is but when i turn on my computer it pretty much starts in mem test and when i press esc it just restarts memtest please help

---

