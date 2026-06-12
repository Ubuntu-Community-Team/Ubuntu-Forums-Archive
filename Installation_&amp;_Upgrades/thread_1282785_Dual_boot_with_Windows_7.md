---
title: "Dual boot with Windows 7"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by gobberpooper on 2009-10-04
My dad is a biologist at building owned by WPI and so he's going to get Windows 7 for $10 come October 22. He doesn't want it because he's happy with XP, so he's giving it to me. I have a bunch of games, such as Oblivion, Guild Wars, BioShock etc which don't run as well on Ubuntu and crash every now and then. So I'm going to dual-boot with Ubuntu and Windows 7. I've already got a separate partition with 150GB on it.

Just to test it, I used Windows XP but it didn't go so great. I reinstalled GRUB, and put XP to the GRUB menu in menu.lst. But then it tells me that there's an there's an error with the OS, something about the executable not being able to start, I don't exactly remember. How do I exactly install a perfect dual-boot of Ubuntu and Windows 7, **with Ubuntu as the main OS** so don't tell me to install Windows 7 and then reinstall Ubuntu.

EDIT:
Oh wait, actually we're getting it tomorrow as a reward for being able to use skin cells as stem cells. Quick replies are much appreciated.

---

### Post by tuxxy on 2009-10-04
You should ideally install Windows before Ubuntu, heres a guide to recovering your install.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by gobberpooper on 2009-10-04
> **tuxxy said:**
> You should ideally install Windows before Ubuntu, heres a guide to recovering your install.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

As I said before, I don't want to reinstall Ubuntu. Ubuntu is going nowhere. There is 150GB of unallocated space upon which I would like to install Win7 and then just reinstall GRUB. Or however you would go about doing it.

---

### Post by tuxxy on 2009-10-04
Yes I understand well in that case you can plan for it then, use that link it will show you how to recover your Ubuntu once you install Win 7.

---

### Post by presence1960 on 2009-10-04
> **gobberpooper said:**
> As I said before, I don't want to reinstall Ubuntu. Ubuntu is going nowhere. There is 150GB of unallocated space upon which I would like to install Win7 and then just reinstall GRUB. Or however you would go about doing it.

Install Windows 7 to a premade primary partition (NTFS) or unallocated space.. Then after the install make sure your machine boots right into windows. If it does then do this to restore GRUB:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

If you are not sure exactly how to restore GRUB post back and we'll walk you through it. I had Windows 7 multi-booting with Ubuntu 9.04, Sabayon 4.1 and Masonux 9.04 on a 3 hard disk machine. Not really hard at all to do. just need to restore GRUB after the windows install.

If you have multiple hard disks let us know, that may change things a little, but still no problem.

Don't believe the myth that you need to install windows before Ubuntu ( not referring to tuxxy). Ideally you should do it whatever way best suits your needs. When you install windows after Linux, windows overwites GRUB on MBR. All you need to do is restore GRUB to MBR. That is the point where a lot panic and make the claim that you can't install windows after Linux. They are just misinformed.

---

### Post by gobberpooper on 2009-10-04
> **tuxxy said:**
> Yes I understand well in that case you can plan for it then, use that link it will show you how to recover your Ubuntu once you install Win 7.

I think I'll try it on a virtual machine just to be safe.

---

### Post by sloppyc on 2009-10-04
> **presence1960 said:**
> 
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```
I'll add to step 4:
If you have a separate /boot partition, you'll get an Error 15/file no found if you type the command as above.  Instead, type "find /grub/stage1" and all will be well.

---

### Post by gobberpooper on 2009-10-05
> **sloppyc said:**
> I'll add to step 4:
If you have a separate /boot partition, you'll get an Error 15/file no found if you type the command as above.  Instead, type "find /grub/stage1" and all will be well.

Ohhhhhh! Yeah that was most likely the problem. I'm pretty sure that that's the error I got. Thank you I'll try this and see if it works.

---

### Post by gobberpooper on 2009-10-05
okay so I installed ubuntu, then windows 7, and then reinstalled GRUB using the Live CD. But now I can't see Windows 7 anymore. should I edit the menu.lst file?

---

### Post by presence1960 on 2009-10-05
> **gobberpooper said:**
> okay so I installed ubuntu, then windows 7, and then reinstalled GRUB using the Live CD. But now I can't see Windows 7 anymore. should I edit the menu.lst file?

yes. if you need help adding/editing the windows entry in menu.lst post back

---

### Post by 2xd on 2009-10-05
although I do not want to install win 7 yet i have some questions please:

a. can u do explain how to add the  windows entry in menu.lst anyway ? just to upgrade my knowledge ?

b. on the 22 Oct i'll receive win 7 to upgrage my Vista Premium, how will that should be executed ?

---

### Post by gobberpooper on 2009-10-05
okay it now works on the virtual machine. So here were my steps to dual boot ubuntu and windows 7 with ubuntu installed first. Remember that it changes from system to system, depending on how you've got your partitions set up. Mine was just installing Ubuntu on the whole hard drive and then installing Windows on a partition I've made, which is what most people will have.

1) Partition the hard drive using GParted from the Live CD
2) Insert the Windows 7 disc
3) Install Windows 7 for your needs, serial key or whatnot
4) Install updates, restart etc
5) Live CD
6) Mount the Ubuntu partition. You can do this by just opening the disk from the "Places" menu
7) In a terminal type "sudo grub"
8) Check where Ubuntu partition is mounted to. Usually it's /media/disk. Type "find (mount point, generally /media/disk)/boot/grub/stage1
9) The output will be (hdX,Y). If you did a simple installation of Ubuntu from the start then it will most likely be (hd0,0)
10)root (hdX,Y)
note the space after "root" but not the comma
11)setup (hdX)
most likely hd0
12)Once that's done type "quit" and then reboot. Take out the Live CD
13)In GRUB, go to the most recent kernel to boot Ubuntu. **Important**. When it boots look for the (hdX,Y). Take note of that.
14)Open up a terminal and type "gksudo gedit /boot/grub/menu.lst
15)Scroll down until you see something similar to
```

#
# examples
#
# title		Windows NT/2000/XP
# root		(hd0,0)
# makeactive
# chainloader	+1

```
16)Remove the #'s and change the title to whatever you like
17) If the (hd0,0) is what it said while booting Ubuntu, then change it to (hd0,1) or whatever fits your partition.
18) Save and reboot
19) Press "esc" to go into GRUB
20) At the top should be what you put in for the title of the menu.lst entry for Windows
21) Select it and watch your new Windows OS load up
22) If you reboot but don't go into GRUB, it will just load Ubuntu as the primary OS, which is what I'm guessing you want

---

### Post by gobberpooper on 2009-10-05
> **2xd said:**
> although I do not want to install win 7 yet i have some questions please:

a. can u do explain how to add the  windows entry in menu.lst anyway ? just to upgrade my knowledge ?

b. on the 22 Oct i'll receive win 7 to upgrage my Vista Premium, how will that should be executed ?

a. check the new post

b. instead of choosing "Custom" or "Full Install" select "Upgrade." You'll get to keep all your files, folders, and I believe programs.

---

### Post by presence1960 on 2009-10-05
> **gobberpooper said:**
> okay it now works on the virtual machine. So here were my steps to dual boot ubuntu and windows 7 with ubuntu installed first. Remember that it changes from system to system, depending on how you've got your partitions set up. Mine was just installing Ubuntu on the whole hard drive and then installing Windows on a partition I've made, which is what most people will have.

1) Partition the hard drive using GParted from the Live CD
2) Insert the Windows 7 disc
3) Install Windows 7 for your needs, serial key or whatnot
4) Install updates, restart etc
5) Live CD
6) Mount the Ubuntu partition. You can do this by just opening the disk from the "Places" menu
7) In a terminal type "sudo grub"
8) Check where Ubuntu partition is mounted to. Usually it's /media/disk. Type "find (mount point, generally /media/disk)/boot/grub/stage1
9) The output will be (hdX,Y). If you did a simple installation of Ubuntu from the start then it will most likely be (hd0,0)
10)root (hdX,Y)
note the space after "root" but not the comma
11)setup (hdX)
most likely hd0
12)Once that's done type "quit" and then reboot. Take out the Live CD
13)In GRUB, go to the most recent kernel to boot Ubuntu. **Important**. When it boots look for the (hdX,Y). Take note of that.
14)Open up a terminal and type "gksudo gedit /boot/grub/menu.lst
15)Scroll down until you see something similar to
```

[COLOR="Red"]#
# examples
#
# title		Windows NT/2000/XP
# root		(hd0,0)
# makeactive
# chainloader	+1[/COLOR]

```
16)Remove the #'s and change the title to whatever you like
17) If the (hd0,0) is what it said while booting Ubuntu, then change it to (hd0,1) or whatever fits your partition.
18) Save and reboot
19) Press "esc" to go into GRUB
20) At the top should be what you put in for the title of the menu.lst entry for Windows
21) Select it and watch your new Windows OS load up
22) If you reboot but don't go into GRUB, it will just load Ubuntu as the primary OS, which is what I'm guessing you want

That text in red is not where you add/edit the windows entry in menu.lst- that red text is just what it says: an example. See my menu.lst to see where windows entry goes (in red also):
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
timeout		4

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
[COLOR="Cyan"]# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 r[/COLOR]o
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
# kopt=root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f31336b1-0908-4580-aad2-6b04ac995b9b

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

[COLOR="Red"]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
chainloader	+1[/COLOR]
```

The cyan is the text you said to edit(incorrect), the red is where windows entries go in menu.lst

---

