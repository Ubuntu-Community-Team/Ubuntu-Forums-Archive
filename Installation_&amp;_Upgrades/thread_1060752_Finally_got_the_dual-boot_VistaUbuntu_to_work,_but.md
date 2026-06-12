---
title: "Finally got the dual-boot Vista/Ubuntu to work, but..."
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by Slacker20 on 2009-02-05
After battling the Vista volume (C drive) that refused to shrink (even after disabling hibernation, disabling pagefile, cleaning up as much as possible on the disk, then defragging with PerfectDisk 10), I just ended up backing up my D drive (Data), deleted it, added a primary partition in it's place, and finally successfully installed Ubuntu 8.10 on my Asus G1 laptop.  Now I have some questions though:

1) The screen for choosing which OS to boot into lists the following:
Ubuntu 8.10, kernal 2.6.27-11-generic
Ubuntu 8.10, kernal 2.6.27-11-generic (recovery mode)
Ubuntu 8.10, kernal 2.6.27-7-generic
Ubuntu 8.10, kernal 2.6.27-7-generic (recovery mode)
Other operating systems:
Windows Vista/Longhorn (loader)
Windows Vista/Longhorn (loader)

I have only tried booting into Ubuntu with the first option listed and it works.  I tried to boot into Vista with the first Vista listed and it gave me a white page with "ERROR" in huge red letters, but the second Vista option worked fine.

- What are all the different options, and why not just "Windows Vista" and "Ubuntu" as my options?
- Why does my first Vista option not work, but the second one does, even though they're called the same?


2) Now when I use GParted, this is what it shows:

[IMG]http://img.photobucket.com/albums/v655/Slacker_Master17/GPartedScreenshot2.png[/IMG]

-Why does it no longer shows how much of the Vista partition is used and unused, nor does it show it's label as "VistaOS"?
- Why is the Ubuntu partition (which is also missing its "UbuntuOS" label) locked and unable to be changed?
- What is the "linux-swap" partition for?

I was trying to setup my hard drive so that it would have the 86.5GB primary partition for Vista, a 20GB primary partition for Ubuntu, and a ~35GB extended partition for the D drive to be used as a data drive.

Any help and information would be greatly appreciated,
~Slacker20

---

### Post by Elfy on 2009-02-05
The ubuntu drive is locked because you are using it - to do any work on that partition, boot withe the livecd and use the partition editor in the sysy admin menu.

You could resize the ubuntu drive and the extended partitions there - shrink them from left to right - though you might need the gparted livecd to shrink left to right - [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Then the unallocated space will be next to the small 66Mb unallocated - you can combine them into a new partition for your d drive.

Swap is much like the win pagefile.

You have differnt ubuntu in the menu list after kernel updates - each has it's own recovery option.

Without seeing the menu list I couldn't comment - but youc an remove the non working one - you can post it here - run this fdrom a terminal

```
cat /boot/grub/menu.lst
```

---

### Post by Slacker20 on 2009-02-05
```
brandon@Dual-boot-laptop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=aecc8aee-aac1-4d07-b3f2-990d7fc9c8aa ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=aecc8aee-aac1-4d07-b3f2-990d7fc9c8aa

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
uuid		aecc8aee-aac1-4d07-b3f2-990d7fc9c8aa
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=aecc8aee-aac1-4d07-b3f2-990d7fc9c8aa ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		aecc8aee-aac1-4d07-b3f2-990d7fc9c8aa
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=aecc8aee-aac1-4d07-b3f2-990d7fc9c8aa ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		aecc8aee-aac1-4d07-b3f2-990d7fc9c8aa
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=aecc8aee-aac1-4d07-b3f2-990d7fc9c8aa ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		aecc8aee-aac1-4d07-b3f2-990d7fc9c8aa
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=aecc8aee-aac1-4d07-b3f2-990d7fc9c8aa ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		aecc8aee-aac1-4d07-b3f2-990d7fc9c8aa
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

brandon@Dual-boot-laptop:~$
```

---

### Post by Elfy on 2009-02-05
OK I assume that the rest makes some sense now then and it's just why one works and the other doesn't in your menu.

If you look at the gparted screenie - you can see /dev/sda1 and /dev/sda2 respectively your' recovery and boot vista partitions - grub has added these to the menu list - 

the one which fails has this line - root	(hd0,0)
the one which works has this line - root	(hd0,1)

The way grub works (bearing in mind that is starts counting at 0) is that the 
first relates to hard drive and second the partition.

Your bad option is then the first hdd and first partition - it points at the recovery partition.

You can remove it easily by deleting the  whole section 
> title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
gksudo gedit /boot/grub/menu.lst
``` will open it to edit it

---

### Post by Slacker20 on 2009-02-05
Thank you very much.  Can I also remove the other unused Ubuntu boot options from the list so that I only have "Ubuntu" and "Vista" to choose from, or do I need to keep them all on there in case I ever need them?  Is there a way to boot into one of those options from a command prompt if they are removed from the list?

Edit: Also, is there a way to create a data partition to use for storing music, videos, and pictures so that both Vista and Ubuntu can access the files?  That way, I wouldn't have to use up hard drive space to put all those files in both partitions

---

### Post by Elfy on 2009-02-06
You can do whatever you like - you could if there was a problem get to the rest - but it's long winded and not particularly simple. You could comment out the 3,4 and 5 sections but I wouldn't remove the second buntu option.

You can read and write to your vista ntfs partition from ubuntu. Install ntfs-config and there will be a tool in system tools to allow you to access them.

---

### Post by Slacker20 on 2009-02-06
Ok, well I did that and was able to access the files on my Vista partition, but now is there a way to remove the VistaOS icon from my desktop, or move it to a panel or AWN?  I tried to drag and drop it to the panel but it just snaps back to the desktop.

---

### Post by Elfy on 2009-02-06
You can stop drive icons appearing on the desktop - do Alt+F2 then in the run dialogue put gconf-editor

Navigate to apps/nautilus/desktop and disable volumes_visible

---

### Post by Slacker20 on 2009-02-06
Wow, you're awesome.  Thanks a lot :D

---

