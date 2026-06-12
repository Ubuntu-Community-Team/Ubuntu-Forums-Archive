---
title: "GRUB Problem...!"
date: 2008-08-30
forum: General Help
---

### Post by Saikarthik on 2008-08-30
system restarts when i select "windows" in grub...
this started happening after a sudden power off from U.P.S...
now i'm able to log only in ubuntu..
im new to ubuntu please help me out to log in into windows..

---

### Post by gmxgeek on 2008-08-30
can you please post the output of
```

cat /boot/grub/menu.lst
sudo fdisk -l

```

---

### Post by Saikarthik on 2008-08-30
thnx for ur reply..

here is the output..


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
# kopt=root=UUID=1107b243-81e1-404a-b6d9-9bf96c02eb77 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1107b243-81e1-404a-b6d9-9bf96c02eb77 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1107b243-81e1-404a-b6d9-9bf96c02eb77 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,6)
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

---

### Post by gmxgeek on 2008-08-30
and
```

sudo fdisk -l

```
please

---

### Post by Saikarthik on 2008-08-30
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c731c73

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        9728    57657285    f  W95 Ext'd (LBA)
/dev/sda5            2551        5100    20482843+   7  HPFS/NTFS
/dev/sda6            7651        9728    16691503+   7  HPFS/NTFS
/dev/sda7            5101        7407    18530946   83  Linux
/dev/sda8            7408        7650     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by gmxgeek on 2008-08-30
does it restart as soon as you hit the grub entry, or midway into windows boot?

---

### Post by Saikarthik on 2008-08-30
it restarts immediately wen i select windows in the grub..!

---

### Post by gmxgeek on 2008-08-30
okay, grab your XP disk, boot to a recovery console and run the command fixmbr

that will kill grub and get windows back. then follow these instructions to get grub back

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

good luck!

---

### Post by prshah on 2008-08-30
> **Saikarthik said:**
> system restarts when i select "windows" in grub...


You need to see why Windows is (instantly) restarting; you can do this in two ways:

1) Immediately after selecting the Windows option in GRUB, keep tapping F8 to get the startup options menu. 

2) From Ubuntu, edit the MSDOS.SYS file in your Windows partition, and add the below line to the [Options] section:```
BootMenu=1
```

 (if there is no [options] section or if the msdos.sys file is blank, then use ```

[Options]
BootMenu=1
```

Now, when you boot Windows, the startup options menu will appear automatically, without the need to tap F8.

Then, from the boot menu, choose the "Disable Automatic Restart on Failure" option. Then let windows boot normally; near the end of the process, you will get a blue screen which will state the cause of the error; post back the error message and details, and we can see how to resolve it easily.

Most likely the error will be similar to "Cannot find NTLDR/System.Dat/User.Dat/SAM/SECURITY" etc. In this case, it's quite easy to resolve, depending on the actual file (area) affected.

btw, This is a Windows problem and should be moved into the suitable forum.

---

### Post by dmizer on 2008-08-30
Moved to General Help.  Forum help is only for needs related to the forum itself, not Ubuntu. :)

---

### Post by caljohnsmith on 2008-08-30
> **gmxgeek said:**
> okay, grab your XP disk, boot to a recovery console and run the command fixmbr

that will kill grub and get windows back. then follow these instructions to get grub back

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

good luck!
When you run fixmbr, all it does is reinstall the Windows boot loader to the master boot record (MBR). And all the Windows MBR does is "chain load" whatever partition on the HDD is "active", i.e. has its boot flag set on. Grub can do the same thing perfectly well, and actually better since you can specify which partition you want to chain load; so I don't think it will accomplish anything to run fixmbr.

Saikarthik, when you say your computer "restarts" after you choose Windows, does it go immediately back to the Grub menu, or do you get a full restart where you see a BIOS screen/notification on start up or something of that sort? That is significant, because it could mean that all that is wrong is that Grub got accidentally written to the boot sector of your Windows partition (which is repairable).

---

