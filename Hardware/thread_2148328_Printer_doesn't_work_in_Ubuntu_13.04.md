---
title: "Printer doesn't work in Ubuntu 13.04"
date: 2013-05-24
forum: Hardware
---

### Post by debodas on 2013-05-24
I made the switch to Ubuntu from Mint (Mint 14, moved to Ubuntu 13,04). My printer,a Brother HL-2140, was automatically detected and worked fine in Mint 14, Kubuntu 12.10 and Xubuntu 12.04, but not in Ubuntu 12.04, 12.10, and now 13.04. When I install the recommended driver, and then print something, it spits our blank pages until I stop the printer.

How can I get my printer to work?

---

### Post by gifford on 2013-05-24
Where did you get the driver from? The Brother site?
If not, go to the Brother site and follow the installation guide for your printer.
Here is the link: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

---

### Post by pdc on 2013-05-26
so are you happy with this, debodas?

the brother instructions say: you need two drivers, lpr and cupswrapper

lpr driver first

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brhl2140lpr-2.0.2-1.i386.deb&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brhl2140lpr-2.0.2-1.i386.deb&lang=English_lpr)

and then cupswrapper

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/cupswrapperHL2140-2.0.2-1.i386.deb&lang=English_gpl](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/cupswrapperHL2140-2.0.2-1.i386.deb&lang=English_gpl)

then open your browser and paste in 

[http://localhost:631/printers](http://localhost:631/printers)

and you should see what you have just installed

then see if you can print

---

### Post by debodas on 2013-05-28
> **pdc said:**
> so are you happy with this, debodas?

the brother instructions say: you need two drivers, lpr and cupswrapper

lpr driver first

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brhl2140lpr-2.0.2-1.i386.deb&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brhl2140lpr-2.0.2-1.i386.deb&lang=English_lpr)

and then cupswrapper

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/cupswrapperHL2140-2.0.2-1.i386.deb&lang=English_gpl](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/cupswrapperHL2140-2.0.2-1.i386.deb&lang=English_gpl)

then open your browser and paste in 

[http://localhost:631/printers](http://localhost:631/printers)

and you should see what you have just installed

then see if you can print

Haven't had time to try it out yet.

Here's hoping it works :D

---

### Post by Gilles2 on 2013-06-01
Your sollution worked for me (Brother HL-2030).
fyi, Ubuntu was just saying that the .deb to install are in bad quality,but i said ok to intall.
Cheers

---

### Post by debodas on 2013-06-05
Sigh. Doesn't work. :(

---

### Post by debodas on 2013-06-09
Brother HL-2140 Foomatic/hpijs-pcl5e (recommended)

On advice from someone, I changed the drivers to this. (which is why it now shows as recommended). This works fine.

---

### Post by aprotopapas on 2013-12-15
I'm glad to hear you sorted it out.  I had a similar problem and eventually figured it out.  It doesn't require any external packages and I believe it would have solved your problem as well so I'll post for future trouble-shooters.

Problem:
Brother HL 2140 started spewing blank pages after upgrading from Lubuntu 13.04 to 13.10

Cause:
The installed driver was the postscript driver when it should be the hpijs-pcl5e driver. 

Fix:
sudo apt-get install printer-driver-hpijs hpijs-ppds

I bounced cups server though I'm not sure that was necessary:
sudo /etc/inet.d/cups restart

Then I had to override the automatic printer driver selection of system-config-printer. To do that, you have to give the printer device location instead of letting it be found automatically.
The cups server provides an admin interface as an http service.  I visited [http://localhost:631/printers](http://localhost:631/printers) and looked at the info for the incorrectly installed printer to get the URI.
[SIZE=2]In my case, the URI was:   usb://Brother/HL-2140%20series?serial=A9J307995

Select "Enter URI" on the first page of the system-config-printer dialog and then enter the URI you got from the cups admin page.
After that, the dialog will give you options for printer manufacturer and then finally the driver selection where you get a chance to pick the correct driver hpijs-pcl5e.

Now you have a new printer defined.  Delete the old misconfigured one and you should be all set.

[/SIZE]

---

### Post by bigonegotaway2 on 2014-07-04
I just went into System Settings/Printer/Properties/Make and Model then set to Brother HL-2140 Foomatic/hl1250. The printer is now working perfectly with Ubuntu 14.04. I'm sure it would also work with earlier distros as well. :p

---

