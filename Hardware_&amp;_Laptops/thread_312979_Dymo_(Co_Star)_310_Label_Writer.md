---
title: "Dymo (Co Star?) 310 Label Writer"
date: 2006-12-05
forum: Hardware &amp; Laptops
---

### Post by drewwa on 2006-12-05
Hello folks,

My first post on here! I've been determined to rid my house of Windows for months, and *ubuntu has gotten me a long way down the road and I'm 99% there. I've learn't a lot and so far I've managed:

Using Xubuntu 6.10...

Wireless networking
Samba shares
Printers including Canon ip5000(remote network) and Lexmark x1100 (usb) acting as both printer and scanner (xsane)
Digital Cameras
Wine for Picasa
Openoffice
Palm PDA Sync (usb)

BUT! One final thing has got me stuck.

My problem stems from my wife using a very handy little label printer in the kitchen called a Dymo 310 Labelwriter (I believe it is the Dymo-Costar varient).

Replacing the printer is not an option, alteast not in the foreseeable future - it's in the kitchen and is essential to my wife. It has to be connected via USB because of the location of the PC.

It is not correctly recognised by the usb system on any of my machines. I get an error code in /var/log/messages from usblp.c - 

usblp: probe of 1-2:1.0 failed with error -5
drivers/usb/class/usblp.c: v0.13: USB Printer Device Class Driver

According to [this site](http://www.linuxprinting.org/show_printer.cgi?recnum=Dymo-CoStar-LabelWriter_XL) I need to modify usblp.c and uhci-hcd.c in order to fudge 'bulk transfer mode'. 

Those instructions refer to kernel version 2.4.9 which is two year old now. I downloaded that source, modified the two files and built the kernel but that blew my xubuntu install away.

I went back to the xubuntu 6.10 current kernel (2.6.17-10) and downloaded that only to find that usblp.c and uhci-hcd.c in this kernel have radically different code to the earlier kernel and I can'f figure out how to fudge them for this 'bulk transfer mode'.

Thus, I cannot get this labelwriter to work, and if I can't get this printer to work I'm stuck with Windows XP on one machine, which is REALLY annoying as it is the one that the family uses most.

Any help would be greatly appreciated.

Cheers,

Drew.

---

### Post by drewwa on 2007-01-11
Short version : Replace Dymo 310 with 330 or better (I used 400 Turbo)

Long Version :

Solved my own problem.

The Dymo 310 is simply not going to work with Linux due to clunky usb hardware design.

After doing some research I was confident enough to buy the Dymo 400 Turbo as a replacement.

On plugging in the 400 dmesg output shows the device correctly (Hurrah!)

The default Dymo driver works with this from CUPS (I found the Dymo-Costar drivers gave me a footmatic-rip failed error)

You can then set up appropriate page sizes.

On thing is not obvious however. When you do a test print you can see the output is in 'portrait' mode. Switching to landscape mode makes no difference.

What you have to do is in the printer configuration 'Settings > Printing', you need to go to 'Job Options' and add 'Landscape' as a default, set to 'True'.

I can now print labels from Openoffice (I need to learn how to link this with a db, but that's another problem ;-)

Tried the dymo software under wine, but because it tries to auto-install the windows print driver and detect the printer over USB it doesn't work.

Cheers,

Drew.

---

