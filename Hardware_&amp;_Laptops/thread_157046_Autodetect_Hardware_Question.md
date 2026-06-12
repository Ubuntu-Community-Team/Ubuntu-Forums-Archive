---
title: "Autodetect Hardware Question"
date: 2006-04-08
forum: Hardware &amp; Laptops
---

### Post by fsgpr on 2006-04-08
I recently reinstalled Linux (Dapper Drake, but this is more of a general question) on my Inspiron 8200 laptop but had the LAN card disabled in the BIOS, so it was not detected during the installation.

I have since enabled the card, how do I go about having Linux autodetect it/install the driver?  A link to a how-to that would apply to this would be useful, I have been searching the forums for a while but cannot find this.

Thanks.

---

### Post by christhemonkey on 2006-04-08
It should just detect it and add it to modules to be booted.
If so, when you go into network properties (in system administration or some other menu) it should show an eth0 device which you can configure and activate.
If not, then its a different story, and would you let us know the model of the LAN card.

---

### Post by ghakko on 2006-04-08
[QUOTE=fsgpr]I recently reinstalled Linux (Dapper Drake, but this is more of a general question) on my Inspiron 8200 laptop but had the LAN card disabled in the BIOS, so it was not detected during the installation.

I have since enabled the card, how do I go about having Linux autodetect it/install the driver?  A link to a how-to that would apply to this would be useful, I have been searching the forums for a while but cannot find this.[/QUOTE]

Your Ethernet driver will be automatically loaded at boot time. To actually configure it, go to "System" -> "Administration" -> "Networking" in your GNOME menu.

---

### Post by fsgpr on 2006-04-08
Thanks for the help to both of you.  Turns out I just needed to power down and back up for the BIOS to actually enable the card (it was autodetected and is listed in the Networking Menu again).

---

