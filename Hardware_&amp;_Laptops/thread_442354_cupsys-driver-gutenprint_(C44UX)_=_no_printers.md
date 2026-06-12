---
title: "cupsys-driver-gutenprint (C44UX) = no printers"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by gromituk on 2007-05-13
Hello.  I just thought it was worth noting somewhere (as it had me scratching my head for a while!) that installing cupsys-driver-gutenprint on Kubuntu Edgy results in an empty Printer Model Selection list in the Add Printers Wizard in the System Settings.  I was trying to install an Epson Stylus C44UX which does not appear in the standard printer list, but has a Foomatic Gutenprint driver.  Running foomatic-cleanupdrivers didn't help.

The *only* package that must be installed is foomatic-db-gutenprint.  Do *not* install cupsys-driver-gutenprint as well.

Hope that helps someone! :)

---

### Post by Justin Trouble on 2007-05-17
I'm suffering from the same, or perhaps a similar problem. Trying to modify a printer driver results in the selection list being completely empty.

I have cupsys-driver-gutenprint installed and not foomatic-db-gutenprint.

The kubuntu-desktop package has a dependency on cupsys-driver-gutenprint! Did you force removal of the cupsys-driver-gutenprint package?
Perhaps the dependencies have changed? I'm using Kubuntu Feisty.

---

### Post by gromituk on 2007-05-17
Hi there.  Yes, maybe the dependencies have changed - I'm pretty sure cupsys-driver-gutenprint was not installed by default.  Time to update to Edgy? ;)  (It was painless for me but your mileage may vary...)

---

### Post by Justin Trouble on 2007-05-17
Feisty (7.04) is the latest! Edgy (6.10) is the old version :)

I installed foomatic-db-gutenprint and now my KDE driver database is back!

I now have both cupsys-driver-gutenprint and foomatic-db-gutenprint installed!

---

### Post by gromituk on 2007-05-17
d'oh!  Swap feisty for edgy in my previous postings!

Glad you've got it sorted, but it's a pity our results are inconsistent.

---

