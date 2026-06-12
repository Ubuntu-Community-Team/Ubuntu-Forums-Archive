---
title: "Printing issue"
date: 2005-04-11
forum: Hardware &amp; Laptops
---

### Post by Brainburp on 2005-04-11
Hi

I can't seem to get Ubuntu/Gnome/Linux to send data to the printer

I have an Epson Stylus Photo 810. The printer is detected, it allows me to select the printer from the driver list and seems to install the GImp-Print driver. However, when i try and print anything, i get absolutely nothing. It doesn't even send the data to the print monitor - I have tried Autodecting, selcting the printer manually, run it on USB and Parallel port but to no avail

Any help is appreciated

Thank you!

---

### Post by David Haas on 2005-04-11
Brainburp--My experience with my Epson Stylus C82 is that when the proper PPD is not selected, the printer remains mute when you send it print jobs or even the "test page."  I have also found that when the drivers and PPD files are not set up correctly, it's best to delete the printer in the GUI and start over from 'new printer." Have you selected in Synaptic Package Manager the cupsys packages (except the one for BSD)? You'll need these. You'll also need the Foomatic packages, except the one for HP printers. Before downloading these, make sure that you have checked the repositories so that you will be able to download these packages (Settings> Repositories in Synaptic).

After your printer is selected, you must click through the file system in the printer GUI to get to the Gimp-Print PPD file for your printer. The list is /usr/share/cups/model/gimp-print/4.2. For your printer, I see only the escp2-photo.ppd.gz. Perhaps this is the one, since it's the only PPD file listed here for Epson photo printers. If not, then it can almost certainly be located elsewhare. 

I hope this helps. More help is available from myself and from others much more knowledgeable if you need it.

David Haas

---

### Post by Brainburp on 2005-04-16
Thanks for the info - 

I've checked and currently i have installed 

foomatic, 
gimp-print
cupsys

What i need to do is upgrade to the latest versions of these packages - unfortunately i only have a modem so it will take a while :) 

I'll do this and see what happens - It's real shame this hasn't been easy to get working, the rest has been fine - although i'm new to Linux i'm not new to computing and was rather hoping i could cure my addiction to Windows..

cheers

---

### Post by David Haas on 2005-04-17
Brainburp--Have you clicked through the printer set up GUI to select your PPD file? By the way, I looked at the gimp-print PPD files again and saw listed what must be your printer: escp2-810.ppd.gz. since you have foomatic, cupsys, and gimp-print installed, I doubt whether you need to upgrade these to set up your printer.
David Haas

---

