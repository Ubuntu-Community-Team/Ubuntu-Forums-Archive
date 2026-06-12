---
title: "Scanner USB problem"
date: 2004-12-20
forum: Hardware &amp; Laptops
---

### Post by jasund on 2004-12-20
I have a Epson Perfection 640U USB scanner.  It works fine when I start xsane from the root terminal.   When I attempt to access it as a normal user, xsane complains – saying “no devices available”.

I also have a Kodak DX3500 digital camera with its own docking station.  When I press the button on the docking station, a pop-up appears asking if I want to import photos from the device.  This appears to work very well.

The strange twist is, after having pushed the button on the camera's docking station, xsane will WORK with my scanner without having to log into root terminal!  

A caveat:  I have 4 motherboard-integrated USB ports on the back of my machine.  This phenomenon will not work on all the available USB ports – so it seems to matter which USB port the scanner is plugged into.  When plugged into one of the other USB ports, xsane forces me to log into root terminal to “find” my scanner.

The hardware:

Celeron 2.0 Ghz CPU (northwood)
ASUS P4R800-VM motherboard 
	since Linux does not appear to like the integrated NIC, I'm using a 3C905B.
	kernel line in menu.lst updated to include “biospnp=off”.

Device manager reports the PCI devices as being ATI Technology Inc. 
	the USB-associated PCI device #s are:  1002:4345, 1002:4347, and 1002:4348  	

Linux version (downloaded from mideastern US mirror on Dec 18, 2004):
Linux hostname 2.6.8.1-3-386 #1 Tue Oct 12 12:41:57 BST 2004 i686 GNU/Linux

In my tests, I have also found that my scanner will not be found as user on another PC – a COMPAQ P450; but is found as root.  The camera docking station's button did not force the scanner to work as user.

Thanks for any input anyone may have on this issue.

---

### Post by m4ng0 on 2005-01-11
[QUOTE=jasund]I have a Epson Perfection 640U USB scanner.  It works fine when I start xsane from the root terminal.   When I attempt to access it as a normal user, xsane complains – saying “no devices available”.
[/QUOTE]

Have you tried to unplug/replug the device after booting? In that case hotplug should call
**/etc/hotplug/usb/libusbscanner**
script, which changes /proc/bus/usb devices permissions to 660: so if your user is in *scanner* group,  he can launch xsane.

---

### Post by alainhenry on 2005-01-11
I have an Epson perfection 1650 scanner on the USB port, with Warty.  It is not detected when I launch xsane.  I launched "sane-find-scanner", following the recommendations from sfw500 in another thread (see quote below).

I did "modprobe sg" as advised, then launched the command.  The terminal displayed the first two commented lines, and then stopped, without returning to prompt.  

How to get that scanner detected?  

Any advice would be appreciated

Alain


Quote from sfw500: 
============
1)
sam@ernie ~ $ sane-find-scanner

# No SCSI scanners found. If you expected something different, make sure that
# you have loaded a SCSI driver for your SCSI adapter.
# Also you need support for SCSI Generic (sg) in your operating system.
# If using Linux, try "modprobe sg".

found USB scanner (vendor=0x04b8, product=0x0110) at libusb:001:005
# Your USB scanner was (probably) detected. It may or may not be supported by
# SANE. Try scanimage -L and read the backend's manpage.

# Not checking for parallel port scanners.

# Most Scanners connected to the parallel port or other proprietary ports
# can't be detected by this program.

2) sam@ernie ~ $ sudo chmod 777 /proc/bus/usb/001/005

Basically by default only root can use the scanner. I filed a bug on this and they added the initial user to the scanner group to get it to work, but even though the initial user is now part of the scanner group I still had to change the permissions on the /proc file to get it working. Since sane-find-scanner found my scanner at libusb:001:005, that's how I know to change the permissions of /proc/bus/usb/001/005 -- those numbers change, I believe, depending on which USB port your scanner is plugged into.

If there's a better way to do this, please let me know! But this does work.

---

### Post by m4ng0 on 2005-01-13
[QUOTE=alainhenry]I have an Epson perfection 1650 scanner on the USB port, with Warty.  It is not detected when I launch xsane.  I launched "sane-find-scanner", following the recommendations from sfw500 in another thread (see quote below).

I did "modprobe sg" as advised, then launched the command.  The terminal displayed the first two commented lines, and then stopped, without returning to prompt.  

How to get that scanner detected?  
[/QUOTE]

Looking at [http://www.sane-project.org/man/sane-epson.5.html](http://www.sane-project.org/man/sane-epson.5.html)
it seems that you should edit epson.conf file to tell that your scanner is USB. Does it help?

---

### Post by alainhenry on 2005-01-15
USB ia s already activaed in epson.conf.  I commented out the SCSI line , just to make sure, but it does change anything.  
I ran usbview and lsusb, but none of these showed anything on USB ports.  I only have the scanner on USB ports.  My linux box is relatively old (Feb. 2000, AMD H7 @ 650 MHz).  Maybe it's a USB compatibility issue ?  However, it worked fine on Mandrake 9.2 and with M$ Windows
Alain

---

### Post by m4ng0 on 2005-01-15
Try this:
```
grep "P:" /proc/bus/usb/devices
```
since you have only your scanner plugged in the USB ports, you shold see something like this:

...
P:  Vendor=0000 ProdID=0000 Rev= 2.06
....

and one line like this:

P:  Vendor=04b8 ProdID=0110 Rev= 1.00

where 0x4b8 is Epson vendor ID, and 0x110 is the ID of your scanner model.
If you see this line, try editing your usb line in epson.conf this way:

usb 0x4b8 0x110

...if you don't see the line,  it is not a Sane problem, but something related to USB.
I hope it helps you.
  Massimo.

---

### Post by alainhenry on 2005-01-16
Thank you for your help.  The file "devices" is empty, and cannot be read or listed or grepped.  Still, it is listed as readable by all.  Strange.  but this is a USB problem, obviously, I'll look at the problem from this angle.  
Grazie
Alain

---

