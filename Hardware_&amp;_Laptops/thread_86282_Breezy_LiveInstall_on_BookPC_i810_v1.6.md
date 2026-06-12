---
title: "Breezy Live/Install on BookPC i810 v1.6"
date: 2005-11-04
forum: Hardware &amp; Laptops
---

### Post by jmb365 on 2005-11-04
I have some strange problems running the Live CD 5.10 "Breezy" on an old Book PC with a PSKBVM1 Ver 1.6A motherboard.  This is one of those cheapy "Telephone Book" sized PCs that has everything on the M/B except a second IDE slot, an AGP or any PCI slots.  It is sold as an entertainment PC at the low end.  It was free, so sinking money into it questionable.  It is labeled a "BookPC BKi810".  The motherboard is by ECS -Elite Computer Systems(?).

It runs for several hours _without rebooting automatically_ when running Win98SE.  I downloaded the Davicom drivers for the built-in network card and I am able to surf the web.

But, when I try the Ubuntu Live CD 5.10, it crashes shortly after the Gnome desktop comes up.

Installing the server version on a 1.6GB Hard Disk causes it to reboot during the configuration process when trying to configure the network.  If I Crtl-C this step, it proceeds further, but reboots as soon as I type the password for the user & hit enter.  I have repeated this several times with consistency.  If I had a slightly larger HD I would have tried a "Normal" install.  The ones I have are over 150GB, too large for this one.

I have tried Knoppix Ver 4, with similar results.  Reboots shortly after I get a KDE desktop.

Bios version was Award ver 6.00PG dated 09/01/1999, which I updated to 11/01/2000.  This did not cure my problems either.  Same symptoms:  Win98SE = fine for several hours; Ubuntu/Knoppix Live CDs = automatic reboots after Gnome/KDE desktop is presented.  BTW, ClusterKnoppix LiveCDs did not work either, but I do not remember the exact location when reboots occured.

I have tested the memory for several hours using memtest86, reseated cable connections, memory chips, etc.  I do not have a replacement P/S otherwise I would try that.  The dinky PC-100 watt P/S I read is notorious for its failures and I have the yellow labeled one, which I am told worse than the green labeled one.  However I did several trials by relieving this power supply by juicing the CD-ROM separately with an old AT type P/S.  If I try to place the HD on the external P/S it does NOT boot!  Never seen such strange behaviour.  Of course these rants are possibly meant for some other forum, but I include them here for completeness, should they provide some essential clues.

Any ideas on this strange behaviour?  I kind of like the form factor of this thing and would like to use it in a vehicle after I design better cooling for it perhaps.  I placed my faith in Ubuntu, because of all the flavors of Linux I have installed in the past it is the easiest & cleanest.

Thanks
JMB

PS: Finding the LiveCD has the option of installing Firefox/OpenOffice/Gaim on Win98 PC was such a surprise & delight!  Wonderful work!  I installed all 3, but having Ubuntu running on this PC would top it all...

---

### Post by jmb365 on 2005-11-16
I solved this problem by repairing the Power Supply circuit board ver 2.0 of this Book PC (replaced some capacitors)

JMB

---

