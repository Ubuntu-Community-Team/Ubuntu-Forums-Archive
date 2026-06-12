---
title: "Missing GRUB"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by mayagrafix on 2009-04-24
My pc has two HD's, one for Windows Vista (HD0) and one for Ubuntu Linux (HD1). At boot the GRUB would appear and I could choose which OS I wanted.

Not satisfied with that set up, I installed a third OS (Windows XP) on HD0 in an already existing  small partition (10 GB)intended for recovery.

Unfortunately the XP install wiped out the GRUB that was on the MBR of HD0. 

So how do I install GRUB again on HD0 (the windows hard drives) and chainlink all 3 OS?

Thanks in advance for all your great help. :)

---

### Post by unutbu on 2009-04-24
This should help:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If you run into any trouble, post back here with a copy of the commands you used.

---

### Post by mayagrafix on 2009-04-24
Thank you very much for the link. The instructions worked perfectly and GRUB shows up at boot like it should.

One small problem, however, but I think I will ask the windows forums for help on this one, but you guys can give it go also if you want:

At boot the GRUB shows up, allowing me to choose which OS. So far so good. But when I choose the original Windows Vista OS, it says that NTLOADER is missing.

I can boot into Ubuntu or Windows XP fine. But Windows Vista is missing the NTLoader file. 

To recap, there are 2 HD, one has Ubuntu and other has 2 partitions with Windows Vista and XP.

So missing NTloader file sounds like a job for Bill gates minions to figure out. Thanks to you guys again at Canonical for all your help so far. ;)

---

### Post by unutbu on 2009-04-24
Please post the output of 
```

sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by mayagrafix on 2009-04-24
Thanks for your help unutbu, here goes screen one:
> 
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1311    10485760    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        1311       30394   233612288    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x971c6f2a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18705   150247881   83  Linux
/dev/sdb2           18706       19457     6040440    5  Extended
/dev/sdb5           18706       19457     6040408+  82  Linux swap / Solaris
doggo@Inspiron-530:~$ 


and here is screen two:
> 

doggo@Inspiron-530:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=ad9b8dab-718a-42b2-9fac-a93abb19838c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ad9b8dab-718a-42b2-9fac-a93abb19838c

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		ad9b8dab-718a-42b2-9fac-a93abb19838c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ad9b8dab-718a-42b2-9fac-a93abb19838c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		ad9b8dab-718a-42b2-9fac-a93abb19838c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ad9b8dab-718a-42b2-9fac-a93abb19838c ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ad9b8dab-718a-42b2-9fac-a93abb19838c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ad9b8dab-718a-42b2-9fac-a93abb19838c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ad9b8dab-718a-42b2-9fac-a93abb19838c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ad9b8dab-718a-42b2-9fac-a93abb19838c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ad9b8dab-718a-42b2-9fac-a93abb19838c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows XP (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

doggo@Inspiron-530:~$ 



Pheeww, Long one!

---

### Post by meierfra. on 2009-04-24
> Unfortunately the XP install wiped out the GRUB that was on the MBR of HD0. 
 Installing XP  also wipes out the Vista boot loader.

I suggest to use EasyBCD to restore the Vista boot loader:

[http://neosmart.net/wiki/display/EBCD/Installing+XP+After+Vista](http://neosmart.net/wiki/display/EBCD/Installing+XP+After+Vista)

---

### Post by unutbu on 2009-04-24
Edit: It appears meierfra. found you. Thanks, meierfra.

Please post a note in this thread: [http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628). Refer to this thread so meierfra. will have your "fdisk" and "menu.lst" output.

I'm afraid I don't know quite enough to help you, but you will be in good hands with meierfra. (or caljohnsmith).

---

### Post by mayagrafix on 2009-04-24
Well, thank you both very much. As so far that the problem is solved, I can now boot into Ubuntu, Vista and XP thanks to your help, gentle-people.

In summary: 
Grub loads fine thanks to info posted in this link:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
and thanks to EasyBCD both Vista and XP will boot, although in a roundabout way (First I use GRUB to choose between Ubuntu and Windows, then windows boot loader comes up and I can select Vista or XP)

What the heck, it works!

Again thanks to all and 3 cheers for Canonical!!!:guitar:

---

