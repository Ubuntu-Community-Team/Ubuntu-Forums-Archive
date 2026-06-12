---
title: "[SOLVED] grub hangs after removing external hdd"
date: 2008-02-09
forum: Hardware &amp; Laptops
---

### Post by BigBurner on 2008-02-09
Here is my situation ....

I installed Ubuntu to an external HDD (USB) and on my internal HDD, I have a windows XP SP2.

currently both are working fine and Ubuntu rocks. :guitar:

The problem is when I removed my external HDD grub waits with Error 21, mostly bcoz it is looking for menu.lst on the external HDD. supposedly grub is installed on my Internal HDD (and replaced MBR)

now since this is a laptop, I can't carry my exteranl HDD every where with me. And need to carry around a lot.

Can please some one give me a solution to this, ie a way I can boot to XP when my external  HDD is not connected. (Also without having to lose Ubuntu :) )

I should tell you that my laptop does not have a floppy drive and can boot from an external HDD. Also I'm a newbie to Linux, so please be gentle on me :lolflag:

---

### Post by buntu_Geek on 2008-02-16
The problem is that now your MBR is pointing to the grub in your external HDD and hence is showing you the Error 21 when MBR is unable to find the stage1(that is the first part of your GRUB) of your GRUB.

Normally there will be a grub installed with every ubuntu's filesystem (/boot/grub) on your harddisk so you also must have a GRUB in your internal HDD.

In order to point your MBR to the Grub in your internal HDD you have to install the grub ( with your external HDD removed) from your live CD.

The procedure is simple...type the following in the terminal:
```

sudo grub

```
YOu will get grub> prompt, then
```

grub> find /boot/grub/stage1

```
This command gives the partition where the stage one of your grub is (hd?,?), then use this for the following commmand(replacing the ? marks):
```

grub> root (hd?,?) #Hit the <Enter> key

grub> setup (hd0) #Hit <Enter> key

grub> quit #Hit <Enter> key, quits grub

```

NOTE: All these must be carried out without the external HDD plugged in...

---

### Post by BigBurner on 2008-03-06
Thanks Buntu_geek, :KS

Sorry I could'nt reply earlier coz I was on a holiday away from my laptop and Internet connection :)

Now I'm back, But in the mean time I had to do FixMBR on my XP laptop since I had to carry along to work.

But I'm going to use your suggestion to install GRUB on my external (yes external) HDD and boot from it, when I need to use Ubuntu. Hopefully the steps would still apply. 

So the plan is to have my laptop directly boot on to XP (using MBR) when external HDD is not connected and when i connect my external HDD I can boot in to Ubutu.

Hopefully this should be possible.

Thanks again.
BigBurner.

---

### Post by buntu_Geek on 2008-03-06
But there is one problem.....

If you dont have any ubuntu on your internal... then there will not be any grub in your internal HDD....
This means the " find /boot/grub/stage1" will not return anything when the external HDD removed....

I think you can understand me...

But to solve this ... its not necessary to install another ubuntu on u r internal but a boot loader called SuperGrubDisk..... i am not sure about the procedure.. but its a small file to download... and there are many howtos to it....

Hope you understand what i say....
If not dont hesitate to ping me.... :D

---

### Post by hydroparasite on 2008-03-07
hi i am loooking for the same setup that ubuntu boots on external hdd detection ,, n windows when no external hdd is connected ! is this possible cause i do not wanna screw up the Rescue n Recovery feature on my laptop by installing onto my internal laptop hdd..??

please help i already have ubuntu on my external hdd but cant boot from it and get error 21  or 22 cant recall.

---

### Post by buntu_Geek on 2008-03-08
The problem is that the boot loader (grub) is in your external hdd.... so with out it the grub doenst load .. thus there is an error message...

In order to solve this you can install a bootloader in your internal hdd (SuperGrubDisk)
with both ur ubuntu (from external hdd) and windows(internal) in your boot menu..

suppose you boot u r laptop with out external hdd and try to chose ubuntu, it will not load u r ubuntu.... but u r windows will load with out external hdd...

You can find a howto for installing SuperGrubDisk ... its quite simple...

Hope that helps you....

---

### Post by BigBurner on 2008-03-10
Hy buntu_Geek,

I followed your instructions, and tried to install grub on my external HDD.
And well it did install it
```

grub> find /boot/grub/stage1
 (hd1,1)

grub> root (hd1,1)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+17 p (hd1,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> quit

```

And now when I have my external HDD connected it boots using Grub and displays the list of OS's.
Fine, till now. But then, when I select any OS it give me "Error 15 File not found".

It displays the list of OS's, so I guess it can find **menu.lst** and then something goes wrong.

Here the output of 
```
sudo  fdisk -l
```

```
ubuntu@ubuntu:/dev$ sudo  fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8f0ffa4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     5116671   12  Compaq diagnostics
/dev/sda2   *         638        7583    55793745    c  W95 FAT32 (LBA)
/dev/sda3            7584       14593    56307825    c  W95 FAT32 (LBA)

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        8586    68967013+   c  W95 FAT32 (LBA)
/dev/sdb2   *        8587        9369     6289447+  83  Linux
/dev/sdb3            9370        9729     2891700    5  Extended
/dev/sdb5            9370        9729     2891668+  82  Linux swap / Solaris
ubuntu@ubuntu:/dev$ 

```

Here is the menu.lst
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
default		5

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
# kopt=root=UUID=b15789d5-89d4-4597-95bd-b43a424d4300 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b15789d5-89d4-4597-95bd-b43a424d4300 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b15789d5-89d4-4597-95bd-b43a424d4300 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


```

As you can see the hd? entries seems to be correct, Also I have checked the files in menu.lst are present in the location (I could give you the ls of the directory)

Now, I could'nt get what the /etc/fstab is, But I have a feeling that something is wrong in it. How do get to see its contents ? is it just a txt file or is there a command for it.

Thanks,

BigBurner.

**PS** I can't install grub to my internal HDD coz, it is all NTFS. And I don't want to touch it with GParted as the laptop(with windows) is very critical for my existence :lolflag:

---

### Post by buntu_Geek on 2008-03-10
The fstab is just a text file only... and gives u the mounting information when your OS is loaded....

So i think there is no problem with those... but i also have the feeling that the UUIDs in the menu.lst and those in the fstab might differ .. (if you a re fortunate... )... check that...
else... then seriously i dunno whats the problem...

---

### Post by buntu_Geek on 2008-03-11
The point is...
your grub is working fine....
Coz, you have all the menus coming  and there is no problem for loading your os...

But the pointers (path) to the kernel is wrong according to your results..(file not found..)

Double check the partitions ... 
and
Are you sure that all menus are not working..??

Other doubts i have are:

> Are you booting from the external hdd ( boot option= USB)...
> Linux partition have the boot flag.... its not necessary.... try to remove the boot flag... through partition editor..( try this finally after trying out the other options....

---

### Post by Ozzz on 2008-03-12
I was having the same issues and was running a separate thread on it. I finally got things working as both you and I want them to. Feel free to read thru my post, might help you out.
[http://http://ubuntuforums.org/showthread.php?t=718904&page=3]("http://http://ubuntuforums.org/showthread.php?t=718904&page=3")

Good luck

---

### Post by BigBurner on 2008-03-13
Here is the content of my fstab file
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=b15789d5-89d4-4597-95bd-b43a424d4300 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=9b5771be-7435-4a97-824a-a513787cd2f2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```
so the UUID are matching with the menu.lst file above.

I try removing the boot flag from the ext hdd and see if it works.
Else, I would reinstall Ubuntu on external hdd again :confused:

Cheers guys !!

---

### Post by BigBurner on 2008-03-14
**I finally got it working !!**:)

It was pretty simple, 
When I boot from the USB HDD, it gets labelled as as hd0 and the internal HDD gets labelled as hd1. which is excatly the opposite of what you would see when you boot from a live CD.

So I changed the menu.lst to reflect the changes and also had to do the map (hd0) (hd1) thingy for windows to work.
And Voila !! I could boot into Ubuntu with my external HHD without making _any_ changes to my internal HDD. And I can boot into windows too with external HDD or internal HDD.

[COLOR="Red"]Now, I still have some questions.[/COLOR]
when Ubuntu boots, the boot screen shows a load of number (possibly cluster counts) and then says
Not Automatically fixing this ....  Boot sector differs with last backup
I hope this thing won't touch my Internal HDD. (I have booted into windows and checked that it is fine, but still I'm concerned)

Buntu_geek,
Just to keep you updated. I tried removing the boot flag from the ext HDD and it did'nt work.

Again, thanks everyone for the help. I would have given up quite early,  if you guys would have replied to this post. :guitar:

If anyone has questions regarding this thing, do not hesitate to ping me.

---

