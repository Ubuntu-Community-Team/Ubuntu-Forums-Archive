---
title: "Wubi Upgrade to Full system FAILED!"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by blade1950 on 2009-04-13
After playing with Ubuntu in the form of a Wubi install I tried the upgrade with LVPM to bring Ubuntu into an active state in preparation for dumping MS XP. My system is a multi HDD system with Wubi on the first physical HDD all by itself. My second HDD is a BIG (1TB) one that is split into 3 partitions. The first (hdb1, AKA hd1,0) is of course MS XP while the second is Ubuntu (hdb2, AKA hd1,1). The third is the swap partition. The transfer went well as far as I can tell. I can mount and browse the Ubuntu HDD installed on hdb2 while in the Wubi installed system. When I tried to boot with the Grub menu I get the error 17. I understand that basically means that Grub cannot properly determine the HDD layout. I attempted to reinstall Grub from the Ubuntu CD using the terminal commands: grub, root (hd1,1) but I got the error that the drive was not valid. I then went to my Wubi install and tried the same commands with the same results even though the drive was mounted. I was even able to set the boot flag on the partition thinking that was the trouble. I have tried the Super Grub Disk but I lack confidence as to my using it correctly with the problem.

Make no mistake, I WILL DUMP MS. Even if I have to slick my HDD and start over fresh with Ubuntu on this desktop PC.

Any help is MOST appreciated.

---

### Post by mikewhatever on 2009-04-14
Can you post some more info while running from the live cd. Perhaps Ubuntu doesn't see your HDDs in the same order or something.
Run **sudo fdisk -l** form Terminal and post the output.

---

### Post by blade1950 on 2009-04-14
I want to KNOW what I'm doing and understand Ubuntu as much as I can so I started over again to try to learn more about HOW this works. I reformated the upgraded Wubi install of Ubuntu to a blank state and reinstalled Wubi on the first HDD (a IDE drive BTW). The BIG (1TB) HDD is a SATA. I am posting the surrent results from the command "sudo fdisk -l" that I did after I got Wubi re-installed on the IDE HDD.
* * * * * * * * * *
Results of sudo -l command

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7247d4fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13076   105032938+   7  HPFS/NTFS
/dev/sda2           13077      121601   871727062+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfce2b218

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe7e6c2c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005fa98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001    7  HPFS/NTFS
* * * * * * * * * *
 Right away I noticed that the HDD are NOT in the same order as they were before I did the re-install/reformat. The sda and sdb drives are reversed.
The sdc and sdd HDD are USB external data only HDD. I'm now wondering if the upgrade of Wubi to the sda2 location will work as advertised. I STILL want to learn HOW this ALL works (Grub, etc.).

If I split hda2 into a ext3 and swap drive partition and upgrade Wubi to the ext3 partition do I need to set the boot flag or what?????

Terry

---

### Post by louieb on 2009-04-14
> **blade1950 said:**
> .. do I need to set the boot flag or what?????

Terry
Linux does not care if the boot flag is set or not. Also Linux can be installed in a primary or logical partition - makes no difference.  

Have not used WUBI or LVPM.

---

### Post by blade1950 on 2009-04-16
**[SIZE="6"]UPDATE[/SIZE]**

**I re-updated Wubi to my HDD using LVPM and was able to boot into that install using the latest Super GRUB Disk. I then ran "sudo fdisk -l" again and got this:**

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfce2b218

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7247d4fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13076   105032938+   7  HPFS/NTFS
/dev/sdb2           13077      121601   871727062+  83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe7e6c2c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005fa98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001    7  HPFS/NTFS
[B]
I noted that sda and sdb switched places AGAIN. I wanted to know what UUID was so a quick Google gave me the command "blkid"

And this is what that command returned:

[/B]/dev/sda1: UUID="ACE04F8EE04F5DA8" LABEL="WUBI-1" TYPE="ntfs" 
/dev/sdb1: UUID="326CB9166CB8D5B7" LABEL="MASTER" TYPE="ntfs" 
/dev/sdb2: UUID="b45ab97a-b9c8-477b-9998-d7e92483f14c" TYPE="ext3"
[B]
It looks to me like the HDD swap is the trouble. I noted that the UUID returned for sdb2 is a match in my menu.lst file as shown below:

[/B]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=b45ab97a-b9c8-477b-9998-d7e92483f14c  ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b45ab97a-b9c8-477b-9998-d7e92483f14c  ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b45ab97a-b9c8-477b-9998-d7e92483f14c  ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b45ab97a-b9c8-477b-9998-d7e92483f14c  ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b45ab97a-b9c8-477b-9998-d7e92483f14c  ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

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
chainloader	+1


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title Windows
root (hd1,0)
makeactive
chainloader +1
boot


title Microsoft Windows XP Home Edition
root (hd0,0)
makeactive
chainloader +1
boot
[B]
All the elements for root, kernal, and initrd appear correct. Booting into windows using the second title entry after "### END DEBIAN AUTOMAGIC KERNELS LIST" seems to work. It would appear that the use of the UUID in the menu.lst/GRUB system is not working. Thank goodness for Super Grub Disk and booting into Linux directly.[/B]

---

### Post by blade1950 on 2009-04-17
Yet Another Update on my progress.

I found a great little script(boot_info_script031.sh) that shows a whole host of info for me to review regarding my learning experience. I have uploaded the file for your review in helping me through this.

I am now looking at the groot entry as well as the use of UUID and how they are related. I have not, as yet, discovered the real trouble.

---

### Post by blade1950 on 2009-04-17
[B][SIZE="5"]I GOT IT!!!!!!!!

WOW!!!!

Here is the answer...

[http://www.linuxhaxor.net/2008/12/06/graduate-from-a-wubi-install-to-a-dedicated-partition/](http://www.linuxhaxor.net/2008/12/06/graduate-from-a-wubi-install-to-a-dedicated-partition/)

Almost at the bottom of the page read what Ben has to say regarding the lines AFTER "## ## End Default Options ##". "()/ubuntu/disks" is NOT to be used there. That was part 1. The last part was discovering that my SATA drive is actually drive0 and not the ata drive as reported.

IT WORKS NOW!!!!

LVPM needs to be fixed to stop this from happening though.[/SIZE][/B]

:):D:popcorn::biggrin:\\:D/

---

