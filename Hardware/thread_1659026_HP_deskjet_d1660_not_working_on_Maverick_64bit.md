---
title: "HP deskjet d1660 not working on Maverick 64bit"
date: 2011-01-03
forum: Hardware
---

### Post by boddhisatva on 2011-01-03
Hi
I've just bought hp deskjet D1660, believing it would work under Ubuntu - having seen some posts with solutions. Unfortunately it doesn't. The driver gets installed automatically and I've installed hplip-gui via Synaptic, but when I run it, I'm only able to run the calibration - that's the only time the printer actually prints something out. The cleaning seems to work too, but nothing is printed. And the test print doesn't work at all. The notification says the print job has been sent, then it says it has been completed, but there's no response from the printer. 
I've tried to install the driver from the HP website link, with the number 3.10.9 (which seems to be a newer version than the 3.10.6 installed from repositories). But when I run it, I get this message:

warning: Missing REQUIRED dependency: gcc (gcc = GNU Project C and C++ Compiler)

But the gcc package IS installed, so I don't know what to do.
I didn't find this particular problem solved on the forums.
Any ideas appreciated.

---

### Post by boddhisatva on 2011-01-03
I seemed to have solved the problem. I first tried to force an upgrade to hplips 3.10.9 by downloading packages for Natty - and it nearly worked, I could print stuff, but there were some quality issues and I couldn't install hplip-gui to calibrate etc. Also, I screwed up some dependencies by having to force-install some packages and I got error messages in Synaptic and Software Center. So instead of upgrading, I decided to downgrade, especially as I've read in people's comments that they managed to make the printer work under Karmic and Lucid. So I installed the 3.10.2 version of the essential packages, and it's now all working - the print quality is good, and I can use hplip-gui to do maintenance and tweaking. 
Thanks! Not for an actual response to this thread, but for all the responses in other threads that have led me to the solution. And for the good vibrations of the forums :)

---

