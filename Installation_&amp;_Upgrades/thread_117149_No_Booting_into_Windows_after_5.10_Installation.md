---
title: "No Booting into Windows after 5.10 Installation"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by fiestaforever on 2006-01-14
Hi, 
after I installed Ubunru 5.10 on a Lifebook that had Windows 98 installed, Grub doesn't recognize the Windows partition (hda1) and doesn't offer me to boot Windows. Ubuntu is inside the extended partition (hda5=swap, hda6=root). 
I had Mepis (with Grub) and STX (with lilo) installed before, where it worked.
Now Windows doesn't appear in the list. 
What should I do?
Thanks for help.

---

### Post by Kipper on 2006-01-14
Do you get any error messages when trying to boot into Windows, or is there just no entry for Windows on the GRUB menu?

As you can still boot Ubuntu, post the contents of your "menu.lst" file ( found in /boot/grub) and the output of the command sudo fdisk -l /dev/hda (that's a lower case letter "L" not a one). I assume you re-installled GRUB in the MBR when you installed Ubuntu. This will show what GRUB is trying to do and what your partition layout is.

---

### Post by fiestaforever on 2006-01-14
(1) What I get from sudo fdisk -l /dev/hda: 

Disk /dev/hda: 12.0 GB, 12068904960 bytes
240 heads, 63 sectors/track, 1559 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         416     3144928+   b  W95 FAT32
/dev/hda2             417        1559     8641080    f  W95 Ext'd (LBA)
/dev/hda5             417         451      264537   82  Linux swap / Solaris
/dev/hda6             452         867     3144928+  83  Linux
/dev/hda7             868        1431     4263808+   c  W95 FAT32 (LBA)
/dev/hda8            1432        1559      967648+   e  W95 FAT16 (LBA)


(2) Contents of menu.lst: 

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
# kopt=root=/dev/hda6 ro

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by fiestaforever on 2006-01-14
I forgot to mention: There is no entry for Windows in the Grub menu.

BTW: How do I get the menu to show up automatically (now I get it only when I hit ESC fast enough)? How can I make it default to Windows? (I'm really sorry for the question, but Ubunu on this machine is only an experiment.)

---

### Post by Kipper on 2006-01-14
Ok, your partitions look healthy. You seem just to be missing the appropriate entries in "menu.lst" for GRUB to boot Windows.  

This example in the "menu. lst" file which is commented out is one you can use.

# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#

 As you wish to make Windows the default OS,  we need to place the text immediatley after ## ## End Default Options ##.  

The reason for having to press escape is the "hiddenmenu" command near the top of the file, this can be commented out.

This version of the "menu.lst" file should get you going. I've highlighted the changes made:

# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
**#hiddenmenu**

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery mode) single
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
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## ## End Default Options ##

[B]title Windows 95/98/NT/2000
root (hd0,0)
makeactive
chainloader +1[/B]

title Ubuntu, kernel 2.6.12-9-386
root (hd0,5)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda6 ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot

title Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root (hd0,5)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda6 ro single
initrd /boot/initrd.img-2.6.12-9-386
boot

title Ubuntu, memtest86+
root (hd0,5)
kernel /boot/memtest86+.bin
boot
### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by SilentCacophony on 2006-01-14
Hi. Just thought I'd point out a possible future problem with putting the Windows entry in the 'automagic kernels list' block. While it will work, I believe I've had a similar entry in the past wiped out after a subsequent kernel update, which also does an update-grub operation. The section after that is immune to change by updates, though.

An alternative would be to move the Windows entry after the **'### END DEBIAN AUTOMAGIC KERNELS LIST'** line, and use this section to specify the default:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default 0

```

You may use the 'savedefault' functionality, or change the 'default 0' to 'default 3' (that is, if the Windows entry is moved to fourth in the list as I described above.)

---

### Post by fiestaforever on 2006-01-15
Thanks to both of you for your advice.
On my first attempt, I got an "Error27: Unrecognized Command", but it works now.
Only one more thing I'd like to know. 
What is 
"makeactive
chainloader +1"?

---

### Post by SilentCacophony on 2006-01-16
I'm a bit sketchy on the details of those, but I'm pretty sure that makeactive provides similar functionality to using DOS's FDisk to set the 'active' (or bootable) partition.

The chainloader +1 line passes boot control from grub to the bootloader included in the partition's OS.

---

