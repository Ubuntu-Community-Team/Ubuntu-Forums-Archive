---
title: "Error 13 on dualboot with Ubuntu 8.04 and Windows XP Pro"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by Halvliter on 2009-03-05
I have used Ubuntu for about a day, so I'm really new to all this.

I followed this guide [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm) on how to dualboot with Windows XP.

This part gave me an error: (Step 5)

> "To enter the GRUB configuration mode, type in "sudo grub" and press Enter. Then type in the following commands in sequence: 
- root (hd0,0) 
- setup (hd0) 
- quit 
- exit"

So I used this method:

> "Code:
sudo grub
This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:
find /boot/grub/stage1
This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:
root (hd?,?)
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:
setup (hd0)
Finally exit the grub shell
Code:
quit

And then I moved on to:

> Reboot the system. You'll get the GRUB bootloader but Vista won't be an option - we need to add this to the boot options. 

Boot into Ubuntu and open up another Terminal session. Then, type in sudo gedit /boot/grub/menu.lst 

Scroll down to the bottom of the file and type in the following text strings:

title Windows XP 
root (hd0,1) 
makeactive 
chainloader +1 

Save the file and reboot. When the GRUB loader launches hit ESC for the boot menu. Windows XP is the last option - select it and XP will load.

I got an error saying:

Error 13: Invalid or unsupported executable format.



Can someone help me ? If someone can, please explain as simple as you can, I'm very new to Linux/Ubuntu.

---

### Post by Halvliter on 2009-03-05
I forgot to mention my hardware setup:

I have 3 partitions on a SATA-disk. 20 GB for Linux and 20 GB for XP, the rest for storage.

I have two other SATA disks and one IDE disk.

Is it necessary to mention the rest of the hardware ?

MSI K9N SLI Motherboard, Geforce 8800 GTS, AMD Athlon X2 4600+ I think...

And last my Grub boot menu file:

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
hiddenmenu

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
# kopt=root=UUID=0c4de856-e355-4026-84fd-eeab0d72eef1 ro

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0c4de856-e355-4026-84fd-eeab0d72eef1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0c4de856-e355-4026-84fd-eeab0d72eef1 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP 
root (hd0,1) 
makeactive 
chainloader +1


---

### Post by 73ckn797 on 2009-03-05
Enter Terminal and type:

```
sudo fdisk -l
```
Post results

---

### Post by Halvliter on 2009-03-06
This is what I got:

> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbaa1baa1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+  83  Linux
/dev/sda2   *        2433        2554      979965   82  Linux swap / Solaris
/dev/sda3            2555        5104    20482875    7  HPFS/NTFS
/dev/sda4            5105       38913   271570792+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00053dfa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x674f8c7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60802   488383488    7  HPFS/NTFS

Disk /dev/sdd: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c40f130

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       36482   293033984    7  HPFS/NTFS

Disk /dev/sdi: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *           1       60801   488384001    7  HPFS/NTFS

---

### Post by Halvliter on 2009-03-06
Does this make any sense?

---

### Post by Halvliter on 2009-03-07
Bump.

---

### Post by Mark Phelps on 2009-03-08
You have an extra partition in there. 

Change "root (hd0,1)" to "rootnoverify (hd0,2)" and see if that works.

---

