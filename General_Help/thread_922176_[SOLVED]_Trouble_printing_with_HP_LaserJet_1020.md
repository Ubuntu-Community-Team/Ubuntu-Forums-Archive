---
title: "[SOLVED] Trouble printing with HP LaserJet 1020"
date: 2008-09-17
forum: General Help
---

### Post by Linux user 66 on 2008-09-17
I've got an HP LaserJet 1020 printer, which I'm trying to get to work with Ubuntu. So far no luck. When I connected the printer, it was recognized and when I try to print documents, the printer interfaces claims to have done so, but there is no physical printer activity and no papers coming out.

What can I do?

---

### Post by bmac on 2008-09-17
Try installing the HPLIP print driver...

[http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)

Hope this helps.....

---

### Post by Linux user 66 on 2008-09-17
> **bmac said:**
> Try installing the HPLIP print driver...

[http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)

Hope this helps.....

I had a look in Synaptic and saw that I already have these packages installed: *hpijs, hplip, hplip-data* and *pxljr*.

These are also available to me:
*hpijs-ppds, hplip-dbg, hplip-doc, hplip-gui* and *hpoj*.

Should I install any of those or should I download and install the HPLIP Automatic installer from the web page you suggested?

---

### Post by bmac on 2008-09-17
I suggest you download and install the HPLIP Automatic installer. You will get the most recent version. 
The installer is simple and installed quickly on my machine, just follow the installation instructions....

Hope this helps......

---

### Post by Linux user 66 on 2008-11-08
> **bmac said:**
> I suggest you download and install the HPLIP Automatic installer. You will get the most recent version. 
The installer is simple and installed quickly on my machine, just follow the installation instructions....

Hope this helps......

Everything works now in Ubuntu 8.10, but thanks anyway!

---

### Post by Jenda on 2009-08-13
I have this issue too. Is it really [solved] by reverting to an older version of Ubuntu? I would really like to find a different solution.

---

### Post by Jenda on 2009-08-13
Bah, nevermind - it all boiled down to checking "Enabled" and unchecking "Shared" (although I didn't check if the latter is necessary).

---

### Post by apester on 2009-09-28
The "shared" unchecking was necessary for me. I had both checked by default. Thanks for the info.

---

### Post by adamkane on 2009-11-24
[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

