---
title: "[SOLVED] Unable to Print Under Ibex with HP Printer."
date: 2008-11-01
forum: Hardware
---

### Post by AlphaMack on 2008-11-01
Something is messed up in Ibex because I never had trouble under Gutsy or Hardy.

HP Deskjet 5440 is connected to an AirPort Express using the default selected driver (HP Deskjet 5400 series Foomatic/hpijs).  I was able to print using HP JetDirect and socket://XXX.XX.X.X:910X.  Test pages came out correctly every time as well as other documents.

Ibex sees the printer, configures it correctly, but when I attempt to print a test page, it prints one line of gibberish, spits out the page, and attempts to print more pages with more gibberish!

I attempted to manually add the printer to no avail.  Edit:  Tried USB directly.  Nope.

The same happens with other documents.

Any ideas?

Edit2:  OK, it is completely broken under Ibex.  Tried to print a test page under the Ibex live CD with the same result.  Then tried again under the Hardy live CD and it worked correctly at that time.

Filed as a regression bug.

---

### Post by AlphaMack on 2008-11-01
Solved by downloading and installing HPLIP 2.8.9 from the HPLIP site.  Let's hope this gets fixed soon.

---

### Post by jweaver28 on 2008-11-01
I'm a newbie to Linux and can't figure out how to configure either of 2 older hp laserjet printers. I cobbled together extra parts and installed Hardy last month, hoping to be able to use an HP laserjet 1000 with it since my other computer is a Vista and that very early (but reliable) printer isn't supported. I followed the FOO2ZJS instructions and it's installed as my default printer on that machine, but nothing actually prints out. I get a message that Hardy thinks the printer's not connected, tho I reset all the connections and the power's on (the model doesn't have a separate power switch but the green light's on). I checked at our local library, and was surprized that the few (older) Linux books don't discuss printer setup, much less explain what a hotplug is, etc.

Well, I have a laserjet 1018 installed with my vista machine. When Intrepid Ibex came out, I splurged on a new hard drive and did a clean install, switching the SATA cable on my vista machine. The install seemed to work like a charm, except now I can't get the 1018 working in this newest Linux, though it works in Vista. I tried the FOO2ZJS instructions, and the 1018 shows as the default printer, but nothing actually comes out clicking to print a test page. I downloaded the HPLIP files twice. Intrepid doesn't know how to open them. Dragging and dropping doesn't work. I tried the HPLIP instructions in terminal mode, even substituting the correct version number to the suggestion on the webpage, which still didn't work. I guess being so new to Linux. the instructions might just be at a level above me. And clearly, I can't switch to Linux if I can't get a printer to work.

:confused: Jane.

---

### Post by jweaver28 on 2008-11-01
Something I did after redownloading the HPLIP files worked. I just restarted the computer and the test page printed fine. Now I'm going to take this hard drive to the Hardy Heron machine with the nearly maxed out hard drive and see if the laserjet 1000 will work. :)

---

