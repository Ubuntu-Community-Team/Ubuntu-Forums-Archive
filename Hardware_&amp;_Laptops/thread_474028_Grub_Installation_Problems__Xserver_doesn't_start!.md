---
title: "Grub Installation Problems / Xserver doesn't start!"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by Kluff on 2007-06-14
Well, I tried to install Ubuntu 7.04 on my newest notebook. 
I didn't get it work really, so that's why I am calling for help!

First, I had the problem to install Grub in the MBR. 

The following error occured (the original message was in german, I translated it into english):
"The execution of "Grub install (hd0)" failed" 
----
"Failed: Installing GRUB-Bootloader on the hard drive"

---
That's a part of the output from the console:
"mainmenu[3292]: WARNING **: Configuring "grub-installer failed with error code 1
WARNING **: Menu item "grub-installer" failed.
INFO: Modifying debconf priority from "medium" to "low""

Well, in the end, I installed LILO.
And it worked, Ubuntu loaded. YAY!!
But.....Xserver failed....the reason why I used the textmode installer CD btw.

I'm sorry, I forgot to save the output somehow, but the general error was that it didn't find any monitor!!
When I run the Xserver configuration it also couldn't detect the graphic card automatically.

Here are my system informations:
Acer Aspire 5103WLMi
AMD Turion 64x Dual-Core TL-52 (1,6Ghz, 2x 512KB L2 Cache)
15,4" WXGA Acer Crystalbrite LCD
ATI Mobility Radeon X1300 Hypermemory
1GB DDR2

I installed Zenwalk at the moment. It made no problems. 
Well, I'm a bit confused by that, because Ubuntu seems to have a bigger community and to be more popular but nevertheless I could never install it without hassle.
Well, I don't want to sound mean. 
But, bugs are always annoying. ;)

---

### Post by dannyboy79 on 2007-06-14
it's because of your ATI card unfortunately. for some reason ubuntu doesn't do well with these cards. You need to install the proper driver for your X to work right and if the installer doesn't install or chose the correct driver, then X will fail, if and when that happens again, you can simply boot to a live cd, then mount your parititon that contains your ubuntu os, then edit the file, /etc/X11/xorg.conf
and change the line that says
Driver "xxxxxx"
(NOte: i don't know what will be there and why it doesn't work)
change it to
Driver "vesa"
and at least your X server will start, then you can figure out what to do to get the ATI proprietary drivers to work. AS far as grub not being able to be installed, I have never heard of that before so I can't help. good luck

---

