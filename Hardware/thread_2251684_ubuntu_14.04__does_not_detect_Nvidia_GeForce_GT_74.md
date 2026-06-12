---
title: "ubuntu 14.04  does not detect Nvidia GeForce GT 740"
date: 2014-11-06
forum: Hardware
---

### Post by ian_matthews on 2014-11-06
Recently purchased a new GT 740, but using 'lshw' does not give this product under *-display output.   Simply decribes the 'product' as NVidia.  Have tried to upgrade depositories to input new driver and Nvidia says a driver is available for linux based systems. The display works OK but under the Noveau drivers. - additional drviers  are shown as Nvidia 340.46   The card is version 340.58 so I assume this  should work, but only if the card is recognised by the system

But if 14.04 doesn't even recognise this card, presumably trying to install a new driver is pointless.   So how do I get Unbuntu 14.04 to identify the card and how can I find out what cards 14.04 will currently support?

I assume this is a problem with any relatively new product - anyone come across this problem before and are there any solutions?

---

### Post by Pilot6 on 2014-11-06
Why do you think that the system does not recognize you videocard.
Run

lspci -k | egrep 'VGA|3D' -A2

and you will see your card.

Install drivers and all should work.

---

