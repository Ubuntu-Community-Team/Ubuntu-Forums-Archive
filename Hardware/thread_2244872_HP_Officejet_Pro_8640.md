---
title: "HP Officejet Pro 8640"
date: 2014-09-19
forum: Hardware
---

### Post by tb75252 on 2014-09-19
I am using Ubuntu 12.04.5 (64-bit).

I just purchased an HP Officejet Pro 8610 and I would like to be able to print using Ubuntu.

The printer is hooked up to a router via Ethernet cable and so is my PC.  The printer discovery utility correctly detects that I have a networked printer.  I go through the motions of setting up the printer up to the window where it informs me that is installing "openprinting-gutenprint" but then it freezes there.  (I.e. the progress bar never moves.)  Clicking the Cancel button does not help as it appears that everything is frozen.

What do I need to do to correctly set up the printer?

---

### Post by ajgreeny on 2014-09-19
You will need a very recent version, hplip-3.14.4 or later for that printer so you may need to get it direct from [http://prdownloads.sourceforge.net/hplip/hplip-3.14.6.run](http://prdownloads.sourceforge.net/hplip/hplip-3.14.6.run) and then install by following the instructions at [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

That will get you version 3.14.6 so should be fine for that machine.

---

### Post by tb75252 on 2014-09-19
> **ajgreeny said:**
> You will need a very recent version, hplip-3.14.4 or later for that printer so you may need to get it direct from [http://prdownloads.sourceforge.net/hplip/hplip-3.14.6.run](http://prdownloads.sourceforge.net/hplip/hplip-3.14.6.run) and then install by following the instructions at [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

That will get you version 3.14.6 so should be fine for that machine.
Is it possible to install this HPLIP thing through an official Ubuntu repository?  That way I don't (hopefully!) have to worry about viruses and also the driver would be updated every time that a new version is posted to the Ubuntu repository.

---

### Post by ajgreeny on 2014-09-21
Not that I am aware of for that newest version that you need.

You do not need to worry about viruses in Linux, however, and as for updating, if you install hplip this way there is an option to update (right hand tab) in the **hplip-toolbox** that is installed with the whole package, and which also gives you the terrific GUI configuration application for your printers.
See screenshot of hplip-toolbox.

---

