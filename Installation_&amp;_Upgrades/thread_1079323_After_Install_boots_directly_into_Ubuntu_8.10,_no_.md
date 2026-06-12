---
title: "After Install boots directly into Ubuntu 8.10, no boot choices"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by bsprowl on 2009-02-24
Installed Ubuntu 8.10 on to my Lenovo T60 laptop which has Windows XP Pro.

XP is in a 55 GB primary NTFS partition.  The 242 GB extended partition is divided into a 120 GB logical NTFS data partition and a 122 GB used space. Ubuntu converted that space into a 1.42 MB unallocated space, a 119 GB ext3 partition and a 3 GB Linux swap partition.

The system now boots directly into Ubuntu.  There is a Grub folder with a menu list that looks correct.  I suspect the MBR is bad but have no idea how to see it.

This is my third attempt at using Linux and I really would like to get away from Windows but I teach Office 2007 and need Windows at work.

I saw this on another thread and tried it "sudo bash ~/Desktop/boot_info_script*.sh" but got "No such file or directory" as a response. Since I not sure what that does I don't know if I should have that directory, etc. 

Any suggestions?

Bob

---

### Post by Pumalite on 2009-02-24
Post:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```

---

### Post by hansdown on 2009-02-24
Hi bsprowl.

When your system starts, you should get a screen that looks like this.








Choose the windows loader before the timer counts down.

---

### Post by bsprowl on 2009-02-24
I don't get that or any other screen when I boot; the system goes directly into Ubuntu.

Bob

---

### Post by bsprowl on 2009-02-24
> **Pumalite said:**
> Post:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```bsprowl@lenovo-laptop:~$ sudo fdisk -lu
[sudo] password for bsprowl: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbf990c72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   116741519    58370728+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2       116741582   625137344   254197881+   f  W95 Ext'd (LBA)
/dev/sda5       116741583   368640719   125949568+   7  HPFS/NTFS
/dev/sda6       368643618   619129034   125242708+  83  Linux
/dev/sda7       619129098   625137344     3004123+  82  Linux swap / Solaris
bsprowl@lenovo-laptop:~$ cat /boot/grub/menu.bat
cat: /boot/grub/menu.bat: No such file or directory
bsprowl@lenovo-laptop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=0fc47a73-1189-42c3-b90a-693a048000b2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0fc47a73-1189-42c3-b90a-693a048000b2

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
uuid		0fc47a73-1189-42c3-b90a-693a048000b2
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=0fc47a73-1189-42c3-b90a-693a048000b2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		0fc47a73-1189-42c3-b90a-693a048000b2
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=0fc47a73-1189-42c3-b90a-693a048000b2 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		0fc47a73-1189-42c3-b90a-693a048000b2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0fc47a73-1189-42c3-b90a-693a048000b2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		0fc47a73-1189-42c3-b90a-693a048000b2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0fc47a73-1189-42c3-b90a-693a048000b2 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		0fc47a73-1189-42c3-b90a-693a048000b2
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

bsprowl@lenovo-laptop:~$

---

### Post by Pumalite on 2009-02-24
Use Super Grub and see if you can boot Windows:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
You might have a Partition Table problem, but try Super Grub first.

---

### Post by bsprowl on 2009-02-24
Well I'd like to make a super grub disk but when I download it I can't find it.  What is the default download folder?

Bob

---

### Post by Pumalite on 2009-02-24
Desktop

---

### Post by bsprowl on 2009-02-24
Well then none of the Supergrub sites (mirrors) are working correctly as I can't get the downloads on this or my other computer. Bummer.

Bob

---

### Post by bsprowl on 2009-02-25
Here's the latest thing I tried but it made no difference.  I still don't get a boot menu.

You can use the following to reinstall Grub to the MBR and point it to your Ubuntu partition for its boot files (and also menu.lst):
Code:

sudo grub
grub> find /boot/grub/stage1

The command above should return your main Ubuntu partition and the OpenSUSE partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,2), but use the one that corresponds to Ubuntu:
Code:

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit

ANy other ideas.  I'm about ready to dump this install and start over.

Bob

---

