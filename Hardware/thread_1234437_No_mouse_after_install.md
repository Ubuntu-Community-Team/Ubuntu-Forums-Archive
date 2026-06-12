---
title: "No mouse after install"
date: 2009-08-07
forum: Hardware
---

### Post by lordhedgehog on 2009-08-07
After power loss during an update to key packages, my entire system was plagued with seg faults.  I upgraded to Jaunty to fix them, but shortly after I smegged my video driver breaking X.  Figuring I'd make a clean start of it, I took a Jaunty install CD and started over.  

The LiveCD works fine, but once it's installed and reboots to the hard drive, the mouse doesn't work.  I'm using a Toshiba laptop with Jaunty 64 bit, and neither the touchpad nor a USB mouse work at all.  The pointer is visible, but never moves.  The log files indicates that no core pointer could be found; HAL seems to start up without error, although other than the status on boot and using ps to verify it's running I don't know how to tell if it sees the mouse.

So Intrepid worked fine, the Jaunty LiveCD works fine, and Jaunty worked when I upgraded from Intrepid, but a fresh install of Jaunty doesn't see the mouse.  Is there an easier fix than installing Intrepid and upgrading to Jaunty?  Any clue what's wrong?

---

### Post by lordhedgehog on 2009-08-08
Problem went away after connecting to the Internet and letting it download and install the latest updates.  Just a pain in the neck to do that without a mouse. :)

---

### Post by luddgopelle on 2009-08-20
> **lordhedgehog said:**
> The LiveCD works fine, but once it's installed and reboots to the hard drive, the mouse doesn't work. ... Problem went away after connecting to the Internet and letting it download and install the latest updates.

 Just want to add that I had the exact same exprience with a Thinkpad T60p, regular Jaunty .

---

