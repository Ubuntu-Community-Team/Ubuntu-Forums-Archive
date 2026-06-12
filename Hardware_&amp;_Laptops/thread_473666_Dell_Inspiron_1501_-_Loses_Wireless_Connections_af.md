---
title: "Dell Inspiron 1501 - Loses Wireless Connections after resume from standby"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by AaronMT on 2007-06-14
I am using Ndiswrapper for my Dell Wireless 1390 WLAN Mini-PCI Card (Broadcom Corporation)

My info.linux.driver is set to "ndiswrapper" and im using NetworkManager Applet 0.6.4

When I resume from standby the program will only let me configure wired connections as wireless functionality has disappeared and thus I can not connect to my wireless network.

How can I fix this?

---

### Post by AaronMT on 2007-06-17
bump

---

### Post by HotShotDJ on 2007-06-17
I had this same problem -- different machine and different wireless card -- but same symptoms.  To solve it, I edited /etc/default/acpi-support (as root -- so be careful!) and added my wireless driver to the line MODULES=""

So, in my case, the line now reads:
```
# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
MODULES="ipw3945"

```
Note that you will need to replace "ipw3945" with the driver appropriate for your system.  Please post back with your results.

---

