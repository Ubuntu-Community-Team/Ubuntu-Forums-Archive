---
title: "XP does not install after ubuntu/Vista"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by virtualcoder on 2008-01-19
Hi all,
  I've been trying to triple boot my system using vista, ubuntu, and xp.
I've succeded in installing Ubuntu, and Vista came with the laptop by default. Now when I'm trying to install XP, I run into different types of problems. I'm not sure whether the problem is with GRUB or something else.

 My system specifications are :

HP Pavilion, model dv6500 notebook,
2.2Ghz, 2Gb Ram, 250 GB hard drive, Vsita pre-installed.

I bought an external hard drive for the purpose of installing multiple operating systems, and its specs are:

Maxtor One Touch III, 500GB external hard drive.

I've been experimenting a lot with getting these systems installed, so the current existing partitions (in order) are:

(Approx Sizes)
Internal Hard Drive (250GB total):
180GB NTFS Windows Vista
6.5GB NTFS System Backup
0.5GB ext3 Grub installed
50GB NTFS Failed XP install

External Hard Drive (500GB):
125GB ext3 Ubuntu
125GB NTFE Failed XP install
250GB Free space


First I tried installing XP on the external hard drive in the second partiion.
XP detected that partition, and it copied its setup files to the partition.
Then when it restarted the system, well firstly grub didnt show windows XP on the list. So I tried adding the entry for XP manually, something like:

title Windows XP
rootnoverify (hd1,1)
savedefault
makeactive
chainloader +1

So when I choose this option in the GRUB menu, it just gives me a blank screen.
I gave up on this option and used some free space to make a fourth partition on the internal hard drive.
I gave it a size of 50gb, but the problem was that XP did not detect that paritition or any other partition on the internal hard drive.

I read something about Windows being picky about being installed only on the primary paritition, if that is the case, and maybe thats why that it detects Windows Vista installed on the primary partition of the internal hard drive, so its not listing any of the parititions of that hard drive in the first place.
On my external hd, linux is installed on the primary partition, so that might be why it is showing all partitions for that hd.

If all this is true, I could instead re-install Linux onto the fourth partition of the internal hd, and try installing XP on the first partition of the external hd.

I dont want to experiment anymore, since I've spent a lot of days trying to install all these systems and I'm running out of time since I need to use these OSes.

If someone knows what problem I'm facing then please help me out, Thanks a lot!

If I'm posting this msg in the wrong place then please excuse me and direct me to the right place.

---

### Post by logos34 on 2008-01-20
> **virtualcoder said:**
> 
First I tried installing XP on the external hard drive in the second partiion.
XP detected that partition, and it copied its setup files to the partition.
Then when it restarted the system, well firstly grub didnt show windows XP on the list. So I tried adding the entry for XP manually, something like:

title Windows XP
rootnoverify (hd1,1)
savedefault
makeactive
chainloader +1

So when I choose this option in the GRUB menu, it just gives me a blank screen.

Read[ this ]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")and [this]("http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows").

---

### Post by virtualcoder on 2008-01-21
No luck. I think I've tried to install XP 7 or 8 times by now, never knew it could be this troublesome.

Can someone tell me why XP cant detect my internal hard drive?

I tried installing it on my second partition of my external hd and got the error:
Starting up...
A disk read error occurred
Press Ctrl+Alt+Del to restart

Also after I installed XP, it messed up my grub so I re-installed grub.

Using the gparted live cd, I tried booting directly into my XP partition, but for some reason it doesnt show that partition in the boot list of "Boot from Partition ..."


I searched this error up but havent been able to find a solution that applies to my situation. For XP, I've added the following entry in menu.lst:

#Manually added entry for windows xp
title		Windows XP Professional
unhide		(hd1,1)
hide		(hd0,0)
hide		(hd0,1)
rootnoverify	(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

----------------------------------------------------

The output of "sudo fdisk -l" is:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8eaa8eaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23068   185293678+  17  Hidden HPFS/NTFS
/dev/sda2           29465       30331     6964177+  17  Hidden HPFS/NTFS
/dev/sda3           30332       30401      562275   83  Linux
/dev/sda4           23069       29464    51375870    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8af2ce83

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       16413   131837391   83  Linux
/dev/sdb2   *       16414       32986   133122622+   7  HPFS/NTFS

-------------------------------------------------------




The menu.lst file contains ('x' is for file start and end for readability sake):

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

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
timeout		15

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
# kopt=root=UUID=611abc1c-56fe-49b1-bc0e-653e577c5e85 ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=611abc1c-56fe-49b1-bc0e-653e577c5e85 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=611abc1c-56fe-49b1-bc0e-653e577c5e85 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


#Manually added entry for windows xp
title		Windows XP Professional
unhide		(hd1,1)
hide		(hd0,0)
hide		(hd0,1)
rootnoverify	(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx


If someone's thinking why I need XP when I already have Vista, well its because Vista is extremely incompatible with "a lot of old stuff" and I intend to use XP to cover up that lack of support.

Also Im new to having linux on my home computer, but have used it at work and university, so my aim is to become a hardcore ubuntu user. Hope me the best :)

Any help is greatly appreciated!

---

### Post by virtualcoder on 2008-01-21
I've tried without the makeactive line and still the same disk read error.

Also I tried hiding the Ubuntu partition with hide (hd1,0). It didnt work and my linux partition stopped working. I've fixed that but I'm back to square one, no XP.

More information, I've got Ubuntu 7.10, 64 bit version.
Do you suggest using the 32 bit instead?

I'm trying to install XP professional with SP2, I think this is the 32 bit version, so should that be a problem?
My system is a Core2duo intel machine, which is supposed to be a 64 bit machine.

Can someone please help!

---

### Post by virtualcoder on 2008-01-26
Finally got xp installed, after formatting the whole system.
Then first i used the vista recovery disks to install vista back to factory condition,
then played around with the partitions until i had two more partitions for ubuntu and xp
on the same hard drive.
Installed xp using sata drivers from hp web site.
Then installed ubuntu after that.
Problem is im not being able to get vista back after installing xp, since i dont have the vista installation dvd, only the recovery disks.
So ill have to recover vista somehow within xp.
Is there any software out there that will run on xp to get back vista.
easybcd doesnt work on xp, so that doesnt seem to be an option.

---

### Post by virtualcoder on 2008-01-26
im not sure if the super grub disk can help, since when i boot from the partition where vista was installed, xp loads up instead.

Im sure im very close to the solution and to finally creating a triple boot on my laptop, although there is much to be done for xp to get it to recognize many of my laptop's hardware.

Any ideas ppl??

---

### Post by virtualcoder on 2008-01-28
Ahh, finally got a triple boot working!
For all those ppl out there who have a laptop which came with Vista pre-installed, if you want to install Windows XP, you might have to find all the drivers for your hardware to make xp run, as well as its installation.
I've still not got my xp to recognize my ethernet card and my sound card, but it now recognizes my graphics geforce 8400m gs card.

similar case is with ubuntu, except that the only thing ubuntu is not recognizing is my sound card, everything else works perfectly.

Finally i can start installing all my favorite apps on these systems and get familiar with ubuntu!

Cheers to all the info out there!

---

