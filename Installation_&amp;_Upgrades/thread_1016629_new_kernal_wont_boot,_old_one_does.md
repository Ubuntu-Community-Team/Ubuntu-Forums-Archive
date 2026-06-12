---
title: "new kernal wont boot, old one does"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by kotmfu on 2008-12-20
after not being able to get the 8.10 cd to boot off my computer i decided to reinstall 8.04 (because that cd works) and juts upgrade from there.. which i did
and i was all find till i realised i didnt let it change my menu.lst, so i change it to the newer kernal (ie from 8.04 to 8.10) and the bootup fails.
i can hear my hdd turning off and on and all it says is cannot find disk with uuid  ****.
i have absolutely no idea what is going on with this so any help at all is appreciated
thanks heaps

---

### Post by Sef on 2008-12-20
Kernels are version specific for Ubuntu.   I would use the old kernel and start a new thread for your problem with menu.lst.

---

### Post by kotmfu on 2008-12-20
but i dont have a problem with menu.lst. i have a problem with that specific version of linux not liking my hard drive and i was wondering what you all had to say about it.

---

### Post by taurus on 2008-12-20
Post

```
cat /boot/grub/menu.lst
sudo fdisk -l
sudo blkid
cat /etc/fstab
```

---

### Post by kotmfu on 2008-12-20
???@???-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=915433de-a600-4b1b-8ea8-3f35bb02df97 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,0)

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=915433de-a600-4b1b-8ea8-3f35bb02df97 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=915433de-a600-4b1b-8ea8-3f35bb02df97 ro single
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
# on /dev/sdc2
title		Windows Vista/Longhorn (loader)
root		(hd2,1)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

???@???-desktop:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69760ed6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5165    41485815    f  W95 Ext'd (LBA)
/dev/sda2   *        5166       38913   271080810    7  HPFS/NTFS
/dev/sda5               1        5165    41485312    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f0f6472

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38156   306488038+  83  Linux
/dev/sdb2           38157       38913     6080602+   5  Extended
/dev/sdb5           38157       38913     6080571   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
240 heads, 63 sectors/track, 64601 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x5561caf5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       64602   488383488    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7d695560

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121602   976759808    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sde: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35233be7

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       19608   157500236    7  HPFS/NTFS
/dev/sde2           19609       45105   204804652+   7  HPFS/NTFS
/dev/sde3           45106       48377    26282340    7  HPFS/NTFS
/dev/sde4           48378       77826   236541952    f  W95 Ext'd (LBA)
/dev/sde5           48378       77826   236540928    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdf: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35233be6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       77826   625129472    7  HPFS/NTFS
/dev/sdf4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.
???@???-desktop:~$ sudo blkid
/dev/sdb1: UUID="915433de-a600-4b1b-8ea8-3f35bb02df97" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="9ea438e5-b597-4b84-80db-a41071fbb145" 
/dev/sdc2: UUID="A45CA9315CA8FF64" LABEL="Documents" TYPE="ntfs" 
/dev/sdc5: UUID="7C24E93824E8F5D4" LABEL="XP" TYPE="ntfs" 
/dev/sdd1: UUID="E6082EF0082EBF83" LABEL="TV Shows 2" TYPE="ntfs" 
/dev/sde1: UUID="9AB0F978B0F95AE9" LABEL="TV Shows" TYPE="ntfs" 
/dev/sdf1: UUID="A63801143800E561" LABEL="Movies" TYPE="ntfs" 
/dev/sda2: UUID="A45CA9315CA8FF64" LABEL="Documents" TYPE="ntfs" 
/dev/sda5: UUID="7C24E93824E8F5D4" LABEL="XP" TYPE="ntfs" 
/dev/sdc1: UUID="0CE4AFF4E4AFDDE8" LABEL="Downloads" TYPE="ntfs" 
/dev/sdd5: TYPE="swap" UUID="9ea438e5-b597-4b84-80db-a41071fbb145" 
/dev/sde2: UUID="148AF0F08AF0CF6C" LABEL="Games" TYPE="ntfs" 
/dev/sde3: UUID="A6DE530BDE52D2E3" LABEL="Desktop Dump" TYPE="ntfs" 
/dev/sde5: UUID="B66E55B86E5571DB" LABEL="Movies 2" TYPE="ntfs" 
???@???-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdd1
UUID=915433de-a600-4b1b-8ea8-3f35bb02df97 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdd5
UUID=9ea438e5-b597-4b84-80db-a41071fbb145 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd2       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by taurus on 2008-12-20
Did you remove the new kernel because I don't see it on the list, /boot/grub/menu.lst?  There is only one kernel entry in there, 2.6.24-19-generic.

Meanwhile, you have a bunch of ntfs partitions and if you want to access them, should consider installing ntfs-config and use it to configure those partitions.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by kotmfu on 2008-12-20
yes i did remove the new kernel from the list as it doesnt boot up. when i try to boot it i just get erratic hdd activity (ie it turns off and on) and then it says it cant find the disk. So i just changed back to the old kernel so i at least have an operating system

---

### Post by kotmfu on 2008-12-22
BUMP... does anyone have any ideas?

---

### Post by upchucky on 2008-12-22
advanced supergrub and knoppix to the rescue.

it was ok, but it did need to change the menu.lst.

supergrub can fix it if you have not actually removed the new kernel.

knoppix can let you edit any files you need to from its live cd environment.

---

### Post by kotmfu on 2008-12-22
what can i do with these 2 tho? there is nothing wrong with grub (as it does actually boot to a minimal shell.) and im not sure why i would need knoppix as i can get into my old kernal fine and i have no idea what i would need to edit

---

### Post by kotmfu on 2008-12-23
after some creative menu.lst tampering i got some error codes.. mostly errno=-16... and after some googling it turns out my mobo chipset(nvidia) and my dvd drive (dvr215) are incompatable when booting into the new kernel, something to do with hard resetting... i unplugged the drive and i am right now playing with the new kernel..
weirdest god damned error ever.. but at least i know whats wrong
thanks heaps all

---

### Post by KermitJr on 2009-01-19
You might be able to solve it anyway:

add the following to the kernel boot line:

rootdelay=90

and possibly add:

irqpoll

---

