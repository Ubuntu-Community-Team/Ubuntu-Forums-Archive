---
title: "Other OS entries in GRUB"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by Messyhair42 on 2009-08-03
I have gone back to a dual boot machine, primarily i use Ubuntu 9.04 on /dev/sdb SCSI 2 (0,1,0) and i recently added Windows 7 to /dev/sda SCSI 1 (0,0,0) and i want to get the entry for windows into the GRUB Menu. I'm also attempting to install Ubuntu 8.04 or Fedora 10 on /dev/sda as well, but i want everything to be controlled with the GRUB on /dev/sdb because that's my primary drive and OS. currently I'm switching between Ubuntu and Windows via BIOS because they're on separate physical hard drives

---

### Post by Messyhair42 on 2009-08-03
I ended up getting Fedora 10 installed besides windows 7, i can boot each but it takes more work than grub. what changes do i need to make to /grub/menu/lst to get all the entries in there?

---

### Post by confused57 on 2009-08-03
Boot into Ubuntu 9.04 on sdb, post the output of:
```
sudo fdisk -l
```

If Windows 7 is on the first partition of sda, a grub entry similar to this would work:
```
title              Windows XP
root               (hd1,0)
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

For Fedora, a configfile entry should work:
```
title    Fedora
root   (hd1,2)/boot/grub/menu.lst
```

To edit grub:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

---

### Post by Messyhair42 on 2009-08-03
```
sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x622b854a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        8924    71577600    7  HPFS/NTFS
/dev/sda3            8925        8936       96390   83  Linux
/dev/sda4            8937       19457    84509932+   5  Extended
/dev/sda5            8937        9191     2048256   82  Linux swap / Solaris
/dev/sda6            9192        9701     4096543+  83  Linux
/dev/sda7            9702       13526    30724281   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007fe0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         267     2144646   83  Linux
/dev/sdb2             268      117954   945320827+   5  Extended
/dev/sdb3          117955      121602    29294592    6  FAT16
/dev/sdb5             268         753     3903763+  82  Linux swap / Solaris
/dev/sdb6             754        1239     3903763+  83  Linux
/dev/sdb7            1240        1506     2144646   83  Linux
/dev/sdb8            1507        1542      289138+  83  Linux
/dev/sdb9            1543      117954   935079358+  83  Linux

Disk /dev/sdc: 4007 MB, 4007657472 bytes
16 heads, 32 sectors/track, 15288 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x0002489b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       15285     3912944   83  Linux

```

/dev/sdb contains Ubuntu 9.04
/dev/sda1&2 are Windows
/dev/sda3-7 are Fedora with /dev/sda3 containing the /boot partition of Fedora
/dev/sdc is a flash drive with Ubuntu 9.04 that is only occasionally attached or used

/grub/menu.lst
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
# kopt=root=UUID=a882d27e-54a7-4e81-ad3e-beeb093307c7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a882d27e-54a7-4e81-ad3e-beeb093307c7

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
# howmany=2

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		a882d27e-54a7-4e81-ad3e-beeb093307c7
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=a882d27e-54a7-4e81-ad3e-beeb093307c7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		a882d27e-54a7-4e81-ad3e-beeb093307c7
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=a882d27e-54a7-4e81-ad3e-beeb093307c7 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		a882d27e-54a7-4e81-ad3e-beeb093307c7
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=a882d27e-54a7-4e81-ad3e-beeb093307c7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		a882d27e-54a7-4e81-ad3e-beeb093307c7
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=a882d27e-54a7-4e81-ad3e-beeb093307c7 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, memtest86+
uuid		a882d27e-54a7-4e81-ad3e-beeb093307c7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, kernel 2.6.27-14-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=30332a03-75e4-4749-a8ee-f80df161c6ba ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=30332a03-75e4-4749-a8ee-f80df161c6ba ro single 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=30332a03-75e4-4749-a8ee-f80df161c6ba ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=30332a03-75e4-4749-a8ee-f80df161c6ba ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5f0e114a-9fd5-45f6-9e9a-9200abadfbe1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=5f0e114a-9fd5-45f6-9e9a-9200abadfbe1 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 9.04, memtest86+ (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

the entry for Ubuntu 8.10 on /dev/sda1 was and old installation on the drive i formatted to install windows so i doubt i need that entry anymore and /dev/sdc1 is the flash drive installation

---

### Post by confused57 on 2009-08-04
I believe the entry I gave you previously will work for Windows 7, but your Fedora entry will be:
```
title     Fedora 10 (or whatever you want to name it)
configfile      (hd1,2)/boot/grub/grub.conf
```
this will work, if Fedora uses grub with menu.lst(it may use grub.conf, instead).

First backup & edit your menu.lst, following the directions I gave you previously.  You can then delete the Ubuntu 8.10 boot entries & replace them with your Windows 7 & Fedora boot entries.  Quit & save.  If Fedora doesn't work, you might want to boot into Fedora from the sda drive & post it's menu.lst(or grub.conf).

Note:  I see Windows 7 created a 100 Mb boot partiton...you can avoid this if you create a NTSF partition before installing Windows 7.  Then during installation, format again, continue with the installation.

Changed Fedora entry from menu.lst to grub.conf.

---

### Post by Messyhair42 on 2009-08-04
This is what my menu.lst file looks like now, or at least the new entries
```
title		Other operating systems:
root


title              Windows 7 (on /dev/sda1)
root               (hd1,0)
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

title     Fedora 10 (on /dev/sda3)
configfile      (hd1,2)/boot/grub/grub.conf
```

windows works, but Fedora doesn't (at least not from the GRUB menu) I get "Error 15 File not Found" and it returns me to the grub menu. i might just need to change the numbers, but i'm not sure of anything.

here is the /dev/sda1 portion of [sudo fdisk -l]
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        8924    71577600    7  HPFS/NTFS
/dev/sda3            8925        8936       96390   83  Linux
/dev/sda4            8937       19457    84509932+   5  Extended
/dev/sda5            8937        9191     2048256   82  Linux swap / Solaris
/dev/sda6            9192        9701     4096543+  83  Linux
/dev/sda7            9702       13526    30724281   83  Linux

```

and a screenshot from gparted

also Fedora has its own instance of GRUB, can i add Ubuntu and windows entries to that instance in case something goes wrong? would i do better asking Fedora people?

edit: here is the menu.lst file from my instance of Fedora
```
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/sda6
#          initrd /initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,2)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.27.5-117.fc10.i686)
	root (hd0,2)
	kernel /vmlinuz-2.6.27.5-117.fc10.i686 ro root=UUID=a302e028-637f-4352-8de5-db38dec69183 rhgb quiet
	initrd /initrd-2.6.27.5-117.fc10.i686.img
title Other
	rootnoverify (hd0,0)
	chainloader +1
```

---

### Post by confused57 on 2009-08-05
Did you try the configfile with menu.lst?:
```
title  Fedora 10
configfile  (hd1,2)/boot/grub/menu.lst
```

You might want to try asking in the Fedora forum & you can check
back if you don't get a solution from there.  I've never used Fedora, so can't help you with specifics.

Added:  This may not work, but since you have a separate boot partition:
```
title   Fedora 10
configfile    (hd1,2)/grub/grub.conf
```

---

### Post by Messyhair42 on 2009-08-05
the first code didn't change anything...error 15
the second instance of code did change something, it says error 17 cannont mount the selected partition, and takes me to something like Fedora's grub menu, it only has Fedora's entry which takes me back to error 17, and "other," which, if i enter through BIOS, takes me into Windows 7. I say it's like fedora's grub menu only because it has the two entries, it doesn't have a background image if i boot to the other HD.
looking back at my screenshot of Gparted should i change the (hd1,2) to (hd1,3) since that's where my boot partiton for fedora?

---

### Post by confused57 on 2009-08-05
I'm not sure why the configfile entry is giving grub error 17, but you can try copying & pasting your grub.conf Fedora entry into Ubuntu's menu.lst:
```
title Fedora (2.6.27.5-117.fc10.i686)
	root (hd1,2)
	kernel /vmlinuz-2.6.27.5-117.fc10.i686 ro root=UUID=a302e028-637f-4352-8de5-db38dec69183 rhgb quiet
	initrd /initrd-2.6.27.5-117.fc10.i686.img
```

Change root (hd0,2) to (hd1,2), as I've done above.

This should give you some idea of grub's numbering system:
[http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html)
(hd1,2) refers to the 2nd hard drive, 3rd partition.

---

### Post by Messyhair42 on 2009-08-05
got it, i copied from grub.config (which was a task in an of itself) and changed the hd(X,X) value, eventually this is what worked
```
title Fedora 10 (on /dev/sda3)
	root (hd1,2)
	kernel /vmlinuz-2.6.27.5-117.fc10.i686 ro root=UUID=a302e028-637f-4352-8de5-db38dec69183 rhgb quiet
	initrd /initrd-2.6.27.5-117.fc10.i686.img

```

i'll try something similar with fedora's grub file.

---

### Post by confused57 on 2009-08-05
I thought using the entry from Fedora's grub.conf would work, you really could have just copied & pasted the entry that I listed in my previous reply or the grub.conf from one of your earlier replies.  This entry will not automatically update, if Fedora updates the kernel, you'll need to copy & paste the new kernel entry into your Ubuntu 9.04 menu.lst.  In fact, you could copy & paste the new grub.conf entry as a reply in this thread, then boot into Ubuntu, copy & paste from here to your menu.lst.

---

