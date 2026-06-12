---
title: "alsa-utils restart required after suspend"
date: 2007-10-09
forum: Hardware &amp; Laptops
---

### Post by alina.bolero on 2007-10-09
Everytime I come back from an s2ram suspend on my Fiesty lappy I have to:

[FONT="Courier New"]/etc/init.d/alsa-utils restart[/FONT]

in order to get sound back

I added alsa-utils to the STOP_SERVICES in /etc/default/acpi-support, but that didn't seem to help:
[FONT="Courier New"]
STOP_SERVICES="mysql alsa-utils"[/FONT]

Any suggestions on how to automate this?

-Alina

---

### Post by komputes on 2008-02-20
You're lucky, sudo /etc/init.d/alsa-utils restart , actually works for you. I need to restart my Aspire 5000 laptop completely to get sound back. My audio apps just freeze.

---

