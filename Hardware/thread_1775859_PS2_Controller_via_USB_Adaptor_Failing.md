---
title: "PS2 Controller via USB Adaptor Failing"
date: 2011-06-05
forum: Hardware
---

### Post by fastball10101 on 2011-06-05
[FONT=Verdana][SIZE=2][COLOR=black]I have a ps2 controller and a usb adapter for it, because I want to be able to play games with a controller on the computer (Specifically portal =]). It isn't being recognised in ubuntu as far as I can tell.

I have this controller:[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=black]
DualShock 2 Analog Controller
[http://www.amazon.com/Analog-Controller-DUAL-SHOCK-Sony-PlayStation/dp/B0032GVBS4/ref=sr_1_1?ie=UTF8&s=miscellaneous&qid=1307284694&sr=1-1](http://www.amazon.com/Analog-Controller-DUAL-SHOCK-Sony-PlayStation/dp/B0032GVBS4/ref=sr_1_1?ie=UTF8&s=miscellaneous&qid=1307284694&sr=1-1)[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=black]


this adapter:[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=black]
PS PS2 USB Dual Controller to PC Adapter Converter
[http://www.amazon.com/gp/product/B000F6BGXY/ref=olp_product_details?ie=UTF8](http://www.amazon.com/gp/product/B000F6BGXY/ref=olp_product_details?ie=UTF8)[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=black]

and am running  [COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C]Ubuntu 11.04 - the *Natty Narwhal*  [/COLOR][/FONT][/COLOR]and GNOME version 2.32.1

The adapter comes with an installation disk with these drivers on it:
DOUBLE USB Drier.exe
PSII & USB Conversion Driver.exe
SINGLE USB Driver.exe
USB Racing Wheel Driver.exe

Obviously for windows, so not much help for linux.

So I am asking either for a way to get it recognised, or just for some application/script that monitors key/button events so i can definitively tell that it isn't being recognised (and not that the buttons just aren't bound to anything useful). I was hoping for something like this [/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=black][http://download.oracle.com/javase/tutorialJWS/uiswing/events/ex6/KeyEventDemo.jnlp](http://download.oracle.com/javase/tutorialJWS/uiswing/events/ex6/KeyEventDemo.jnlp) that would catch the controller events....


I have searched the forums for this issue, but it seems like it either just works for most people.[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=black]

THANKS[/COLOR][/SIZE][/FONT]

---

### Post by fastball10101 on 2011-06-09
Four day bump.
If this is in the wrong section, please let me know!

---

### Post by BrandonC19 on 2011-06-09
Welcome to he Forums. :D

First off, can you plug the controller in and post the output of the terminal command "lsusb" here in a new reply? 
Post the contents of the output in CODE tags, by clicking the hash (#) mark in the reply window.

---

### Post by fastball10101 on 2011-06-09
with it plugged in:
```
~$ lsusb
Bus 008 Device 002: ID 1b1a:0000  
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 007 Device 002: ID 0810:0001 Personal Communication Systems, Inc. Dual PSX Adaptor**
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:09a1 Logitech, Inc. QuickCam Communicate MP/S5500
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```So it seems that the adapter is recognised. The output stays the same if I unplug the controller from the adapter.

---

### Post by BrandonC19 on 2011-06-09
Okay, it sees the device, so it should have no trouble utilizing it. There's a command you can run and actually see if pressing a button on the controller cause a hardware interrupt, but I can't remember nor find it. 
So here's a workaround. 
Can you open Ubuntu Software Center, and install mupen64? 
Then run it from the Games section of your Applications menu, and under the Options menu of the program, select "Input Settings". 
Its the easiest way I know of outside of that blasted command.

---

### Post by coolleo83 on 2011-08-20
I know a old post but I am also having the same problem 


#
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:8140 Dell Computer Corp. Wireless 360 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:8100 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
#

This is the output of my lsusb

---

### Post by flangemonkey on 2012-03-13
the program to monitor events is called **xev**.

However, my Personal Communication Systems, Inc. Dual PSX Adaptor shows no input received by X.

I'm running gentoo, and need to check what modules are loaded into my kernel, if I get success beyond this, I'll post more here.

EDIT: (update)

My basic kernel seems to support the device; downloading and installing **joystick** (it is in the repositories for ubuntu) will provide jstest

I used:
```

jstest --event /dev/input/js1

```

then make sure you have xserver-xorg-input-joystick (or xorg-driver-input metapackage) installed, then I'm stuck, probably a good idea to regenerate your xorg.conf..?

---

### Post by ahgblopes on 2012-05-17
> **flangemonkey said:**
> the program to monitor events is called **xev**.

However, my Personal Communication Systems, Inc. Dual PSX Adaptor shows no input received by X.

I'm running gentoo, and need to check what modules are loaded into my kernel, if I get success beyond this, I'll post more here.

EDIT: (update)

My basic kernel seems to support the device; downloading and installing **joystick** (it is in the repositories for ubuntu) will provide jstest

I used:
```

jstest --event /dev/input/js1

```then make sure you have xserver-xorg-input-joystick (or xorg-driver-input metapackage) installed, then I'm stuck, probably a good idea to regenerate your xorg.conf..?

I also have this adaptor and i'm running Gentoo. What kernel config do you use for Gentoo recognizes it?

---

### Post by Iowan on 2012-06-03
Wouldn't a Gentoo forum be a better place for Gentoo problems?

---

