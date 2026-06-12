---
title: "XEROX Workcentre 4118 prints ok, but 2 pages at a time"
date: 2009-06-17
forum: Hardware
---

### Post by lanhelp on 2009-06-17
Hello,

I have Xerox Workcentre 4118 printer on ubuntu 9.04. It installs automatically but the selected driver not work. I use instead the HP Laserjet 4L (ljet4) cups driver and now is printing correctly, perfectly, but always got another page printed with the word "RESET", any ideas for save the planet?? Thank you.

---

### Post by halitech on 2009-06-20
Download the Xerox driver from here:
[http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=WC4118&Xlang=en_US&Xcntry=USA](http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=WC4118&Xlang=en_US&Xcntry=USA)

use the Linux CUPS Printing Package. Download it, extract it and then readd the printer. When it asks what model to use, you should have an option to browse for a driver, browse to where the PPD files have been extracted and select the correct model.

---

