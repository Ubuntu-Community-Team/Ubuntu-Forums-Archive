---
title: "recognizing dual video cards"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by coolgenes on 2009-10-07
I'm trying to install Ubuntu 9.04 on a custom machine made originally for Windows this spring.  Ubuntu has no problems recognizing all the hardware except the dual Radeon HD4550 video cards.  Or is this a dual monitor problem?  I have one monitor hooked up to each video card, both are the same make and model LCD 17" screen.  Is there a way to test that both video cards are recognized on the install or can it be added somehow after the install or should I start looking into Xinerama or XRandR or some dual monitor support?  Thanks for any help.

---

### Post by Mark Phelps on 2009-10-07
Have you confirmed that you're running the restricted ATI drivers, and the latest ones at that?  Enter "fglrxinfo" in a terminal to see what driver version you're using.

---

### Post by coolgenes on 2009-10-14
thanks, it says:
couldn't find RGB GLX visual!

I followed the directions of the ATI driver and when I ran sh ./ati-driver-installer-9-9-x86.x86_64.run everything stabilized for the one vga card and the Catalyst Control panel is present, but whenever I put in the second card it still goes straight to nongraphical login and reverts to a server like interface when logged in.  

From the info above it's pretty obvious that it's not installed correctly but what can be done?

---

### Post by coolgenes on 2009-10-15
I tried a new approach this morning.  Instead of using the driver I downloaded from ATI and trying to use it from bash, I found [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#2._Create_.deb_packages](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#2._Create_.deb_packages).
which described how to install the hardware driver from Ubuntu.  It was the only proprietary driver listed as available but after activating it it says "this driver was just disabled, but still in use"  Anyone have time to explain this?  Further, after typing fglrxinfo in terminal I now get:
display:  :0.0  screen:0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4550
OpenGL version string: 2.1.8575

I have second card but as you can read from the previous post it caused problems whenever I reinstalled it and had to reset the driver in a very shaky screen.  I'm worried it will be a problem now since the driver didn't seem to install.  Any advice?

---

### Post by coolgenes on 2009-10-16
anyone? bump :)

---

### Post by coolgenes on 2009-10-20
I could really use some help with this... bump

---

### Post by coolgenes on 2009-10-23
bump...

---

### Post by markbuntu on 2009-10-23
First, download the latest driver from the ati site (9.10 has just been released) to your Desktop.

Remove the driver you got with hardware manager, it is too old and has no support for the 4550. You can use the synaptic package manager and do a search for fglrx and choose all the fglrx packages and completely remove them.

after that finishes reboot into the recovery kernel and use the fix x option. Resume. This should get you to a desktop using the generic Vesa driver.

Open a terminal
 cd Desktop

sudo sh ./ati-driver-installer-9-10-x86.x86_64.run

type your password. When the installer screen asks you what you want to do just hit enter, same with the license. When it finishes
 close the window and in terminal

sudo aticonfig --initial

reboot again

Hopefully you will have one screen working

In your menus you will find the Catalyst Control Center and there you can enable the second screen/card in the display manager by dragging it into the window. Reboot. You should now have both screens with independent displays. Now you can enable xinerama and reboot again.

Due to a lack of RandR capability you need to use xinerama with multiple gpus. 

There is a way to get compiz effects working on one screen but I do not know how and have not tried it.

Let us know if this helps.

---

### Post by coolgenes on 2009-10-29
ok, I did what you suggested with the one video card installed and all was well. upon shutting down, adding the second video card, and restarting I can no longer get the graphical gnome display it asks for user name and password in black/white text then when I input that I get text based system.  I tried rerunning the ati driver install with the same results.

OK I give up, I uninstalled the ATI Catalyst software and driver, installed a Nvidia card and added the Nvdia-glx-180 driver and both screens came up immediately.

---

