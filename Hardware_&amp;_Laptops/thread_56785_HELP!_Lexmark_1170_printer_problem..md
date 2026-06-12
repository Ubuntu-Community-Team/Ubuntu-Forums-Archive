---
title: "HELP! Lexmark 1170 printer problem."
date: 2005-08-14
forum: Hardware &amp; Laptops
---

### Post by Flashes of Sky on 2005-08-14
Ok, this all started today. I needed to use the printer so I plugged it in, Ubuntu picked it up, and I proceeded to install the driver. Then I went to print the document from Presentation, and it all went haywire from there. Absolutly nothing happend. No spooling, no printing.

I've heard, here and other places that Lexmark printers are win-printers. So that means they need a speical driver. And where do I get one of those! Also, if you can't get one of those, what do I do?

---

### Post by manicka on 2005-08-14
The driver for the x1170 in cups doesn't work. You need to use the z600 drivers available from lexmark, but they only come in rpm format. I have aliened these into debs if you want to use them (usual caveats apply). 

In a terminal run

wget [http://members.iinet.net.au/~gracey88/z600cups_1.0-2_i386.deb](http://members.iinet.net.au/~gracey88/z600cups_1.0-2_i386.deb)
wget [http://members.iinet.net.au/~gracey88/z600llpddk_2.0-2_i386.deb](http://members.iinet.net.au/~gracey88/z600llpddk_2.0-2_i386.deb)

then install them both

sudo dpkg -i z600*.deb

Restart the Cups daemon
sudo /etc/rc2.d/S19cupsys restart


The z600 driver should now be available when you add and configure your x1170 printer.

Using these packages worked just fine for me on hoary. I'm not sure how they'll go 
in warty. You can always remove them if they don't work.

HTH

---

### Post by Flashes of Sky on 2005-08-15
Thank you, I haven't tried them yet, but I will say that you are deeply appreciated for this.

---

### Post by shizow on 2005-09-08
i have a lexmark x 1170
i downloaded the drivers
but how do i enable the printer, when i add the printer over kde control center it doesnot work

---

### Post by manicka on 2005-09-08
[QUOTE=shizow]i have a lexmark x 1170
i downloaded the drivers
but how do i enable the printer, when i add the printer over kde control center it doesnot work[/QUOTE]
Are you using the z600 driver and not the 1170 one when adding the printer?

did you restart the Cups Daemon   sudo /etc/rc2.d/S19cupsys restart

---

### Post by mjpieters on 2005-09-25
[QUOTE=shizow]i have a lexmark x 1170
i downloaded the drivers
but how do i enable the printer, when i add the printer over kde control center it doesnot work[/QUOTE]
 Do you get a '**Cannot Process Raster**' messages? It appears that the rastertoz600 filter (supplied by Lexmark) doesn't work in certain environments. I am still not sure exactly what causes this program to fail like this, but I have seen messages listing this failure as early as April 2004 (the drivers where released August 2003).

---

### Post by mjpieters on 2005-09-25
I solved the problem. If you get a **'Cannot Process Raster**' errors, the Z600 raster filter cannot read the required datafiles. When converting the RPMs and installing the resulting tarball or deb package, certain directories end up being readable only to root.

To check if this is the problem, try and look at the /usr/local/z600llpddk/utility/ directory (with ls or with your favourite file manager). If you get a permission denied error, chances are the conversion filter cannot read it either.

The following two commands will fix this for you. Run these as root (sudo or log in as root) to fix this, and another directory likely to have the wrong permissions:

 ```
chmod -R +rX /usr/local/z600llpddk/
chmod -R +rX /usr/include/lexmark/
``` 

These changes made the printer work for me.

---

