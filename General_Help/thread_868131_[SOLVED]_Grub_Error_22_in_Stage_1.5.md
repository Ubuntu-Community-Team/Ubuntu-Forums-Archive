---
title: "[SOLVED] Grub Error 22 in Stage 1.5"
date: 2008-07-23
forum: General Help
---

### Post by pgn674 on 2008-07-23
In summary, I just upgraded my computer and now I'm getting [error 22]("http://www.uruk.org/orig-grub/errors.html#stage1_5") on Grub's stage 1.5 during boot up.

I just upgraded the motherboard, but did not touch the hard drives. I have 3 hard drives: one fully NTFS, one with an EXT3 partition for my Ubuntu install as well as an NTFS partition, and one with just an NTFS partition for my Windows XP install. All are IDE, no SATA.

My new motherboard has only one IDE slot on it, so I got a PCI > IDE adapter card. I had forgotten my configuration on what was on IDE1 and what was on IDE2 at first, but I'm sure I have that sorted out now, and the master/slave settings are still how I had them before. I'm using the PCI > IDE adapter card for my IDE2 channel. I can always see the CD drive and hard drive that are on that channel, whether in the BIOS or in a boot CD.

The Windows install partition is the first partition on my IDE1 master drive, and the Linux install partition is the second partition on my IDE2 master drive.

But, now when I try to boot off the IDE1 master, Grub gives me error 22, the description of which I linked to above. I tried reinstalling Grub using [this guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick%20Start"), but that didn't change anything. In fact, I can rename the /boot/grub/ folder on my Ubuntu install, and I still get the same error.

One thing I noticed is that aanother part of [the guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Overwriting%20the%20Windows%20bootloader") tells me to find the boot partition and mount it, but from what I can tell, I have no boot partition.

Using the Ubuntu boot CD, here is sudo fdisk –l```
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac85ac85

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         131     1052226   82  Linux swap / Solaris
/dev/sda2             132        2089    15727635   83  Linux
/dev/sda3            2090       10010    63625432+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd3bfd3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2aeb2aea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9729    78148161    7  HPFS/NTFS
```SDA2 is my Linux install, and SDB1 is my Windows XP install.
Here is /boot/grub/menu.lst from my Linux install:```
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=e7777bb8-bc7c-4f41-82ae-bdb658f0b505 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,1)

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e7777bb8-bc7c-4f41-82ae-bdb658f0b505 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e7777bb8-bc7c-4f41-82ae-bdb658f0b505 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=e7777bb8-bc7c-4f41-82ae-bdb658f0b505 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=e7777bb8-bc7c-4f41-82ae-bdb658f0b505 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=e7777bb8-bc7c-4f41-82ae-bdb658f0b505 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=e7777bb8-bc7c-4f41-82ae-bdb658f0b505 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e7777bb8-bc7c-4f41-82ae-bdb658f0b505 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e7777bb8-bc7c-4f41-82ae-bdb658f0b505 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e7777bb8-bc7c-4f41-82ae-bdb658f0b505 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e7777bb8-bc7c-4f41-82ae-bdb658f0b505 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e7777bb8-bc7c-4f41-82ae-bdb658f0b505 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e7777bb8-bc7c-4f41-82ae-bdb658f0b505 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04.1, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e7777bb8-bc7c-4f41-82ae-bdb658f0b505 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e7777bb8-bc7c-4f41-82ae-bdb658f0b505 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
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
root		(hd1,0)
savedefault
makeactive
chainloader	+1
```So, does anybody know why this might be happening, or have any idea how to straighten things out. Once I get something done, I promise to post in this thread again.

---

### Post by jocko on 2008-07-23
So grub is installed on your ide1 drive, and the ubuntu install, containing the /boot folder, is on the drive which used to be ide2?

Have you tried disconnecting the third drive to see if it works better?

Another thing you can try is to check which order your drives have now:

Boot up a live cd and open up a terminal.
type:```
sudo grub
```then:```
find /boot/grub/stage1
```This will tell you which partition(s) contain grub files (with "grub-language", i.e (hd0,1) instead of device nodes).
Then edit your menu.lst and make sure to set the correct partition in these lines:

```
## default grub root device
## e.g. groot=(hd0,0)
# groot=[COLOR=Red](hd0,1)[/COLOR]

```(This is very important, if you don't change this line, grub will get misconfigured every time you get a kernel update).
And:
```
title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        [COLOR=Red](hd0,1)[/COLOR]
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=e7777bb8-bc7c-4f41-82ae-bdb658f0b505 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet
``` Just change the top kernel, the lines for the other kernels can be updated later by running the command "sudo update-grub" once you manage to boot your system.

---

### Post by pgn674 on 2008-07-23
> **jocko said:**
> So grub is installed on your ide1 drive, and the ubuntu install, containing the /boot folder, is on the drive which used to be ide2?Yes, although the drive that used to be on IDE2 is still on IDE2, I made sure the cables were correct that way. And, I'm not sure if Grub is actually installed on the IDE1 drive. I guess it has to be, as Grub comes up (with the error) when I tell my BIOS to boot that IDE1 drive.

> **jocko said:**
> Have you tried disconnecting the third drive to see if it works better?I tried that. On the first boot, it gave me an error of 16. Subsequent boots were error 21, and it never actually worked.

> **jocko said:**
> Another thing you can try is to check which order your drives have now:...When I tell Grub to find the grub files, it returns (hd0,1). So, I don't have to update my menu.lst file for that. I did notice that the groot setting was commented out. I uncommented it and set it to (hd0,1), but I'm still getting the same error 22.

Thank you for your time and the help. I'm going to keep hammering at it, and if you or anyone else get an idea, please post!

---

### Post by pgn674 on 2008-07-23
Here's an update.

I went back to that other part of that [guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Overwriting%20the%20Windows%20bootloader") I mentioned, and saw that it actually says to find the boot partition *if* I made one. So I continued with that part, and it went smoothly enough. Now, when I try and boot, I get error 18.

Hmm, errors 16, 18, 21, and 22. I'm gonna get a full rainbow of [errors]("http://www.uruk.org/orig-grub/errors.html#stage1_5") here at this rate. :(

---

### Post by jocko on 2008-07-24
> **pgn674 said:**
> Yes, although the drive that used to be on IDE2 is still on IDE2, I made sure the cables were correct that way. And, I'm not sure if Grub is actually installed on the IDE1 drive. I guess it has to be, as Grub comes up (with the error) when I tell my BIOS to boot that IDE1 drive.

I tried that. On the first boot, it gave me an error of 16. Subsequent boots were error 21, and it never actually worked.

When I tell Grub to find the grub files, it returns (hd0,1). So, I don't have to update my menu.lst file for that. I did notice that the groot setting was commented out. I uncommented it and set it to (hd0,1), but I'm still getting the same error 22.

Thank you for your time and the help. I'm going to keep hammering at it, and if you or anyone else get an idea, please post!

The groot setting, like the other options in grub, *should* be commented out, see this part of menu.lst:> # Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs so put the # back. It's probably not what's causing your problems, but having it set to the wrong partition there will screw up your grub every time the kernel is updated (or update-grub is run by some other reason) and having it uncommented will probably also mess things up.

I noticed one thing in your menu.lst:
The drive you think is your secondary drive is actually recognized as (hd0), which means it really is your first drive.
The order of the drives is not set by which ide connection they are connected to, but by which order the bios is set to boot. 
Try changing the order of the drives in your bios boot order, or even make sure it *only *tries to boot from one of your drives.
My suspicion is that somewhere along the line you have managed to install grub on another hard drive, and now your bios tries to boot from the wrong drive, meaning the copy of grub installed on that drive will look for the rest of the grub files in the wrong partition.
If that doesn't help, try booting from each of your 3 drives without any of the others connected, and see which drives give you grub errors (and which errors) and which only gives you bios errors (such as "invalid system disk").

---

### Post by pgn674 on 2008-07-24
Here's an update. It's kind of long, but I tried a lot of things. Reads like a cross between a post and a log. jocko, I tried out your suggestions first, so this long post starts with the results of trying them.

OK, I put the # back. Thanks for catching that, I hadn’t seen that “do not uncomment” comment in the file.

I had changed the boot order in the BIOS to reflect what I think it should be before attacking the Grub problem. I just re-checked the order, and it’s still good: CD/DVD, then USB, then the 120GB Windows installed HDD, which Grub’s find identifies as sdb. The BIOS is a little unclear on this, but I think if the sdb drive fails to boot, I have it trying sda then sdc.

By the way, the motherboard is an ASRock 4Core1600Twins-P35 (P1.10), and the BIOS is American Megatrends v02.61. And… Hmm, the BIOS claims the processor is 64 bit. I got an Intel Core 2 Duo E8400. The package says “Intel 64 Architecture for 64-bit computing.” I never noticed that before, not when I was buying or installing. I wonder if it has a 32 bit mode, ‘cause everything I’ve installed before this upgrade, including Grub, Ubuntu, Windows XP, and all applications have not been 64 bit versions. I’ll have to research this.

OK, I’ll try telling the BIOS to boot only the sdb drive. No CD, USB, or other drives. And… No error message, it just stops at saying “GRUB” with a blinking curser. Curses!

Now I’ll try booting from each drive with the others unplugged. Hmm, the NTFS data one is a slave, so that might not work – guess I’ll see.

Linux installed drive alone (was sda): Error 18. Windows installed drive alone (was sdb): “GRUB Hard Disk Error”. NTFS data drive alone (was sdc): BIOS can’t boot from it.

I’m going to have just my Linux install drive plugged in alone, and reinstall Grub following the guide and see what happens. Maybe I can just boot Linux alone, and take it from there. Tried the quick start and the overwriting the Windows bootloader procedures, and neither worked. For the second attempt, I had to fix the file at /mnt/root/boot/grub/device.map to have sda be hd0 (removed references to sdb, sdc, and fd0, since fdisk -l only came up with my one hard drive I have plugged in, of course), but it’s still not working, still error 18.

I checked the menu.lst file, and the reference to Windows XP did not get removed. I wonder why not? Shouldn’t the Grub installer update that file to be current? My Windows XP install drive is not plugged in, and I ran the installer, yet the reference to Windows XP remains (as hd1,0). That makes no sense!

I tried the “overwriting the Windows bootloader” procedure again, this time using --recheck, and device.map got updated to have fd0 back, but menu.lst still hasn’t been updated.

So I tried updating menu.lst manually. I commented out all references to Windows and old kernel versions, and I still get error 18. So I deleted menu.lst altogether. Still error 18. I’m not even getting to a point where that file matters. Now that I think of it, I did something like that already, when I renamed the /boot/grub/ folder. I tried renaming that folder again and reinstalling Grub using the quick start method from the guide, and it complained that /boot/grub/stage1 doesn’t exist. So I tried the “overwriting the Windows bootloader” method with the --replace, and it created a new /boot/grub/ folder. No new menu.lst though, but there is a device.map, and it looks normal. Tried booting; still error 18. And by the way, I still only have the Linux install drive plugged in, the other two are unplugged.

Next ideas: My Linux install drive is going through the PCI to IDE adapter card right now. I'll try plugging it into the one IDE slot on the motherboard. If that doesn't work, I'll update the BIOS, make a /boot partition, or have Windows write the master boot record.

---

### Post by pgn674 on 2008-07-28
It's at least partially working now.

I found that I had to take any drive that Grub would work with, whether it was the drive that the BIOS boots off of, the drive that /boot/grub/ is written to, or any drive that has an OS that Grub might give control to, and put it on the motherboard IDE channel, not the PCI to IDE adapter card. The adapter card is a ```
Rosewill ATA-133 2 port PCI adapter without RAID (RC-208)
```. Apparently Grub doesn't like it. So, after getting the drives in the right place and checking the cabling and channels and master vs. slave stuff, I used the [guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") to re-install Grub, then checked menu.lst and device.map to make sure thay made sense, and Grub started booting OK. 

But, it wasn't able to boot either Ubuntu or Windows. So I got an idea and told it to boot into hd0 for Ubuntu, and not hd1 as everything was telling me during any Grub reinstall. And that worked. Apparently, the Grub installer and the Grub boot runner have different ideas on what order the drives are in. I think the PCI to IDE adapter is putting the one hard drive that is on it now at the beginning of the list when I boot off the Ubuntu Live CD, but it doesn't happen when Grub is running from boot.

So, now I can boot Ubuntu fine. I'm still working on Windows, though. I've tried changing the drive and partition to attempt to boot from, but it freezes at "Starting up ..." when ever I try to boot Windows from a drive and partition that I think has a reasonable chance of being right.

I'm going to bed now. I'll post here once I figure out this last bit.

---

### Post by pgn674 on 2008-08-14
OK, I got it all working.

To get by the "Starting up ..." freeze, I changed my Windows entry in menu.lst to```
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader	+1
```I think it's the map lines that did it.

Then I was getting a BSoD on boot, and found that I would get a similar one if I tried booting a Windows CD. So I put both my Windows install drive and the CD drive on the motherboard IDE channel (instead of on the PCI to IDE adapter card), and did a Windows repair install. That got Windows working, and I was able to put the CD drive back on the adapter card.

And so, in conclusion: Booters don't like PCI to IDE adapter cards.

---

### Post by pgn674 on 2008-10-03
So, I'm working on a friend's laptop. Internal HDD is broken, for the time being I'm going to have her running Windows from her external USB drive. Went ahead and installed Windows XP on it, and I got that same BSoD again. Turns out Windows doesn't like being installed on USB drives. I found [this guide]("http://www.ngine.de/article/id/8") for how to install and run a full Windows XP from a USB drive to bypass that, and I just looked over my shoulder and can see that it just worked :)  BTW, I used the free ISO Master instead of WinISO.

I'm wondering, maybe Windows views my PCI to IDE adapter card like a USB port, and any drive behind it is not going to get a good installation or Windows boot. I wonder if this guide would have helped me out several months ago.

---

