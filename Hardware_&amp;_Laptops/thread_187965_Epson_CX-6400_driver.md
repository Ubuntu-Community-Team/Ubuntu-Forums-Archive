---
title: "Epson CX-6400 driver"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by jlhughes on 2006-06-03
Under Breezy my two printers connected to a Pricom SX-5000U2 print server were working fine.

After Dapper upgrade everything related to printing stopped working.  Unable to figure out why the cups error log reported 

E [02/Jun/2006:23:45:26 -0700] Creating missing directory "/var/run/cups/certs"

even though the directory existed, I decided to uninstall and reinstall all cups and foomatic applicaitons.

In the process of reinstalling cups and foomatic I got my Samsung ML-1710 laser to work, but the Epson CX-6400 driver was no longer listed in the printer drivers.

It turns out that restoring the Epson-CX(n) drivers required the installation of gimpprint

Uninstalling and reinstalling ALL cups and footmatic plus gimpprint restored my printing abilities. I have no idea what caused the system not to work after the Dapper upgrade.

---

