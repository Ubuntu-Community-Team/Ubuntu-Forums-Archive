---
title: "2 internal wireless cards inside acer 5520 notebook"
date: 2009-03-19
forum: Hardware
---

### Post by lifereversal on 2009-03-19
While upgrading my memory I noticed my acer 5520 has an empty mini pci express card slot.

I'm looking in getting a AR5008E-3NX(Chipset: AR5BXB72).

Can 2 internal wireless cards work on ubuntu 8.10 at the same time by using 1 for surfing the net and the other with aircrack?

Acer 5520 Specs:

Atheros AR5007(Chipset: AR5BXB63) - Madwifi 10.5.6 Hal patched
Ubuntu 8.10 x64

Any info is appreciated.

---

### Post by pytheas22 on 2009-03-20
Yes, you can easily have two cards active at the same time, one running aircrack (in monitor mode) and the other managing a normal connection (in managed mode).

Also, with Atheros cards, I think it's actually possible to use a single card for both aircrack and a normal connection at the same time, by creating virtual interfaces--in other words, you would have a virtual 'ath0' interface in managed mode, and an 'ath1' running aircrack, but they'd both be based on the physical interface wifi0.

This works under the madwifi (ath_pci) driver.  I'm not positive about the newer madwifi-ng (ath5k and ath9k) drivers, but I suspect that this feature is also supported by them.  You might want to do some googling if you're interested; it could save you from buying a second wireless card.

---

