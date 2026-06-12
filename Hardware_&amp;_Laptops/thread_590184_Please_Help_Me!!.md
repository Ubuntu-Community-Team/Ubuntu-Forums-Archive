---
title: "Please Help Me!!"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by red_forman on 2007-10-24
How can i see my network cards name is???
Im useing a Acer Aspire 5630 laptop.

I need to know couse in XP my network card dosent work and i cant see the name there and if i downloaded the drivers thrue ubuntu it probebly would work.

My english is real bad as you can see. :)

Regards

---

### Post by kebes on 2007-10-24
[Open a terminal]("http://www.psychocats.net/ubuntu/terminal"), and type the command "lspci" (then press enter). This will list many devices. One of them should say something like "Ethernet device."

You can also run the command "lshw" to get a more complete listing for devices, which should give more details on the device you are interested in.

---

### Post by red_forman on 2007-10-24
THANKS!!!


 Broadcom Corporation BCM4401

---

