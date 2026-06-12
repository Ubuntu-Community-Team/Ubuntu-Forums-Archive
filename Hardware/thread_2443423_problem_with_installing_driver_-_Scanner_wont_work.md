---
title: "problem with installing driver - Scanner wont work"
date: 2020-05-15
forum: Hardware
---

### Post by weltenwandelnde on 2020-05-15
[B]Hello, 
I was trying to install a driver for a printer/scanner HP Color Laser Jet Pro M182n
in ubuntu 18.04
The printer works but the scanner doesnt and I dont know what to do

  	 	 	 	   [/B]**I tried to install HP driver:**

 
 
 ./Downloads/hplip-3.19.12.run

[B]it all worked fine until this happened:

[/B]
PRINTER SETUP
 -------------
 Please make sure your printer is connected and powered on at this time.
 Do you want to setup printer in GUI mode? (u=GUI mode*, i=Interactive mode) : u
 
 
 HP Linux Imaging and Printing System (ver. 3.19.12)
 Printer/Fax Setup Utility ver. 9.0
 
 
 Copyright (c) 2001-18 HP Development Company, LP
 This software comes with ABSOLUTELY NO WARRANTY.
 This is free software, and you are welcome to distribute it
 under certain conditions. See COPYING file for more details.
 
 
 Searching... (bus=usb, search=(None), desc=0)
 error: No devices found on bus: usb
 Searching... (bus=net, timeout=5, ttl=4, search=(None) desc=0, method=slp)
 error: Unable To read the XML data from device
 error: Unable To read the XML data from device
 
 
 Done.
 
 
 RE-STARTING HP_SYSTRAY
 ----------------------
 
 
 HP Linux Imaging and Printing System (ver. 3.19.12)
 System Tray Status Service ver. 2.0
 
 
 Copyright (c) 2001-18 HP Development Company, LP
 This software comes with ABSOLUTELY NO WARRANTY.
 This is free software, and you are welcome to distribute it
 under certain conditions. See COPYING file for more details.
 
 
 /usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
   set_interactive(1)
 No systemtrayicon available

---

