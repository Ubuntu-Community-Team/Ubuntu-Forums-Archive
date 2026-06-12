---
title: "GRUB error 17. On a USB Pen Drive."
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by djwkd on 2009-09-19
Hello everyone.
I installed #! (Yes, i know this is the ubuntu forum, but #! is Ubuntu based, so...) on my USB Pen drive. Live CD worked fine, USB didnt. I got Grub Error 17. I've been searching on other threads (so *please* dont tell me how great the search function is lol) and all i can find is changing the hard drives function to auto in BIOS, but i cant do this. There doesnt seem to be an option to do this.
PLEASE HELP! I cant boot into windows OR crunchbang. And i can only find options that you can use in windows. See? Catch 22. No getting into windows, no fixing it. No fixing it, no getting into windows.

---

### Post by AmerNewbieInDE on 2009-09-19
hmm.  think we need more info.. but try this, boot live cd, run fdisk -l ... where did you install grub, to hd or usb stick.. check /boot/grub/menu.lst and make sure it is pointing to linux on the usb stick.. oh, and a stupid question, is your pc capable to boot from usb???

try here.

[http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/](http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/)

also, make sure the usb stick is in the same port, and that no other usb drives are plugged in that werent there when you installed it...

---

### Post by djwkd on 2009-09-19
Its capable of running from a USB drive.

---

### Post by djwkd on 2009-09-19
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

In other words, damn.

---

### Post by AmerNewbieInDE on 2009-09-19
if you are getting rejected saving the menu.lst file, you must open the file as admin.. try gksu kate to edit the file

---

### Post by djwkd on 2009-09-19
Ok, i took the USB Drive out and rebooted (thinking this would be akin to deleting grub) and i got the same error. So where on earth is grub stored? Will just deleting it cold help or will that mess things up worse?

---

### Post by AmerNewbieInDE on 2009-09-19
ok, call me stupid, but what is #! you mean windows? what version do you have installed

---

### Post by djwkd on 2009-09-19
I can get in now and save, but i dont know what to save. I dont know what the location is supposed to be for it. Anyway, here is the entire list in case it is of help.
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        100

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
# kopt=root=UUID=659a2a64-40e5-42c2-993f-333f9a504ae5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=659a2a64-40e5-42c2-993f-333f9a504ae5

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

title        CrunchBang, kernel 2.6.28-13-generic
uuid        659a2a64-40e5-42c2-993f-333f9a504ae5
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=659a2a64-40e5-42c2-993f-333f9a504ae5 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        CrunchBang, kernel 2.6.28-13-generic (recovery mode)
uuid        659a2a64-40e5-42c2-993f-333f9a504ae5
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=659a2a64-40e5-42c2-993f-333f9a504ae5 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        CrunchBang, memtest86+
uuid        659a2a64-40e5-42c2-993f-333f9a504ae5
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

```

---

### Post by djwkd on 2009-09-19
#! is crunchbang linux. Sorry for the confusion!

---

### Post by AmerNewbieInDE on 2009-09-19
crunchbang is on the usb?? is windows the only os on the pc? you can fix windows with the install disk, start pc with cd, look here..

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

if you want to fix grub boot loader it is a little more difficult.. but can be done..

---

### Post by djwkd on 2009-09-19
Dont have the disc. Computer came pre-installed without the windows disc.
How do you fix/delete grub? Im aware that i'll probably have to delete Crunchbang also, but its no use the way it is, so thats fine!

---

### Post by AmerNewbieInDE on 2009-09-19
i had ubuntu running from usb before i put it onto my hd. i had grub on the usb and first boot devise was usb, so when usb was in, it booted to linux and if the usb was not there, then it booted of the hard drive and booted to windows. so i know it works good this way. with the usb in, boot with live cd, open terminal and run sudo grub, then type, find /boot/grub/stage1. it should give output like (hd2,0) or what ever it labeled your usb as. type, root (hd*.*) what ever find showed... then type, setup (hd*) again what ever drive the usb is labled... type quit and reboot.. that should get your linux to boot...

well, no windows disk, the instead of puting grub on the usb, use, setup (hd0) to put grub on the main disk.

---

### Post by djwkd on 2009-09-19
Ok, i tried putting grub on the usb, using setup hd (2), but when i rebooted the all-too-familiar error still showed.
Thankyou, by the way for all you're help so far!

---

### Post by AmerNewbieInDE on 2009-09-19
if you typed "setup hd(2)" and not "setup (hd2)" look at the parentheses. i assume, "find" showed (hd2) for your /boot/grub/stage1, in otherwords, your usb drive?

---

### Post by djwkd on 2009-09-19
Yep. Ok, this isnt working properly, and i need to really try and fix it within 2 hours 15 minutes, so im figuring the easiest way would be to permanently uninstall grub and crumchbang. How would i do this?

---

### Post by AmerNewbieInDE on 2009-09-19
grub is in your mbr, you need windows disk to replace it with a windows boot mbr.. dont get frustrated.. look here...

[http://roshan18.wordpress.com/2008/02/03/reinstalling-grub-boot-loader/](http://roshan18.wordpress.com/2008/02/03/reinstalling-grub-boot-loader/)

---

### Post by djwkd on 2009-09-19
Still get the dreaded 1-7 :(
So theres no way to delete grub without windows? Man thats a sucky bootloader. (No offence, grub developers!). Hmm...If i install grub on the main hard drive, will that damage windows?

---

### Post by AmerNewbieInDE on 2009-09-19
> **djwkd said:**
> Still get the dreaded 1-7 :(
So theres no way to delete grub without windows? Man thats a sucky bootloader. (No offence, grub developers!). Hmm...If i install grub on the main hard drive, will that damage windows?

no, the boot loader is a small section just before the windows partition.. that is why i mentioned earlier, when you said you didnt have the windows cd, to <setup (hd0)>...

is your usb drive plugged in? (if not, plug it in) goto terminal, type, <sudo fdisk -l> and post the output

i just found this.. maybe it will help..

[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

---

### Post by djwkd on 2009-09-19
Hmm...
```
sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys
ubuntu@ubuntu:~$ 
```I've added the universe repository...
Oh, and im on the ubuntu live disc now.

---

### Post by AmerNewbieInDE on 2009-09-19
when you did "find /boot/grub/stage1" what was the output

---

### Post by djwkd on 2009-09-19
I installed ms-sys. All i can say is...

THANK YOU!!!THANK YOUTHANKYOUTHANKYOUTHANKYOUTHANKYOU!

THANNNNNNKKKKKKKKKKKKKKKKKKKKKKKKKKKKKYYYYYYYYYYOOOOOOOOOOOOOOOUUUUUUUUUUUUUUUUUUUUUUUUUUUUU!!!

Thankyou so much for spending your time helping me!

---

