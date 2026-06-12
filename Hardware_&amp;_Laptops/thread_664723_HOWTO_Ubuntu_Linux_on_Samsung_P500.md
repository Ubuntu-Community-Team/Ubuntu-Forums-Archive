---
title: "HOWTO: Ubuntu Linux on Samsung P500"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by ornati on 2008-01-11
Hello. I've managed to get Ubuntu working on this laptop, Samsung P500, so here there's an HOWTO, maybe someone will find it useful.


1) chapter one: dynticks
===================
As you probably know, from kernel 2.6.21 (i386) and 2.6.24-rcX (x86-64), there's this great thing called "dynticks". Basically timer ticks fires only when needed (previously they where a fixed number, like 1000 every second).

This laptop seems to have troubles with dynticks, at least with the 32-bit kernels shipped with Ubuntu 7.10 and 8.04 Alpha 2.

64 bit kernels seems to work (the 7.10 one doesn't have dynticks and the 8.04 one, based on 2.6.24-rcX, works for me).

The problem looks like this: sometimes the laptop seems to "freeze", but if you do anything that generates an interrupt (press a key) it will go on.

Workaround: use "nohz=off" kernel boot option or go with a 64bit system.

PS: this problem needs more investigation


2) chapter two: Video
=================
Ubuntu (both 7.10 and 8.04 Alpha2) tries to use the VESA driver and fails (because the monitor wants a particular mode that isn't compatible with any VESA mode).

So basically you have to use the "fglrx" driver. If you install it, reconfigure xserver-xorg and start X it will screw up the video so you can't see anything anymore. You have to  use the "Modeline" found by the VESA driver (see /var/log/Xorg.0.log).


3) chapter three: step by step
======================
Assuming you have no problems with dinticks (64bit Ubuntu or "nohz=off" kernel boot option) and you have working network:

1 - boot from Ubuntu CD

2 - failed to start X server... oh great!

3 - ALT + F1

4 - sudo apt-get update

5 - sudo apt-get install fglrx-driver

6 - sudo dpkg-reconfigure xserver-xorg (then tell him to use fglrx driver)

7 - edit /etc/X11/xorg.conf adding the "Modeline" found by the VESA driver:

```

grep Modeline /var/log/Xorg.0.log
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)

```

Add the modeline to your xorg.conf:
```

...
Section "Monitor"
    Identifier      "Configured Monitor"
    Modeline "1280x800"  68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync
EndSection
...
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth 24
                Modes           "1280x800"
        EndSubsection
EndSection
...

```


8 - Try the X server ("X" and kill him witjh CTRL+ALT+Backspace).

9 - sudo /etc/init.d/gdm restart

10 - install Ubuntu

11 - reboot and redo steps 2- -> 9 (before you where working on the LiveCD!)

12 - enjoy!


EDIT: the exact model is "Samsung NP-P500Y"

EDIT2: with Ubuntu 7.10, when you do "dpkg-reconfigure xserver-xorg" it asks for  "monitor/LCD" autodetection... just say no, it screws up video.

EDIT 3: Ubuntu 7.10
- it seems that splash screen screws up video sometimes, it's better to disable it (remove "splash" from kernel boot options)
- this version keeps the "Modeline" setting manually added to "xorg.conf", so after the reboot you just have to install "fglrx-driver" and restart gdm.

---

### Post by gitte on 2008-03-30
Hi, 

I'm trying to install ubuntu 7.10 on my new p500. Thank for the help with the video card.
This works fine!

But how did you get the wlan to work? In my case, it does not recognize any wireless interfaces. (I'm using th 64bit version of ubuntu.)

I would appreciate your help very much!

Thank you very much, 
gitte

---

### Post by koalacurioso on 2008-04-10
I'm trying to install Ubuntu Gusty on my new Samsung P500
But this command 
> sudo dpkg-reconfigure xserver-xorg
start a configuration program that make me a lot of question... 
I suppose that I've to answer "NO" when it ask me if autodetect the monitor... I've tried with "Yes" and the screen is still black

sorry for my bad english

---

### Post by koalacurioso on 2008-04-18
So, first of all thanks to Ornati for the How-To...

Now I'm writing from my new Samsung p500 on Ubuntu Guty Installed.
There are still many troubles to solve: 

1) Wifi: the wireless card didn't works after the installation, 
         > wifi%%d: unable to attach hardware: 'Hardware revision not supported' (HAL status)
   message at the boot time, searching i've find that this laptop make uses of Atheros chipset for wifi connection... So is needed madwifi drivers...

2) Audio: I can get it works,  

3) integration with the function key (luminosity adj, monitor off/on, battery state)

4) I'm trying to understand if it's necessary to modify yet  the kernel boot option to nohz=off or if this was only for the cd boot.. now starting ubuntu I have to keep pressed some key (anyone) to make the process continue... another thing, the splash screen wasn't visible so i keep it disabled but if anyone knows how to make it works..... :)

I hope the someone could understand at least 50% of that I wrote, 
sorry for my english  and thanks

---

### Post by ornati on 2008-04-25
> **gitte said:**
> Hi, 

But how did you get the wlan to work? In my case, it does not recognize any wireless interfaces. (I'm using th 64bit version of ubuntu.)


I didn't. I just use ethernet cables! ;D

Note for the casual reader: don't buy this Laptop! Buy hardware with proper documentation and open drivers!

---

### Post by ornati on 2008-04-25
> **koalacurioso said:**
> 
3) integration with the function key (luminosity adj, monitor off/on, battery state)

4) I'm trying to understand if it's necessary to modify yet  the kernel boot option to nohz=off or if this was only for the cd boot.. now starting ubuntu I have to keep pressed some key (anyone) to make the process continue... another thing, the splash screen wasn't visible so i keep it disabled but if anyone knows how to make it works..... :)

I hope the someone could understand at least 50% of that I wrote, 
sorry for my english  and thanks

100% understood :)

I'll look at the NOHZ thing because it's a nice "power saving" feature (I've it working on my Desktop PC!! But that's documented Intel hardware...).

---

### Post by ornati on 2008-04-26
From a quick test it seems that this Laptop works better with Ubuntu 8.04 (64 bit version).

Updated HOWTO for 8.04:

------------ 8< --------- 8< ------------

1) install fglrx driver:
```

sudo apt-get update  (optional)
sudo apt-get install fglrx-driver

```

2) edit "/etc/X11/xorg.conf"

```

Section "Device"
        Identifier      "Configured Video Device"
**        Driver          "fglrx"**
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
[B]        DefaultDepth    24
        SubSection "Display"
                Depth 24
                Modes           "1280x800"
        EndSubsection[/B]
EndSection

```

3) restart installation process

sudo telinit 1
(choose "root")
telinit 2

4) once installed and rebooted:
sudo apt-get install fglrx-driver

------- >8 ---------- >8 ---------

So, no need for modeline and "nohz=off".

Good stuff that seems to work:
- dyntick/nohz: you have to disable bluetooth (System->Admin->Services) to get decent power saving... use "powertop" to monitor/improve this aspect
- suspend (and resume too!)
- hibernate
- compiz :)

Now I'm going to test 32 bit version.

---

### Post by ornati on 2008-04-26
> **ornati said:**
> 
Now I'm going to test 32 bit version.

32bit version LiveCD-tested, the NOHZ problem seems gone :)

---

### Post by xbs2008 on 2008-07-04
Wondering if you might be able to give me a tip or two

I have Ubuntu 8.04 i386 which I'm trying to install on the Samsung P500

I'm brand new to linux still, it's now running on my main PC but I still don't fully understand the workings of it.

On my Laptop it returns to a command line instead of finishing the install to the GUI.  I don't see much in the way of errors and I don't know what to do from there.

It does flash up about turning off the plug and play bios but you can't in my lappys bios. 

Any baby step ideas for linux noob? 

When Ubuntu is running properly I love it, editing text to fix things like a scroll wheel on a mouse doesn't bother me but hopefully this will get better in time.

---

### Post by ornati on 2008-07-05
> **xbs2008 said:**
> 
On my Laptop it returns to a command line instead of finishing the install to the GUI.  I don't see much in the way of errors and I don't know what to do from there.

Any baby step ideas for linux noob? 



This is what this thread is all about: the tricks needed to get Ubuntu install on this (crappy) laptop.

With Ubuntu 8.04 there is only ONE problem to intall it (it fails to bring X up so you end up with text mode instead of the graphical installer).

Read mine previous posts and you'll find what you need to do.

Basically you have to:

1)
- install the proprietary ATI driver
- edit "/etc/X11/xorg.conf" and tell it to use that driver
- restart the installation process

when installation is done:
- reboot
- graphics still doesn't work! Why? Because you installed the driver in the "LiveCD" temporary FS... so just reinstall it for real.
- reboot (or restart X)

OR

2) buy a sane laptop

:)

---

