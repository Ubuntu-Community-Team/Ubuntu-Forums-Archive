---
title: "Lost PDF Printer on upgrade to 8.10"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by BarryM on 2009-06-25
I have just upgraded from 8.04 to 8.10 and have lost the PDF printer that I had (installed with 8.04 by default, I think).

How do I get it back?

---

### Post by tgalati4 on 2009-06-25
After reboot, go into a browser and report:

[http://localhost:631](http://localhost:631)

---

### Post by BarryM on 2009-06-25
I tried this, and the CUPS tells me what printers I have, but not how to get my PDF printer back! Am I being incredibly thick here? I can see that there is an option to install a new printer, but I need to know what I am looking for before I can install said printer. I presume that there is something in the synaptic package manager I should be looking for? Any ideas what?

Thanks for any help in advance!

---

### Post by tgalati4 on 2009-06-26
What version of CUPS are you running?

Try to create a new printer and mimic the following:

Description: Print to a PDF File
Location: In your Documents folder
Printer Driver: Local Raw Printer
Printer State: idle, accepting jobs, published.
Device URI: cups-pdf:/

This is what is in CUPS 1.3.2 for Gutsy.

I also have CUPS 1.3.9 on an Intrepid machine and it shows the same information.  

It looks like the dist-update borked your PDF printer.  Perhaps a bug has been filed?

---

### Post by ad_267 on 2009-06-26
I think I recall the cups-pdf package was removed from the default installation for 8.10, as many applications provide native PDF export. Try installing cups-pdf.

---

### Post by BarryM on 2009-06-26
Got it! Many thanks. I imagine I will have to do the same again when I upgrade to 9.04.

Can't think why it was removed, I mainly use it for printing from Firefox, and I am sure I am not the only one to want to do that.

---

### Post by ad_267 on 2009-06-26
If you've manually installed the package then you shouldn't need to install it again after an upgrade. :)

---

### Post by tgalati4 on 2009-06-26
Perhaps it was removed to make room for mono.

---

