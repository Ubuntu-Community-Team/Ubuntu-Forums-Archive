---
title: "Help! - Deinstall graphics drivers from the command line"
date: 2009-09-09
forum: Hardware
---

### Post by stevebond001 on 2009-09-09
Help!
I have just installed Envy to help me install a driver for my (ATI based) graphics card.  Envy downloaded the recommended driver and asked me to reboot, which I did.
However, when the PC boots up now I just get a garbled screen and it locks up.

Does anyone know how to de-install the driver from the command line (as I can boot into recovery mode OK)

Many thanks in advance

---

### Post by bumanie on 2009-09-09
Should be > sudo envy --uninstall-allThen reboot > sudo shutdown -r now

---

### Post by stevebond001 on 2009-09-09
Thanks for the reply

When I try to follow your instruction I get an error message:
envy: command not found

Also, sudo dpkg-reconfigure xserver-xorg -phigh returned no error. However when I rebooted after this I still have the same problem (garbled screen)

How can I list and deinstall the offending graphics driver?

---

### Post by stevebond001 on 2009-09-09
Sorted
I ran the following command
sudo envy**ng** --uninstall-all 

This deinstalled envy and all the appropriate drivers

Many thanks for your help

---

### Post by hockeytux on 2009-09-09
I had a similar problem (also with an ATI card) and had to uninstall drivers from the command line as well.

Best not try to 'update' the ATI drivers at all, it'll just make it worse, I tried various things.

Hopefully we will get some better supported drivers soon :KS

---

