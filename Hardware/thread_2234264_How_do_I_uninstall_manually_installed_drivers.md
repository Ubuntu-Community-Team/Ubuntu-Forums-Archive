---
title: "How do I uninstall manually installed drivers?"
date: 2014-07-13
forum: Hardware
---

### Post by isaiah-courtney96 on 2014-07-13
I'm running on Ubuntu 14.04 64-bit. I'm using the amd catalyst 14.10 drivers. When ever I launch steam it says I'm not using direct rendering even though glxinfo says I am. Someone on their forums told me to uninstall my drivers and reinstall them. How do I do that?

---

### Post by Yellow Pasque on 2014-07-13
That depends on how you installed it.

---

### Post by isaiah-courtney96 on 2014-07-13
> **Temüjin said:**
> That depends on how you installed it.
I downloaded the drivers from AMDs website and installed it through the terminal.

---

### Post by ubudog on 2014-07-13
Were they in a .deb package form?

---

### Post by Yellow Pasque on 2014-07-14
> **isaiah-courtney96 said:**
> I downloaded the drivers from AMDs website and installed it through the terminal.

Did you follow instructions here?: [http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_STABLE](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_STABLE)
If you did not have lib32gcc1 package installed, the 32-bit libs may not have been built, which would cause issues with Steam since it's a 32-bit program.

---

### Post by isaiah-courtney96 on 2014-07-14
> **ubudog said:**
> Were they in a .deb package form?
Yes.

---

### Post by isaiah-courtney96 on 2014-07-14
> **Temüjin said:**
> Did you follow instructions here?: [http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_STABLE](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_STABLE)
If you did not have lib32gcc1 package installed, the 32-bit libs may not have been built, which would cause issues with Steam since it's a 32-bit program.
No I didn't I followed another guide. Do I have to uninstall the drivers or will it do it for me when I use this guide?

---

### Post by Yellow Pasque on 2014-07-14
> **isaiah-courtney96 said:**
> No I didn't I followed another guide. Do I have to uninstall the drivers or will it do it for me when I use this guide?

Read the instructions:
> If you have previously attempted installing Catalyst, remove any leftover files by following the Removing the Driver section
[http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

