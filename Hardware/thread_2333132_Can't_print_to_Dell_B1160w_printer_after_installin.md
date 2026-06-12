---
title: "Can't print to Dell B1160w printer after installing Xenial"
date: 2016-08-07
forum: Hardware
---

### Post by cwmccabe on 2016-08-07
Until recently, I was using Trusty Tahr and had no problems printing to my Dell B1160w USB direct-attached USB printer.  But when I installed Xenial Xerus, I can no longer print.  The printer appears to be recognized correctly, and it appears in the Printers settings panel. But when I click the "Print Test Page" button, nothing happens.

When I "lpr testDoc.txt", the lights blink on the printer, but nothing prints.  A pop-up prompt tells me it is "Printing" and then "Printing Completed" -- but nothing prints.

##

Here are some error messages in /var/log/cups/error_log:

> tail -f /var/log/cups/error_log (...when printing test page from printer settings panel)

E [28/Jul/2016:18:48:42 -0400] [Client 59] Returning IPP client-error-document-format-not-supported for Print-Job (ipp://localhost/printers/B1160w-Mono-Laser-Printer) from localhost

> tail -f /var/log/cups/error_log (...when re-attaching USB cable after removing printer from printer settings panel)

E [07/Aug/2016:08:47:47 -0400] [cups-deviced] PID 4140 (gutenprint52+usb) stopped with status 1!
W [07/Aug/2016:08:48:01 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id \'B1160w-Mono-Laser-Printer-Gray..\' already exists

##

Looking into Gutenprint, I do not see that Dell printers are supported.  Is this the problem?  If so, how to get around it?  Or if not, what else should I be doing to get my printer working with Xerus?

Thanks!

---

### Post by kurt18947 on 2016-08-07
I have no experience with Dell printers. Are they still rebadged Lexmarks? Or is someone else making them?  I had a Brother printer do that a couple years ago. The problem was a CUPS filter, or lack of one I don't recall. Sorry I can't be of more help.

---

### Post by him610 on 2016-08-07
Don't know if this is applicable in your situation, but I own a Dell 1700N B&W laser printer. Avoid using the Dell or Lexmark drivers.

To get mine to work, I used for Make: Generic, for Model: PCL 5 LF (you may need to research and compare your capabilities with the different drivers)

Mine is connected through my local network while yours is connected through a USB port which should not make any difference if you can get it right.

System Settings>Printers>+Add
You will need to identify/set the URI ( box will appear that says it is searching for drivers, eventually comes up with a listing of Makes)
Choose *Generic*
Next you get to choose the Driver (It may even recommend one for you - choose text only as a last resort) (This is where I chose *PCL 5 LF.)* 

PCL stands for Printer Control Language which was developed by HP many years ago; many printer manufacturers use PCL for their printers; it's kind of like a standard because HP made it available and so many use it.

---

### Post by cwmccabe on 2016-08-09
Thanks Kurt18947 and Him610.  I tested all the Dell and most of the Generic drivers and wasn't able to find one that worked.  I had to use the CUPS web interface ([http://127.0.0.1:631/](http://127.0.0.1:631/)) because the Add-Printer feature in the Printers Settings panel didn't give me much control.  I still got it working though, by (what I should have known to try first) using the Dell Unified Linux Driver Installer from here: [http://www.dell.com/support/home/us/en/04/Drivers/DriversDetails?driverId=M4HVD](http://www.dell.com/support/home/us/en/04/Drivers/DriversDetails?driverId=M4HVD)

---

### Post by kurt18947 on 2016-08-09
> **cwmccabe said:**
> Thanks Kurt18947 and Him610.  I tested all the Dell and most of the Generic drivers and wasn't able to find one that worked.  I had to use the CUPS web interface ([http://127.0.0.1:631/](http://127.0.0.1:631/)) because the Add-Printer feature in the Printers Settings panel didn't give me much control.  I still got it working though, by (what I should have known to try first) using the Dell Unified Linux Driver Installer from here: [http://www.dell.com/support/home/us/en/04/Drivers/DriversDetails?driverId=M4HVD](http://www.dell.com/support/home/us/en/04/Drivers/DriversDetails?driverId=M4HVD)

Good deal! It's nice the Dell makes an effort.  For more printer control I use 'system-config-printer' on Ubuntu-Gnome. Either run it from the 'run' box (alt+F2) or via a .desktop file. Xubuntu and I think Lubuntu among others use it for printer administration by default. The default 'printers' app in Ubuntu-Gnome and I guess Ubuntu is pretty limited.

---

