---
title: "Bluetooth Wacom Tablets and VMWare"
date: 2007-02-15
forum: Hardware &amp; Laptops
---

### Post by Kat of Zion on 2007-02-15
Okay...

First off I have a theory.  I think somehow Linux and VMWare are fighting with eachother over the control of Bluetooth. 

I plugged in my USB Bluetooth Dongle to a port.  Ubuntu (Edgy) saw the dongle no problem.  However I cannot get my wacom tablet to be seen by the dongle in Linux.  I do have the driver software for the Wacom Graphire 6x8 tablet but of course it is windoze based.

I tried to also see if VMWare could see it instead. After installing the drivers, I told VMWare to load Bluetooth into one of the 2 USB ports Im allowed and again, it saw the dongle with no problem.  I added the Wacom to the Bluetooth device list as the tablet's instructions say and again no problem.

However, when it attempts to connect the Wacom tablet via bluetooth, suddenly Ubuntu Edgy takes the dongle back to itself.  The Bluetooth device list in VMWare still says it is connected but Im still unable to get any reaction from using the pen on the tablet.

What am I doing wrong?:confused: :confused: :confused: :confused:

---

### Post by Kat of Zion on 2007-03-01
Well, one solution that was tried was to uninstall bluetooth from linux, in hopes that Linux would stop grabbing it back from VMWare constantly. That seems to have done the trick.  

Still, now when I go to add a device in the Bluetooth control panel of my windows machine, it gets detected.  As windoze installs the bluetooth device, the actual bluetooth device dies mid-action.  

What the hell is going on???

-Kat:confused: :confused: :confused: :confused:

---

