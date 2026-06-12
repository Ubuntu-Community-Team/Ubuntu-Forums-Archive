---
title: "How add Windows 7 In GRUB?"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by koekjestrommel on 2009-05-16
How do I add Windows 7 into my GRUB.

I have 3 OS's. XP Ubuntu and Windows 7.

When booting, my GRUB shows up, and I can choose from XP and Ubuntu. When I click on XP I go to the XP startup menu where I can choose from Windows 7 OR an earlier version of windows. Is there any way how I can add Windows XP and Windows 7 directly to my grub?

PS: I'm a linux noob, so don't make it too hard ;)

---

### Post by coffeecat on 2009-05-16
It's not too difficult. You just need to add another stanza to your grub configuration menu (menu.lst). But we need a bit of information first. Post the contents of your /boot/grub/menu.lst file. Post them in [noparse]```

```[/noparse] tags to retain the formatting otherwise it's difficult to read. Also, open a terminal and post the output of:

```
sudo fdisk -l
```... so that we can see your partition layout.

---

### Post by koekjestrommel on 2009-05-16
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
# kopt=root=UUID=99c2c8d2-2698-49a1-b825-8c6756fc6b88 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=99c2c8d2-2698-49a1-b825-8c6756fc6b88

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		99c2c8d2-2698-49a1-b825-8c6756fc6b88
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=99c2c8d2-2698-49a1-b825-8c6756fc6b88 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		99c2c8d2-2698-49a1-b825-8c6756fc6b88
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=99c2c8d2-2698-49a1-b825-8c6756fc6b88 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		99c2c8d2-2698-49a1-b825-8c6756fc6b88
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)      NOTE VISTA RECOVERY PARTITION
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)       NOTE XP AND WIN 7
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

```

```
joost@joost-laptop:~$ sudo fdisk -l
[sudo] password for joost: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b63dfd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1529    12281661   12  Compaq diagnostics
/dev/sda2   *        1530        8112    52877947+   7  HPFS/NTFS
/dev/sda3            8113       11395    26370697+  83  Linux
/dev/sda4           11396       30401   152665695    5  Extended
/dev/sda5           11396       20594    73890936    7  HPFS/NTFS
/dev/sda6           20595       30401    78774696    7  HPFS/NTFS
joost@joost-laptop:~$ 




```

NOTE: Win7 is on sda5

---

### Post by coffeecat on 2009-05-16
> **koekjestrommel said:**
> NOTE: Win7 is on sda5

Right. :( I didn't expect that - Windows on a logical partition. I don't believe this is going to be possible with grub. When I said "not too difficult", I was assuming you had XP and W7 on two primary partitions, and then it really would have been straightforward. But as you probably know, Windows can only reside on a logical partition if it has all its boot files on a primary. Clearly the W7 boot files are on the XP partition, so grub will have to point there for both versions of Windows.

If it is possible with grub, then you'll need someone with experience of Windows boot loaders. Sorry I can't help any further - I've always taken the easy way with Windows.

Good luck.

---

### Post by koekjestrommel on 2009-05-16
I had to do it on a logical partitions, i'm out of space for more partitions :(

No other suggestions?

---

### Post by Mark Phelps on 2009-05-16
> **koekjestrommel said:**
> Is there any way how I can add Windows XP and Windows 7 directly to my grub?
Yesy ... but it involves more than just GRUB changes.  You will have to move the necessary Windows OS Boot files each to their own separate partitions, because right now, they're all located in the XP Partition.  It's not an easy process and involves editing not only the menu.lst file but also boot loader files in MS Windows. You also will need to install easyBCD and mess with the Vista and Seven loader files.  

Word of warning -- I tried it on mine and messed it up so bad I had to restore to get functionality back.

So, unless using the MS Windows boot menu to select each of the different Windows OS's is simply not working, I would leave it alone.

Perhaps others who have been more successful can give you specific advice.

---

### Post by coffeecat on 2009-05-16
> **koekjestrommel said:**
> I had to do it on a logical partitions, i'm out of space for more partitions :(

Unless you do a reinstall of both Ubuntu and W7. Then you could re-order your partitions to best use the space, and give yourself a Linux swap partition which seems to be missing.

If you did want to go down that road, here's what I would do:

1 Backup all personal files. :wink:

2 Delete sda3, 4, 5 and 6.

3 Create a new sda3, formatted NTFS for W7

4 Create a new sda4 extended partition containing 3 logicals: one ext3 for Ubuntu root, one swap for swap and 1 NTFS to replace the present sda6 which I guess is a data partition - something like E:\ in Windows I suppose.

Of course, if your present sda3 is the right size for W7, you could simply reformat it to NTFS, and then redo the logicals in sda4. Either way, it's a bit better than having Ubuntu on a primary, when Linux is quite happy on a logical, and having Windows on a logical with all the problems that entails.

---

### Post by cyphur335 on 2009-05-16
When I ran Vista and XP on the same hard drive, I used Grub to point to Vista, and Vista had it's own bootloader menu which allowed me to pick from the two. 

However, in my case, Vista was on the primary partition.  I am not sure how Windows 7 will behave as I haven't tried installing it yet.

---

