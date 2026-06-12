---
title: "install on 2nd drive"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by leegould on 2009-09-21
How to install Ubuntu on a second internal hard drive not to boot or dual-boot 
at start-up? My daughter also uses this computer and needs W2K. I prefer to boot to W2K and then go to drive 1 for Ubuntu.
Drive 0 has W2K on NTSF   
Drive 1 has NTFS no OS. (drive for Ubuntu)

---

### Post by BraedenNaylor on 2009-09-21
> **leegould said:**
> How to install Ubuntu on a second internal hard drive not to boot or dual-boot 
at start-up? My daughter also uses this computer and needs W2K. I prefer to boot to W2K and then go to drive 1 for Ubuntu.
Drive 0 has W2K on NTSF   
Drive 1 has NTFS no OS. (drive for Ubuntu)

Boot from the live CD or form a usb drive you create. Install it selecting your second drive. Probably something like "sdb" or "sdb1" If using newer equiptment. Go through everything. On the last page install the bootloader under the drive you installed it on sdb or sdb1. Make sure it is the same drive you already selected. Then reboot, under your BIOS settings edit your config so it's primary drive to boot from is your first HD, then second is your 2nd HD. after that it should boot first from your first hd with W2K. If you hold down your boot options key. something like esc. It will let you choose which drive to boot from. I believe some people use a boot changer that allows them to select which drive to boot from every time before booting.

-Braeden

---

### Post by presence1960 on 2009-09-21
when installing Ubuntu and you get to this screen click the advanced tab to select where to install GRUB. If windows is on sda and ubuntu is on sdb select /dev/sdb. You want GRUB on MBR of disk with Ubuntu so don't select a partition such as /dev/sdb1

---

### Post by leegould on 2009-09-22
Braden & Presence. I'm a newbe and having a "learning experience"
I got to the Ready to install screen and must have blown it. Upon reboot There is nothing on disk2 (H) NTFS Active Primary. (J) Swapspace NTFS None Logical. Looks like Ubuntu didn't install. I'll try again and again and get back to you.  Thanks

---

### Post by leegould on 2009-09-23
Got lucky and it is installed on the 2nd drive. I wish I could either stop grub's countdown clock or get rid of it and log on to W2K or 9.04 as I wish.
Thanks again

---

### Post by peterthinking on 2009-09-23
> **leegould said:**
> Got lucky and it is installed on the 2nd drive. I wish I could either stop grub's countdown clock or get rid of it and log on to W2K or 9.04 as I wish.
Thanks again

You can

press Alt+F2
then enter this into window.....

gksu gedit /boot/grub/menu.lst

Edit Grub file and save

you'll see the countdown timer in there, just change the value to whatever you want.

---

### Post by leegould on 2009-09-25
I did the alt f2 and got a text "menu.lst

I'm not sure what to do now.

thanks

---

### Post by presence1960 on 2009-09-26
In ubuntu open a terminal (Applications > Accessories > Terminal) and run this command: ```
gksu gedit /boot/grub/menu.lst
``` That is a lowerccase L in .lst

The output will look like this:
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

[COLOR="Red"]## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		4

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu[/COLOR]

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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
chainloader	+1
```
 Change the red to:

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		[COLOR="Red"]4[/COLOR]

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"]#[/COLOR]hiddenmenu
```

The red 4 = the amount of seconds before the default selection is booted.

The red # will hide the countdown and display the GRUB menu.

Be aware whatever number you set for timeout will be the countdown timer.

Of course don't make your entries red, I highlighted them for easier reference for you.

---

### Post by leegould on 2009-09-27
Thanks for your patience with a 74 year old guy. I started with command line in DOS and didn't know what a MOUSE was. I have long sense forgotten this line stuff and was looking for a GUI thing. I have refused to go past W2K and hope my Ubuntu journey works. It would not if it wasn't for forum folks like you. lee

---

### Post by presence1960 on 2009-09-27
> **leegould said:**
> Thanks for your patience with a 74 year old guy. I started with command line in DOS and didn't know what a MOUSE was. I have long sense forgotten this line stuff and was looking for a GUI thing. I have refused to go past W2K and hope my Ubuntu journey works. It would not if it wasn't for forum folks like you. lee

Glad you got it working! Enjoy Ubuntu.

---

