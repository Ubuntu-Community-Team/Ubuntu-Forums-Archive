---
title: "Double Boot and change HDD"
date: 2009-04-12
forum: Hardware
---

### Post by GabrielWolff on 2009-04-12
I have a double boot Ubuntu/XP.
I want to change my HDD to a larger one.
After sitting in front of the screen for two days (!!!) I still didn't find a way to move that darn WIN partition to a different HDD!
Thing is: 
- both the old and the new HDD are internal HDDs (and I'm using a laptop => I can connect only one internal HDD at a time)
- I have an external (USB) HDD on which I could possibly mirror the old HDD.

But how? Windows will not start up after moving it to the new drive!

---

### Post by uidb4056 on 2009-04-12
You can try to backuo your Win Partition to USB an then restore it to new HDD using [http://www.clonezilla.org]("http://www.clonezilla.org/")

---

### Post by GabrielWolff on 2009-04-12
> **uidb4056 said:**
> You can try to backuo your Win Partition to USB an then restore it to new HDD using [http://www.clonezilla.org]("http://www.clonezilla.org/")

Previously I just copied the partitions using gparted and after that Windows wouldn't start up.
Will this problem be solved using clonezilla?

---

### Post by GabrielWolff on 2009-04-12
I cloned the HDD with clonezilla.
The Ubuntu partition boots alright.
When trying to boot windows, it states the following:
```
Booting Microsoft Windows Professional
root (hd0,1)
Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1
```
That's it. It stays there.

What's wrong? Is it fixable?

---

### Post by uidb4056 on 2009-04-12
Please post the result of sudo blkid and make sure that with gparted your ntfs partition is marked as 'boot' in the options.

---

### Post by GabrielWolff on 2009-04-12
> **uidb4056 said:**
> Please post the result of sudo blkid and make sure that with gparted your ntfs partition is marked as 'boot' in the options.

I flagged the first partition as "boot" (was it that? I didn't find any *options*)
But that didn't help. Same thing. 
Here's the result: ```
gabriel@gabriel-laptop:~$ sudo blkid
[sudo] password for gabriel: 
/dev/sda1: UUID="36DA800DDA7FC81F" LABEL="ServiceV002" TYPE="ntfs" 
/dev/sda2: UUID="2A70989D709870F5" LABEL="Preload" TYPE="ntfs" 
/dev/sda5: UUID="f8c1735c-599f-4ad8-a6d2-852890f1ee1f" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="0289029d-1b9c-430f-9584-a7e1b3a74ec8" 
/dev/sdb1: LABEL="Elements" UUID="A0EE-A2DC" TYPE="vfat" 
gabriel@gabriel-laptop:~$ 

```Does it help?

---

### Post by uidb4056 on 2009-04-13
> **GabrielWolff said:**
> I flagged the first partition as "boot" (was it that? I didn't find any *options*)
But that didn't help. Same thing. 
Here's the result: ```
gabriel@gabriel-laptop:~$ sudo blkid
[sudo] password for gabriel: 
/dev/sda1: UUID="36DA800DDA7FC81F" LABEL="ServiceV002" TYPE="ntfs" 
/dev/sda2: UUID="2A70989D709870F5" LABEL="Preload" TYPE="ntfs" 
/dev/sda5: UUID="f8c1735c-599f-4ad8-a6d2-852890f1ee1f" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="0289029d-1b9c-430f-9584-a7e1b3a74ec8" 
/dev/sdb1: LABEL="Elements" UUID="A0EE-A2DC" TYPE="vfat" 
gabriel@gabriel-laptop:~$ 

```Does it help?

It seems that sdb1 would be your external USB disk, you said that you have marked the first partition as "boot" (I suppose sda1) however you are trying to boot Wndows from sda2, could you clarify what of the two ntfs partitions holds your windows OS, do you have in windows c:\ and d:\ or one of this partitions are Recovery partition for your laptop?

---

### Post by GabrielWolff on 2009-04-13
Sorry, to make it perfectly clear, let me post the same thing again, after having unplugged the external HDD:
```
gabriel@gabriel-laptop:~$ sudo blkid
[sudo] password for gabriel: 
/dev/sda1: UUID="36DA800DDA7FC81F" LABEL="ServiceV002" TYPE="ntfs" 
/dev/sda2: UUID="2A70989D709870F5" LABEL="Preload" TYPE="ntfs" 
/dev/sda5: UUID="f8c1735c-599f-4ad8-a6d2-852890f1ee1f" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="0289029d-1b9c-430f-9584-a7e1b3a74ec8" 
gabriel@gabriel-laptop:~$ 

```
As far as I understand the situation, serviceV002 is the boot partition. But I have to say, I'm not quite sure. The windows came with the machine, and I just installed Ubuntu aside of it and never even remembered Windows until I needed it.
To make things more clear, here's a screenshot of gparted. Hope it helps.

---

### Post by uidb4056 on 2009-04-13
Ok, can you please from Nautilus try to open sda1 and sda2 (selecting places instead tree) to check which one have your XP ?

---

### Post by GabrielWolff on 2009-04-13
> **uidb4056 said:**
> Ok, can you please from Nautilus try to open sda1 and sda2 (selecting places instead tree) to check which one have your XP ?

Sorry, I think we had a misunderstanding: both are Windows partitions. I think one is d: and one is c:.

I send you a ls result of both:
```
gabriel@gabriel-laptop:/media/ServiceV002$ ls
boot  bootmgr  MFGSTAT  preboot  recovery  $RECYCLE.BIN  SCRREC.VER  swwork  System Volume Information  tvtos  windows
```
```
gabriel@gabriel-laptop:/media/Preload$ ls
AUTOEXEC.BAT            hiberfil.sys  NTLDR          SWSHARE
autorun.inf             I386          pagefile.sys   SWTOOLS
boot.ini                Icons         Program Files  syslevel.lgl
CONFIG.SYS              install.log   PSFONTS        System Volume Information
CreateMarkers.log       IO.SYS        RECYCLER       tvtpktfilter.dat
Documents and Settings  MSDOS.SYS     resycled       VALUEADD
drivers                 New Folder 1  RRbackups      WINDOWS
drivez.log              NTDETECT.COM  SUPPORT
```
Does this make it clear?

---

### Post by uidb4056 on 2009-04-13
Ok, your Windows partition is sda2. Can you edit your menu.lst file replacing root (hd0,1) by rootnoverify (hd0,1). To edit from terminal type 'sudo gedit /boot/grub/menu.lst'.

---

### Post by GabrielWolff on 2009-04-13
> **uidb4056 said:**
> Ok, your Windows partition is sda2. Can you edit your menu.lst file replacing root (hd0,1) by rootnoverify (hd0,1). To edit from terminal type 'sudo gedit /boot/grub/menu.lst'.

Did that - but no change. I post here the content of my menu.lst. Does this help in any way?
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
# kopt=root=UUID=f8c1735c-599f-4ad8-a6d2-852890f1ee1f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=f8c1735c-599f-4ad8-a6d2-852890f1ee1f ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=f8c1735c-599f-4ad8-a6d2-852890f1ee1f ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f8c1735c-599f-4ad8-a6d2-852890f1ee1f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f8c1735c-599f-4ad8-a6d2-852890f1ee1f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=f8c1735c-599f-4ad8-a6d2-852890f1ee1f ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=f8c1735c-599f-4ad8-a6d2-852890f1ee1f ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=f8c1735c-599f-4ad8-a6d2-852890f1ee1f ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=f8c1735c-599f-4ad8-a6d2-852890f1ee1f ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f8c1735c-599f-4ad8-a6d2-852890f1ee1f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f8c1735c-599f-4ad8-a6d2-852890f1ee1f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

### Post by uidb4056 on 2009-04-13
Do you have also Vista on sda1? or is a mistake?.

Anyway maybe the problem could be that windows want to boot from the first partition, can you add between 'makeactive' and 'chainloader'

hide (hd0,0)
unhide (hd0,1)

to see if it fix your problem

---

### Post by GabrielWolff on 2009-04-13
> **uidb4056 said:**
> Do you have also Vista on sda1? or is a mistake?.

Anyway maybe the problem could be that windows want to boot from the first partition, can you add between 'makeactive' and 'chainloader'

hide (hd0,0)
unhide (hd0,1)

to see if it fix your problem

Yeah, I was stumbling over that as well, when reading what I posted (here comes the part where I admit to myself that I don't actually know what's on my machine). 

Where should I put the 
```
hide (hd0,0)
unhide (hd0,1
```)?

Between which of the two instances of 
```
makeactive
chainloader	+1
```?

---

### Post by uidb4056 on 2009-04-13
On the second instance that makes reference to sda2

---

### Post by GabrielWolff on 2009-04-13
> **uidb4056 said:**
> On the second instance that makes reference to sda2

Same thing. It gives me the very same result, plus, of course, the different commands, so what I see when I boot the XP partition, is:
```
Booting Microsoft Windows Professional
root (hd0,1)
Filesystem type unknown, partition type 0x7
savedefault
makeactive
hide (hd0,0)
unhide (hd0,1)
chainloader +1
```

Could you shortly explain what you think the problem is?

---

### Post by uidb4056 on 2009-04-13
It's not completely clear for me, can be two things:

  - Windows doesn't like to boot from a partition that is not the first one.
  - Another possibility because you have replaced your HH by a biggest one can be that you have to verify what is in your BIOS you have to set the disk mode to LBA instead of auto, some times this make the trick.

One more question, do you remember when you start XP from your original disk if it goes straight to boot XP or there appears another kind of boot menu?

With your current disk what happens if you choose to boot from first Windows option (the one that says is Vista)?

---

