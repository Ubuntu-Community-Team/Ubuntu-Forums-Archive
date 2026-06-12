---
title: "Everything can see my printer, except Libre Office"
date: 2017-09-28
forum: Hardware
---

### Post by freesitebuilder on 2017-09-28
I'm running 16.04 LTS, and have a Canon MP270 printer/scanner. After a Libre Office update, it was printing everything with a two-inch margin - everything else was printing OK. To double-check I installed OO on my second machine (same configuration) and that printed OK.

Having seen people saying OO wasn't really supported for Ubuntu, I thought I'd do a clean install of Libre first - now it can't see the printer at all, just "generic printer". CUPS can see it OK, and Evince can see it and print, so i know it's there!

So is there something simple in Libre that I'm missing? Or is it safe to install OO instead?

TIA

---

### Post by ajgreeny on 2017-09-28
I once had a similar problem, years ago now, with a Brother printer; it was solved by making sure the default page/paper setup was the same in both LO and the printer which somehow had changed in one or the other; I can't remember which it was..

---

### Post by freesitebuilder on 2017-09-29
My CUPS settings for the printer are:

Description:	Canon MP270 series
Location:	dianne-Studio-1749
Driver:	Canon MP270 series - CUPS+Gutenprint v5.2.11 (color)
Connection:	usb://Canon/MP270%20series?serial=2429D8&interface=1
Defaults:	job-sheets=none, none media=iso_a4_210x297mm sides=one-sided

Which seem OK. LO has default page settings A4 portrait.

---

### Post by freesitebuilder on 2017-10-19
Finally found time to do an install of OO on one machine, and a clean install of LO on the other. 
OO - no problems.
LO - now it can only see a generic printer, so won't print at all, even though CUPS can see it. :( 
So for now I'm using OO on my spare machine, and moving it when I need to print from it. Looks like I'll have to install OO on my main machine if I want to print from it (which I do), despite the terrible warnings about not using OO on Ubuntu!

---

### Post by howefield on 2017-10-19
> **freesitebuilder said:**
> I'm running 16.04 LTS, and have a Canon MP270 printer/scanner. After a Libre Office update, it was printing everything with a two-inch margin - everything else was printing OK. To double-check I installed OO on my second machine (same configuration) and that printed OK.

Having seen people saying OO wasn't really supported for Ubuntu, I thought I'd do a clean install of Libre first - now it can't see the printer at all, just "generic printer". CUPS can see it OK, and Evince can see it and print, so i know it's there!

So is there something simple in Libre that I'm missing? Or is it safe to install OO instead?

TIA

How did you install LibreOffice, there was an issue with the LibreOffice snap package not seeing printers a few months ago.

Go to the LibreOffice "About" menu, what is the build ID ?

---

### Post by freesitebuilder on 2017-10-19
That might be it - libreoffice-5.3.4.2-snap1

---

### Post by howefield on 2017-10-19
> **freesitebuilder said:**
> That might be it - libreoffice-5.3.4.2-snap1

OK, open a terminal and use the following command..

```
sudo snap connect libreoffice:cups-control :cups-control
```

you may not need ```
:cups-control
``` at the end.

---

### Post by freesitebuilder on 2017-10-19
That's solved both problems - my printer is there, and it's printing full size pages. Thanks!

---

### Post by howefield on 2017-10-19
> **freesitebuilder said:**
> That's solved both problems - my printer is there, and it's printing full size pages. Thanks!

Cool, you're very welcome.

---

