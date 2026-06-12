---
title: "Problem Dual Booting with Debian-Lenny"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by CMJ Tech on 2009-04-23
I have been struggling trying to setup a dual boot with Debian.  I am currently running 7.10 installed on 20GB IDE. I ran the install for Debian and set it up on my second hard drive 10GB IDE.  The 20GB is set as primary and the 10GB slave on the same IDE channel.  after the install completes and I reboot the system I get Error 21.  I used my Ultimate Boot CD to try and repair the grub.  Now I get to the menu and I see both 7.10 and debian listed.  7.10 boots up fine.  When I select Debian I get the Error 21 again.  I have read " Reconfiguring the MBR for Multiple Boot Installations"  and "Installing Multiple Linux Distribution on a Single Machine" by Whil Hentzen but I cannot figure out where my problem is.
Any assistance I can get would be appreciated.

The following is the output from :sudo fdisk -l
Disk /dev/hda: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d4b6d4b

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2422    19454683+  83  Linux
/dev/hda2            2423        2491      554242+   5  Extended
/dev/hda5            2423        2491      554211   82  Linux swap / Solaris

Disk /dev/hdb: 10.2 GB, 10246569984 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb84238e1

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1187     9534546   83  Linux
/dev/hdb2            1188        1245      465885    5  Extended
/dev/hdb5            1188        1245      465853+  82  Linux swap / Solaris


Here is my menu.1st contents in grub on 20GB drive:
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
timeout		15

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
# kopt=root=UUID=668e4172-535b-4472-b0a9-07f0948815ed ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=668e4172-535b-4472-b0a9-07f0948815ed ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=668e4172-535b-4472-b0a9-07f0948815ed ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Debian GNU/Linux, kernel 2.6.26-2-486 (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.26-2-486 root=/dev/hdb1 ro quiet 
initrd		/boot/initrd.img-2.6.26-2-486
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Debian GNU/Linux, kernel 2.6.26-2-486 (single-user mode) (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.26-2-486 root=/dev/hdb1 ro single 
initrd		/boot/initrd.img-2.6.26-2-486
savedefault
boot



title UNetbootin
root (hd0,0)
kernel  /boot/ubnkern 
initrd /boot/ubninit 
boot


Here is the menu.1st contains from grub on 10GB drive:
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/hdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=quiet

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title		Debian GNU/Linux, kernel 2.6.26-2-486
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.26-2-486 root=/dev/hdb1 ro quiet
initrd		/boot/initrd.img-2.6.26-2-486

title		Debian GNU/Linux, kernel 2.6.26-2-486 (single-user mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.26-2-486 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.26-2-486

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=668e4172-535b-4472-b0a9-07f0948815ed ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=668e4172-535b-4472-b0a9-07f0948815ed ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu 7.10, memtest86+ (on /dev/hda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


Thanks in advance!

---

### Post by tommcd on 2009-04-23
First off, Ubuntu 7.10 has reached end of life, and is no longer supported.
[http://www.ubuntu.com/news/ubuntu-7.10-eol](http://www.ubuntu.com/news/ubuntu-7.10-eol)
It looks like you have Ubuntu's grub installed to the mbr of the 20GB master drive; and Debian's grub installed to the mbr of the 10GB slave drive. Is that correct?
The best way to deal with this would be to do a clean install of Ubuntu 8.04, 8.10, or 9.04 on the 20GB master drive. Hopefully, when you install grub to the mbr of the 20GB drive it will correctly add an entry for Debian on the 10GB drive.
If it does not, then just add this to the end of Ubuntu's grub menu.lst to boot Debian on the 10GB drive:
```

title Debian-Lenny
root (hd1,0)
chainloader +1

```
Don't remove the automatically created entry for Debian in Ubuntu's menu.lst until you are sure the chainload entry works.

---

### Post by CMJ Tech on 2009-04-23
Thanks tommcd,
Yes you are correct.  7.10 was installed first and when I ran the install for Debian it installed grub to the MBR of the 10GB.  During the install I did select to use the MBR on the 20GB. So I thought.  I ran the install for Debian twice before I posted.  
I know about the end of life with 7.10 .  I started with 8.10 but had problems with my display drivers with my system.  Next, I tried to upgrade to 9.04 to see if that would corret my display issue but after the reboot my system would not boot.  Tried to reinstall 8.10 and all of a sudden my CD drive would not read the ISO I burned.  After many  failed tries at burning a new ISO, I decided to try an 7.10 disk I burned a while back and it worked.   

I will take your suggestion install 8.04 clean and see if that corrects the problem.

Thanks again!

---

### Post by tommcd on 2009-04-23
You should not continue to run an unsupported version of Ubuntu.
If you can not get any version of Ubuntu working on the 20GB drive, you could just switch drives and make the 10GB master and the 20GB slave. You output of fdisk indicates that /dev/sdb1 on the 10GB drive is set to be bootable, and Debian's grub is installed to the mbr of the 10GB drive. So making that drive master should boot Debian just fine. 
Then you can work on trying to get Ubuntu, or some other distro perhaps, working on the 20GB drive.

---

### Post by CMJ Tech on 2009-04-23
> **tommcd said:**
> You should not continue to run an unsupported version of Ubuntu.
If you can not get any version of Ubuntu working on the 20GB drive, you could just switch drives and make the 10GB master and the 20GB slave. You output of fdisk indicates that /dev/sdb1 on the 10GB drive is set to be bootable, and Debian's grub is installed to the mbr of the 10GB drive. So making that drive master should boot Debian just fine. 
Then you can work on trying to get Ubuntu, or some other distro perhaps, working on the 20GB drive.

Ok, Thanks!:)
That will be my next step if I am not able to get a more current version of Ubuntu working on the 20GB drive.

---

### Post by CMJ Tech on 2009-04-23
Just wanted to update on how I solved this problem.

While I downloading the ISO for 8.04 I decided to try to reinstall Debian again.  But this time I re-partitioned the 20GB drive and installed Debian in the free space.  After install completed and the system rebooted I was able to boot into both debian and ubuntu.  The new grub also was picked up the previous install of debian on the 10GB drive.  
Also when I ran debian install this third time, I selected not to connect to a mirror.  I just install straight for the CD.

Thanks again tommcd for your help!

---

