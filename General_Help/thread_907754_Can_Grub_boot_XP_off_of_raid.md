---
title: "Can Grub boot XP off of raid?"
date: 2008-09-01
forum: General Help
---

### Post by jabrumbaugh on 2008-09-01
I'm new to the whole linux thing in general, and on reference of a friend decided to try Ubuntu out.  I had to fiddle around with editing grub to get it to boot the Ubuntu, but after changing the hard drive from (1,0) to (0,0) I got it going.  Of course I installed the ATI drivers, and it screwed the system and I had to reinstall again. But thats not really important 

For a couple years I've been booting XP off of a raid 0 array on a Sil 1334 SATA controller onboard my nforce 2 board.  I added an old 20Gb HD as the master on my secondary IDE channel, and installed Ubuntu 8.04.  Ubuntu doesn't detect the raid array, which doesn't surprise me, but I can't seem to get grub to let me boot my XP system, which is on the raid.  Grub gave me no option to choose XP.  I attempted to edit in an XP option, but i've apparently failed.  I get the choice now in the option menu, but when I choose windows, is says "Starting up"  but then gives a few random artifact looking things and freezes.  I've tried to remove the ubuntu HD physically, but when my PC gets to the point where it should boot windows, it doesn't do anything, presumably because it can't find an OS to boot.  I've got no problem using Ubuntu for surfing the web, etc, but I'm kinda fearful that I've screwed the pooch here and have lsot everything on my raid.   S

I ran "sudo fdisk -lu" and got this 
> Disk /dev/sda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders, total 39876480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000f186

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    38122244    19061091   83  Linux
/dev/sda2        38122245    39873329      875542+   5  Extended
/dev/sda5        38122308    39873329      875511   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x840fc00b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  3892460094  2305310731  1353908967   1e  Hidden W95 FAT16 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       47462  3127294309  1563623424   80  Old Minix
Partition 2 does not end on cylinder boundary.
/dev/sdb3      2232401931  1047904328  1555234847   e8  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdb4   *  1711823336  3927448050  1107812357+  66  Unknown
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f6f94d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   625153409   312576673+   7  HPFS/NTFS


So ubuntu sees all my disks, which is ok, but its says some odd things about the one 160gb drive.  I don't really know what to make of my dilemma, but I've been searching for about 6 hours now trying to get this figured out, and I'm out of ideas.  

If anyone can help me fix this that would be great.  If not, I"m prolly gonna cry, lol.

---

### Post by caljohnsmith on 2008-09-01
So is the Windows you want to boot on sdc1? Is your RAID array software or hardware driven? Is sdb your RAID array? And also, please post your Grub's menu.lst:
```
cat /boot/grub/menu.lst
```

---

### Post by jabrumbaugh on 2008-09-01
My raid array is one of those that was advertised as hardware, but it uses CPU cycles to run.  My raid array is 2 160GB drives, so presumably sdb and sdc.  The odd thing is they are raid 0 set to appear like one 320gb drive.  

menu.lst:
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=801ecd95-de04-48ea-aaac-6502d432e753 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=801ecd95-de04-48ea-aaac-6502d432e753 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=801ecd95-de04-48ea-aaac-6502d432e753 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title           Windows CP
root            (hd1,0)
savedefault
makeactive
chainloader     +1 
### END DEBIAN AUTOMAGIC KERNELS LIST


"Windows CP" is a typo for XP, lol

---

### Post by caljohnsmith on 2008-09-01
It's hard to say with your RAID array, but I think one of the following will work to boot your Windows if you don't have an entirely RAID-related problem. Try adding both to your menu.lst and see if either works on start up:
```
title Windows XP (hd1)
root (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
savedefault
makeactive
chainloader +1 

title Windows XP (hd2)
root (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
savedefault
makeactive
chainloader +1 
```
And in case you don't know how to edit your menu.lst, one way to do it is:
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by jabrumbaugh on 2008-09-01
The Hd1 option says "starting up" and then a line of gibberish, and then nothing happens.  

The Hd2 option gives an error about the disk not existing.

---

### Post by caljohnsmith on 2008-09-01
Since neither of those two options worked to boot Windows, I think there is a high probability that the problem is with your RAID set up and not with Grub. Like you originally said:
[QUOTE=jabrumbaugh]Ubuntu doesn't detect the raid array, which doesn't surprise me, but I can't seem to get grub to let me boot my XP system, which is on the raid.[/QUOTE]
I have very little experience with RAID configurations, so I won't be able to help you there. Good luck though, sorry I can't be of more assistance.

---

### Post by jabrumbaugh on 2008-09-01
Hey, it was a good effort.  Thanks for trying.  Can you give me some insight as to what the map command in the code does?

---

### Post by caljohnsmith on 2008-09-01
> **jabrumbaugh said:**
> Hey, it was a good effort.  Thanks for trying.  Can you give me some insight as to what the map command in the code does?
Sure, the map command is critical to use whenever you try to boot a Windows OS from a HDD that is not first in the BIOS boot order. That's because Windows can't be booted from anything but the boot HDD (the HDD first in the BIOS boot order). So essentially what the map command does is map whatever HDD Windows is on to look like the first HDD in the BIOS boot order (which is (hd0) in Grub's Convoluted World). That way Grub "fools" Windows into thinking it is on the boot HDD, and Windows will boot.

---

