---
title: "Printer Colors WAY Off"
date: 2008-11-14
forum: General Help
---

### Post by quentoli on 2008-11-14
Greetings all,

  I have an Epson Stylus CX9400 on 8.04 that I can't seem to color calibrate.  I've tried both the _Epson Stylus CX9400 - CUPS+Gutenprint v5.0.2 Simplified_ and _Epson Stylus CX9400 - CUPS+Gutenprint v5.0.2 [en]_ drivers, have tried both CMYK and RGB color models (this is a CMYK printer), and it always turns out the same.  Attached is a test print.  Everything drops out at 70% except for the R, G, and B lines, which are just plain screwy.  Any thoughts?

---

### Post by Daktyls on 2008-11-16
I have the Fax version of this printer (CX9400F), but I think the solution might be the same, try this out:

[http://ubuntuforums.org/showthread.php?t=976991](http://ubuntuforums.org/showthread.php?t=976991)

---

### Post by quentoli on 2008-11-22
That didn't directly solve the problem, but sent me in the right direction.

The only drivers I had available were from gutenprint 5.0.2 (standard in Hardy?), whereas the one you listed is from 5.2.1.  I grabbed the [deb for gutenprint 5.2.1]("http://openprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-i386/openprinting-gutenprint_5.2.1-2lsb3.2_i386.deb") from openprinting.org, installed it, then changed my driver to what you suggested.  Color model is set to CMYK and it now prints beautifully.

Many thanks Daktyls!

---

