---
title: "[SOLVED] Booting issues with GRUB error 17"
date: 2008-10-28
forum: General Help
---

### Post by AvvY on 2008-10-28
I just installed a new fan to my graphics card which involved pulling my system apart to get to it etc (I built the computer so I know what I'm doing), but when I went to boot up I started having issues. Firstly BIOS went a bit funny, but after checking all the hardware connections it seemed Grub was the problem. I booted the live CD and everything is running fine, so I know the system is all good, and I can see all my drives with their info.

I reinstalled GRUB with the live CD, and now it comes up when I boot the computer, however it is now giving me an Error 17 cannot mount selected partition. I have checked and it seems to be all correct (menu.lst) etc. I ran a file system check and there were no problems.

I'm not sure what would have caused all this, however it seems like I just need to get Grub to boot the partition and it should all be good again.

Thanx

---

### Post by caljohnsmith on 2008-10-28
In some special circumstances, there have been cases in the forums where people were able to solve Grub error 17 by changing their BIOS settings for the HDD or even changing their HDD cabling; I'm wondering if that might be your issue since it sounds like you've all ready checked the obvious. From your Live CD, how about posting:
```
sudo fdisk -lu
sudo blkid
```
Figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
Please post that, and we can work from there if you want. :)

---

### Post by AvvY on 2008-10-28
Thanx for the advice. Here are the outputs of the commands you suggested. 

sdc1 is the / partition. I have /home as sdc2 so if it comes down to formatting it's not a drama - I know it's somewhat drastic (especially if it's a simple fix) but since 8.10 is out in a day or so, perhaps it's a good excuse? Although it'd be nice not to have to worry about all that. Thanx again

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05de05dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   390716864   195358401    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7b747b74

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   390716864   195358401    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x70407040

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63    39070079    19535008+  83  Linux
/dev/sdc2        39070080   117194174    39062047+  83  Linux
/dev/sdc3       117194175   146496734    14651280    b  W95 FAT32
/dev/sdc4       146496735   156296384     4899825   82  Linux swap / Solaris

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xadc5adc5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   234436544   117218241    7  HPFS/NTFS

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0abf66ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63   488392064   244196001    7  HPFS/NTFS

```
```
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="825834E15834D59F" LABEL="Data 2" TYPE="ntfs" 
/dev/sdb1: UUID="94B4E17BB4E1606A" LABEL="Data 1" TYPE="ntfs" 
/dev/sdc1: UUID="291c01cc-1038-4d8d-8176-275ef65950a8" TYPE="ext3" 
/dev/sdc2: UUID="4f436acc-21cd-42bf-94b4-537c72ddb6cf" TYPE="ext3" 
/dev/sdc3: UUID="C5E1-FCF3" TYPE="vfat" 
/dev/sdc4: UUID="b70e376f-aebd-49aa-9e52-4c9c04334e2a" TYPE="swap" 
/dev/sdd1: UUID="988CAFDD8CAFB3E2" LABEL="Backup pre rebuild" TYPE="ntfs" 
/dev/sde1: UUID="B236921F3691E49F" LABEL="Media 1" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

```
```
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
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
# kopt=root=UUID=291c01cc-1038-4d8d-8176-275ef65950a8 ro

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
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=291c01cc-1038-4d8d-8176-275ef65950a8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=291c01cc-1038-4d8d-8176-275ef65950a8 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=291c01cc-1038-4d8d-8176-275ef65950a8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=291c01cc-1038-4d8d-8176-275ef65950a8 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by caljohnsmith on 2008-10-28
It looks like your Grub error 17 might possibly be easy to fix; go ahead and reboot again, and when you get the Grub menu, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hd2,0)", press "e" to edit it, change it to "root (hd0,0)", press return to save the change, then press "b" to boot. If that doesn't work, then also try (hd1,0), (hd3,0) and (hd4,0). One of those combinations should work if you don't have a more serious issue. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent. Let me know how it goes. :)

---

### Post by AvvY on 2008-10-28
Of course! I had some feeling that wasn't right but couldn't figure it out. Changing it to (hd0,0) was the trick! Thanx heaps for this. I'm annoyed I forgot about this, but thanx for helping me figure out it was a simple fix and not in need for anything drastic.

Once again the user support of the ubuntuforums comes through on top!

---

### Post by caljohnsmith on 2008-10-28
I'm really glad too that it turned out to be a simple problem. Cheers and have fun Ubuntu-ing. :)

---

### Post by 4kfooler on 2008-10-28
I HAD the same problem.............................

---

