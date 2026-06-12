---
title: "Xp and Kubuntu Dual Boot Error"
date: 2005-12-07
forum: Installation &amp; Upgrades
---

### Post by ephesius on 2005-12-07
The kubuntu install went clean and it recongnized my xp install. When i try to boot the xp i get a b.s.o.d. and it says that there is an unmountable_boot_volume anyone know wuts up with this?

---

### Post by BLTicklemonster on 2005-12-07
partitions or seperate drives?

---

### Post by x__dark on 2005-12-07
Probably due to your partition number in the GRUB menu. Trying playing around with it.

---

### Post by ephesius on 2005-12-07
It is on partitions. My windows partition is hda1 followed by a swap partition and ext3 partition. I just copied everything i need off of it and I'm going to wipe out XP but I am still wondering why this has happened.

---

### Post by bwog on 2005-12-07
Perhaps there is no need to wipe your windows. 

At boot did you see the grub menu where you can choose between ubuntu and windows?

When you did not see that you have to reinstall grub. When you installed grub succesfully and cant boot  windows come back here and we probably will get it working.

---

### Post by djalias on 2005-12-08
i have exactly the same problem he is having. I have the windows on hda1 ntfs, and hda2 for linux with an extended swap partition. grub is installed to the linux partition and the MBR boots the linux partition. the grub menu come up fine and boots linux ok. but when i try xp it shows the windows loading screen and then bsod's with the "unmountable boot volume" error. i have tried making the MBR boot straight to the windows, but the error still occurs. any ideas??

---

### Post by bwog on 2005-12-08
@djalias: you may have a slightly different problem as the TS. The solution lies in editing grub. 

You have to edit grubs menu.list. In a terminal do

sudo gedit /boot/grub/menu.lst

below the line ### END DEBIAN AUTOMAGIC KERNELS LIST there should be an entry for windows (it is probably there already).

Check whether it points to the right disk and partition first. Also look at /boot/grub/device.map. You may need to use an entry with the map command. 

There are examples here: [http://ubuntuforums.org/showthread.php?t=99077&highlight=map+automagic](http://ubuntuforums.org/showthread.php?t=99077&highlight=map+automagic)

Windows likes to be at the first partition of the first disk, and the map command makes it think it is there.

---

### Post by djalias on 2005-12-08
thanks for the ideas, i messed around with them for a while though and couldnt get anything to work. although, i have only one hard disk, and the windows partition is the first partition. perhaps you can spot a problem ive missed? here is my fdisk list:

```
Disk /dev/hda: 30.0 GB, 30005821440 bytes
15 heads, 63 sectors/track, 62016 cylinders
Units = cylinders of 945 * 512 = 483840 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       32512    15361888+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2   *       32522       60741    13333950   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/hda3           60742       62016      602437+   5  Extended
Partition 3 does not end on cylinder boundary.
/dev/hda5           60742       62016      602406   82  Linux swap / Solaris
```

and here is my grub menu:

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
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
chainloader +1
```

and here is my disk map:

```
(hd0)	/dev/hda
```

any help would be greatly appreciated, as i really really need to work this out. thanks!

---

### Post by bwog on 2005-12-08
I cant find anything wrong, only that in the fdisk output hda1 is not bootable.
Perhaps I let you look at the wrong place for this problem. 

you write: i have tried making the MBR boot straight to the windows

Does that mean you tried fixmbr in the rescue mode of the Windows CD?

Edit: To get winXP working again you could try fixmbr in the rescue mode of the Windows install CD. Other options are fixboot and editing boot.ini, but I would check a windows tutorial first so that you know what you are doing. This will overwrite grub, but that may be solved later. 

Perhaps there a better options, so wait a bit in case someone else replies. At least overwriting grub can be reversed, so it wont create more problems.

---

### Post by martz on 2005-12-16
i have the same issue... did this ever get resolved?

---

### Post by Herman on 2005-12-16
You have:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
chainloader +1
``` All mine have:
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Windows 95/98/Me
root        (hd0,0)
savedefault
[COLOR=Red]makeactive[/COLOR]
chainloader    +1 This is what all the computers in my house have, XP or Win98, dual booting with Ubuntu. They all have 'makeactive' for the second from the bottom line. Maybe try that. Be sure to make a back-up of your menu/lst first though, in case I'm wrong. :D (Herman).

---

### Post by simonr on 2006-01-03
I currently have the same issue, is there a solution for this yet? (Help!!)
I returned my XP installation back by fdisk /mbr and deleted Linux partitons

It looks like the partitons are in the wrong order??? (I don't know if this has any bearing on the issue, the ntfs partition appears (in Fdisk) to move to the end of the list. Once the non dos partitions have been removed, it returns to normal and boots. This happens even though during the Ubuntu install you can specify where the partitions should be. I tried to modify the Win boot .ini file  but was unsuccessfull.
Any suggestions would really be appreciated for this.

---

