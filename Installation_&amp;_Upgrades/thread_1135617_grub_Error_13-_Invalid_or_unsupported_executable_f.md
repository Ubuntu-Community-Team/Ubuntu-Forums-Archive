---
title: "grub Error 13- Invalid or unsupported executable format"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by SirSlipALot on 2009-04-24
Hello all!

I finally moved away from my old windows 2000 (and hope never to look back...) and installed Kubuntu.

I got to install it but now i can't boot windows (go figure: i thought linux was a nice OS! :)

At boot time in grub when i choose windows i get the error message:
"Error 13- Invalid or unsupported executable format"

I don't know anything about grub (and i am afraid to know :)) ...) so i hope anyone can help me out (googling is confusing because each person has a different system and that means RTFM of grub ;))


My hard drives story in short:
I have two hard drives and naturally windoze goes in the first partition (sda1).
First i tried to install ubuntu with Wibu but it failed (i don't know if this had any effect because i coulnd't uninstall it and there are some wubildr files in the root of the first partition left...)
Next i cleaned some partitions in my messy drives to make room for linux, made a live CD of Kubuntu and installed it on sda6.
Meanwhile i also upgraded 8.10 to 9.04 (i hope that doesn't change anything)


Some information on my system (you got to love how verbose and gregarious linux is :)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf7fcf7fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2089    16779861    7  HPFS/NTFS
/dev/sda2            2090       60801   471604140    f  W95 Ext'd (LBA)
/dev/sda5            2090        6266    33551721    7  HPFS/NTFS
/dev/sda6            6267       10443    33551721   83  Linux
/dev/sda7           10444       11096     5245191    7  HPFS/NTFS
/dev/sda8           11097       60801   399255381    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1387    10485688+   7  HPFS/NTFS
/dev/sdb2            1388       41206   301031609    f  W95 Ext'd (LBA)
/dev/sdb3           41207       41345     1050840   82  Linux swap / Solaris
/dev/sdb5            1388       41206   301031608+   7  HPFS/NTFS


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


(parted) print
Model: ATA WDC WD5000AAKB-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  17.2GB  17.2GB  primary   ntfs         boot
 2      17.2GB  500GB   483GB   extended               lba
 5      17.2GB  51.5GB  34.4GB  logical   ntfs
 6      51.5GB  85.9GB  34.4GB  logical   ext3
 7      85.9GB  91.3GB  5371MB  logical   ntfs
 8      91.3GB  500GB   409GB   logical   ntfs

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

/boot/grub/menu.lst:


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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=fa74c514-a45e-4696-b241-369d3b62d879 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fa74c514-a45e-4696-b241-369d3b62d879

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        fa74c514-a45e-4696-b241-369d3b62d879
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=fa74c514-a45e-4696-b241-369d3b62d879 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        fa74c514-a45e-4696-b241-369d3b62d879
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=fa74c514-a45e-4696-b241-369d3b62d879 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.27-11-generic
uuid        fa74c514-a45e-4696-b241-369d3b62d879
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=fa74c514-a45e-4696-b241-369d3b62d879 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid        fa74c514-a45e-4696-b241-369d3b62d879
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=fa74c514-a45e-4696-b241-369d3b62d879 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 9.04, memtest86+
uuid        fa74c514-a45e-4696-b241-369d3b62d879
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows 2000 Professional
root        (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

/boot/grub/device.map:


(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


I hope someone takes the time to give some tips and clues!
Many thanks!

---

### Post by cariboo on 2009-04-24
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows 2000 Professional
root (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


According to the above, it looks like grub is looking for you windows installation on the first partition of your second hard drive. I would suggest you change:

```
root (hd1,0)
```

to

```
root (hd0,0)
```

which is the first partition of your first hard drive.

---

### Post by SirSlipALot on 2009-04-24
Hi,

tried with 
root (hd0,0)
but after i get the message:
Starting up ...


the PC freezes/hangs ...

any clue?

---

### Post by meierfra. on 2009-04-24
> tried with
root (hd0,0)

Did you remove the "map"lines?

Try

title Microsoft Windows 2000 Professional
rootnoverify (hd0,0)
chainloader +1 

(nothing else, just those three lines)

---

### Post by SirSlipALot on 2009-04-24
Great! Problem SOLVED. :D

title Microsoft Windows 2000 Professional
rootnoverify (hd0,0)
chainloader +1


works well.
Thanks meierfra.

---

### Post by meierfra. on 2009-04-24
> works well.
Good.
> Thanks meierfra. 
You are welcome.

---

