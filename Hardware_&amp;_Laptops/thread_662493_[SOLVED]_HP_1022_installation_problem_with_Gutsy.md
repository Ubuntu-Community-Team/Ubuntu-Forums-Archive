---
title: "[SOLVED] HP 1022 installation problem with Gutsy"
date: 2008-01-09
forum: Hardware &amp; Laptops
---

### Post by mamboze on 2008-01-09
Hi, 

I'm not sure whether I should start a new thread on this subject, but I've been trying to install my new HP 1022 on Gutsy. for the past few days and I'm out of ideas. I'm a Ubuntu newbie, a refugee from Windows! 

I read the threads here and elsewhere on HP laserjet 1022 installation problems, so I have some idea of what it's about. My problem is that Ubuntu does not see (recognize) the printer. I've tried the printer configuration - localhost - dialog does not show the printer, and neither does it come up after new printers search. I've tried a cold boot of the printer, no change. Synaptic shows foo2zjs is installed.

I read somewhere that this could be a USB configuration issue. I haven't researched that tho. Today, some (maybe all) of the cups (or name like that) printing system was updated.   Is it necessary to install the HP printer support software HPLIP?? Or where should I go from here.  .

Any help would be much appreciated.

cheers

---

### Post by mamboze on 2008-01-09
I'm still stuck at the point of Gutsy not recognizing the 1022. I can't see how to get around this one.The printer is not detected. How does Gutsy detect new printers or what do I have to do (something obviously) to ensure the printer is detected? 

Maybe a clean install, I don't know if anything is broken. 

any help etc

thanx

---

### Post by knudsen83 on 2008-01-09
try this

[https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp)

---

### Post by schmandr on 2008-01-11
Your USB port might have a problem with USB 2.0 (as mine does). So before plugging the printer into your PC, enter ```
sudo rmmod ehci_hcd
``` at the terminal. This somehow sets the USB ports temporarily to USB 1. Now enter ```
lsusb
``` this should show "Hewlett Packard" on one of several lines now. Printer detection should now work.

Andreas

---

### Post by mamboze on 2008-01-12
Thanx knudsen83 and Andreas,

I've just come back to the forum after working out how to get the 1022 working. 

I used the foo2zjs driver     and followed the INSTALL instructions listed there. [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) 
  
Next step was to go to the CUPS help (for me [http://localhost:631/](http://localhost:631/) - I didn't even know this was on my machine). Anyhow, after following the Add Printer instructions, the printer was installed.

It works perfectly and at 1200x600dpi too. 

Interestingly, Andreas, I'm running a dual boot Ubuntu/win xp setup and I had some hassles installing the win driver but after I had disabled the USB controller (excepting the one used by the mouse), the installation went ahead OK. I picked up this point in a review of the 1022 on amazon. 

I'm not sure whether that was a critical step because the HP CD that came with the printer would only list the instructions in Thai (I live in Thailand) so I installed thru the win add new hardware wizard. 

At any rate, with 2 successes in the one evening, I was pretty happy.

thanx again .

---

