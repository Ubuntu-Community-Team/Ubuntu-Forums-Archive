---
title: "HP USB Printer Fails After Upgrade"
date: 2008-04-08
forum: Hardware &amp; Laptops
---

### Post by schnarff on 2008-04-08
So I finally bit the bullet and decided to upgrade from Hoary to Dapper (the LTS version, so please no sniping about not being on the latest & greatest version). One of the problems I anticipated, that kept me from upgrading earlier, of course happened: printing quit working.

I've got an HP LaserJet 1150 connected via USB. If I go to System -> Administration -> Printers, it doesn't show up. If I then try "New Printer", not only does it not show up as detected, I can't even specify a port to use (the drop-down box is empty). I've tried adding it as a network printer, selecting "Cups Printer (IPP)", giving it the URI I found via the CUPS web interface (hp:/usb/hp_LaserJet_1150?device=/dev/usblp0); unfortunately, after that failing to make the printer show up once, whenever I select the appropriate PPD file (which I must do manually because my list of manufacturers/models is blank), it complains that that particular PPD is already installed.

What's really wacky is that I can get a test page to print via the Cups web interface. Of course, since Ubuntu is, for some reason, not recognizing this fact, I can't print anything useful from any of my apps, such as Firefox, Xpdf, etc., ad nauseum -- my only printer option is "Postscript/Default", and when I print there, the app looks like it's sending data, but my printer sits and quietly does nothing. Even lpoptions says there are no printers.

Oh, and to top it off:

alex@home: /etc/cups$ sudo lpstat -p -d
lpstat: Forbidden
no system default destination


Any idea WTF is going on here, and how I can get it fixed?

---

