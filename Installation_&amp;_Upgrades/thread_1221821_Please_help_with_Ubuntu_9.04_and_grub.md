---
title: "Please help with Ubuntu 9.04 and grub"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by hoopy10 on 2009-07-24
Ok, here is my situation.  I have spent many hours trying to get it to work but no luck.  Right now, I have WinXP that was installed first on the first partition on the primary hd.  Then I installed Ubuntu 9.04 was installed next on the first partition on the secondary hd.  Grub works great and everything is fine.  Now here comes the problem.  I install Windows 7 next on the third parition on the primary hd (had to split the second partition to make room for Win7, thus why it went on the third partition and not the second.)  

Win7 overwrote the grub loader.  No problem, I used the livecd to get back into ubuntu and reloaded grub.  Then went into menu.lst and added Win7's boot info:

title    Windows 7
rootnoverify   hd(0,2)
savedefault
makeactive
chainloader   +1

Reboot and I see the Windows 7 option under the already Windows XP option.  I chose Wndows 7 but then I get:

Starting .....
NTLDR is missing
Press CTL-ALT-Del to reboot

I have tried everything but can't get Windows 7 to boot.  Please help and sorry about the long post.  Thanks.

---

### Post by merlinus on 2009-07-24
First of all

rootnoverify   hd(0,2)

shoud be

rootnoverify   (hd0,2)

and you might post results of

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by philcamlin on 2009-07-24
heres what ytou want 

[http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm)

---

### Post by hoopy10 on 2009-07-24
Fellas, very weird.  I booted from the Win7 dvd, and let it find and repair any boot errors.  It found some and repaired them.  Then when I booted back up, grub loaded.  I choose the WinXP option and it loaded the Win7 boot loader.  So now I can boot into Winxp and Win7 but it's like I have to go through 2 boot loaders.  I don't really mind, but weird as hell.  What do you think?

---

### Post by merlinus on 2009-07-24
Another thread detailed the same situation and result.  Windows does things according to the whims of Microsoft, so the fact that it works at all is better than nothing.

:D

For checking, however, post results of

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by Herman on 2009-07-24
Windows always does that, it has nothing to do with Ubuntu or GRUB.
What you have there is a 'Microsoft Default Dual Boot', where the first Windows installation is in a primary partition and the Windows installation you add afterwards gets automatically installed in a logical partition. 
Your Windows XP in the primary partition becomes your 'boot partition' for Windows 7 in the logical partition, and Windows 7 has copied it's boot loader files into Windows XP.
As long as you keep Windows XP, everything will be fine, except you can't boot Windows 7 without booting through Windows XP.

[Understanding MultiBooting and Booting Windows from an Extended Partition]("http://www.goodells.net/multiboot/index.htm")
Back in the Windows 95/98/XP days, people used to be able to use GRUB's 'hide' and 'unhide' commands for setting up a dual boot between two Windows, so one Windows didn't detect the other. Now Microsoft has become smarter and with recent version of Windows even that doesn't work anymore, Windows Vista and Windows 7 ignore the 'hidden' flag, and even detect Windows in other hard disks. 

I'm sure Microsoft would be smart enough to come up with a decent way to dual boot if they tried. I imagine they probably think dual booting two Windows installations is not in their interest. Microsoft is all about making money, and they want you to pay for new software that's made for Windows 7, not keep using your old Windows XP software that you already have paid for. I'm only guessing.
It's too bad they don't bother to inform their paying customers about what they're doing behind the scenes when the customer sets up a Windows-Windows dual boot.  It's all done silently, without informing the user. Some people might later delete their first Windows, (because it needs to be re-installed for some reason), and lose the use of their newer Windows installation that way. Very scary for the average user!
I guess that's to punish people for trying to save their money.

It is possible to fix it by copying your Windows 7 boot loader back into Windows 7, but it's a bit of messing around. There are a few other things you need to do to get Windows 7 to be independently bootable, it involves a little bit of work. I wouldn't bother with it unless you really need to.

The best way to fix it is to learn how to use Ubuntu instead, and become independant from proprietary software and it's trickery. ;)

---

### Post by hoopy10 on 2009-07-24
merlinus:  Here is my menu.lst file:

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
# kopt=root=UUID=8b84b8d0-d977-4b9b-9e44-a601a8adee43 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8b84b8d0-d977-4b9b-9e44-a601a8adee43

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

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        8b84b8d0-d977-4b9b-9e44-a601a8adee43
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=8b84b8d0-d977-4b9b-9e44-a601a8adee43 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        8b84b8d0-d977-4b9b-9e44-a601a8adee43
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=8b84b8d0-d977-4b9b-9e44-a601a8adee43 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        8b84b8d0-d977-4b9b-9e44-a601a8adee43
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=8b84b8d0-d977-4b9b-9e44-a601a8adee43 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        8b84b8d0-d977-4b9b-9e44-a601a8adee43
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=8b84b8d0-d977-4b9b-9e44-a601a8adee43 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-12-generic
uuid        8b84b8d0-d977-4b9b-9e44-a601a8adee43
kernel        /boot/vmlinuz-2.6.28-12-generic root=UUID=8b84b8d0-d977-4b9b-9e44-a601a8adee43 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-12-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid        8b84b8d0-d977-4b9b-9e44-a601a8adee43
kernel        /boot/vmlinuz-2.6.28-12-generic root=UUID=8b84b8d0-d977-4b9b-9e44-a601a8adee43 ro  single
initrd        /boot/initrd.img-2.6.28-12-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        8b84b8d0-d977-4b9b-9e44-a601a8adee43
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8b84b8d0-d977-4b9b-9e44-a601a8adee43 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        8b84b8d0-d977-4b9b-9e44-a601a8adee43
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8b84b8d0-d977-4b9b-9e44-a601a8adee43 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        8b84b8d0-d977-4b9b-9e44-a601a8adee43
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


I took out the additional boot info that I added for Win7, it didn't work any way.  What do you think?

---

### Post by merlinus on 2009-07-24
What about results of

```
sudo fdisk -l
```and if xp is on sda1, then its entry in menu.lst is correct.

---

### Post by hoopy10 on 2009-07-24
merlinus:  Here is what the 'sudo fdisk -l' command gave:

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3444d080

   Device Boot          Start            End             Blocks            Id     System
/dev/sda1   *                1               6402        51424033+      7     HPFS/NTFS
/dev/sda2                 6403           18794     99538740          5     Extended
/dev/sda3                18795         24792        48178935         7      HPFS/NTFS
/dev/sda5                  6403           18794        99538708+     7     HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37673766

   Device Boot            Start              End                  Blocks           Id       System
/dev/sdb1                          1              14219         114214086       83      Linux
/dev/sdb2                   14220          14593           3004155            5       Extended
/dev/sdb5                   14220          14593           3004123+       82      Linux swap / Solaris


What do you think?

---

### Post by merlinus on 2009-07-24
So which one is win7?  And is the hdd with windows first in bios boot order?

Also, Herman gave a very learned description of what happens when trying to run two different versions of windows.  If you can live with how it is working, then probably best to do so.

---

### Post by hoopy10 on 2009-07-24
Yeah I can live with it for now.  BTW, to answer your question, yes Winxp is on the primary hd and also on the 1st partition.  Win7 is also on the primary hd and is on the 3rd parition.

---

### Post by merlinus on 2009-07-24
That's exactly what it seemed.  And if you look, win7 is indeed in a logical partition, just as Herman said it would be.

So trying to get it to run directly via grub would be about impossible.

---

### Post by hoopy10 on 2009-07-25
merlin:  so my best bet would be to wipe the Winxp partition, and install Win7 there.  That way I could leave ubuntu as it is and grub would work fine with win7 installed where winxp is currently?

---

### Post by merlinus on 2009-07-25
That is certainly an option.  Win7 will install its own bootloader, however, but it is easy to restore grub afterwards.

Then you can reformat the existing win7 partition to either ext3 or ntfs, depending upon what you want to use it for.

---

