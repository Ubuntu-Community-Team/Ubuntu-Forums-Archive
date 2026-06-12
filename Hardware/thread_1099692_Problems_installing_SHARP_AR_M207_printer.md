---
title: "Problems installing SHARP AR M207 printer"
date: 2009-03-18
forum: Hardware
---

### Post by Tranzistors on 2009-03-18
Hello everyone!
I am having some trouble installing SHARP AR M207 printer. Although in OpenPrinting database it is considered paperweight, I did find a driver in my CUPS installation:
/usr/share/ppd/openprinting/Sharp/sharm207.ppd.gz

However, I have no idea how to feed it to [x]ubuntu. It is connected through USB and is recognised by lsusb. Is there some URI I have to know, or should it be connected via parallel port?

Thanks for hearing me out

---

### Post by orkas on 2009-10-05
Here's what I did to get the AR M207 running (I am using it as a LAN attached network printer):

When asked to choose a driver click on Generic (NOT Sharp) -> PCL 6/PCL XL Printer -> Generic PCL 6/PCL XL Printer Foomatic/pxlmono [en]. 

If you already installed a driver for the printer and are changing it, then you will be asked wether you want to copy the old settings (default). Do NOT do this but use the new PPD as is.

Thanks to the [Open Printing Database]("http://www.openprinting.org/show_printer.cgi?recnum=Sharp-AR-M207") for setting me on the right track ...

---

### Post by nmgraywiz on 2009-11-25
Have been attempting to get sharp printers to work with ubuntu for some time now.. had it working marginaly, but now things are worthlessly useless.... I have an AL-2040CS, which I managed to get working once. however since upgrading to 9.10 I'm having to re-hunt things down to get a working configuration. Has anyone had any luck with Sharp Printers. Personally the best recommendation I can make to folks with Sharp Products.

Send them back to the company with a letter that will selfdistruct once read.

Currently I am ADAMANTLY UN RECOMMENDING ANY AND ALL SHARP Products. Their support is worthless, and they have NO plans on supporting their crappy products. Publish this far and wide. DO NOT BUY SHARP PRODUCTS. The company will not support their products being sold.

---

### Post by pmwangi80ke on 2011-12-17
> **orkas said:**
> Here's what I did to get the AR M207 running (I am using it as a LAN attached network printer):

When asked to choose a driver click on Generic (NOT Sharp) -> PCL 6/PCL XL Printer -> Generic PCL 6/PCL XL Printer Foomatic/pxlmono [en]. 

If you already installed a driver for the printer and are changing it, then you will be asked wether you want to copy the old settings (default). Do NOT do this but use the new PPD as is.

Thanks to the [Open Printing Database]("http://www.openprinting.org/show_printer.cgi?recnum=Sharp-AR-M207") for setting me on the right track ...

Hello,

I have a sharp AR-5316E am trying to install in ubuntu 10.10 but i cant get drivers for it. It is listed as paperweight in the open printing database(i dunno what that means) Please help me out....

peter

---

