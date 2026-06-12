---
title: "Can't restore Grub / Partitions not recognized"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by vfontanela on 2009-08-03
Hello! The problem I'm going to post is really weird, but please don't tell me "You'll have to format your pc.".

I have on my pc both Ubuntu 9.04 and Windows Xp, I had to reinstall Windows Xp and - naturally - Grub was deleted. So I used Ubuntu LiveCd to restore it.

After booting from the LiveCD, in terminal, I typed:
sudo grub install
then
find /boot/grub/stage1
It prompted (hd0,5)
then:
root (hd0,5)
and finally:
setup (hd0) -> Doesnt matter what I do, I get an Error 22.

I looked for thousand ways of restoring Grub, I tryed each one of them, without success.

I tried start installing Ubuntu from Live CD, but Gparted didn't show any partition on my hard disk it shows a 160gb hard disk completelly empty, with no partitions in it. I think the problem with installing grub has something to do with this other problem. If I type fdisk -l no partitions appear, but if I enter in cfdisk, all partition are there. And Ubuntu Live CD can mount the partitions Gparted says that don't exist.

I tried downloading Super Grub Disk, I burned the cd, boot from it and voilà, my Linux loads ok. Grub wasnt restored, but with that cd my system boots ok. And I couldnt restore Grub even with Ubuntu running. I started Gparted and it says that my hard disk is empty, there is only one hard disk in my pc, so no mistake, it says the hardisk Linux was running from on that moment was empty, but cfdisk shows my partitions and I can mount them perfectlly.

My other try was installing old Lilo, Lilo was recorded ok into my MBR, it loads Windows, but not my Ubuntu, when I select Ubuntu and press Enter it keeps loading forever.
I also tryed WinGrub but with no success.

Remember that my system is intact, because with Super Grub Disk it runs ok.

Any help is appreciated.

---

### Post by merlinus on 2009-08-03
Post results of

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by vfontanela on 2009-08-03
I booted in Linux with Super Grub Disk


vfontanela@vfontanela-laptop:/$ sudo fdisk -l
[sudo] password for vfontanela: 
omitting empty partition (5)

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cilindros of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08430843

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/sda1   *           1       16678   133966003+   7  HPFS ou NTFS
/dev/sda2           16679       19457    22322317+   5  Estendida
/dev/sda3           19336       19457      979933+  82  Linux swap / Solaris
/dev/sda5   *       16679       19335    21342289+  83  Linux


-----------------------------


vfontanela@vfontanela-laptop:~$ cat /boot/grub/menu.lst
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
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=b01f0c0a-b27a-4ce3-bdff-834d260bafe3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b01f0c0a-b27a-4ce3-bdff-834d260bafe3

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

#title		Ubuntu 9.04, kernel 2.6.30-020630rc2-generic
#uuid		b01f0c0a-b27a-4ce3-bdff-834d260bafe3
#kernel		/boot/vmlinuz-2.6.30-020630rc2-generic root=UUID=b01f0c0a-b27a-4ce3-bdff-834d260bafe3 ro locale=pt_BR quiet splash 
#initrd		/boot/initrd.img-2.6.30-020630rc2-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.30-020630rc2-generic (recovery mode)
#uuid		b01f0c0a-b27a-4ce3-bdff-834d260bafe3
#kernel		/boot/vmlinuz-2.6.30-020630rc2-generic root=UUID=b01f0c0a-b27a-4ce3-bdff-834d260bafe3 ro locale=pt_BR  single
#initrd		/boot/initrd.img-2.6.30-020630rc2-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		b01f0c0a-b27a-4ce3-bdff-834d260bafe3
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b01f0c0a-b27a-4ce3-bdff-834d260bafe3 ro locale=pt_BR quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		b01f0c0a-b27a-4ce3-bdff-834d260bafe3
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b01f0c0a-b27a-4ce3-bdff-834d260bafe3 ro locale=pt_BR  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		b01f0c0a-b27a-4ce3-bdff-834d260bafe3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

---

### Post by merlinus on 2009-08-03
For starters, this

title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

needs to be below these lines:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title        Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

Then run these commands from a terminal:

```
sudo grub
root (hd0,4)
setup (hd0)
quit
```

and restart.

---

### Post by vfontanela on 2009-08-03
grub> root (hd0,4)
grub> setup (hd0)
Error 17: Cannot mount selected partition

---

### Post by merlinus on 2009-08-03
Try supergrub:

[http://supergrubdisk.org](http://supergrubdisk.org)

---

### Post by vfontanela on 2009-08-03
I have already tried it. This cd is the only way I have to start Linux. When I boot from it, my Linux starts, but my Grub is not restored.

---

### Post by merlinus on 2009-08-03
I wonder if your partition numbering being off has something to do with it?

It can be fixed this way:

```
sudo fdisk /dev/sda
x
f
w
```

and restart.

---

### Post by vfontanela on 2009-08-03
Wow, it worked! Thank you very much, Merlin!

Well, I typed sudo fdisk /dev/sda

x
f - Then it said that it was all right and that nothing was done.
w - It said I should restart, to use the new partition table, once Kernel was using the old one.

Then I restarted and tried again:

sudo grub

root (hd0,5) - It prompted: No such partition.
Then I tried
root (hd0,4) - Ok
setup (hd0) - Done, worked like a charm!

How do you know it was 0,4 and not 0,5?

---

### Post by merlinus on 2009-08-03
Excellent news!  As for (hd0,4) -- numbering for these things begins at 0 (zero), so hd0 is first hdd (sda), 4 is partition 5, and linux is on sda5.

Have fun...

---

