---
title: "Litle help for new Ubuntu user"
date: 2008-08-26
forum: General Help
---

### Post by eggibm on 2008-08-26
Hi, I new here and I having some problems here with Ubuntu.

Firstly, I dual booted Ubuntu with Vista on 2 separate hard drives.
Now when I try to boot Vista then it's stops before it goes into the loading screen and stands GRUB and nothing happens. I hope I can fix this without having to format the Vista partition.

And second, I'm having a real trouble of installing the drivers for sound card, witch is X-Fi Extreme Gamer Pro.
I've tried google put I don't understand any thing of this.

I hope someone can help me with this.

---

### Post by monkeyking on 2008-08-26
give us you menu.lst in /boot/grub/menu.lst, or somewhere around this directory. Futhermore tell us your hard drive partition structure.

---

### Post by Garratt on 2008-08-26
if you can get ubuntu up that is good, i am having similar problems.. but whatever you do don't format cause it can be fixed.

This is my post so check yours and my post regularly.

[http://ubuntuforums.org/showthread.php?t=898326]("http://ubuntuforums.org/showthread.php?t=898326")

ok now go into terminal that should be under applications > accessories

open terminal and copy and paste this:

```
sudo fdisk -lu 
```

now go to file open new tab> this will open a new tab just like the new versions of internet explorer or firefox.

now copy and paste this:

```
sudo grub
```

this will open up the grub command line...
now copy/paste this:

```
find /boot/grub/stage1
```
and...
```
geometry (hd0)
```

ok now reply to this post by copying and pasting both tabs.

you can use the code commands by clicking the # at the toolbar for pasting your code into a little box on the forums, makes it easier to read and lets us identify your post between the code. or you can just type [.CODE.][./CODE.] without the fullstops

Generally you don't need drivers for hardware except for video cards, soundcards usually just work, but you may need to muck around a bit with the sound, a tip to checking if it is working is putting a mp3 on the desktop and hover your mouse over it, it should play automatically while you hold your mouse over it.

check this thread for other solutions/problems:
[Comprehensive sound solutions guide]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by Garratt on 2008-08-26
additionally to boot up vista you can try this.

download [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

and burn it to disk, now restart the comp, you will go into the supergrub boot loader (you may have to go thru a tutorial at first, but eventually will get to the screen with all your partitions on it), and if you scroll down(using arrow keys) to "Live Swap" hit enter key on that once, the screen will just flash momentarily if its anything like mine, and then scroll up to one of the !~WIN----->::))))) options and hit it, if it doesn't work click on one of the other WIN or LONGHORN options, that should boot into vista. At the moment I have to keep this boot disk in my cdrom whenever i wanna bootup, untill i get it fixed. 

if it still does not boot into vista, try the "LIVE SWAP" again, and then one of the win options. if nothing happens then the super grub isn't going to work obviously.

---

### Post by Garratt on 2008-08-26
Ok i was just able to fix mine, you may want to do some reading about it read the Super grub forums or jsut follow my examples:

I loaded up disk this time instead of booting straight into the OS i wanted, i selected, the first option which is something like, boot super grub English version...

then read the help files that automatically appear, i then selected to do
fix of windows boot, then i chose a "LIVE SWAP" which physically changes the grub boot loader to the other drive, 

I chose manual swap, but when it got to the window i only had one option so i chose that, and it works fine now.

Thats all going by memory and i'm sure i left out a step or 2, so just read as much as you can while searching around inside the Super grub disk, it doesn't really explain much but you kinda get the picture after reading a bit, 

IF YOU GET STUCK, on an option and can't go back, just hit the restart button on your pc, and it will boot-up again and you can search thru more documentation. 

GL.

If you have any problems try the super grub forums they seem to have more luck there.

---

### Post by eggibm on 2008-08-26
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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=198b1a60-9a34-4b58-afe4-28d84c7cb3c3 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=198b1a60-9a34-4b58-afe4-28d84c7cb3c3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=198b1a60-9a34-4b58-afe4-28d84c7cb3c3 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Garratt on 2008-08-27
hmmm thats not good, no windows in there....


DID you put ubuntu on the second or first hDD?
because there it looks like ubuntu is on the second hdd, if you can tell us the grub output, you didnt post that... you only seem to post the fdisk -lu, so see my above post.... open terminal and type: sudo grub, then: find /boot/grub/stage1, then: geometry (hd0)

```
## ## End Default Options ##

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=198b1a60-9a34-4b58-afe4-28d84c7cb3c3 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=198b1a60-9a34-4b58-afe4-28d84c7cb3c3 ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, memtest86+
root (hd1,0)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```


I'm not sure about that one, either wait for mods to reply or goto supergrub forums and print that output and tell them of your problem..

Mayb it's just not reading the windows longhorn loader properly or something...

---

### Post by eggibm on 2008-08-28
I don't now, when I was installing Ubuntu it failed the first time so I tried again, then I messed around in "Advance" button in part 7 of the installation and then Ubuntu worked but Windows not.

I tried Life Swap disk and then Vista rescue disk but nether of them seemed to find Windows installed.
But I decided, there was nothing on the Windows partition that was worth saving, every thing was on an separate hard drives or partitions, so I just reinstalled Windows and then I reinstalled Ubuntu and everything is working fine now.

And I manage to fix the sound, in sted of just sitting here and wait for some one to hold my hand to fix them, I looked harder and finally I found a good guide that helped me. The sound is on.

But thanks for the all your help and your posts. It's refreshing to get out for air and try some thing else than Windows. :-)

---

