---
title: "Printer Drivers..."
date: 2010-03-08
forum: Hardware
---

### Post by Midnight Star on 2010-03-08
Is there a program for linux like NDISWRAPPER, that will let us use drivers written for Windows? I'm in the process of converting all my Windows boxes over to Ubuntu, and would like to use my existing printer hardware (Lexmark X75) until I can upgrade to a linux compatible laser printer. The X74 driver doesn't seem to work, and dropping an e-mail to the developer hasn't netted anything yet.

I'm also wondering if it would be possible to run the printer driver through Wine, maybe?

---

### Post by myth1914 on 2010-03-08
Have you looked on [http://www.openprinting.org?](http://www.openprinting.org?)

---

### Post by Midnight Star on 2010-03-08
Yeah, that's what I was going to use as a resource when buying a new one. From what I was able to find, there isn't a compatible Linux driver for that model. The lxx74 driver didn't work for some reason.

I was hoping, or kinda "laying a suggestion" out that maybe someone might have already made or was working on something similar to ndiswrapper, except for printer drivers. If they hadn't and was possible, it would really boost the use of current printing hardware for us Linux users.

---

### Post by efflandt on 2010-03-08
There have been numerous threads about getting Lexmark inkjet printers working.  Some are totally dumb Windows raster printers that need an additional utility to rasterize all the data/fonts.

But Lexmark laser printers are fairly easy because they do HP PCL and postscript.  For example I was able to use my C543dn color laser by simply using an older C534dn driver from default installation.  When I got proper ppd files from Lexmark, the included script did not seem to install them properly in Ubuntu (maybe I didn't know to use sudo yet).  But all I had to do to configure it once printer setup found the network printer, was point cups to the ppd file in the directory I had unzipped.

When our HP LaserJet P3005x started crumpling paper at work and I temporarily needed something until warranty replacement, I picked up a Lexmark X204n all-in-one mono laser (on sale for $150), and it worked with the existing HP drivers (locally and factory computers 1700 miles away on VPN) doing nothing more than setting it to the IP that the HP P3005x had been using (since it also does HP PCL and postscript).

---

### Post by Midnight Star on 2010-03-08
That's the problem. I don't think there's a ppd file for the Lexmark x75 that I could find.

---

