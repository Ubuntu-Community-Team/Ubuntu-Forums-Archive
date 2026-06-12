---
title: "printing never stop;s"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by SBarretDolph on 2005-06-06
We have an HP laserjet 1100 which used to run fine but now it just keeps printing nonsense without stopping.

---

### Post by David Haas on 2005-06-06
I assume that it had been working well in Ubuntu, Hoary. I can't tell you why it's doing what it's doing, but I see no harm in re-installing it by deleting the recognized printer from the gnome printer manager and selecting "New Printer." Thn you can re-select the HP Laserjet 1100, for which Ubuntu has the drivers, and then select the PPD file for it, which is located at /usr/share/cups/model/foomatic-ppds/HP.  I see these two PPD files listed : HP-LaserJet_1100-hpijs.ppd.gz and HP-LaserJet_1100-ljet4.ppd.gz. I don't know the differences between them, but I think that the former is given free to the Linux community by HP.
David Haas

---

