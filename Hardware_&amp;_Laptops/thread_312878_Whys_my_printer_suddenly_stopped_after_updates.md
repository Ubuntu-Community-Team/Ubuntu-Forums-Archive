---
title: "Whys my printer suddenly stopped after updates"
date: 2006-12-05
forum: Hardware &amp; Laptops
---

### Post by dgrafix on 2006-12-05
My printer is saying not connected in properties. Working fine for months, I changed nothing, all i did was install the latest updates.

Im dapper, using cannon mp360 turboprint driver.

Tried same lead into my win laptop, worked no problems. So not power or lead problem, all other usb devices ok.

---

### Post by jml on 2006-12-05
One of the updates installed may have been a new printer driver, or configuration file.  Try adding a new printer.  If your printer is recognized, then go through the install process and see it that helps.

Joe

---

### Post by dgrafix on 2006-12-05
Unfortunately, altready tried adding a new one. Same prob.:-k

---

### Post by budgie9 on 2006-12-05
Try loading another Canon printer driver it is a quick easy test to try. Also have a look at the cups driver at least you will rule out problems related to the printer itself try
[http://localhost:631/admin](http://localhost:631/admin)

From an Englishman living in Canada.

---

### Post by dgrafix on 2006-12-05
im using local printer, i thought cups was for a network prn?

anyway checked in cups and it is here but theres no location, not sure if thats an issue:

Description: Canon_MP360
Location:
Make and Model: Canon_MP360 TurboPrint
Printer State: processing, accepting jobs, published.
Device URI: usb://Canon/MP360%20Series

---

### Post by budgie9 on 2006-12-05
I believe it should be showing in Cups, My Canon i860 is on a parallel port, but I think yours should be showing in the cups as well.
Try to determine if the printer is working first 
If you are using USB try unplugging the unit and see if the icon goes away, whilst the printer is powered on.  That being the icon in the printer settings, that would normally indicate the cable is working and the computer is seeing the printer itself.
 
You should also be able to do a test page print directly at the printer to test that the actual printer is working. A combination of holding a button down and powering up the printer normally gives a test page.
If you are working at this stage then you should be looking at the drivers installed.
Have you looked at the Canon Japan site to see if there is a driver for your printer? As I have stated before some of the other drivers work with other printers, I think Turboprint only redirects the printer to these drivers. I certainly found this with my printer. 
I hope this helps you.
This should take you to the PDF or HTML page where all are listed

[http://72.14.253.104/search?q=cache:7HzkwcopYrQJ:www.freestandards.org/images/9/9b/2006-10-23-Linux_Printer_Drivers_from_Canon_061022-1.pdf+Canon+Japan+linux&hl=en&gl=us&ct=clnk&cd=1&client=opera](http://72.14.253.104/search?q=cache:7HzkwcopYrQJ:www.freestandards.org/images/9/9b/2006-10-23-Linux_Printer_Drivers_from_Canon_061022-1.pdf+Canon+Japan+linux&hl=en&gl=us&ct=clnk&cd=1&client=opera)

---

### Post by dgrafix on 2006-12-06
It is usb, is working fine on windows pc (and fine on linux too until last update), icon doesnt dissapear when unplugged etc, just allways says 'ready' but when i try and print to it, the dialouge line in properties says 'printing.. 6%' for ages then refreshes with 'printer not connected' athough sometimes this says error opening device.

---

### Post by budgie9 on 2006-12-06
Seems to me you have ruled out everything else bar the driver itself or the spooling software.
I would suggest you un-install/complete removal of the Turboprint drivers using the Synaptic Manager, then try to re-install them again. Perhaps the update has corrupted one of the Turboprint drivers. Or Turboprint is not compatable with one or another of the  version of latest drivers you have installed. A roll back may also resolve that issue.
I did have this happen myself, in Suse 9.3. That was when I gave up with Turboprint, I then found the correct drivers for my Canon.
Best of luck.

---

### Post by dgrafix on 2006-12-06
how do u remove it? i didnt install it with synaptic and apt-get doesnt work either

also  when i choose local printer the choices of port ar HP_nodevice_found or cannon(parelell) or epson(paralell) No mention of USB

---

### Post by budgie9 on 2006-12-06
I am also a noobie, trying to learn and help. Still new to Ubuntu and Linux but am learning fast.

What ever program you installed should be listed in Synaptic package manager, so look there first. Turboprint was I think listed in my Package manager but I can't swear to that, as it was also in the Woarty version, which I never used much at the time.
 
If you go to System - Printers, and look in there you should have a printer listed. RIGHT click on it and use that to remove.
Even a USB printer should show up in there as it is still a printer. 
I use my Canon on the parallel port, as I need it to connect to  five computers. 
Does your printer have a parallel port by any chance?
 


 This bit is taken from the Ubuntu help Printing list 
MP_360
Printer works using the MultiPASS C5500 bjc600 driver, not tested scanning as yet So you should be able to get it to work with the above. Go here to view details
[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters)

---

