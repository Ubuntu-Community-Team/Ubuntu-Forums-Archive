---
title: "[SOLVED] Can't get back into linux! Grub won't work"
date: 2008-10-29
forum: General Help
---

### Post by kcredden on 2008-10-29
Hi folks, ran into a major problem.

My system's specs are as follows:
HDA1 - 80g PATA, Windows 2000 Pro installed, system boots from here.
SDA1 - 200g SATA, Kubuntu 8.04.1, Ext2
SDA2 - 320g SATA, Ext2

When I installed Kubuntu, I installed it on SDA1, and GRUB was on the MBR of HDA1. I managed to kick off GRUB, when I was looking at the windows partitions with the windows install disk.

After some work, I managed to get GRUB installed on the SDA1 drive (which I prefer, since this will keep Windows from kicking it off again, is that right?)

However, this doesn't work. **If I click ** on Ubuntu 8.04.1, Kernel 2.6.24-21-generic, I get: *Error 17:* Cannot mount selected partition. However if I click on: **Microsoft Windows 2000 **Proofessional, it *loops back* into the GRUB menu.

I used [System Rescue Disk CD]("http://www.sysresccd.org/Main_Page") to do this. So can anyone tell me what I must do? I have no idea how to even boot into linux, and fire it up via a bootable disk. I just need a basic how-to on how to rebuild GRUB, or reinstall it right, the next time.

Thanks
- Kc

---

### Post by caljohnsmith on 2008-10-29
When you get the Grub menu on start up, select the first Kubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Kubuntu if there are no major problems with your Grub's menu.lst. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Kubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" to use the (hd0,Y) that worked to boot Kubuntu; save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set about booting Kubuntu. In order to figure out your Windows booting problem, please post:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
And we can work from there. :)

---

### Post by alienprdkt on 2008-10-29
WOW,
that's a great way to edit grub, wish i knew that when I had problems with grub before. Have to take note that you can edit the grub menu that way.

---

### Post by kcredden on 2008-10-29
Thanks. I'll try that tomarrow, when I'm back home from work. I be sure to put this into my linux notebook. Slowly I'm building up a book of linux :)

- Kc

> **caljohnsmith said:**
> When you get the Grub menu on start up, select the first Kubuntu entry, press "e" to edit it,

---

### Post by kcredden on 2008-11-02
Cal: Thanks for the help. I got back into linux without a problem (After work, work...oh yes, more work :)

Here's the data you requested to help with getting grub fixed for windows:

--Fdisk data:
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x89b789b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    21253994    10626966    7  HPFS/NTFS
/dev/sda2        21253995    42861419    10803712+   7  HPFS/NTFS
/dev/sda3        42861420   156296384    56717482+   5  Extended
/dev/sda5        42861483    51102764     4120641    b  W95 FAT32
/dev/sda6        51102828   112953014    30925093+   c  W95 FAT32 (LBA)
/dev/sda7       112953078   156296384    21671653+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7e45b14c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   384660359   192330148+  83  Linux
/dev/sdb2       384660360   390716864     3028252+   5  Extended
/dev/sdb5       384660423   390716864     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a1f10

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   619080839   309540388+  83  Linux
/dev/sdc2       619080840   625137344     3028252+   5  Extended
/dev/sdc5       619080903   625137344     3028221   82  Linux swap / Solaris

--

--and Grub menu

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
# kopt=root=UUID=191c01a3-5082-46eb-af1c-1e309bb9f803 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
# defoptions=quiet splash access=v1

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=191c01a3-5082-46eb-af1c-1e309bb9f803 ro quiet splash access=v1
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=191c01a3-5082-46eb-af1c-1e309bb9f803 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=191c01a3-5082-46eb-af1c-1e309bb9f803 ro quiet splash access=v1
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=191c01a3-5082-46eb-af1c-1e309bb9f803 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
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
--

Hope this helps!

- Kc

> **caljohnsmith said:**
> And you should be all set about booting Kubuntu. In order to figure out your Windows booting problem, please post:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
And we can work from there. :)

---

### Post by caljohnsmith on 2008-11-02
Glad to hear you made it into Kubuntu OK. Since you have two other drives besides the kubuntu drive, and since I don't know what order those drives are in your BIOS boot order, I can't know for sure how to boot Windows from your Kubuntu drive; but since there are only two possibilities, just add the following two Windows entries to your Grub menu.lst, and one should work:
```

title	   Windows 2000 (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows 2000 (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Hopefully one of those entries will work, and then you can delete the other entry once you know. Let me know how it goes.

---

### Post by kcredden on 2008-11-06
Cal: Though you'd like to know that when I got the time to fix this, it was a simple fix (The first entry was the correct one) and now I can use GRUB to get into Windows or linux all the time

Also wanted to tell you, you are the only linux helper that I ever came across that does it right. You spell it out, in simple step by step terms, and show patience, without patranizing. Very refreshing, and the way it should be.

For now I'm still a windows user, but after 10 years I *want to go into linux full time*. So with your help, and the others here, I think I'll make it :) (But I'll still have TONS of questions - over time however :)

Thanks again
-Kc

> **caljohnsmith said:**
> Hopefully one of those entries will work, and then you can delete the other entry once you know. Let me know how it goes.

---

### Post by caljohnsmith on 2008-11-06
> **kcredden said:**
> Cal: Though you'd like to know that when I got the time to fix this, it was a simple fix (The first entry was the correct one) and now I can use GRUB to get into Windows or linux all the time

Also wanted to tell you, you are the only linux helper that I ever came across that does it right. You spell it out, in simple step by step terms, and show patience, without patranizing. Very refreshing, and the way it should be.

For now I'm still a windows user, but after 10 years I *want to go into linux full time*. So with your help, and the others here, I think I'll make it :) (But I'll still have TONS of questions - over time however :)

Thanks again
-Kc
You're certainly welcome, and I'm glad it worked. And thanks for following up to let me know what happened; unfortunately, I've found that not everybody has the courtesy to do that. Cheers and have fun with Ubuntu. :)

---

