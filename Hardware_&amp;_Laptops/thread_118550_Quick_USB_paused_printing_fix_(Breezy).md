---
title: "Quick USB paused printing fix? (Breezy)"
date: 2006-01-17
forum: Hardware &amp; Laptops
---

### Post by Tripmonkey_uk on 2006-01-17
If your having trouble printing to a USB printer because of the paused printing error, then try this quick (& dirty) fix before u start messing about un-installing cups & re-writing config settings. 
It worked for my Epson R300 printer anyway.
Create a Desktop or taskbar application launcher with the following settings:
Name - Whatever u like! 
Command - sudo chmod a+rw /dev/usb/lp0
Type - Application
Icon - I used the bug icon :razz: 
Make sure that it's set to run in terminal.

It seems that Ubuntu sets the printer permissions back to Root every time u reboot.
U should just need to click this shortcut once (everytime u boot up) to enable the printer.

I can't offer any more info on this as i've only just rearly started to use Linux.. Sorry.
Goodluck!

***EDIT***
Looks like this will only let u print the test page from the printer properties :(
This sucks!
I've tried editing /etc/udev/permissions.rules.
I've tried re-installing cups etc.
I've also tried changing the permissions of /dev/usb/lp0.
This is my only vice so far with Ubuntu Breezy & it worked fine with Hoary.
I'm out of ideas so if any one else can help then I would be forever grateful.

---

### Post by Tripmonkey_uk on 2006-01-17
***UPDATE***
This seems to work after all :) 
Managed to print from Gimp & OpenOffice.
I just have to make sure that the printer doesn't set itself to pause after every print by going into the printer control panel.

---

### Post by FloSynergy on 2006-01-30
i'm having exactly the same  problem.

how can anyone in their right mind release an os that regularly screws up the printing system?

whether open source or not, this is just unacceptable - ubuntu linux was released prematurely.:mad: 

how will this distro ever go mainstream if ordinary users have to start hacking about in the dark underbelly of their system?:mad: i don't have the time to fiddle with this stuff - and fix what i break in  the process.

kubuntu needs to sort out its twisted permissions issues quickly...

flo

---

### Post by amarra on 2006-04-19
To cleanly solve the permissions trouble on the /dev/usb/lp0 device it is better to change the udev configuration, since it creates the device relative to the printer the first time it is turned on after a boot.
To do this modify the /etc/udev/permissions.rules

sudo joe /etc/udev/permissions.rules

then modify the line

BUS=="usb", KERNEL=="lp[0-9]*", GROUP="lp"

into 

BUS=="usb", KERNEL=="lp[0-9]*", GROUP="lp", MODE="0666"

So the next time the device is created by udev, it will have the right permissions.

Hope this can be useful.

Bye

**Edit of 2007.08.26 ===============**
On Kubuntu 7.04 the file to change is:
/etc/udev/rules.d/40-permissions.rules

and the line is:
SUBSYSTEM=="usb", KERNEL=="lp[0-9]*",   GROUP="lp"
that should become:
SUBSYSTEM=="usb", KERNEL=="lp[0-9]*",   GROUP="lp",     MODE="0666"
Bye

---

### Post by topgi on 2006-04-21
This last trick, doesn't work for me with the canon ip4000R.

---

