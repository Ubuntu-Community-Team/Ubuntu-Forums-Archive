---
title: "USB Printer not properly detected - Epson Stylus Photo 870"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by Tim Prosser on 2007-05-31
Apologies if this is already answered somewhere - can't find any reference.

I've got a fairly old Epson USB Photo Printer, which has worked pretty well for a long time.  After upgrading to Feisty (upgrade not rebuild) from Edgy, I've had a few problems.  The printer is listed in kprinter/localhost:631 etc but only in the HAL context, not as a direct USB printer:

> 
lpinfo -v

network beh
network bluetooth
direct hal:///org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_printer_noserial
direct canon:/dev/lp0
direct epson:/dev/lp0
direct scsi
serial serial:/dev/ttyS0?baud=115200
serial serial:/dev/ttyS1?baud=115200
serial serial:/dev/ttyUSB0?baud=230400


I have an even older parallel Epson Stylus 800 (! still working !) which is used with extra cheap ink for drafts etc, and this behaves fine.


The problem is that if I set everything up using the hal:/// pointer, it eventually drops out, usually after a reboot, and anything sent to the queue gets stuck as "Held".

lsusb shows it well enough:

> 
lsusb

Bus 003 Device 007: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 003 Device 006: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:08d9 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000



Any ideas why it doesn't show up as a direct USB Printer?  It always used to in Edgy and Dapper.

Thanks

Tim

PS I've messed around with permissions (made sure cupsys is in plugdev group etc) but that doesn't seem to have had any effect, nor has chmodding a+rw /dev/usblp0

---

### Post by hummingbird59 on 2007-05-31
I'm having problems with printing as well.  I had two printers connected, and had to go back to just one because something somewhere keeps setting me from parallel local to usb network when I have more than one printer connected.  Check the bug reports on launchpad.net (specifically #117825 and 104166).  I don't know enough to say whether this will be helpful to you or not (you seem to know more than I technically) but researching launchpad led me to believe there is a problem, ie bug somewhere.  Hope this helps-wish I knew more!

---

### Post by Tim Prosser on 2007-06-07
Thanks for the quick reply - I hadn't spotted those bugs on Launchpad.

Unfortunately, I think the problem I have is slightly different, although it may well be related.  No luck so far, just have to keep removing/adding the printer every time it stops working.

I'll have another trawl through the bug list and the forum...

---

### Post by Tim Prosser on 2007-06-11
I tried the following:

Removed all printers

Removed hal-cups-utils using Synaptic (disabling the HAL interface)

ran

sudo dpkg-reconfigure cupsys

Deactivated all backends except USB and Parallel


Following this, was able to add the USB Epson printer as direct USB rather than only using the HAL identifier.

Suspect this has solved the problem but time will tell.



> 
lpinfo -v

network beh
direct usb://EPSON/Stylus%20Photo%20870
direct parallel:/dev/lp0
direct canon:/dev/lp0
direct epson:/dev/lp0
network smb


---

