---
title: "Xubuntu, CUPS, and my old HP LaserJet IIIP"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by quigleydoor on 2006-11-23
I'm using Xubuntu 6.06 on a PC with a 433 MHz Celeron processor.  I have a 15 year old Hewlett Packard LaserJet IIIP printer, which is in great shape for its age with some replaced parts and a new toner cartridge.  I have gotten it to work with CUPS using the standard ljet4 driver that came with CUPS.  However, because of the low RAM size of this old printer, I can only print in 150 dpi.

I have also set it up as a shared printer in SAMBA.  I can print to it from a Windows PC in 300 dpi, but there is a memory overflow problem when I print complex pages.

Now, from what I have read in the User Notes section on [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_3P_w_PCL5](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_3P_w_PCL5), there is a better driver available, called hp4laser, which correctly manages the memory of this old printer.

What is required to get this driver to work with CUPS?  The driver was last updated before CUPS was released.  I am a Linux newbie and I hope someone can explain what I need to do here.

Thanks!

---

