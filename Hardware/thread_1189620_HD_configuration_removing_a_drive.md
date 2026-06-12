---
title: "HD configuration: removing a drive"
date: 2009-06-16
forum: Hardware
---

### Post by Messyhair42 on 2009-06-16
My current problem is I have a HD that needs to be sent in for replacement, so i took out the drive and configured my 2nd drive (Intrepid) in it's place. after i had removed the drive i couldn't boot into ubuntu. the drive needing replacing is set as first in boot order but i havent been booting to it since it went bad, i always just switch to the older installation through grub. whenever i boot i get a "media test failure" message. I've tried different cable and BIOS configurations and nothing works. My MB is an intel DG43NB with a relatively current BIOS. the sata connectors work in hierarchy i think, moving clockwise from the right. how do i get it to boot to the 2nd drive while the 1st is missing? b/c right now i have the old drive hanging out the side while i work around this and can send it in and have my computer working correclty. as soon as i put the non functioning drive back in it's original configuration it booted no problem.

---

### Post by Messyhair42 on 2009-06-17
i hate to bump it so early but this is urgent

---

### Post by Messyhair42 on 2009-06-18
I need to have a bootable computer, i'm still thinking it something in the BIOS, or possibly GRUB, it exists on both drives but the big drive (one being replaced) is set as primary drive.

---

### Post by markbuntu on 2009-06-18
SATA drives are ordered as they are found so, if you removed the first one (sda) the second one (sdb) now becomes sda regardless of where it is plugged in. If you have grub installed on the drive then you need to edit the /boot/grub/menu.lst and change (hd1,0) to (hd0,0). You may also need to change the boot order in bios but most likely not.

If you do not have a boot sector or grub on that drive you need to make a boot sector and install grub. 

You can boot up with a live cd to do that. There is instructions somewhere around here.

Just a little advice. If you install multiple distributions it is a good idea for each one to have its own grub on the same drive/partition as you installed the distro and to have a boot sector at the beginning of each drive so when the first drive craps out you can recover fairly easily. The bios looks in the first sector of the first drive for a boot sector. If it does not find it, then no boot.

---

### Post by Messyhair42 on 2009-06-19
k, i'll try that. what lines do i change?
i was also have problems with livecds, since the big drive went bad no livecd i have recognizes either device. hopefully this will change.

---

### Post by Messyhair42 on 2009-06-19
I'm weary about editing the file without help. so here is my /boot/grub/menu.lst for reference. it wont have the jaunty(big drive) entry in there since it's newer. but the only reference i find to (hd1,0) is in the examples. anyway here's the file
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
# kopt=root=UUID=30332a03-75e4-4749-a8ee-f80df161c6ba ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=30332a03-75e4-4749-a8ee-f80df161c6ba

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
# howmany=2

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		30332a03-75e4-4749-a8ee-f80df161c6ba
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=30332a03-75e4-4749-a8ee-f80df161c6ba ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		30332a03-75e4-4749-a8ee-f80df161c6ba
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=30332a03-75e4-4749-a8ee-f80df161c6ba ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		30332a03-75e4-4749-a8ee-f80df161c6ba
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=30332a03-75e4-4749-a8ee-f80df161c6ba ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		30332a03-75e4-4749-a8ee-f80df161c6ba
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=30332a03-75e4-4749-a8ee-f80df161c6ba ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
uuid		30332a03-75e4-4749-a8ee-f80df161c6ba
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by markbuntu on 2009-06-19
Ok, I see what is going on. The problem seems to be that the first stage grub was on the boot sector of the first hard drive which was removed. That is a very small thing that points to the other grub stages which are on your surrent drive.

So, you basically have no boot sector/first stage grub on this drive. You need to install grub and aim it at the current drive sda.

There are some directions for that around here somewhere....ahh here they are


[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

good luck and let us know how you make out.

---

### Post by Messyhair42 on 2009-06-20
which leads me back to the problem that any livecd i use doesn't recognize either of my hard drives. therefore i can't install grub from a livecd
when i first set up the drive i'm using now i did a clean install of Intrepid, at the time i had XP on the big drive and it would boot into grub from the drive i'm using now. what part of menu.lst tells you i dont have a boot sector?

---

### Post by Messyhair42 on 2009-06-21
so instead of making a boot sector with grub on the drive b/c i cant, can i make it on a flash drive instead? i just looked at this [http://ubuntuforums.org/showthread.php?t=992426]("http://ubuntuforums.org/showthread.php?t=992426") howto but it didn't work they way it was supposed to.

---

### Post by markmckee601 on 2009-06-21
I'm surprised that the livecd doesn't recognize your hard drive.

1: You could find out what module needs to be loaded/installed and load/install it. Then you can install grub on the MBR of the drive.

2: You can install GRUB on a floppy/usb/zip drive or if you have another drive you can install GRUB to that drive.

3: If you have a windows boot loader installed you can add linux to the boot loader menu.

[http://bkpavan.wordpress.com/2008/04/02/how-to-boot-linux-using-windows-bootloader-xp/](http://bkpavan.wordpress.com/2008/04/02/how-to-boot-linux-using-windows-bootloader-xp/)

4: You could download a copy of UBCD and see if it recognizes your drive and can boot to linux using one of the tools on the cd.

[www.ultimatebootcd.com](www.ultimatebootcd.com)

---

### Post by Messyhair42 on 2009-06-21
what to do/where to look for option #2 with a USB flash drive, just for booting temporarily while i'm down a drive.

---

### Post by markmckee601 on 2009-06-22
I found another how to for installing grub to a flash drive
[http://www.freesoftwaremagazine.com/articles/grub_intro/](http://www.freesoftwaremagazine.com/articles/grub_intro/)

Another how to for restoring grub can be found here:
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by markmckee601 on 2009-06-22
I think I know what the problem is with your current GRUB configuration.

You don't have the entry root (hd0,0) because it is set using the volume id of the drive instead.

If your second drive (the healthy drive) is sdb which would then change to sda when the failing drive is removed you would set root to (hd0,0) or get the volume id sudo vol_id /dev/sdb1 (if linux is on the first partition) then backup menu.lst on the healthy drive and change or modify uuid.

To backup menu.lst just type cp /boot/grub/menu.lst /boot/grub/menu.lst.bak.

---

### Post by Messyhair42 on 2009-06-22
except every time i enter
```
grub

find /boot/grub/stage1
```

as i've seen it gives me error 15: file not found. if one more try on the tutorial doesn't work i'll take the drive out and send it in and just wait. i can use live cds and i have everything accessible through a portable HD anyway

i think my kernel is having serious issues recognizing my devices.

---

### Post by Messyhair42 on 2009-06-25
solved, i just installed jaunty on a jump drive and the grub installaition took care of the rest

---

