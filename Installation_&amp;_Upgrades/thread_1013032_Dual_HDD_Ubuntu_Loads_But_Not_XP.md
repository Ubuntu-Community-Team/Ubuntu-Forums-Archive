---
title: "Dual HDD Ubuntu Loads But Not XP"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by Sierra_Dave on 2008-12-16
Hi,

I built this from scavenged parts and a new MB.  I have :

Foxconn MB P9657AA
4gb PC-6400 Ram
Asus 3450 256mb PCI-16
320gb WD SATA2 HDD
120 IDE HDD Win XP Home
LG HL DT ST DVD/rw CDR GSA H41N

Ubuntu Loaded on SATA 320gb 8.10 runs fine and I can access Win XP on IDE, but when I go to load Win XP on using BIOS boot/order, it loads the drivers and then crashs back to Boot-up.

I have the DVD/rw on "CS" and IDE on "CS" on same ribbon [not set as master/slave].  SATA is it's own controller.

Ideally, I would like to use grub to choose loading of either Ubuntu or Win XP.

Any Ideas?
Thanks,
Dave

---

### Post by cariboo on 2008-12-16
Could you paste the results of:

```
sudo fdisk -l
```

and 

```
cat /boot/grub/menu.lst
```

in your next post. THe above commands must be run in a Applications-->Accessories-->Terminal.

JIm

---

### Post by Sierra_Dave on 2008-12-16
Hi cariboo907,

The output from sudo fdisk -l---

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005af5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37684   302696698+  83  Linux
/dev/sda2           37685       38913     9871942+   5  Extended
/dev/sda5           37685       38913     9871911   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae706b65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    7  HPFS/NTFS

-----------

The output from cat /boot/grub/menu.lst--------

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
# kopt=root=UUID=2ff216c4-a9b6-4c92-bb22-a4b39950a74e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2ff216c4-a9b6-4c92-bb22-a4b39950a74e

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		2ff216c4-a9b6-4c92-bb22-a4b39950a74e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=2ff216c4-a9b6-4c92-bb22-a4b39950a74e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		2ff216c4-a9b6-4c92-bb22-a4b39950a74e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=2ff216c4-a9b6-4c92-bb22-a4b39950a74e ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		2ff216c4-a9b6-4c92-bb22-a4b39950a74e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2ff216c4-a9b6-4c92-bb22-a4b39950a74e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		2ff216c4-a9b6-4c92-bb22-a4b39950a74e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2ff216c4-a9b6-4c92-bb22-a4b39950a74e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		2ff216c4-a9b6-4c92-bb22-a4b39950a74e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
 
----------
That's it.
Dave

---

### Post by caljohnsmith on 2008-12-16
If booting the Windows drive directly on start up leads to Windows crashing, then adding an entry in Grub to boot Windows is unfortunately not going to fix your problem with Windows. I would start by booting your Windows Install CD, going to the "recovery console" and run:
```
chkdsk /r
```
And run it as many times as it takes until it reports no errors. Then reboot and see if you get any further booting Windows. If not, I would again boot your Windows Install CD and do a "Windows Repair". Since you seemed to have changed around your hardware, I don't think you'll be able to get Windows working without doing the Windows Repair. But maybe you'll get lucky and a chkdsk will get you far enough to at least boot into Windows. Let us know how it goes.

---

### Post by Sierra_Dave on 2008-12-16
What happens is that I get to the blue screen:"Windows shutdown unexpectedly...
1. Safe mode...
2. etc.

"
When I make any selection it starts to load drivers [c:/...windows/system/drivers/...] and then reboots.  I think it is a path problem and in the Foxconn bios it indicates there is no "A" drive [reserved for floppy dd].  The BIOS lists the HDD as:
1. Ch0 M.:  WDC WD3200aak
2. SCSI -0: WD1200AB

I checked the boot.ini file and it appears ok.

Odd.

---

### Post by Sierra_Dave on 2008-12-16
This is how the Boot.ini file reads:
"[boot loader]
timeout=30
Default= multi(0)disk(0)rdisk(0)partition(1)\windows
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\windows="<OperatingSystem>"

MS sets this online:

"If your computer starts from a SCSI hard disk drive, you may have to replace the multi(0) entry with scsi(0). If you are using scsi(x) in the Boot.ini file, copy the correct device driver for the SCSI controller that is used on the computer to the root of the boot disk, and then rename the device driver to Ntbootdd.sys. Change the disk(0) number to represent the SCSI-ID of the hard disk drive you want to start. If you are using multi(x) in the Boot.ini file, you do not have to change the code in the Boot.ini file."

I will try to change the boot.ini and find the right scsi driver.

---

