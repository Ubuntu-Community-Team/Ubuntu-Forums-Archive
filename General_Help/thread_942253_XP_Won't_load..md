---
title: "XP Won't load."
date: 2008-10-09
forum: General Help
---

### Post by Captain Chaos on 2008-10-09
Today I decided to install Ubuntu 8.04 and dedicate 20 gigs of space in my main pc, now Windows XP won't start. I can see my documents from XP and everything else in Ubuntu but I'm not ready to switch just yet. Anybody want to help me? I'm also having trouble in sites like youtube, I'm not getting any sound.

---

### Post by neilengineer on 2008-10-09
When you power on your PC, use up and down key to select OS, should find something like Other OS(Windows XP) there.

For Youtube, Ubuntu doesn't have flash player preinstalled, you need to download and install. Firefox shall inform you when you browse webpages with Flash.

---

### Post by Captain Chaos on 2008-10-09
> **neilengineer said:**
> When you power on your PC, use up and down key to select OS, should find Windows XP there.

For Youtube, Ubuntu doesn't have flash player preinstalled, you need to download and install. Firefox shall inform you when you browse webpages with Flash.

I know about selecting OS, but the screen won't get past "Starting..." I have already installed flash player but do not get any sound when I visit sites like youtube.

---

### Post by WWSmith36 on 2008-10-09
For your windows boot issue, please post the output of 

```
sudo fdisk -lu
cat /boot/grub/menu.lst
```

---

### Post by WWSmith36 on 2008-10-09
For flash issues, I suggest you enable the multiverse repository and install ubuntu-restricted-extras.  It contains the flashplugin-nonfree.

---

### Post by Captain Chaos on 2008-10-09
> **WWSmith36 said:**
> For your windows boot issue, please post the output of 

```
sudo fdisk -lu
cat /boot/grub/menu.lst
```

Here is the result.

> 
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfb29fb29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   445064759   222532348+   7  HPFS/NTFS
/dev/sda2       445064760   488392064    21663652+   5  Extended
/dev/sda5       445064823   486496394    20715786   83  Linux
/dev/sda6       486496458   488392064      947803+  82  Linux swap / Solaris
gabriel@gabriel-desktop:~$ 



> gabriel@gabriel-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=851a0dab-3e8f-4bc0-8ca1-6d126735e2a8 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=851a0dab-3e8f-4bc0-8ca1-6d126735e2a8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=851a0dab-3e8f-4bc0-8ca1-6d126735e2a8 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

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
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1




---

### Post by abhilashm86 on 2008-10-09
u need to make a dual boot for xp to run or you better make a separate disk drive for windows xp.The problem is linux becomes "lost +found" format,that means it becomes invisible with any other operating systems..................even i had same problem

---

### Post by WWSmith36 on 2008-10-09
Your partition table and menu.lst file look good.  What sort of error message are you getting while trying to boot to windows.

---

### Post by Captain Chaos on 2008-10-09
> **WWSmith36 said:**
> Your partition table and menu.lst file look good.  What sort of error message are you getting while trying to boot to windows.

It doesn't go past the "Starting up..." message.

---

### Post by WWSmith36 on 2008-10-09
When you resize Windows (shrink it) in order to make space to install Ubuntu ?

---

### Post by WWSmith36 on 2008-10-09
If your windows partition was resized, it might contain errors preventing it from booting properly.  Before resizing windows partitions, they must be defragmented 2-3 times before shrinking them.

You will have to boot to your Windows install CD and choose ´R´ at the first screen to get into Recovery Console.  When you get to the command prompt, run chkdsk

---

### Post by neilengineer on 2008-10-09
> **Captain Chaos said:**
> It doesn't go past the "Starting up..." message.

Before you see "Starting up...", press "up" and "down" key to select.

---

### Post by Interpreter on 2008-10-09
The point is, he can select  "boot XP" just fine, ..and after that it wont get him past "starting up..."

Had this one myself.
Did not fix it, actually reinstalled vereything from scratch ((.

---

### Post by musthafapm on 2008-10-09
Hi all,

I am new to ubuntu. I installed ubuntu first and then windows xp. For the last two weeks GRUB was working fine. Now It is not loading windows xp. The output of sudo fdisk -l command is as follows. Pls guide me... 




 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       35023   230123092+   f  W95 Ext'd (LBA)
/dev/sda5            6375       12748    51199123+   7  HPFS/NTFS
/dev/sda6           12749       17847    40957686    7  HPFS/NTFS
/dev/sda7           17848       18343     3984088+   7  HPFS/NTFS
/dev/sda8           18344       23206    39062016    b  W95 FAT32
/dev/sda9           23207       28069    39062016    b  W95 FAT32
/dev/sda10          28070       32932    39062016    b  W95 FAT32
/dev/sda11          32933       33181     2000061   82  Linux swap / Solaris
/dev/sda12          33182       35023    14795833+  83  Linux
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 1026 MB, 1026555904 bytes
178 heads, 44 sectors/track, 64 cylinders
Units = cylinders of 7832 * 2048 = 16039936 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          64     1002408    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 44) logical=(0, 1, 1)

---

### Post by caljohnsmith on 2008-10-09
Captain Chaos, how about booting your Windows Install CD like WWSmith36 mentioned and run:
```
chkdsk /r
```
Let us know if that helps boot Windows at all, and if not, we can work from there.

---

### Post by Captain Chaos on 2008-10-09
> **caljohnsmith said:**
> Captain Chaos, how about booting your Windows Install CD like WWSmith36 mentioned and run:
```
chkdsk /r
```
Let us know if that helps boot Windows at all, and if not, we can work from there.

The problem is that I don't know where the cd is. :(

---

### Post by Captain Chaos on 2008-10-09
Also one of my fans is going on and off, that it is driving me crazy. Does anybody know how to fix this?

---

### Post by caleb12 on 2008-10-09
you could try opening a terminal and running 

sudo ntfsfix /dev/sda1 

ntfsfix is part of ntfsprogs, which may need to be installed first.

sudo apt-get install ntfsprogs

According to the manpage, it does some very basic file system checks, resets the NTFS journal and schedules a disk check on the next startup... Who knows it may do something for you...

---

### Post by TeXtonyx on 2008-10-09
I've seen Testdisk fix this Windows Starting Up hang problem. Perhaps somebody reading
has some expertise with the Testdisk program. Otherwise, I think  a repair installation
using the XP install cd will be needed. I borrowed this advice from meierfra about using 
Testdisk.  sda is the first drive and sdb is the second drive and so on. 

"You might try testdisk to rebuild the Boot sector:

Code:

sudo apt-get install testdisk
sudo testdisk /dev/sda

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"

TeX: If it reports "Extrapolated boot sector and current boot sector are different."
Then "Write" the rebuild and it hopefully will report they are now the same, so reboot and
see if the Rebuild fixes the problem.

---

### Post by Captain Chaos on 2008-10-09
> **TeXtonyx said:**
> I've seen Testdisk fix this Windows Starting Up hang problem. Perhaps somebody reading
has some expertise with the Testdisk program. Otherwise, I think  a repair installation
using the XP install cd will be needed. I borrowed this advice from meierfra about using 
Testdisk.  sda is the first drive and sdb is the second drive and so on. 

"You might try testdisk to rebuild the Boot sector:

Code:

sudo apt-get install testdisk
sudo testdisk /dev/sda

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"

TeX: If it reports "Extrapolated boot sector and current boot sector are different."
Then "Write" the rebuild and it hopefully will report they are now the same, so reboot and
see if the Rebuild fixes the problem.

[SIZE="6"]THANK YOU!![/SIZE] :cool::biggrin:

---

### Post by dgmdoug on 2009-02-10
Hi all, I was suffering from exactly the same problem and TeXtonyx advice worked a treat. I had installed Ubuntu to dual boot with the installer, xp was installed first on a single partition and the installer used to resize. Initially linux would boot, but not windows, simpling hanging at the "starting up" line. Once testdisk was run both OSes boot fine.

Glad I found this thread!

---

