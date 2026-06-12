---
title: "[SOLVED] Dual Boot - Vista Fails to Boot"
date: 2008-09-23
forum: General Help
---

### Post by gabe.c on 2008-09-23
hi guys i just started using ubuntu. i installed it together with vista using a grub menu. ubuntu is working fine, but i cant get into vista through the grub. at first i thought that it was because i had a hard time mounting the partitions on which i had vista, but i managed to force them and it still doesnt work. i have a compaq presario c700. now the thing with my computer is that it doesnt have a recovery disk. vista included it in the computer as another partition. so i had to add another partition in the grub just for the recovery. i dont know if that has something to do with my problem.
can anyone please help?

when i enter "sudo fdisk -l" in terminal i get this output:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1477763c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        3825       17941   113394802+   7  HPFS/NTFS
/dev/sda2           17942       19457    12177270    7  HPFS/NTFS
/dev/sda3             638        3824    25599577+   5  Extended
/dev/sda4               1         637     5116671   83  Linux
/dev/sda5             893        3824    23551290   83  Linux
/dev/sda6             638         892     2048224+  82  Linux swap / Solaris

Partition table entries are not in disk order


does the last line mean anything? can that be my problem?

---

### Post by northern lights on 2008-09-23
Windows partition(s) need not be mounted in Ubuntu for GRUB to work. There's no correlation here. Can you please also post the output of ```
cat /boot/grub/menu.lst
```Thank you.

---

### Post by Elfy on 2008-09-23
No that line isn't anthing to do with it.

Can you post your menu list please, run this in a terminal and post the whole output enclosed in [noparse]```

```[/noparse] tags please

```
cat /boot/grub/menu.lst
```

---

### Post by gabe.c on 2008-09-23
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
timeout		10

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
# kopt=root=UUID=daa13356-f5d3-4532-90da-1c8fcc807038 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=daa13356-f5d3-4532-90da-1c8fcc807038 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=daa13356-f5d3-4532-90da-1c8fcc807038 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by caljohnsmith on 2008-09-23
One of those two menu entries that you have for Vista should work, since you only have two NTFS partitions on your HDD. I suspect your problem is not with Grub, but with your Vista actually booting. On start up, when you select the Vista entries in Grub's menu, what exactly happens when you try each one? What errors do you get?

---

### Post by gabe.c on 2008-09-23
the screen turn blue. and tries to automatically fix the problem. but then i get a message that it was unable to fix the problem. it then reads that the problem might be because i have something connected to the computer such as a camera.
but i dont have anything conected.
any suggestions?

you said one entry is supposed to work. which one is it? the (hd0,0) or (hd0,1)
because its (hd0,0) that vista OS is on. the other one is the vista recovery. is there some way to switch between the two?

---

### Post by caljohnsmith on 2008-09-23
It definitely sounds like you have a Vista problem and not a Grub problem at this point; and yes, the (hd0,0) entry in menu.lst should work if your Vista is on the first partition. If you want to remove the other (hd0,1) entry, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And delete the second Vista entry.

Do you have a Vista Install/Recovery CD? If not, you can download one from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Once you get that, boot it up, and do a "Vista Repair" from the menu choices. If that doesn't solve your problem, I can give you specific commands to run from the Vista Repair CD that should help you get Vista running again. Let me know how it goes or if you need more details/info. :)

---

### Post by gabe.c on 2008-09-23
thanks a lot. it works now. i got vista and its the same as it was before. 
but after i select vista in the grub menu i get another menu, to select either "microsoft windows vista" or windows vista recovered. when i went into microsoft windows vista (the first one) i had the same problem. but the second one worked. is there some way to remove the first one from that menu?

---

### Post by northern lights on 2008-09-23
Check the *boot.inf* in *C:\Windows*

---

### Post by caljohnsmith on 2008-09-23
> **gabe.c said:**
> thanks a lot. it works now. i got vista and its the same as it was before. 
but after i select vista in the grub menu i get another menu, to select either "microsoft windows vista" or windows vista recovered. when i went into microsoft windows vista (the first one) i had the same problem. but the second one worked. is there some way to remove the first one from that menu?
Sure, probably the easiest way to configure Windows Vista's boot loader menu is to use a program called "EasyBCD":

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Give that a shot and let me know how it goes. :)

---

### Post by gabe.c on 2008-09-27
hey man thanks for all your help. everything is working like a charm now.

---

### Post by caljohnsmith on 2008-09-27
You're welcome, glad everything is running smoothly now. Cheers and have fun. :)

---

