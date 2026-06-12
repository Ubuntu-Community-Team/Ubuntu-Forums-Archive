---
title: "Laptop Dual Monitor Setup Issue"
date: 2011-06-01
forum: Hardware
---

### Post by stracky on 2011-06-01
I have a Dell Inspiron 1545

Here's some stuff from [FONT=Arial Narrow][SIZE=1]hardinfo[/SIZE]
[/FONT]
-Computer-
Processor        : Genuine Intel(R) CPU        585  @ 2.16GHz
Memory            : 2021MB (507MB used)
Operating System    : Ubuntu 10.10

-Display-
OpenGL Renderer        : Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20100330 DEVELOPMENT x86/MMX/SSE2

-Monitors-
Monitor 0        : 1366x768 pixels (the one on the laptop)
Monitor 1        : 1024x768 pixels (the external one attached to the laptop)

-OpenGL-
Vendor            : Tungsten Graphics, Inc
Renderer        : Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20100330 DEVELOPMENT x86/MMX/SSE2
Version            : 2.1 Mesa 7.9-devel
Direct Rendering    : Yes


The second monitor worked perfectly, i had to change the resolution, but other than that, it worked fine
I also hit "Make Default"

The settings carry over with reboots
However, when I close the lid (NOT sleep mode) the second monitor is set to "OFF"
When it goes to sleep, it is changed to "same display on all screens"



Also, when i launched gnome-display-properties through terminal, i got this
[FONT=Arial Narrow][SIZE=1]user@laptop:~$ gnome-display-properties

(gnome-display-properties:2979): Gtk-WARNING **: Ignoring the separator setting

(gnome-display-properties:2979): Gtk-WARNING **: No object called: [/SIZE][/FONT] 


Any help is much appreciated.

---

### Post by stracky on 2011-06-08
I configured the [FONT=Arial Narrow][SIZE=1]~/.xsession[/SIZE][/FONT] settings for [FONT=Arial Narrow][SIZE=1]xrandr[/SIZE][/FONT]

[https://wiki.ubuntu.com/X/Config/Resolution#By%20Session%20with%20.xprofile](https://wiki.ubuntu.com/X/Config/Resolution#By%20Session%20with%20.xprofile)


"Look with your eyes, not your mouth," I guess  ;)

---

