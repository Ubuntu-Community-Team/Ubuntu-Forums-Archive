---
title: "printer not detected, cannot setup (officejet 6110 in Breezy)"
date: 2006-01-25
forum: Hardware &amp; Laptops
---

### Post by rekurzion on 2006-01-25
I recently upgraded to Breezy and the only problem I have run into is getting my printer to work again.  I noticed that cups has been upgraded as well so I am not sure if this is the problem.  

As the cups web interface has been "disabled", I am using the printer setup in System -> Administration -> Printing.  

However, my USB printer is not detected and I have no port options to choose from which leaves me unable to load anything manuallly.  If I select the network printer option to use cups, I am asked for a URI which I don't know.  To get forward I just enter some letters and then proceed to find and install the drivers for printer.  I have the correct PPD files and in the right location.  But after finishing the setup, no printer icon shows up.  I have tried unplugging and plugging the printer back in, restarting the system, restart the cups service.  Nothing seems to work. 

Please, I had my printer working in Hoary 5.04 fine, but now all these problems.  I know that my printer is supported, why would it not be detected.  When i run the command to display my USB devices it shows up, as well as is my device manager.  It's almost as if cups isn't really running, its just a GUI with no heart.  

I am running a WInbook J4 laptop with 4 USB slots.  I have tried the printer in all 5 to no avail.

---

### Post by rpaller on 2006-01-25
You may need to install the latest version GutenPrint (new name for GIMP Print). I have the same problem with my Epson CX7800 MFP.

---

