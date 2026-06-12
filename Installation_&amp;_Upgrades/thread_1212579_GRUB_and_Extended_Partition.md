---
title: "GRUB and Extended Partition"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by jfreak53 on 2009-07-13
I'm having a lot of trouble getting grub to work with a certain setup of mine and I don't know where to go with it.

Here is the setup.  I have two IDE drives, one 80GB one 20GB set as secondary master.  Linux I have installed on the second 20GB drive and the first drive has the grub boot loader and two windows xp system (Seperate systems), one for games, stripped down, and one for work.  The third partition is just for storing files, it's an extra part.  The primary partition on this drive is the work xp part, and the extended partition with two logicals as the games and extra part, in that order.  Now grub works fine, for booting linux and the work partition, primary part on first drive.  No problems, loads right up.  But!  It will not boot my first logical partition on the extended space, the games partition.  Now just incase you would like to know, the grub bug where it won't display the logicals inside of the windows systems to windows isn't here, I don't have a problem with that, the other NTFS partitions display just fine inside both work and games system.  I can get games to boot, but I have to edit boot.ini and add a windows bootloader inside of the work partition.  Which sucks, I want grub to do it's job fully.

Here is the setup for the secondary boot to xp, the games partition, which again is the first logical inside the extended partition on my first drive:

```
title		Games
rootnoverify	(hd0,4)
savedefault
makeactive
chainloader	+1
```

Now according to what I see when I search for info on google on how to boot extendeds it says to use hd0,4.  That 4 is the first logical inside an extended.  But when I do that it gives me this error:

> Error 18: Selected cylinder exceeds maximum supported by BIOS

Now when I try it just root, instead of the rootnoverify it gives me this one:

> Error 12: Invalid device requested

It also gives me error 12 if I try another partition number like 2 or 1.  And of course 3 tells me that the partition doesn't exist.

Ok so now, how do I boot that logical xp partition using grub??

Here is my complete grub file:

```
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
default		3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

# Splash Image
splashimage=(hd1,0)/boot/grub/splashimages/edgy.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/

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
# kopt=root=UUID=aae63196-94dd-47c9-a0c1-bf96dd279832 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=aae63196-94dd-47c9-a0c1-bf96dd279832

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
# defoptions=splash vga=758 quiet

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
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		aae63196-94dd-47c9-a0c1-bf96dd279832
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=aae63196-94dd-47c9-a0c1-bf96dd279832 ro splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		aae63196-94dd-47c9-a0c1-bf96dd279832
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=aae63196-94dd-47c9-a0c1-bf96dd279832 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Work
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

title		Games
rootnoverify	(hd0,4)
savedefault
makeactive
chainloader	+1

```

Thanks in advance for any help.

---

### Post by merlinus on 2009-07-13
Post results of

```
sudo fdisk -l
```

---

### Post by jfreak53 on 2009-07-13
Here are the results:

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38223821

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        9728    47423880    f  W95 Ext'd (LBA)
/dev/sda5            3825        7011    25599546    7  HPFS/NTFS
/dev/sda6            7012        9728    21824271    7  HPFS/NTFS

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24581055

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2198    17655403+  83  Linux
/dev/sdb2            2199        2434     1895670   82  Linux swap / Solaris

---

### Post by merlinus on 2009-07-13
And does your windows hdd boot first in bios?

If so, then the menu.lst entries seem correct, with sda5 being your games partition.

You also might try placing a boot flag on sda5.

---

### Post by jfreak53 on 2009-07-13
Correct this drive is the bios boot drive, ide-0 in the bios.  And yes sda5 is the games partition.

Boot flag on partition, ok you mean making this the main partition the system boots from if there was no boot loader?  I will try.

---

### Post by merlinus on 2009-07-13
Add a boot flag to sda5, and leave the one on sda1 as well.

---

### Post by louieb on 2009-07-13
Don't think its a GRUB problem. Grub doesn't care its just chain loading the code in the boot sector of the partition. Doesn't  matter if the partition is logical or primary. 

> I can get games to boot, but I have to edit boot.ini and add a windows bootloader inside of the work partition

Thats the MS way of dual booting it only keeps 1 copy of its boot loader. You can try putting the loader files back in the 2nd copy of XP. But then you you run into the problem of the boot flag. The norm is only 1 partition per drive can have its boot flag on. 
[Multi-Booting with Windows in an Extended Partition]("http://www.goodells.net/multiboot/principles.htm")

---

### Post by dandnsmith on 2009-07-14
I agree that it isn't a GRUB problem per se.
I'm willing to bet that the 2nd XP install was never fully independent (made so, for example, by hiding the first install before doing the install), and was booted via the boot menu of Windows.

The best that can be done easily is to get the Windows boot working from the GRUB, and then select the appropriate Windows version to run.

To get a boot flag you can get GRUB to place one via *makeactive*, but that doesn't really help, as the rest of the Windows booting chain is too monomaniac.

I tried quite extensively to get this to work a couple of years back, and capitulated in the end.

---

### Post by jfreak53 on 2009-07-14
Ok as it stands now, still no go.  I changed the boot flags last night before I shut down and today still same errors with new boot flags.  So still no go.  Would it work if I hid partition 1, primary and booted xp cd, then ran fixboot and fixmbr to add a boot to the logical seperate then tried it?  Or got any more ideas?

---

### Post by merlinus on 2009-07-14
You can try, but IIRC windows will only run on a primary partition.

You are probably better off using grub to boot to your sda1 partition, and set up the window bootloader to go to either that install or your games.

---

### Post by dandnsmith on 2009-07-15
> **merlinus said:**
> You can try, but IIRC windows will only run on a primary partition.

Not entirely true, as I have a couple of PCs with XP installed in a logical partition inside an extended partition.
However, it does seem to have a dependency which may mean the bootloader code has to be in an active primary (both my PCs configured this way have an older Windows in a primary.

---

### Post by presence1960 on 2009-07-15
> **merlinus said:**
> You can try, but IIRC windows will only run on a primary partition.

You are probably better off using grub to boot to your sda1 partition, and set up the window bootloader to go to either that install or your games.
Your Games windows install is on an extended partition. Windows does not like booting from an extended partition. Windows should be on a primary partition. I am not saying it can't be done, but from the threads I have seen on here most, not all are unsuccessful trying to run windows from an extended partition. Maybe one of the few who have successfully done it will share the solution with you.

---

### Post by jfreak53 on 2009-07-15
For right now I'm leaving it the way it is, at least it works right!  :lolflag:

But I WILL FIGURE THIS OUT!!  There has to be a way to do it, I cannot believe that Windows can bump out grub, no way. ha ha

Thanks guys :p

---

### Post by louieb on 2009-07-25
Herman knows how. [http://ubuntuforums.org/showpost.php?p=7488261&postcount=17](http://ubuntuforums.org/showpost.php?p=7488261&postcount=17)

---

### Post by bosco24 on 2009-07-26
I had the same problem. Wasn't happy at all with ubuntu's installer.
I ended up using a SLAX USB stick to boot into XP using the following module.
[http://www.slax.org/modules.php?action=detail&id=2577](http://www.slax.org/modules.php?action=detail&id=2577)
Was pretty easy.  Just had to edit some boot files on the stick. But at least now
I'm able to access my XP partition and boot it correctly.
Found a page explaining how to remove the ubuntu partitions and restore the 
MBR using Disk Manager in XP and the restore option on a legit XP install CD.
Must say I was very dissapointed in the installer for not configuring GRUB
correctly the first time around.
Gonna stick with SLAX here,...works everytime. And I can just run it off my usb stick
with no need to install to HD at all.
Shouldn't have to jump through hoops to make it work.
If they fix the installer,...I might consider trying it out again.
I'll keep checking back and see if they fix it.
Hope this helped some.

Dan

---

