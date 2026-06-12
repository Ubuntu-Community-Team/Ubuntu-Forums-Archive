---
title: "Newbie here - Please help installing printer"
date: 2007-08-23
forum: Hardware &amp; Laptops
---

### Post by Roque on 2007-08-23
Hi.

I am using Kubuntu.
I tried to install my Epson c64 printer several times in the last year with no success. I've installed Gimp-Print and followed the instructions here:
[http://www.linux-foundation.org/en/OpenPrinting/Database/CUPSDocumentation](http://www.linux-foundation.org/en/OpenPrinting/Database/CUPSDocumentation)

But [http://localhost:631/](http://localhost:631/) doesn't work (returns a timeout on server). I tried the kde print manager (kmenu->settings->peripherals->printers) but when I try to Add Printer/Class it takes **30 minutes** to start the wizard and it doesn't show any printer list.

Other people in the forum succeded, so this should be an easy task. Could someone please help a bit? I have no idea what to do and could not find any useful explanation of the steps to follow. 

Many thanks in advance.

---

### Post by Roque on 2007-08-23
Well, after waiting for about **45 minutes**, the KDE printmanager wizard indeed showed a list of printers, but there's **no** Epson cXX printer listed. Some people in other posts wrote about c64, c68, c63 drivers being shown, but this not the case (Kubuntu Feisty)

Could someone please tell me where I can find these PPD drivers? They don't seem to be in the repositories; apparently Feisty brought too few of these?

Thanks

---

### Post by Roque on 2007-08-23
I just found out that kprinter's available drivers listing is broken in Feisty. See here: 
[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/99372](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/99372)

So one must set the driver within [http://localhost:631](http://localhost:631)
But, once more, I cannot access it:
[b]An error occurred while loading [http://localhost:631:](http://localhost:631:)
Timeout on server
 Connection was to localhost at port 631[/b]

(I cannot even ping it)

Any ideas will be appreciated.

---

