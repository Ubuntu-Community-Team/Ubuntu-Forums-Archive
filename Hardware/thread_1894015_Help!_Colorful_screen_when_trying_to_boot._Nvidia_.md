---
title: "Help! Colorful screen when trying to boot. Nvidia geforce gt 240"
date: 2011-12-11
forum: Hardware
---

### Post by JohnDaniel on 2011-12-11
Hi ubutnu forums! This is my first post and I'm glad to be here :)

Anyway. This is probably the best place to find some support from some great experianced people. 
I've looked around all over the internet, but couldn't find a solution for the problem (but I might be wrong, haven't solved my problem though..)

I'm trying to boot ubuntu 11.10 on my PC. Everything seems to be fine. I get to the splash screen, but after about 2 minutes, still on the splash screen, i get this: [IMG]https://lh6.googleusercontent.com/-CIQ528N87zI/Tj68g7rTunI/AAAAAAAAAG4/jz9B0kZqX5E/s640/2011-08-07%2B-%2B1[/IMG]

I had the same problem with ubuntu 11.04. 
I can still install 10.04 perfectly though, without any kind of problems, and the windows 7 works with no issues either. 

I've only tried to boot ubuntu 11.10 and 11.04 from a live usb disk made with universal usb installer [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)


My hardware: 
intel quad core core i5 x64 
Graphic: Nvidia geforce gt 240
VGA screen.
Uhm... I don't know what more I should mention :P

Edit: The first time booted into ubuntu 11.10 I got this screen:
 [IMG]http://a4.sphotos.ak.fbcdn.net/hphotos-ak-snc7/374312_10150451343109591_531554590_8408570_528754865_n.jpg[/IMG]
It looks like a fragmented windows 7 screen. There are some icons for folders, some programs and my background :P
I know, it's the mac OSX lion background...

Please answer and help me! I can give more information if it is necessarily :) 
I've tried several other Linux distros, like Linux Mint and Fedora, but I get the same problem.

Thanks in advance! :D

---

### Post by JohnDaniel on 2011-12-12
I managed to solve it!
When I got to the point were the "fragmented" screen appeared, I managed to get into the terminal by hitting ctr-shift-F1. 
I the terminal i typed:
sodu apt-get remove xserver-xorg-video-nouveau

sudo apt-get install nvidia-current


Now could I run ubuntu live from the USB and install it.
After that, I rebooted and ran recuperation mode in GRUB, ran the terminal in root mode with network interface, and installed "nvidia-current"! :D

---

