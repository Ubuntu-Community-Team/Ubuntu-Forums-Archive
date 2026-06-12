---
title: "From Fedora Core 4 to Ubuntu"
date: 2005-11-14
forum: General Help
---

### Post by jan247 on 2005-11-14
[IMG]http://www.geocities.com/an2king_kid/partition.jpg[/IMG]

Newbie here, I have Windows XP and Fedora Core 4 currently on my computer. The partitions are showin above. How can I write over my Fedora Core installation and replace it with Ubuntu? I don't need to save anything from Fedora Core anyway. Oh, btw, I am using the 64 bit version.:confused:

---

### Post by matthewv on 2005-11-14
When you come to the partitioning part of the ubuntu install just delete your fedora partitions and tell the ubuntu installer to use the free space..

---

### Post by darknuala on 2005-11-14
You could keep Fedora Core 4 and just install Ubuntu and drop XP? :p

---

### Post by dbott67 on 2005-11-14
When installing Ubuntu (or any OS, for that matter) it should give you a listing of the current partitions that have been detected.  In your case, I'm guessing that FC4 is installed on the 20 GB partition, and the swap file is on the 102 MB partition.  You could choose to delete the 2 non-NTFS partitions and install Ubuntu in the newly created free space.

-Dave

---

### Post by dbott67 on 2005-11-14
[QUOTE=matthewv]When you come to the partitioning part of the ubuntu install just delete your fedora partitions and tell the ubuntu installer to use the free space..[/QUOTE]
I've really got to learn to type faster! :)

---

### Post by Noelinho on 2005-11-14
I'm not wishing to hijack this thread - but I have a very similar problem. I used to have Ubuntu installed, but switched to FC4 - now I have installed Breezy alongside, (I also have Windows XP installed). Trouble is, GRUB doesn't recognise FC4 is installed.

How do I get it to recognise it?

---

### Post by dbott67 on 2005-11-14
You need to edit the /boot/grub/menu.lst file to include the partition information to where FC4 is:
```
dbott@breezy:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, kernel 2.6.12-8-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-8-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-8-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-8-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-8-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.12-8-386
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title           Ubuntu, kernel 2.6.10-5-386 (on /dev/hda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title           Ubuntu, kernel 2.6.10-5-386 (recovery mode) (on /dev/hda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title           Ubuntu, kernel memtest86+ (on /dev/hda1)
root            (hd0,0)
kernel          /boot/memtest86+.bin
savedefault
boot
```

You would add FC4 after the last entry, in a similar format to the main Ubuntu kernel, but replace the HD and partition info for FC4.

-Dave

---

### Post by matthewv on 2005-11-14
[QUOTE=Noelinho]I'm not wishing to hijack this thread - but I have a very similar problem. I used to have Ubuntu installed, but switched to FC4 - now I have installed Breezy alongside, (I also have Windows XP installed). Trouble is, GRUB doesn't recognise FC4 is installed.

How do I get it to recognise it?[/QUOTE]
You'll need to edit your /boot/grub/menu.lst file. Try searching elsewhere for instructions, and make sure you *back up* your menu.lst before trying anything

EDIT: Now dbott beat me to it :)

---

### Post by Noelinho on 2005-11-14
I had looked at that file. The only trouble was, I don't know the exact build of the Kernel. I guess I could find out from the Fedora Core forums.

---

### Post by psyguy92 on 2005-11-14
[QUOTE=Noelinho]I had looked at that file. The only trouble was, I don't know the exact build of the Kernel. I guess I could find out from the Fedora Core forums.[/QUOTE]


Do this:

```
uname -a
```

---

### Post by Noelinho on 2005-11-14
Hehe, if I could do that, I'd not be needing to change the boot loader :) 

I can't get into Fedora to do that, if I could get into it, it wouldn't matter in the slightest. Thanks anyway.

---

### Post by denisesballs on 2005-11-14
If you did FC4 defualt partitioning it's gonna be a little harder since there's LVM. Here's an example of my Dad's:

```
title Fedora Core 4
        root (hd0,0)
        kernel /vmlinuz-2.6.12-1.1398_FC4 ro root=/dev/CyberSourceOffice/LogVol00 rhgb quiet
        initrd /initrd-2.6.12-1.1398_FC4.img
```

---

### Post by Noelinho on 2005-11-14
In that case, mine could be something like:

```
title Fedora Core 4
        root (hd0,3)
        kernel /vmlinuz-2.6.14-1.1637_FC4 ro root=/dev/CyberSourceOffice/LogVol00 rhgb quiet
        initrd /initrd-2.6.14-1.1637_FC4.img
```

(I found out my kernel)

Not sure about '/dev/CyberSourceOffice/LogVol00' though. (Well, more directly, the 'CyberSourceOffice' bit)

---

### Post by Noelinho on 2005-11-14
Actually, as an alternative, would I not be able to mount the partition on Ubuntu?

---

### Post by denisesballs on 2005-11-14
[QUOTE=Noelinho]In that case, mine could be something like:

```
title Fedora Core 4
        root (hd0,3)
        kernel /vmlinuz-2.6.14-1.1637_FC4 ro root=/dev/CyberSourceOffice/LogVol00 rhgb quiet
        initrd /initrd-2.6.14-1.1637_FC4.img
```

(I found out my kernel)

Not sure about '/dev/CyberSourceOffice/LogVol00' though. (Well, more directly, the 'CyberSourceOffice' bit)[/QUOTE]

That's the name of your volume group. Boot with your FC4 rescue cd. I think by default it's VolGroup00 or something. In FC4, type lvscan to see.

---

