---
title: "[SOLVED] chg mbr to ubuntu hd &amp;amp; remove win2k"
date: 2008-11-15
forum: General Help
---

### Post by hubiedo on 2008-11-15
i am trying to find out how to remove my windows 2k system completely. it is now on the first hd on the system. i think i need to install the mbr ?? on my unbuntu hd and edit grub to reflect where it is at. can anyone help point me the right direction. 

my system is working great and i dont want to mess it up or wreck my ubuntu install so i want to be careful to do it right, if possible.

any help would be appreciated

---

### Post by Th3Professor on 2008-11-16
sudo fdisk -l
(for starters)
...what does it show?

---

### Post by hubiedo on 2008-11-17
thanks th3 for any help you can give me.

below is the result of fdisk -l

hjk@hjk-linux:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9cf79cf7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3024    24290248+   7  HPFS/NTFS
/dev/sda2            3025        9729    53857912+   f  W95 Ext'd (LBA)
/dev/sda5            3025        6049    24298281    b  W95 FAT32
/dev/sda6            6050        6687     5124703+   b  W95 FAT32
/dev/sda7            6688        9729    24434833+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00068c9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2        9729    78140160    f  W95 Ext'd (LBA)
/dev/sdb5               2        9729    78140128+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         243     1951866   83  Linux
/dev/sdc2             244        3772    28346692+  82  Linux swap / Solaris
/dev/sdc3            3773       12401    69312442+  83  Linux
/dev/sdc4           12402       60801   388773000    5  Extended
/dev/sdc5           12402       18480    48829536   83  Linux
/dev/sdc6           18481       24559    48829536   83  Linux
/dev/sdc7           24560       24802     1951866   83  Linux
/dev/sdc8           24803       60801   289161936   83  Linux
hjk@hjk-linux:~$

---

### Post by Th3Professor on 2008-11-17
I see the following currently set aside for Windows...

Disk /dev/sda: 80.0 GB, 80026361856 bytes
/dev/sda1   *           1        3024    24290248+   7  HPFS/NTFS
/dev/sda2            3025        9729    53857912+   f  W95 Ext'd (LBA)
/dev/sda5            3025        6049    24298281    b  W95 FAT32
/dev/sda6            6050        6687     5124703+   b  W95 FAT32
/dev/sda7            6688        9729    24434833+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
/dev/sdb1   *           2        9729    78140160    f  W95 Ext'd (LBA)
/dev/sdb5               2        9729    78140128+   7  HPFS/NTFS

...and I see the following currently set aside for Linux...

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
/dev/sdc1               1         243     1951866   83  Linux
/dev/sdc2             244        3772    28346692+  82  Linux swap / Solaris
/dev/sdc3            3773       12401    69312442+  83  Linux
/dev/sdc4           12402       60801   388773000    5  Extended
/dev/sdc5           12402       18480    48829536   83  Linux
/dev/sdc6           18481       24559    48829536   83  Linux
/dev/sdc7           24560       24802     1951866   83  Linux
/dev/sdc8           24803       60801   289161936   83  Linux

You could completely wipe sda and sdb if you like, reformat them for anything else, such as Linux (or Unix). First, though, be sure to **back up** anything that you wish to keep. ;)

Plus, before you wipe the 1st 2 drives, go ahead and set sdc to boot, which can be done via...
fdisk sdc
m (shows menu options)
a (to select the partition to flag as boot)
w (to write/exit fdisk application)

I'm guessing it's your sdc1 that you'd like to boot from, though I don't know where your /boot directory is (put the boot flag on the partition that holds /boot (grub) or lilo or whatever you'd like to boot with)... 

One way to set grub to recognize your new boot is:
su
grub
root (hd2,0)
setup (hd2)
quit

(That is... if hard drive 3, partition 1 (sdc1) is your booting drive. 0=1, 1=2, 2=3.)

You might also want to edit your menu.lst to your liking.

At this point we're ignoring hard drives 1 and 2 so you can have a *nix-only computer... though before you reboot (and after you back-up important data) you may want to go ahead and wipe sda and sdb...

fdisk sda
d
("d" 1,2,5,6,7)
w
fdisk sdb
d
("d" 1,5)
w

Explore fdisk and discover neat ways you can set up your 1st 2 hard drives for use with *nix. :-)

---

### Post by hubiedo on 2008-11-21
Th3, thanks for all the help.

i have reviewed your post and have a couple of questions, if you don't mind.

you are correct in the setup that you reviewed and commented on. i am pretty sure i understand how to do it generally. one big question is will the renumber my linux drive (hd2) to hd0 when i remove the original hd0 and hd1?

it would seem that i would need to redo my grub and device.map accordingly if that is the case. if not and it stays as hd2 then i would only need to edit the device map to remove the sda and sdb entries and fix the grub as you suggested.

right now i plan to remove sdb first and see how it goes but even then if i mess up the grub or device.map files it wouldnt boot so maybe i should do both at once. what do you think? 

these two drives are going into a new bu computer for my office and i really dont need to fdisk them. i intend to only have the sdc / hd2 left on my linux box. any comments or suggestions? 

from my prior experience, i know i can fix grub from original install disk emergency boot etc. but i want to avoid this if i can and do it carefully the first time to have the best chance of it going well. not that anything goes according to plan!!
here is my device.map now and grub.conf

root@hjk-linux:/boot/grub# more device.map
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
root@hjk-linux:/boot/grub# more menu.lst
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
timeout		20

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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=66e6abb9-66cf-4060-b506-5d5b4ede7985 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd2,0)
kernel		/vmlinuz-2.6.24-21-generic root=UUID=66e6abb9-66cf-4060-b506-5d5
b4ede7985 ro quiet splash
initrd		/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd2,0)
kernel		/vmlinuz-2.6.24-21-generic root=UUID=66e6abb9-66cf-4060-b506-5d5
b4ede7985 ro single
initrd		/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd2,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=66e6abb9-66cf-4060-b506-5d5
b4ede7985 ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd2,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=66e6abb9-66cf-4060-b506-5d5
b4ede7985 ro single
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd2,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=66e6abb9-66cf-4060-b506-5d5
b4ede7985 ro quiet splash
initrd		/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=66e6abb9-66cf-4060-b506-5d5
b4ede7985 ro single
initrd		/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd2,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Windows NT/2000/XP
root		(hd0,4)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda6
title		Windows NT/2000/XP
root		(hd0,5)
savedefault
makeactive
chainloader	+1

---

### Post by Th3Professor on 2008-11-22
> **hubiedo said:**
> Th3, thanks for all the help.

Sure thing.

> **hubiedo said:**
> ...will the renumber my linux drive (hd2) to hd0 when i remove the original hd0 and hd1?

The hard drive label depends partially on how you set up the drives via fdisk and grub.

> **hubiedo said:**
> ...right now i plan to remove sdb first and see how it goes but even then if i mess up the grub or device.map files it wouldnt boot so maybe i should do both at once. what do you think?

Well, it sounds like you might be bouncing some ideas back and forth - how to go about this - if you are unsure of anything the safest bet is always to start fresh from the top.

> **hubiedo said:**
> ...these two drives are going into a new bu computer for my office and i really dont need to fdisk them. i intend to only have the sdc / hd2 left on my linux box. any comments or suggestions?

Perhaps what may determine whether or not you need to make any adjustments in the set-up via fdisk will be if you believe you need to make a change in MBR (or any similar top-level hard drive changes), which will also more than likely require grub changes. On the other hand, if you make changes in grub, you may need to make changes via fdisk. At the very least, you'll need to flag a new boot via fdisk.

> **hubiedo said:**
> 
root@hjk-linux:/boot/grub# more device.map
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
root@hjk-linux:/boot/grub# more menu.lst
...
title        Ubuntu 8.04.1, kernel 2.6.24-21-generic
root        (hd2,0)
...
title        Microsoft Windows 2000 Professional
root        (hd0,0)
...
title        Windows NT/2000/XP
root        (hd0,4)
...
title        Windows NT/2000/XP
root        (hd0,5)


Clear something up if ya could please :) ...did you mean you intend on removing Windows 2000 *only* or all Windows operating systems?

I'm going to make a hunch... that you have 1 Windows OS running, on the current "hd0,0" and the "hd0,4" and "hd0,5" are partitions set aside for storage/apps/etc. for use with that 1 Windows OS.

Do you still plan on using the hard drives?

Yes = don't remove them. ;)
No = remove them.

If yes, also remove the Win-related entries from grub. You can set them up for use with *nix systems via... yep... fdisk. Though there are other programs that do that too.

If no, also remove (still) the Win-related entries from grub.

On another note, let's put everything aside that you have right now and consider this:

What specifically would you like to have set up on the computer?

:)

We can work something out from there.

EDIT:
You might also consider using LVM. I recently set up 3 of my 4 hard drives with a combo RAID5+LVM, it is working beautifully. :D My remaining hard drive houses operating systems, apps, temp storage, etc. and the 3 drives grouped together are primary storage with flexible "partitions" (volume management) and extra security (RAID5) in case a hard drive dies or fritzs out on me. When you set up hard drives you need to decide on things like... if you would like to partition them... what kind of file systems (or other) you would like to use on them... and similar.

How would you like to use that computer?

---

### Post by hubiedo on 2008-11-24
th3,

thanks for all the info and help. i have successfully removed 2 hd with all windows os & partitions etc. i am on linux only on my desktop now. i edited the grub etc. and it worked out fine.

---

### Post by Th3Professor on 2008-11-25
> **hubiedo said:**
> th3,

thanks for all the info and help. i have successfully removed 2 hd with all windows os & partitions etc. i am on linux only on my desktop now. i edited the grub etc. and it worked out fine.

That's excellent news! :D I'm glad to hear it. Rock on.

:guitar:

---

