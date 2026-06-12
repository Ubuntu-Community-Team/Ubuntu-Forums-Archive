---
title: "Dual boot Windows/Linux using NTLDR"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by Howard Kaikow on 2009-07-25
A bit over two years ago, after doing tumblesaults, with the help of others, I was able to install Ubuntu 7.04 so that I could dual boot Windows and Ubuntu via the Windows NTLDR, using boot.ini.

In order to do so, there were modifications made to menu,lst, and a copy of the GRUB boot record was placed in the Windows C drive.

Of course, I did not understand what I did.

In recent weeks, I decided to install Ubuntu 9.04.
But I cannot get the multiboot thingee working as before.

If I use a Super Grub Disk, I can find the ubuntu install and use it, but there's gotta be an easier way.

I used the following to make a copy of the boot sector:

sudo dd if/dev/sdg6 of=.media/MicronM/grubboot.lnk bs =512 count=1

MicronM is a FAT32 drive.
After booting to Windows I copied grubboot.lnx to the C drive and use the same boot.ini I used 2+ years ago:

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(2)partition(2)\WINNT
[operating systems]
multi(0)disk(0)rdisk(2)partition(2)\WINNT="J: Microsoft Windows 2000 Professional" /fastdetect
signature(32a7e53f)disk(1)rdisk(0)partition(2)\WINNT="G: Microsoft Windows 2000 Professional" /fastdetect
signature(32a7e53f)disk(1)rdisk(0)partition(1)\WINNT="F: Microsoft Windows 2000 Professional" /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="C: Microsoft Windows 2000 Professional" /fastdetect
C:\grubboot.lnx="Ubuntu Linux"

```

The menu.lst file is given below.

I replaced:

```
title           Windows NT/2000/XP (loader)
rootnoverify    (hd3,0)
savedefault
makeactive
map             (hd0) (hd3)
map             (hd3) (hd0)
chainloader     +1

```

with
```
title           Windows NT/2000/XP (loader)
rootnoverify    (hd0,0)
makeactive
chainloader     +1

```

Why?
I have no idea, but that's what was done 2+ years ago.

The following is the current menu.lst.
What needs to change?

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
# kopt=root=UUID=7ddf536f-6ad6-4063-ab78-e0af592e6988 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7ddf536f-6ad6-4063-ab78-e0af592e6988

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7ddf536f-6ad6-4063-ab78-e0af592e6988
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7ddf536f-6ad6-4063-ab78-e0af592e6988 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7ddf536f-6ad6-4063-ab78-e0af592e6988
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7ddf536f-6ad6-4063-ab78-e0af592e6988 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		7ddf536f-6ad6-4063-ab78-e0af592e6988
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title		Windows NT/2000/XP (loader)
rootnoverify	(hd0,0)
makeactive
chainloader	+1
```

---

### Post by dandnsmith on 2009-07-25
You've provided a lot of info, but not enough for diagnosis/correction.
In order to have a hope of a fix I suggest you download [this script](http://sourceforge.net/projects/bootinfoscript/) and run it under Ubuntu.
That will find out where everything is, and provide enough to start on a fix.

---

### Post by Howard Kaikow on 2009-07-25
> **dandnsmith said:**
> You've provided a lot of info, but not enough for diagnosis/correction.
In order to have a hope of a fix I suggest you download [this script](http://sourceforge.net/projects/bootinfoscript/) and run it under Ubuntu.
That will find out where everything is, and provide enough to start on a fix.

Thanx.

I'll run the script, but I am waiting to hear from someone who indicated a possible solution using Super Grub Disk. I think that there is a step I left out in the process, and I might be able to correct using SGD.

---

### Post by oldfred on 2009-07-25
Without the bootinfo script it is hard to tell what is happening. The change you made to your menu.lst is saying you moved your windows hard drive from hd3 to hd0, did you use the BIOS to change hard disk boot order or move the cables around in the computer. Supergrub will reinstall Grub and if it is on a different drive your windows set up does not matter.
Run the script.

---

### Post by Howard Kaikow on 2009-07-26
> **oldfred said:**
> Without the bootinfo script it is hard to tell what is happening. The change you made to your menu.lst is saying you moved your windows hard drive from hd3 to hd0, did you use the BIOS to change hard disk boot order or move the cables around in the computer. Supergrub will reinstall Grub and if it is on a different drive your windows set up does not matter.
Run the script.

The change I made was not the only change needed.

According to [How to Boot Grub from Windows]("http://www.supergrubdisk.org/w/index.php5?title=Howto_Boot_Grub_from_windows"), I missed a step.

I am using the method described as Common Final Solution for Windows 2000. And this is what I did for ubie 7.04.

I think that the missing step is what is described as GRUB solution(Linux shell).

2+ years ago, for ubie 7.04, I used the following:

```
$ sudo grub
type your password
grub> device (hd0) /dev/sdc
grub> device (hd2) /dev/sdc
grub> root (hd2,9)
grub> setup (hd0,9)
grub> quit
$ sync
$ reboot

```

This time, Ubuntu is installed in /dev/sdg6, I believe that this is (hd3,5). So, I believe that I would need to do the following:

```
$ sudo grub
type your password
grub> device (hd0) /dev/sdg
grub> device (hd3) /dev/sdg
grub> root (hd3,5)
grub> setup (hd0,5)
grub> quit
$ sync
$ reboot
```

I would then have to redo

```
sudo dd if/dev/sdg6 of=.media/MicronM/grubboot.lnx bs =512 
count=1
```

And copy grubboot.lnx to the C drive.

Is the above correct?

In addition, to using, as described in my original post in this thread:

```
title           Windows NT/2000/XP (loader)
rootnoverify    (hd0,0)
makeactive
chainloader     +1
```

---

### Post by Howard Kaikow on 2009-07-27
> **dandnsmith said:**
> You've provided a lot of info, but not enough for diagnosis/correction.
In order to have a hope of a fix I suggest you download [this script](http://sourceforge.net/projects/bootinfoscript/) and run it under Ubuntu.
That will find out where everything is, and provide enough to start on a fix.

OK, I have tried to attach a .zip of Result.txt.

There are some-non-related issues raised, but not relevant to this thread.

---

### Post by Howard Kaikow on 2009-07-29
Eureka!
And I do not mean the TV show.

The method I listed in post #5 of this thread did the deed, except, I used (hd3,5) instead of (hd0,5) in the grub commands.

Also, I made a copy of only the first 446 bytes of the boot sedtor.

Seems to work.
As we speak, I'm running Update Manager.

---

### Post by dandnsmith on 2009-07-29
> **Howard Kaikow said:**
> The method I listed in post #5 of this thread did the deed, except, I used (hd3,5) instead of (hd0,5) in the grub commands.
Glad you managed to resolve it - I was away for a while

> Also, I made a copy of only the first 446 bytes of the boot sedtor.
That would limit it to the boot code (mainly), and exclude some bits which could, in the wrong circumstances, mess you up.

---

### Post by Howard Kaikow on 2009-07-29
> **dandnsmith said:**
> Glad you managed to resolve it - I was away for a while


That would limit it to the boot code (mainly), and exclude some bits which could, in the wrong circumstances, mess you up.

What  is in bytes 447-512?

I did make a copy of both lengths,but I put the 446 length on the C drive.

What problems can this cause?

---

### Post by dandnsmith on 2009-07-29
Towards the end of the first disk sector is the partition table - not something you want to mess up by copying that from one disk to another.

I've forgotten where to look this stuff up, I'm afraid.

---

### Post by Howard Kaikow on 2009-07-29
> **dandnsmith said:**
> Towards the end of the first disk sector is the partition table - not something you want to mess up by copying that from one disk to another.

I've forgotten where to look this stuff up, I'm afraid.

Yes, but all I want to do is protect the boot loader.
If I repartition, and I an using the 512 bytes, my recollection is that Ubuntu will warn me at the backup copy is not the same as the original, or some such message.

I believe that using 446 avoids this problem.

See the discussion in [Backup & Restore]("http://members.iinet.net.au/~herman546/p13.html").

---

### Post by Howard Kaikow on 2009-07-30
> **dandnsmith said:**
> Towards the end of the first disk sector is the partition table - not something you want to mess up by copying that from one disk to another.

I've forgotten where to look this stuff up, I'm afraid.

You no longer need be afraid!


[MBR]("http://en.wikipedia.org/wiki/Master_boot_record#cite_note-endianness-0")

---

### Post by dandnsmith on 2009-07-30
> **Howard Kaikow said:**
> You no longer need be afraid!

[MBR]("http://en.wikipedia.org/wiki/Master_boot_record#cite_note-endianness-0")

Thanks for that reference.

---

