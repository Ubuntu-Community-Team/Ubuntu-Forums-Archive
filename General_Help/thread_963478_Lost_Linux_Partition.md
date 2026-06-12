---
title: "Lost Linux Partition"
date: 2008-10-30
forum: General Help
---

### Post by DuXati on 2008-10-30
Dear all,

I've got a serious error with my hard disk partitions. My hard disk is split into two partitions: a Ubuntu partition (ext3 I presume) and a Windows partion (NTFS), and the swap space for Ubuntu is on that disk too. Nothing was wrong with the system till yesterday:

When booting the system, GRUB fails, giving the 

```
GRUB Loading stage 1.5.
GRUB loading, please wait...
Error 17
```

message. So I booted from the Ubuntu Live cd to take a look at my /boot/grub/menu.lst. Than the real problem began to show: My Ubuntu partition wasn't mounted and a new disk appeared, named "1kB Media". Never seen this disk before... The Windows partition on the disk, does work correctly.

gparted does not list both partitions on the sda disk, while the Windows partition is mounted as sda2 and works. fdisk /dev/sda gives:

```
Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe22ce22c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5874    47182873+   7  HPFS/NTFS
/dev/sda2            5875        9843    31880992+   f  W95 Ext'd (LBA)
/dev/sda5   ?      206520      221875   123339962   78  Unknown
/dev/sda6            5875        9843    31880961   83  Linux

```

I thing sda2 is the former Ubuntu partition, but it is now a W95 system. On top of that, sda6 totally overlaps with sda2. What is going on and how do I fix it?

Possible cause: Yesterday I was trying to install Mandriva Linux on a now Eee laptop and I had to make a bootable usb stick with system type W95 using fdisk. Maybe I had a typo, making sda2 a W95 system? I didn't notice anything unusual until I rebooted the pc later on.

I really need some data from my home dir on the Ubuntu partition, does anyone know how to solve this?

I hope I gave some useful information about the problem. I don't really know how to put the problem in words, so if any more information is needed, please ask for it.

Thanks for reading this in the first place!

DuXati

---

### Post by PsychedelicReaction on 2008-10-30
Try Test Disk utility

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by caljohnsmith on 2008-10-30
sda2 is an "extended" partition, meaning that it is a container for your logical partition sda6; so it is perfectly normal that sda6 "overlaps" or is actually contained inside sda2. 

It looks like sda5 could be your Ubuntu partition, but it shouldn't be labeled sda5 unless it is part of your sda2 extended partition, which it currently isn't. And of course the other problem is that the file system for sda5 is "unknown", when it should be type "83" or "linux" if it is your Ubuntu partition. The other thing I notice is that you have a huge block of unused space right before the sda5 partition, so it could be that Ubuntu is hiding in that space. 

I would begin with PsychedelicReaction's advice and use testdisk to try and fix your partition table, and then you can maybe try and recover the sda5 Ubuntu partition. If you want help with testdisk, then first boot your Live CD, enable all your repositories in System > Admin > Software Sources, then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "proceed", Y/N depending on if you have any Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Post the output of that screen if you would like help recovering your Ubuntu partition. :)

---

### Post by DuXati on 2008-10-30
Thanks for the quick responses, guys!

With Test Disk, I managed to save the documents I was afraid to lose to an working disk. Nothing important is lost, and that is what I was hoping for!

But restoring the hard disks would be even better, so lets go for it :) The output from the deeper search is:

```
Disk /dev/sda - 81 GB / 76 GiB - CHS 9964 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  5873 254 63   94365747
D HPFS - NTFS           2550   1  1  9962 254 63  119089782
D FAT16 <32M            5874   0  1  5875 254 63      32130
D HPFS - NTFS           5874   1  1  9443 254 63   57351987 [Linux]
D Linux                 5874   2  1  9332 254 63   55568709
D Linux Swap            9333   0  1  9842 254 63    8193150
```

If I'me not mistaken, this says that all the partitions on the disk were deleted, no? In the partition named 'Linux' (not the one with '[Linux]' at the back), I was able to find the files I was looking for. That partition contains the former Ubuntu file system.

What to do next? 

Thanks again, you guys :guitar:

---

### Post by caljohnsmith on 2008-10-30
OK, based on your fdisk output and from what you have described, here is how I think you should mark your partitions:
```
Disk /dev/sda - 81 GB / 76 GiB - CHS 9964 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]*[/COLOR] HPFS - NTFS              0   1  1  5873 254 63   94365747
[COLOR="Red"]D[/COLOR] HPFS - NTFS           2550   1  1  9962 254 63  119089782
[COLOR="Red"]D[/COLOR] FAT16 <32M            5874   0  1  5875 254 63      32130
[COLOR="Red"]D[/COLOR] HPFS - NTFS           5874   1  1  9443 254 63   57351987 [Linux]
[COLOR="Red"]L[/COLOR] Linux                 5874   2  1  9332 254 63   55568709
[COLOR="Red"]L[/COLOR] Linux Swap            9333   0  1  9842 254 63    8193150
```
Note the asterisk * means primary bootable, and for your Linux partition above, I'm assuming that it will be logical or "L", but testdisk will only let you select L or P depending on whatever it originally was; so use whichever testdisk allows you to pick. The other partitions should be marked "D" for delete as shown above. Then use the "write" function to write the partition table (you might have to first press enter or something to get to the next screen). 

Next reboot, see if hopefully your drive boots again, but if not, post the output of "sudo fdisk -l" again and we can work from there. :)

---

### Post by DuXati on 2008-10-30
Yeeha, we made some very decent progress :popcorn:

After I did what you said, GRUB came up with another error: error 22. When booting the Ubuntu Live CD, I noticed that my old Ubuntu partition could be mounted and so could my Windows partition, which is very nice! So I googled the GRUB error and used the following commands:

```
sudo grub
grub> find /boot/grub/stage1
[INDENT](hd0,4)[/INDENT]
grub> root (hd0,4)
grub> setup(hd0)
grub> quit
```

This solved the GRUB error 22 and now I get the boot loader screen where I can choose which OS to boot. But there I hit another error. When loading my former Ubuntu installation, an error arose saying the location to boot from could not be found. The contents of my /boot/grub/menu.lst are given below. I'm not an expert at it, but nothing seems weird about that file. And here is the output of fdisk (only the part that contains information about sda):

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe22ce22c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5874    47182873+   7  HPFS/NTFS
/dev/sda2            5875        9333    27784386    f  W95 Ext'd (LBA)
/dev/sda3            9334        9843     4096575   82  Linux swap / Solaris
/dev/sda5            5875        9333    27784354+  83  Linux

```

sda2 overlaps completely with sda5, maybe this is causing the booting problems? 

Dunno what to do next :)

Menu.lst:

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
# kopt=root=UUID=b8b1cd3f-fbb6-4f9f-8e8f-56fe23912257 ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b8b1cd3f-fbb6-4f9f-8e8f-56fe23912257 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b8b1cd3f-fbb6-4f9f-8e8f-56fe23912257 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


```

---

### Post by caljohnsmith on 2008-10-30
OK, I definitely see at least one problem; just replace the (hd0,5) in all the ubuntu entries to use (hd0,4). So from your Live CD:
```
sudo mount /dev/sda5 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
Also do:
```
sudo blkid | grep sda5
```
And make sure the UUID for sda5 from the above command matches the UUID used in your Ubuntu entries:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		[COLOR="Blue"](hd0,4)[/COLOR]
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=[COLOR="Blue"]b8b1cd3f-fbb6-4f9f-8e8f-56fe23912257[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```
Also while you are at it, make sure to replace the "#groot=(hd0,5)" line with:
```
# groot=(hd0,4)
```
And if you change the UUID for the Ubuntu entries, you'll also need to change the "#kopt=root=UUID=<sda5 UUID>" line to use the correct UUID. Give that a shot and let me know how it goes.

---

### Post by DuXati on 2008-10-31
Works! I can boot Ubuntu again!

Question: how did you know the Ubuntu partition was at  (hd0,4) and not (hd0,5)? I googled menu.lst but could not find a clear answer to what this number should be and I guessed it should be the same as the X in sdaX. Apparently that was a wrong guess :)

Thanks, caljohnsmith, you saved the day =D>

---

### Post by caljohnsmith on 2008-10-31
> **DuXati said:**
> Works! I can boot Ubuntu again!

Question: how did you know the Ubuntu partition was at  (hd0,4) and not (hd0,5)? I googled menu.lst but could not find a clear answer to what this number should be and I guessed it should be the same as the X in sdaX. Apparently that was a wrong guess :)

Thanks, caljohnsmith, you saved the day =D>
Unfortunately, just to be confusing for all of us, in Grub's Convoluted World all numbering begins with 0 and not 1, so:
```
(hd0) = sda or 1st HDD
(hd0,0) = sda1 or 1st HDD, 1st partition
(hd0,1) = sda2 or 1st HDD, 2nd partition
(hd1) = sdb or 2nd HDD
(hd1,0) = sdb1 or 2nd HDD, 1st partition
...etc.
```
So sda5 is (hd0,4). If you want to learn more about Grub, here's some good resources:

[http://www.users.bigpond.net.au/hermanzone/p15.htm](http://www.users.bigpond.net.au/hermanzone/p15.htm)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

Anyway, glad it's all working; cheers and have fun Ubuntu-ing. :)

---

