---
title: "Use printer from Windows via Ubuntu"
date: 2010-04-04
forum: Hardware
---

### Post by koma77 on 2010-04-04
I have a fried who recently installed Windows 7 (poor sod).
In Windows 7 there are no more drivers for his trusty HP LaserJet 1000 printer. (Shame on you HP!)

We installed Ubuntu on his old computer and printing works fine from that.

Is there any way to print from a Windows computer via an Ubuntu one without requiring the correct drivers on the Windows machine?

---

### Post by koma77 on 2010-04-07
Would it be possible to use a PDF-printer-driver (or PS) on the Windows machine and then transfer the file to the Ubuntu-machine which then automatically prints it?

Not a very beautiful solution, but at least it does not require the darn Windows machine to have a HP driver...

---

### Post by lemuriaX on 2010-04-07
Check out Samba.

---

### Post by koma77 on 2010-04-07
Yes, well, doesn't Samba require the windows machine to have the HP printer driver? 

The one that does not exist?

---

### Post by shazbut on 2010-04-07
Yes, it can be done via CUPS/IPP and using the generic/MS Publisher Imagesetter driver on the windows PC.  I can't find the exact guide I used but it goes something like this (note I've only tried this for windows XP):

On the Ubuntu print server
1. Go to system -> administration -> printing , and under server/settings make sure 'publish shared printers' is set.

2. Browse to [http://[ip_address_or_hostname]:631/printers/](http://[ip_address_or_hostname]:631/printers/)
Click the printer you want and note the full adress, eg: [http://[ip_address_or_hostname]:631/printers/hp-laserjet-1000](http://[ip_address_or_hostname]:631/printers/hp-laserjet-1000)

On the windows PC (these steps not tested on W7)
1. Add new printer via the wizard, and manually specify the full printer URL (eg: [http://[ip_address_or_hostname]:631/printers/hp-laserjet-1000](http://[ip_address_or_hostname]:631/printers/hp-laserjet-1000) )

2. When asked for a driver choose generic / MS Publisher Imagesetter.

Printer administration such as deleting/pausing/restarting jobs/printers can be done through the URL (I sometimes get old stuck jobs holding up the queue for some reason).  Hope this helps.

---

### Post by koma77 on 2010-04-07
That is interesting! I will try that next time I visit my friend!

---

