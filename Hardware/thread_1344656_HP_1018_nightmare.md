---
title: "HP 1018 nightmare"
date: 2009-12-03
forum: Hardware
---

### Post by VinisLentoje on 2009-12-03
Hello,

Sorry if this have already been posted, but long searches on several occasions could not give me a solution to this problem.

I have HP 1018 printer. Ever since I moved to Ubuntu ~2.5 years ago, it was very difficult to actually make it print. The situation right now:
Using HPLIP 3.9.8
When I turn on the printer while it's hooked up to the computer or turn on the printer and then hook it up, the printer's orange alert light turns on and I get either "Device communication error (5012)" or "Unknown error (1018)". if I then unplug it and plug it back again without turning it off, or take the cartridge out and put it in back again, the green "ok" light turns on on the printer, but the computer cannot "see" the printer, as it would be unplugged and I get those errors again.
Sometimes, if I am lucky (which happens pretty rarely) after ~20 mins of different turning on/of, plugging/unplugging, etc. combinations it starts to work. And it's never the same combination that makes it work. And if I am unlucky, I do not succeed to print anything by the time my patience runs out.
Also, HPLIP could only detect it while adding this printer when I unplugged my usb keyboard and mouse.
I tried installing new firmware using HPLIP several times, but it couldn't communicate with the printer.

Please, someone, help me figure this. This issue really gets on my nerves.

And, if You need more info, just write.

thank You for Your time.

---

### Post by aj3 on 2009-12-04
I have exactly the same issue as you. Please fix this soon.

---

### Post by ajgreeny on 2009-12-04
If you look on the hplip site you will see a comment about a downloadable driver being **required**, I quote:-

8 ("**Required**") A downloadable driver plug-in is required for printing support. ("Optional") A downloadable driver plug-in is optional for printing support and may increase the speed, quality, or other aspect of printed output. ("No" or "None") A driver plug-in is not required nor available. Driver plug-ins are released under a proprietary (non-open) license and are not part of the HPLIP tarball release.

You can get it with instructions on installing from [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)

---

### Post by TKoorn on 2009-12-20
I have a HP 1018 and it used to work, sort of, under 9.04. Since I upgraded to Karmic (clean install) I can't get it to do anything.
I have tried everything 3 times.
The Ubuntu version of hplip, the hp version of hplip, and the foo2zjs.
Nothing does anything.
I have tried it both on my desktop and my laptop. Nothing happens.

I managed to get it detected at one point but after that I only get "communication errors" in cups.

---

