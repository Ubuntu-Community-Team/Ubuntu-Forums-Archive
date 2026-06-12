---
title: "How can I make Vista the default OS instead of Ubuntu?"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by bubbagumper6 on 2008-12-13
I just installed Ubuntu onto a secondary partition and everything seems to be working.  My only complaint is that Ubuntu is the first OS on the list so it's automatically loaded if I don't choose Vista instead...how can I move Vista to the top?

---

### Post by cdtech on 2008-12-13
Change your "default" setting within your "/boot/grub/menu.lst" to reflect the number sequence of your Vista OS. The default is set to "0" meaning the first OS in the list. Start with "0" and count down including your recovery and text modes.

---

### Post by bubbagumper6 on 2008-12-13
your over my head...I've never used linux before :)  This is my first time so I have no idea how to do what you just said...

---

### Post by cdtech on 2008-12-13
Open a terminal (System menu > Accessories > Terminal) and type this command:
```
sudo gedit /boot/grub/menu.lst
```
Copy and paste the contents to this post, using the code block above your post.

---

### Post by bubbagumper6 on 2008-12-13
while I was waiting for you to reply I started fishing around and found the file you were talking about.  I just don't know how to make the changes you said.  I see the section in there about the "default num" but am I supposed to manually type stuff or am I just making changes to something that's already in there?

---

### Post by cdtech on 2008-12-13
Yes, you have to manually edit it yourself.

If you follow my previous post you'll see how to edit the file, or just copy and paste here and we'll configure it for you then all you have to do is copy and paste it back into your editor. It's much better if you learn though...:p

---

### Post by bubbagumper6 on 2008-12-13
Yay I figured it out :)


Also on a side note, is there any way to use software built for windows?  I have a microsoft wireless keyboard and mouse I would love to configure but the software is micrsoft brand so theres no linux version...lol

and thanks for being so patient with me :)

---

### Post by cdtech on 2008-12-13
just plug it in and see if it detects it. Mine just works out of the box...

---

### Post by bubbagumper6 on 2008-12-13
oh yeah it works ok but the scroll wheel moves REALLY fast and I couldn't find a way to turn it down in the Ubuntu settings so I was just going to get the official software which lets you turn the speed down manually.  That and my keyboard has a lot of user defined keys that you need the software to use.

---

### Post by cdtech on 2008-12-13
Unless you have drivers specifically for GNU/Linux the install CD wont work. Have you tried adjusting through "System menu > System > Preferences > Mouse/Keyboard"?

---

### Post by bubbagumper6 on 2008-12-13
yeah, it only had the speed setings for the mouse movement and double click.  Not the scroll wheel in the middle.

And the thing I'm trying to get is a program not so much a driver...I think

---

### Post by drpas2k on 2008-12-14
help me make win xp as my default

thanks

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
# kopt=root=UUID=5b07a494-5426-496b-8c3c-93dec0f21e9b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5b07a494-5426-496b-8c3c-93dec0f21e9b

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		5b07a494-5426-496b-8c3c-93dec0f21e9b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5b07a494-5426-496b-8c3c-93dec0f21e9b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		5b07a494-5426-496b-8c3c-93dec0f21e9b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=5b07a494-5426-496b-8c3c-93dec0f21e9b ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		5b07a494-5426-496b-8c3c-93dec0f21e9b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5b07a494-5426-496b-8c3c-93dec0f21e9b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		5b07a494-5426-496b-8c3c-93dec0f21e9b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5b07a494-5426-496b-8c3c-93dec0f21e9b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		5b07a494-5426-496b-8c3c-93dec0f21e9b
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
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by bubbagumper6 on 2008-12-14
Ok count down 13 lines in that file, to where it says "Default 0"

that 0 is the number you want to change.  If you go down to the bottom it shows all your different options.  0 is the first one you just have to count down till you get to windows.  Also note that "Other Operating Systems" counts as one.  But in any case you should just change that 0 to a 6 and save the file.

So it will say "Default 6" and you should be good :)

---

### Post by cdtech on 2008-12-14
That should be "default 5" for your setup. Count from 0-5 and not 1-6.

Good luck.......

---

### Post by bubbagumper6 on 2008-12-14
No your missing that "Other Operating System" part right above XP.  Even though there's nothing listed there, it counts as a selection because it's on the list when you boot.  I had the same thing.  I thought it was 5 and put that in.  It's actually 6.

---

### Post by dsample on 2008-12-14
Ubuntu supports some good utilities for editing your grub config. Just search on something like "grub editor".  

I use kgrubeditor...

or qgrubeditor. 

[http://www.ubuntugeek.com/qgrubeditor-a-visual-grub-configuration-editor.html](http://www.ubuntugeek.com/qgrubeditor-a-visual-grub-configuration-editor.html)

---

### Post by cdtech on 2008-12-15
> **bubbagumper6 said:**
> No your missing that "Other Operating System" part right above XP.  Even though there's nothing listed there, it counts as a selection because it's on the list when you boot.  I had the same thing.  I thought it was 5 and put that in.  It's actually 6.

My bad, your absolutly correct.......:p

---

