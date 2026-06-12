---
title: "No XP in Grub"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by DMonkey08 on 2008-12-14
I just installed 8.04 (the 8.10 installer was having problems), and for some reason Windows XP isn't showing up in grub.  I know the partition is there, but it's not in the grub menu, and when I try to mount the XP filesystem in Ubuntu, it gives me an error.

Anyone know how to fix this?  I really need to access a file on my XP partition.

---

### Post by Partyboi2 on 2008-12-14
Can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
cat /boot/grub/menu.lst
``` Also what is the error message you are getting when you try to mount the  xp partition?

---

### Post by caljohnsmith on 2008-12-14
How about booting your Live CD, download the attached "boot_info6.sh.txt" file to your desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info6.sh.txt
```
That will create a "BootInfo.txt" file on your desktop; please attach that to your next post, or simply copy/paste the contents to your next post. That will greatly clarify your setup in order to know how to boot XP.

---

### Post by logos34 on 2008-12-14
You might also want to post 

sudo fdisk -l

For editing menu.lst and mouunting windows in ubuntu:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu)
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by DMonkey08 on 2008-12-14
> **Partyboi2 said:**
> Can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
cat /boot/grub/menu.lst
``` Also what is the error message you are getting when you try to mount the  xp partition?
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
# kopt=root=UUID=a18fca64-7df9-4f0b-b95b-b33418c1528a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a18fca64-7df9-4f0b-b95b-b33418c1528a ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a18fca64-7df9-4f0b-b95b-b33418c1528a ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

> **Partyboi2 said:**
> Also what is the error message you are getting when you try to mount the xp partition? 
"$MFTMirr does not match $MFT (record 1).  Failed to mount '/dev/sda1': Input/output error NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/FakeRAID hardware."  It then gives me some useless instructions because I have to execute them in Windows, which I can't.

---

### Post by logos34 on 2008-12-14
> **DMonkey08 said:**
> It then gives me some useless instructions because I have to execute them in Windows, which I can't.

like this:

> In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details. 

??

If so, boot the windows install cd (i.e recovery console) and run that command at the prompt

or else add windows entry to grub and if it boots run error checking w/repair

---

### Post by DMonkey08 on 2008-12-14
[QUOTE=logos34]For editing menu.lst and mouunting windows in ubuntu:

[http://ubuntuguide.org/wiki/Ubuntu:F...into_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu:F...into_GRUB_menu)
[https://help.ubuntu.com/community/Mo...irdPartyNTFS3G](https://help.ubuntu.com/community/Mo...irdPartyNTFS3G)[/QUOTE]
Oh jeez, I didn't see that in your original post... probably too busy banging my against a wall.

Anyways, I followed the instructions to add Windows to menu.lst and it works now.  Thanks.:guitar:

---

### Post by logos34 on 2008-12-14
no prob.  glad to hear everything's ok now.  -->thread tools>mark as solved.  enjoy

---

