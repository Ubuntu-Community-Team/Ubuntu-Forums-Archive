---
title: "Printing Problem"
date: 2015-06-12
forum: Hardware
---

### Post by merlinus on 2015-06-12
Had no problems with local and network printing until recent kernel and cups updates.

Here is the syntax:

Device URI: ipp://192.168.1.100:631/printers/HP-LaserJet-4-Plus

Policies: Enabled, Accepting Jobs, Shared

Access Control: Allow Printing for Everyone

I have tried all the various driver options (not Postscript, since I do not have that installed in the printer), to no avail.

---

### Post by merlinus on 2015-06-12
The printer works when configured as local with these parameters, however:

Device URI: usb://HP/LaserJet%204%20Plus

Make and Model: HP LaserJet 4 Plus - CUPS+Gutenprint v5.2.10-pre2

Same policies as above.

But it also needs to be configured as a network printer for my other computers to be able to use it.

---

### Post by merlinus on 2015-07-23
The latest kernel upgrade fixed the problem automagically.  3.13.0-58.

---

### Post by mojohn on 2015-07-24
I have the same problem as Merlinus, I think. I have had an HP Color LaserJet Pro MFP M177fw for several months and it "just worked." But, after the recent update to the Linux kernel, it stopped working. The MFP is recognized by Ubuntu (14.04), but print jobs go to the queue and stay there forever. This printer is connected by USB.

I use my computer for work and need to be able to print. Is there a way to safely roll back the kernel to the previous version? If so, how do I go about it?

Thanks!

---

### Post by merlinus on 2015-07-24
You might try reinstalling.  My problem was not with setting up the HP LaserJet as a local printer (never had difficulties with that, using a parallel to USB cable), but as a network one.

---

