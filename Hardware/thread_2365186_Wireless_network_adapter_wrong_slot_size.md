---
title: "Wireless network adapter wrong slot size"
date: 2017-07-03
forum: Hardware
---

### Post by jason13 on 2017-07-03
[FONT=arial]I've got a [/FONT][FONT=arial]GIGABYTE G1 Gaming GA-Z170X-Gaming 7 MB and the PCI adapter I have doesn't fit it, the first indentation in the large and small slots seem to be able to fit 10 pins while the card has 11 rows of pins. What kind of interface do I need to fit a card in?[/FONT]

---

### Post by QIII on 2017-07-03
Hello!

Would you care to tell us the manufacturer and model of the card?

Thanks!

---

### Post by Autodave on 2017-07-04
There are quite a few nowadays: even I have to look them up often. If I were you, I would probably consider a USB wifi card. The cost isn't bad and most of them behave well w/Linux.

If you want to still figure out what slot you have available, you could refer to the documentation of the motherboard. Or, check here: [https://superuser.com/questions/71945/how-to-identify-what-slot-type-a-particular-pc-card-is](https://superuser.com/questions/71945/how-to-identify-what-slot-type-a-particular-pc-card-is).

---

### Post by jason13 on 2017-07-04
It's a Rosewill rns-n250pc2 card

---

### Post by CatKiller on 2017-07-04
It seems that your wireless card is [PCI]("https://en.wikipedia.org/wiki/Conventional_PCI"), whereas your motherboard only has slots for the newer [PCI Express]("https://en.wikipedia.org/wiki/PCI_Express"). You could get a newer wireless card, or a USB wifi adaptor, but your motherboard has GbE LAN ports, which would be faster than any WiFi.

---

