---
title: "dell 1700n printer issues..."
date: 2005-12-06
forum: General Help
---

### Post by Trab on 2005-12-06
well, my printer is being a turd...

i have a dell 1700n and i know its set to use 10.1.1.25...
before a recent reinstall of just the root files (/home was untouched) setting it up was a snap.... i just entered 10.1.1.25 as the uri and tried both of the dell drivers (i dont remember which worked...)
now, niether of them seem to even communicate to my printer...
whereas trying the reccomended HP LaserJet 4 driver (And i even tried the laserjet 6 just to test) will only print on about the top 3 inches or so of the paper... its not a printer issue, as a test page from within itself printed fine...

please help, i have numerious school reports comming up, and i need my printer!

thanks!
-Trab

---

### Post by Staceman on 2006-03-23
Did you ever get anywhere with this?

I'm having the exact same problem, with the exact same printer. Neither of the two Dell drivers provided ever worked for me, though.

I read somewhere where someone had the generic PCL6/XL driver working with it, but when I tried that, all I get on the printed pages is "IllegalAttributeDataType" along with some other stuff.

I even downloaded and installed the "official" driver from Lexmark's site, to no avail. After I finally figured out the stuff with the license agreement, running their "Lexmark Print Drivers" program does nothing, no errors or anything, no matter if I run it from the command line, menu, sudo, or anything.

---

### Post by Staceman on 2006-03-24
OK, I finally got it working, and I figured I'd share what I found here.

In the Add a Printer setup thing, you need to use the LPD protocol, NOT CUPS/IPP. Then put in the IP and queue name.

I then chose the "LaserJet 4 Series" driver under HP.

That's pretty much it, it works perfectly with this setup.

It still doesn't answer the question as to why it doesn't work with the CUPS driver, since myself and others I work with have had this printer working correctly with the same CUPS drivers in other distros (GenToo, Fedora), but at this point, why ask why, at least it's working now, and that's what counts. :)

---

### Post by dppowell on 2006-09-29
> **Staceman said:**
> 
I then chose the "LaserJet 4 Series" driver under HP.


This solution works, though for me this driver did not work.  It resulted in the test page being spread across two pages (truncated on right side) and an error light on the printer after the job was done.

The generic Postscript driver produced much better results for me.  If the Laserjet 4 driver is giving you trouble, try this.

ETA: I'm on 6.06 (Dapper), YMMV with other releases.

---

