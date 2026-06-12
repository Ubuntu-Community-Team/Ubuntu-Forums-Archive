---
title: "Epson Stylus Photo R260 printer"
date: 2007-04-15
forum: Hardware &amp; Laptops
---

### Post by argentum2f on 2007-04-15
I have an Epson printer that I have to use, the Stylus Photo R260. When I tried installing a new printer, there was no drivers for it, so I tried the drivers for the R200, R220, and R300, but they were no good. The only other printers that use the same kind of ink cartridges are the R380, and RX580 but there were no drivers for them either.

Is there anything I can try to install/update to get support for this, or anything else I can do?

---

### Post by ramjet_1953 on 2007-04-16
If you follow this link, you will see that the prognosis is not good:

[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_R260](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_R260)

Even TurboPrint don't list it. [http://www.turboprint.de/english.htm](http://www.turboprint.de/english.htm)

However, it may be worth dropping them an email, to see if one of the drivers in TurboPrint will work.

Best of luck,
Roger :cool:

---

### Post by jester805 on 2007-04-30
> **argentum2f said:**
> I have an Epson printer that I have to use, the Stylus Photo R260. When I tried installing a new printer, there was no drivers for it, so I tried the drivers for the R200, R220, and R300, but they were no good. The only other printers that use the same kind of ink cartridges are the R380, and RX580 but there were no drivers for them either.

Is there anything I can try to install/update to get support for this, or anything else I can do?

Can I ask where you got the drivers for the R200??  I have that printer, but cannot find the drivers.

Thanks

---

### Post by mabhatter on 2007-05-13
It appears there is a company that makes proprietary[?] drivers for Epson printers.  They are, of course, unsupported, but they might work for you.

link to post on Epson Avasys Corp page.
[http://www.avasys.jp/english/linux_e/bbs_ink.html]("http://www.avasys.jp/english/linux_e/bbs_ink.html")

Find the drivers for Epson RX580

under "All-in-One"
under "Image Scan! for Linux & Photo Image Print System Lite"
pick the "Stylus Photo RX560/RX580/RX590"

There's no option for Ubuntu, so I choose Debian as my distro... got an RPM anyway!!

Used "sudo alien -d -c pipslite-cups-1.0.0-1.i386.rpm" to convert... note without the -c it gave an error for scripts not being converted.

> Here's the installation post:

Convert the RPM to DEB with alien
Install the DEB

open /etc/ekpdrc
change PrinterDevicePath = /dev/usb/lp0 to /dev/usblp0
run /usr/local/EPAva/LITE/pipslite-install
this will create a PPD file in /usr/share/cups/model
Open gnome-cups-manager and add Photo Image Print System (EPSON Inkjet)
as the new printer, not the USB printer it also lists.
Select Epson and scroll down until you see your printer (which should be
in the list now that the PPD is in the cups directory.)
If you don't see you printer select Install Driver and navigate to
/usr/share/cups/model and select the PPD file that we created earlier.
hit Apply and you're set. Right-click the new printer and select
Make Default. Go to properties and tinker if you want.
You should now be able to print using most apps. I have best luck with
mozilla software (firefox, thunderbird) and GNOME Office (Abiword, GNUmeric.)
Not such good luck with OO.o or F-SPOT. Picasa works good too.
JPGs print nice..PNGs don't. That sucks, oh well. It's my fault for buying not-so-well
supported hardware. I'll be sure to get an HP next time.

I had to hunt down a few changes.  

First to make the compiler for the .PPD file work I had to remove any other printers other than the Epson from the computer.  I also removed all my other printer drivers as well (I had an HP inkjet working and set up... conflict?)  When I restarted the computer I had to make sure the Epson Printer was turned on so it was detected at startup.   I'm not sure all those steps are NECESSARY (perhaps there's a command line way to fix those issues) but it was the easiest.  

The installer created the .PPD file eksprx580.ppd in /usr/share/cups/model directory.  Under Ubuntu this is completely empty with only a link to custom drivers.

I used nautilus under sudo to copy the exsprx580.ppd file to /usr/share/ppd/custom.  Now the driver appears correctly as "Epson Stylus Photo RX580" as a driver choice under CUPS setup.  I haven't tried out much yet, but the test page prints nicely.

Now I have to get the scanner working!!!! There's a separate download available on that 
site for scanners as well.

---

### Post by mabhatter on 2007-05-13
installing the scanner:

download package from Avasys site

use "sudo alien -d -c iscan-2.6.0-0.c2.i386.rpm"

go to the file in Nautilus and install the .deb package (I like shiny buttons, this isn't the best answer, but it works)

All I had to do was power cycle the printer for usb hotplug to pick it up with the new drivers. (YMMV)

It seemed to show up right away under the default Ubuntu XSane.

---

### Post by bertock85 on 2007-05-16
yeaa!!!!! :guitar: 

Thank you very very much!!

This method work correctly also with my Epson Stylus Photo R265!

---

### Post by Fos23 on 2007-09-14
Ummm, I'm a noob at Linux and I'm trying this method out with my Stylus Photo RX580.
i got as far as making the DEB

 so where exactly do i install the DEB to?

---

### Post by ernz on 2007-09-23
> **mabhatter said:**
> ...All I had to do was power cycle the printer for usb hotplug to pick it up with the new drivers. (YMMV)... 

This sort of comment doesn't help noobs at all. Can anyone expand on this please?

---

### Post by justinmiller87 on 2007-09-30
The site in this list has been updated by this point to have a driver for the R26x series. It's still an RPM though. Do I need to use the CUPS or LPR? Or will it just work under Feisty or Gutsy?

---

