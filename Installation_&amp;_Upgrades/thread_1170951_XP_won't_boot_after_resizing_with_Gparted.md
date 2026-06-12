---
title: "XP won't boot after resizing with Gparted"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by antony_css on 2009-05-26
This webpage tells the exact same problem that I encountered:
[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/")

except in my case it is windows xp.

I resized the xp partition (in sda2) because I found the windows recovery partition (in  sda1) obsolete; I already have the xp installation disk. So I deleted the sda1 partition and "grow" the sda2 to the unallocated space once occupied by sda1.

The grub bootloader in MBR works fine to me because I can boot into ubuntu (in sda4) without any problem. But if I choose "Windows XP" from the grub menu, the text "Starting up..." appears at the top left hand corner and nothing appears afterthat.

Here is the partition table of my SATA hard disk:
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf968f968

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        5716    45913738+   7  HPFS/NTFS
/dev/sda3            9543        9729     1496880   82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.
/dev/sda4            5717        9543    30731400   83  Linux
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

And here is the menu.lst file:
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
# kopt=root=UUID=0b82d154-2059-40fd-a66d-ea45d3fe50c5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

[B]title		Ubuntu 8.04.2, kernel 2.6.24-24-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=0b82d154-2059-40fd-a66d-ea45d3fe50c5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=0b82d154-2059-40fd-a66d-ea45d3fe50c5 ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet[/B]

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
[B]title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1
[/B]

```
I am sure the xp partition after resizing does not corrupt because I can always mount it from ubuntu and read the content.

So, what should I do?

P.S. Similiar problem has been posted by *Pro-reason*:
[http://ubuntuforums.org/showthread.php?t=908987]("http://ubuntuforums.org/showthread.php?t=908987")
but I found his/her situation is much more complex than mine, and he/she didn't state clearly the solution.

---

### Post by presence1960 on 2009-05-26
This is just a whim but give it a try. Your windows partition is now the first partition of your disk since the recovery partition is gone even though the name in sudo fdisk -l has not changed. In menu.lst change your Windows entry to 

```
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

see what happens.

---

### Post by antony_css on 2009-05-26
I've tried this, but the grub said there is no such partition and it refuses to boot

---

### Post by presence1960 on 2009-05-26
i was reading the 2 links you provided. Did you defrag windows prior to the partitioning operation?

Edit : here is a link to repairing XP bootloader : [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If successful you will have to restore GRUB.

---

### Post by antony_css on 2009-05-26
I followed the instruction trying to repair and restore XP bootloader, but afterthat the harddisk won't boot at all. Luckily I am able to recover the original grub boot loader using the ubuntu live cd.

I am reading this link on reinstalling the windows' core without changing the program and document setting:
[http://michaelstevenstech.com/XPrepairinstall.htm]("http://michaelstevenstech.com/XPrepairinstall.htm")

But since my install cd does not have such option (which is a home edition), now I am thinking of having a full system recovery instead (which does not alter document setting, but erase all programs installed).

---

### Post by logos34 on 2009-05-26
> **presence1960 said:**
> 
Edit : here is a link to repairing XP bootloader : [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


yes, but try just the **fixboot** command first--that may be all you need (it writes the windows bootloader code to the first sector of sda2.  When you resized the partition you changed its position). fixmbr will overwrite grub

---

### Post by antony_css on 2009-05-27
Well, I've finished the full system recovery, and I was expecting the windows boot loader would overwrite the grub; but the hard disk just doesn't boot at all.

Now I recovered the grub using the ubuntu live cd for the second time so that I can at least boot ubuntu... Any other suggestion? Should I recover the sda1 partition that I have once deleted?

---

### Post by antony_css on 2009-05-27
> **logos34 said:**
> yes, but try just the **fixboot** command first--that may be all you need (it writes the windows bootloader code to the first sector of sda2.  When you resized the partition you changed its position). fixmbr will overwrite grub

Yes, after I recovered the grub boot loader, I tried to boot xp from the boot menu. But the same issue occurred - "Starting up..." appears at the top-left hand corner and nothing appears.

EDIT: that's why I finally decided to have the full system recovery

---

### Post by lisati on 2009-05-27
I'm wondering if this will help within Ubuntu:
```
sudo update-grub
```

<aside>When I was dual-booting XP & Ubuntu on a desktop with a recovery partition, where were two entries for XP in Grub - one for the main XP installation (worked well) and one which was presumably a reference to the recovery partition (didn't work, needed to run a software-repair "wizard" to access the recovery partition) I recently completely removed Windows (recovery partition and all) from that machine, so I'm not currently in a position to play around in a search for suggestions</aside>

---

### Post by presence1960 on 2009-05-27
> **lisati said:**
> I'm wondering if this will help within Ubuntu:
```
sudo update-grub
```

I would try that as GRUB definitely was not updated during the upgrade process to Jaunty. Is it me or have I noticed a lot of threads with problems for those who have used the upgrade process to get Jaunty? I always do a clean install, just my preference.

Edit: it is too early for me yet, I don't know why I thought the OP upgraded to Jaunty. I guess I need a little caffeine to get me going. I was reading another thread with that problem. I would try it though, what have you got to lose!

---

### Post by perspectoff on 2009-06-04
Get your Windows XP installation disk and boot into it.

Go into the Recovery Console (option R).

Choose your Windows installation (usually 1). When presented with the command line (e.g. C:\WINDOWS> ), type:

chkdsk /r

Chkdsk is usually run automatically for you when you restart Windows after resizing the partition (with GParted).

However, if you resize the partition (with Gparted) and then install Ubuntu directly immediately afterwards, without rebooting Windows first, you don't give a chance for chkdsk to be run by Windows. Since Ubuntu changes the Master boot record, all the settings get diced up.

I had to fix Windows and repair the Master boot record in order for the changed partition to be recognized, and then had to re-install Ubuntu after that.

After chkdsk /r,

also try (also from the XP Recovery console):

 fixmbr

 and

 fixboot c:

and

 bootcfg /rebuild 

Hopefully this recreates your boot files on the Windows partition so that it can be booted. 

If this doesn't work, using the Linux utility testdisk often does. Use it from your Ubuntu partition.

 sudo apt-get install testdisk
 sudo testdisk

---

