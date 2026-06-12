---
title: "I messed up my Ubuntu again"
date: 2005-11-19
forum: General Help
---

### Post by commodore on 2005-11-19
I wanted to install a second Ubuntu so I could test stuff on it and not kill the primary one. No I cant start the primary Ubuntu where I have all my files but I am posting from the testing Ubuntu. Anyways, I got this error /bin/sh: cant access tty job control turned off.

---

### Post by metoo on 2005-11-19
Dive into /boot/grub/menu.lst and see if the settings for your primary installation do make sense (similar to your testing install).
(There might be a backup of this file from the time before the testing installation, check this too)

Of course, the partition or hd/partition in the kernel line will be different.
Remember this entry, so you can mount the partition from the 2nd install in case you need to rescue the data.

---

### Post by commodore on 2005-11-20
I didn't notice anything wierd. My menu.lst looks like this:
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
default		4

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sdb5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sdb5 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sdb5 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Teised OS-id:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		M$ Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu, nummah (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sdb6 ro quiet splash 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu, kernel 2.6.12-9-386 (recovery mode) (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sdb6 ro single 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title		Ubuntu, memtest86+ (on /dev/sdb7)
root		(hd1,6)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

---

### Post by commodore on 2005-11-21
help mee

---

### Post by commodore on 2005-11-21
Please

---

### Post by aysiu on 2005-11-21
You're not a paying customer, and we are not the official help desk.

Everyone here is a volunteer and a regular Ubuntu user--just like you.

If no one answers, it's usually because no one knows the answer.

No one is sitting around here thinking, *Ha ha ha! Insolent newbie! I know the answer, but I think I'm going to make you beg for it. Beg, I say! Beg!*

That said... have you tried [reinstalling Grub](http://ubuntuforums.org/showthread.php?t=24113)?

---

### Post by commodore on 2005-11-22
Sorry, but if I don't say anything people wont see my thread.

I don't know why but I installed grub when I installed my test Ubuntu. Is that bad?

---

### Post by michael_salcher on 2005-11-22
you could try the "install and upgrade" forum

---

