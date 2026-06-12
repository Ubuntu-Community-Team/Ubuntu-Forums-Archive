---
title: "Drivers IBM RSA-I adapter &amp; Qlogic QLA2300 HBA"
date: 2006-09-11
forum: Hardware &amp; Laptops
---

### Post by cable2000 on 2006-09-11
@all:

I'm looking for drivers for 2 components included in my IVM x335 Server

IBM supports only RH and Suse for their components so my RSA-I adapter is not ruinning :( Is there someone with the same problem and does anybody know how to create/resolve such a driver?

further, also the Qlogic QLA2300 HBA is not functioning. The same story here, Qlogic does not provide a driver for Ubuntu, only RH and Suse Linux Distro's :(

Is there someone out there who can help me with one or both of my problems??

Regards
Robert

---

### Post by tstreit on 2006-12-26
cable2000,

I am in the same boat as you, I am looking to have Ubuntu install on a IBM BladeCenter with the blade HS20 and a DS400 SAN.  My blade has a qlogic card installed in it and I can't get the card working.  If you have made any progress I would appriecate the help.

Thanks!

---

### Post by cable2000 on 2006-12-26
Hi

Yes i did made progression on the qlogic (qla2340) HBA

just download the redhat driver (rpm) and convert that one
using alien, Then install the .deb result with dpkg -i driver.deb

the HBA is working good after installation :)

Regards
Robert

---

### Post by tstreit on 2006-12-26
Thanks I will give it a shot!

---

