---
title: "Synchronizing Treo 680 in Ubuntu 9.10"
date: 2009-12-19
forum: Hardware
---

### Post by drums907 on 2009-12-19
I have gone through setting up my Tre680 (AT&T) through the PalmOS Devices applet.  I am able to retrieve the PDA name and ID from the device.  I set the settings to synchronise with Evolution.  However, when I press the hot sync button on the cable, the device appears to start syncing and then hangs on 'synchronising Address'.  After a time a message comes up that the connection between the computer and the device was lost.  What can I do to correct this and actually get the data from my PDA into Evolution?

I am running Ubuntu 9.10 on an AMD Athlon64 processor.  125GB drive. 3GB RAM.  Everything appears to be working well except this at the moment.

---

### Post by drums907 on 2009-12-19
I was able to finally get this to synchronise.  I disabled all conduits.  I then enabled only the Calendar conduit and performed a hot sync.  This succeeded.  I then enabled the Eaddress conduit and performed a hot sync.  This too succeeded.  It appears there must be a conduit that is not compatible with my device so I will continue to add conduits one at a time until I find the one that stops up the works.

---

