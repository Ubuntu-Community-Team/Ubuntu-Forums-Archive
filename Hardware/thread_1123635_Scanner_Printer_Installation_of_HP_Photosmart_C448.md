---
title: "Scanner Printer Installation of HP Photosmart C4480 on Hardy Heron 8.04"
date: 2009-04-12
forum: Hardware
---

### Post by Trent T on 2009-04-12
My HP Photosmart C4480 printer installed OK with the utilities that came with Ubuntu Hardy Heron 8.04.  However, I could not get the scanner function to work -- until today.

0) Close all other applications and save all data as needed.
   This is step zero, because you already know to do this before 
   ANY installation, right?  ;)

1) Download and install HPLIP.

Here's the link;  [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

HPLIP stands for "HP Linux Imaging and Printing."  It is a utility that installs printer and scanner functions to a wide variety of Linux systems for a wide variety of HP Printers.

Procedure:
a) Click on the link above, and download HPLIP.
b) make a clean directory, and move HPLIP into it.
   The downloaded file will be named something like hplip.3.9.2.run.
   Synaptic was unable to install it--at least, not for me!  
   One can install it manually however.
c) OPTIONAL --Disconnect the USB cable to your printer (ie., unplug the printer). I left mine plugged in, and it may have required me to do an 
   extra step.  
d) open a terminal window.
e) at the bash prompt, type
   sh hplip.3.9.2.run   
   to start the installation program. 
   Substitute the name of the file above, if hplip.3.9.2 is not the 
   version you downloaded.
f) Select 'a' for Automatic installation.
   There are other options including (I think) 'c' for custom.
   I chose 'a'.

   HPLIP asks you several questions about your computer, printer, and connection. It then installs utilities needed to run the printer and scanner.
   At the end of this process, you need to restart Ubuntu

2) Restart Ubuntu

3) Run HP Setup (Possibly Optional Step)
   
If you left your HP Photosmart C4480 plugged in, as I did, you will have to run hp setup after rebooting.  Leave the printer plugged in, then 

a) Open a terminal window
b) At the bash prompt, type
   sudo hp-setup

   hp-setup will detect your printer, and finish installation.

4) Test Scanner ability.

a) By menu, click
   Applications
        Graphics
              Xsane Image Scanner

-OR-
b) From the bash prompt in Terminal, type
   xsane

Either way, Xsane should pop up and allow you to scan via USB.
This worked for me the first time I tried it--
Hope everyone else has the same trouble-free experience.

--Trent T

---

### Post by Trent T on 2009-04-12
PS--
An added benefit;
The new printer driver for the HP Photosmart C4480 that HPLIP added to my printer list can now be detected by my Win XP laptop thru the wireless network.  
(Previously, I could not get Win XP to detect the printer on my Ubuntu desktop).
Win XP says (on the printer list) that 'Access is denied,' however, the C4480 prints anything I send.
No more need to cable in the laptop when I want to print.  Wahoo!

---

### Post by wightghost on 2009-04-16
Thank you very, very much for this guide.  If it wasn't for this I would still be trying to get the scanner on my new HP C5380 working.  This guide worked a treat for me.

For the record, the HP C5380 works flawlessly on Hardy. 

Brad

---

### Post by Trent T on 2009-09-11
I just upgraded my OS to Ubuntu 9.04--
This Ubuntu version recognized the printer and scans with the scanner without any additional tweaking--
Good work, Ubuntu programmers!

---

