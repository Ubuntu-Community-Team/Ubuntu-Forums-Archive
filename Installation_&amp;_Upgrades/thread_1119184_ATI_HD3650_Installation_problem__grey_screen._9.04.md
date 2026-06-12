---
title: "ATI HD3650 Installation problem : grey screen. 9.04 issue ?"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by Javier92 on 2009-04-07
Hello,

First of all, my apologies for the poor quality of my english due to many horrible french teachers ^^ 

As I was trying to install Ubuntu 8.10  on my Laptop (Asus F8 series), I was confronted to a huge problem : an horrible grey screen with some black lines...

I tried first with Wubi, then I managed to make a live-usb (my CD drive is out of business). Both ways leaded many to that horrible grey screen... I found a bug report regarding this problem where someone complained about this, he was using the same laptop as me.

He told he never saw such a thing with Hardy, that's why I tried to install Hardy the same way (live-usb). The only thing I saw was the "BusyBox" screen, so I didn't understand...

I'd like to know if I could get a chance to success the installation using the 9.04 version or if it's hopeless. 

If you have any issue related to the "grey screen problem", I'd be pleased to discuss about it.

Thanks for your time :)

---

### Post by balaknair on 2009-04-07
Ubuntu 9.04 does seem to have better support for ATI cards, with the new version of the opensource ATI drivers. The version of the drivers on the Ubuntu 8.10 CD often have issues with some ATI cards.
If you want to try 9.04, you could just wait till it's released later this month(April 23rd), or get the beta version now(but it has some small defects of its own which will be fixed in the final version).

If you want to go ahead with 8.10 for now, try using the 'Safe Graphics Mode' when booting from the CD/USB drive. This usually enables you to install Ubuntu(but with a lower screen resolution). After installing, boot into the newly install, and enable the restricted hardware drivers(System menu> Administration> Hardware Drivers). Ubuntu will download and install the updated proprietary ATI drivers. Reboot to complete installation. Do not change the resolution or modify any graphics settings till you have installed the drivers. After rebooting, you should be able to get the best out of your graphics card, including Desktop Effects.

---

### Post by Javier92 on 2009-04-08
Thanks for the answer.

I tried to boot using the safe graphics mode (I pressed F4 then chose safe Graphics mode). Then whether I choose install or try ubuntu, I get the same console screen.

Shouldn't I view the normal desktop (with a lower resolution) ? there's no "installgui" command available like Debian had some time ago.

I tried "startx" but it told me "failed, no screen available".

Did I do something wrong ?

---

### Post by balaknair on 2009-04-08
Seems your GPU isn't even talking to Ubuntu.

There is a way around this that might work for you(it's never failed me yet), if you're willing to get your hands dirty playing with the command line.

Basically, we enable the VESA drivers. 
1) When you get to the blank screen, press Ctrl-Alt-F1 to start a console

2) Open the xorg.conf file with the command ```
sudo nano /etc/X11/xorg.conf
```

3) Find the section
```
Section "Device"
     Identifier     "Configured Video Device"
EndSection

```

4) Add the line**Driver "vesa"** so that it looks like this
```
Section "Device"
     Identifier     "Configured Video Device"
     Driver	    "vesa"
EndSection

```

5) Save the file and exit(press Ctrl+X --> Y --> Enter)

6) Press Ctrl-Alt-F7 to switch to GUI, and press Ctrl-Alt-Bkspce to restart X-Server. If your card works with the Vesa drivers, you should get a GUI now. Continue to install, reboot into the new install and update the ATI drivers.

I hope this helps you.
If not, you're probably better off waiting for Ubuntu 9.04.

Wishing you luck.

---

### Post by Javier92 on 2009-04-09
It told me "VESA(0) : no valid mode"


"Fatal Error : no screens found" aso...


Thanks for the help, it really seems hopeless now ;)

---

