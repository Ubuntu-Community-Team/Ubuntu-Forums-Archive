---
title: "Laptop HP 8560w + NVidia Qadro 2000M flashing"
date: 2011-12-14
forum: Hardware
---

### Post by sasoc on 2011-12-14
Hi!

I have laptop HP 8560w (I7 quad core) + NVidia Quadro 2000M graphics card. I was able to install linux(es) with nouveau.modeset=0 boot option and then after install i was able to install Nvidia driver (now i have 290.10 for Linux-x86_64).

But then arise the following annoying issue:
Screen (because of inactivity) goes to sleep mode, then I start actions (by using keyboard or mouse) and screen goes active. I am asked for password, and I am able to enter the password, but between and then monitor starts flashing : every half second it become black and then visible again (it can cause an epileptic attack) and I must log off and log on (of course close all applications - if I am able because of flashing) and then situation is stabilized.

I tried with Ubuntu 11.10 (Gnome 3 and Unity), and Linux Mint 12 (Gnome 3, Gnome Classic) and all they have this problem (maybe just frequency of flashing is different ).
Some idea, how to solve this?

There are some other issues - When window of some application is maximized, the mouse pointer focus is not at position where mouse pointer is visible on the screen (but one or two centimeters around) - so selection/dragging or menu selection fails and I can select or drag some unwanted element on screen. I don't know  this is  raleted to NVidia drivers.

Regards, Sa&#353;o

---

### Post by gordintoronto on 2011-12-14
What if you don't install the Nvidia driver?

---

### Post by sasoc on 2011-12-14
Well, I will try to uninstall. Let me see.

---

### Post by sasoc on 2011-12-14
I uninstalled nvidia-current and restart.
Machine hangs at boot (just black screen). 
From black screen I was somehow able to get command line interface (I think pressing more times Ctrl-Alt-Del) and then install drivers back manually (apt-get nvidia-common).

When I open "Additional drivers" dialog I can see two lines:
(gray dot) NVIDIA binary Xorg driver, kernel module and VDPAU library
(green dot) nvidia_current_updates

But also for the green one there is statement: "This driver is activated but not currently in use".

It is mess, isn't it ?

---

### Post by sasoc on 2011-12-15
My flashing is similar as this one: [http://www.youtube.com/watch?v=VfSozXKLuIs](http://www.youtube.com/watch?v=VfSozXKLuIs), except my has higher frequency.

---

