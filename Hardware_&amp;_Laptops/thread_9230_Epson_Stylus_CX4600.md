---
title: "Epson Stylus CX4600"
date: 2004-12-26
forum: Hardware &amp; Laptops
---

### Post by Useless on 2004-12-26
I have purchased an epson stylus cx4600 and i cannot get it working.  I have tried seting it up but to no avail.  The printer is being detected corectly, but i cant seem to get the proper drivers for it.  I am using the stylus drivers, but they dont seem to work. An ideas?

---

### Post by orbitalbears on 2004-12-30
I'm having the same problem with an Epson CX6400.  The printer is displayed, but I have no idea what driver to use and a dozen drivers I've installed don't work.  I thought Ubuntu was just supposed to work?

---

### Post by cascademiles on 2005-01-07
Setting it up as a Stylus Photo 1280 works in Xandros.  I haven't experimented much with the driver, though.

Miles

---

### Post by nlp on 2005-01-09
For most Epson printers, you will need to add the 'gimpprint' drivers from the 'universe' repository:

1) Make sure that 'universe' is enabled in Synaptic (look in Settings - Repositories, then enable any unchecked repos.  Apply, then hit the 'Reload' button to make them available.

2) Search for 'cupsys', then load the package called 'cupsys-driver-gimpprint' and its dependencies.

3) Optional: if you live in the US/Canada, you should probably change the default paper size from 'a4' to 'letter' before configuring your print driver.  Just open a root terminal, then type 'gedit /etc/papersize'.  Change the line that says 'a4' to 'letter' and save.

4) Load Computer - System Configuration - Printing, then remove any non-working, generic Epson drivers you may have added.

5) Double-click on 'Add Printer', and find your specific Epson model in the list, then configure the driver.  If you did step 3, your printer driver should default to the correct paper type.

I hope this helps!

---

### Post by coyote721 on 2005-02-20
Hello, 

  You wrote " I'm having the same problem with an Epson CX6400. The printer is displayed, but I have no idea what driver to use and a dozen drivers I've installed don't work. I thought Ubuntu was just supposed to work?
12-26-2004 01:03 AM "
   The printer uses the EPSON C64 driver. I am not sure as to how to get the scanner working with Ubuntu. It can scan manually so I am not that concerned.

---

### Post by BlackHawk on 2005-03-28
[QUOTE=nlp]For most Epson printers, you will need to add the 'gimpprint' drivers from the 'universe' repository:

1) Make sure that 'universe' is enabled in Synaptic (look in Settings - Repositories, then enable any unchecked repos.  Apply, then hit the 'Reload' button to make them available.

2) Search for 'cupsys', then load the package called 'cupsys-driver-gimpprint' and its dependencies.

3) Optional: if you live in the US/Canada, you should probably change the default paper size from 'a4' to 'letter' before configuring your print driver.  Just open a root terminal, then type 'gedit /etc/papersize'.  Change the line that says 'a4' to 'letter' and save.

4) Load Computer - System Configuration - Printing, then remove any non-working, generic Epson drivers you may have added.

5) Double-click on 'Add Printer', and find your specific Epson model in the list, then configure the driver.  If you did step 3, your printer driver should default to the correct paper type.

I hope this helps![/QUOTE]


Did just fine up until adding the printer.  When I get to the part about configuring the driver I get lost.  When I click on "install driver" it gives me a folder navigation window.  I think it wants me to find the driver for it?

Being new to linux, I'm lost at this point.

Any help?

---

### Post by David Haas on 2005-03-28
I see that the Epson stylus CX6400 is among the printers listed in Ubuntu, so all the drivers and PPD files are probably within the distribution, but not yet made available by yourself yet. 

(Turn on your printer before the computer for ease of recognition.)

Then work in "Synaptic Package Manager" to make sure that CUPS (common unix printing system) is installed on your computer. To get to Synaptic, click "Computer" at the top menu bar, then "System configuration," and then "Synaptic Package Manager" type in your password to be in root). In Synaptic, first click "settings" and then "repositories." Enable all the repositories. This will allow you to download via Synaptic the necessary files, if they are not yet installed.

Then go to the cups  packages in Synaptic--It's quickest to set the left column in Synaptic as "alphabetic". Here you'll see "cupsys, cupsys-bsd, cupsys-client, cupsys-driver-gimprint, and cupsys-driver-gimprint-data". If not marked as installed, install all but cupsys-bsd (I'm quite sure that this latter isn't needed--bsd is an old "flavor" of unix) 

Next, make sure that all the "foomatic" packages are installed. This is a big database of filters for almost every printer. 

Now click "computer > system configuration > printing. If you already have a printer icon there listed as Epson stylus CX6400, right click on it and select properties. If not work to add a printer to "Newprinter." In the properties dialog box, select the Epson stylus CX-6400 (it'd listed) and then click "install driver". Here is where you select the PPD file. The ppd file is present in my Warty, but it's listed as escp2-cx6400.ppd.gz ("escp" is for epson stylus color printer). It is in the directory "/usr/share/cups/model/gimp-print/4.2". So it should be selectable within the "printing" GUI. To locate it, you'll need to work through the directory system. Click on "Filesystem". Then select the following directories in order: usr>share>cups>model>gimp-print>4.2. In this last one scroll down to escp2-cx6400.ppd.gz and select this for your PPD file. 

Before I did all this, my Epson stylus C82 was dead (mute). Let me know if you follow this and if it helps.

---

