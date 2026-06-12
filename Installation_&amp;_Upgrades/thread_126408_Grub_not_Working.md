---
title: "Grub not Working"
date: 2006-02-06
forum: Installation &amp; Upgrades
---

### Post by WelterPelter on 2006-02-06
My box has a linux drive and a windows drive. In the past, when I installed Mandrake on this machine, Grub worked fine out of the box. I would get a menu that included the windows drive on boot. 

However, so far with ubuntu, Grub doesn't present that option. I can mount the windows drive and use it fine, but I can't boot to windows (not something I do often, but I need to be able to for various games, etc.)

My question is how to tackle this without risking the death of all the important mediat files, etc. I have stored on the windows drive.

Thanks, ubuntu folk!

---

### Post by katanacb on 2006-02-06
Just curious, does your machine right-off boot into Linux after POSTing, or do you get a grub menu with some choices *BEFORE* it boots into linux?

---

### Post by WelterPelter on 2006-02-06
Grub asks if I want to see a menu, which has only various kernel options. No windows.

---

### Post by katanacb on 2006-02-06
hmm... sounds like (obviously) Windows wasn't added to your grub.conf.

Check out this post and see if it helps .... it says what you might need to add to your /boot/grub/menu.lst file to get Windows as a boot option:

[http://ubuntuforums.org/showthread.php?t=98182&highlight=dual+boot+windows+grub.conf]("http://ubuntuforums.org/showthread.php?t=98182&highlight=dual+boot+windows+grub.conf")

I'm not sure where your Windows partition is located on your hard drive(s) so you might have to tweak the (hd0,0) references in the grub.conf file, but hopefully this should get you going.

---

### Post by WelterPelter on 2006-02-06
Here's my /boot/grub/menu.lwt. My windows drive is hdb (the whole drive). Do I just uncomment the windows section in this file and change (hd0,0) to (hdb1,0)? 

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro

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

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Here's the result of fdisk -l :
Disk /dev/hda: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2385    19157481   83  Linux
/dev/hda2            2386        2491      851445    5  Extended
/dev/hda5            2386        2491      851413+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9729    78148161    c  W95 FAT32 (LBA)

---

### Post by lha on 2006-02-06
[QUOTE=WelterPelter]Here's my /boot/grub/menu.lwt. My windows drive is hdb (the whole drive). Do I just uncomment the windows section in this file and change (hd0,0) to (hdb1,0)? [/QUOTE]

It won't work. Paste these lines in the very end of menu.lst, under the line '### END DEBIAN AUTOMAGIC KERNELS LIST'

```
title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

---

### Post by WelterPelter on 2006-02-06
[QUOTE=lha]It won't work. Paste these lines in the very end of menu.lst, under the line '### END DEBIAN AUTOMAGIC KERNELS LIST'

```
title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```[/QUOTE]

:-D Thanks! That works perfectly. Was able to reboot to windows, then reboot to ubuntu, no problem. I appreciate your help. :-D

---

### Post by lha on 2006-02-06
[QUOTE=WelterPelter]:-D Thanks! That works perfectly. Was able to reboot to windows, then reboot to ubuntu, no problem. I appreciate your help. :-D[/QUOTE]
You're welcome. I'm glad I could help.

---

