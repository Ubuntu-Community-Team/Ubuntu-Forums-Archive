---
title: "install HP1018 printer in Ubuntu 16.04"
date: 2016-08-28
forum: Hardware
---

### Post by bobptz on 2016-08-28
Can somebody please help me install an HP1018 in ubuntu 16.04?

I had some trouble installing it in 12.04 and 14.04 but I finally made it work (see [http://bbb-solutions.blogspot.gr/2014/03/install-hp1018-printer-driver-in-ubuntu.html](http://bbb-solutions.blogspot.gr/2014/03/install-hp1018-printer-driver-in-ubuntu.html)  and [http://bbb-solutions.blogspot.gr/2014/12/hplip-error-unable-to-communicate-with.html](http://bbb-solutions.blogspot.gr/2014/12/hplip-error-unable-to-communicate-with.html) ).  However now I am totally stuck.  What's more, the pc will not boot is the printer is turned on (and connected with the usb cable.

I have changed usb cables and usb ports.  Same thing.

The problem appeared as soon as I upgraded from 14.04 to 16.04.

Here are the results of some related commands:
```

bob@bob-pc:~$ lsusb
Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:082d Logitech, Inc. HD Pro Webcam C920
Bus 003 Device 004: ID 03f0:4117 Hewlett-Packard LaserJet 1018
Bus 003 Device 002: ID 045e:07b9 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
$ sudo hp-setup
[sudo] password for bob: 

HP Linux Imaging and Printing System (ver. 3.16.3)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None), desc=0)
error: No devices found on bus: usb

```

```

$ hp-firmware

HP Linux Imaging and Printing System (ver. 3.16.3)
Firmware Download Utility ver. 2.4

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: No device found that support this feature.

```

---

### Post by Bucky Ball on 2016-08-28
Have you [tried this]("http://hplipopensource.com/hplip-web/install_wizard/index.html")? You need HPLip installed.

---

### Post by bobptz on 2016-08-28
HPLIP was already installed (since 12.04).  Maybe if you tell me a diagnostic I can run it ans see what it gives.

---

### Post by Bucky Ball on 2016-08-28
You have chosen your printer model, Ubuntu and 16.04, downloaded and installed in your current 16.04 the software from the link I provided?

---

### Post by bobptz on 2016-08-28
> **Bucky Ball said:**
> You have chosen your printer model, Ubuntu and 16.04, downloaded and installed in your current 16.04 the software from the link I provided?

No, hplip was already installed from 12.04.

So you mean I have to remove it and then follow the procedure again?

How about CUPS?  Do I have to uninstall and reinstall too?

---

### Post by Bucky Ball on 2016-08-28
No, no need to remove CUPS, nor the old HPLip. From memory, when you install the new one it will see the old one, upgrade or replace it if necessary. If you are running the HPLip from 12.04, that is old. A lot has changed and that probably includes with HPLip. You are better to go with the HPLip that is specifically for your release so choose the 16.04 version from the link I provided.

You should find some instructions for the HPLip install either on the HP website where you get the driver or in a README file somewhere in the download.

---

### Post by bobptz on 2016-08-29
Sorry, I do not understand.

So are you saying that all software applications are upgraded with the ubuntu upgrade?  If yes, then I should not have to worry with installing fresh cups or hplip.

Likewise I see now I have filezilla 3.15.0.2, build date Feb 2016.  From what I see here this is the one bundled with ubuntu 16.04:  [https://launchpad.net/ubuntu/xenial/+source/filezilla](https://launchpad.net/ubuntu/xenial/+source/filezilla)

I will follow your instructions. But from what I understand I should have right now the cups and hplip bundled with 16.04.  If it was working in 14.04, there is no reason it is not working now.

---

### Post by Bucky Ball on 2016-08-29
Forget about CUPS. You don't need to do anything with that. That would have been upgraded with 16.04.

---

### Post by bobptz on 2016-08-29
I followed the instructions and installed the latest HPLIP.

Same problem.  The pc will not boot if the printer is on.

Then I run hp-setup.  This is the result:   **error: No devices found on bus: usb **

This is what was happening before, when I opened this thread.

```
$ hp-setup

HP Linux Imaging and Printing System (ver. 3.16.8)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None), desc=0)
error: No devices found on bus: usb

```

Back to square one.

---

### Post by bobptz on 2016-08-29
Rebooted a couple of times.  Unplugged all cables.  Now it seems to detect the printer, but still it gives me this error message, which I am trying to google solve it:

 [B]error printer queue setup failed. 
error successful-ok-ignored-or-substituted-attributes
[/B]

---

### Post by bobptz on 2016-09-03
Yet another installation of hplip, then run "sudo hp-setup".  It gave error:

```

$ sudo hp-setup
[sudo] password for bob: 

HP Linux Imaging and Printing System (ver. 3.16.8)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
Searching... (bus=usb, search=(None), desc=0)
error: No devices found on bus: usb


```

---

### Post by bobptz on 2016-09-03
After many reinstallations, the situation seems worse.  Now I get the extra error message:
[B]Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon [/B]


```

$ sudo hp-setup
[sudo] password for bob: 

HP Linux Imaging and Printing System (ver. 3.16.8)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
Searching... (bus=usb, search=(None), desc=0)
error: No devices found on bus: usb

```

I disabled the IBUS in Language Support but the problem remains.


I would gladly through away the printer and buy a new one if I knew it some kind of incompatibility.  I am just not sure that if I buy a new printer I will not face the same problem.

---

### Post by bobptz on 2016-09-04
After a clean reinstall of ubuntu 16.04, all problems disappeared.  The HP1018 is printing with no problems.  I was ready to throw it away.

---

### Post by Bucky Ball on 2016-09-04
Good news and thanks for marking solved.

Enjoy. :)

---

