---
title: "Atheros wireless works!"
date: 2009-05-03
forum: Hardware
---

### Post by screwballl on 2009-05-03
I recently got a Compaq CQ60-211DX laptop that has the Atheros ar242x wireless. I decided to use GPARTED to shrink the Vista partition and use 10GB or so for Ubuntu. The newest version I had handy was 8.10 which installed perfectly. I did have to manually create the partitions (1GB for swap and the other 9GB for the installation) or else it would have taken over the entire hard drive.
The instructions I used to get it working where here (Method 2):

[How to get Atheros AR5007EG or AR242x wireless cards (may be other models) working in Ubuntu 8.10](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)

---

### Post by John Cheng on 2009-05-03
Congrats. I have a wireless card with an Atheros chipset too. It is an Airlink, PCI card (I picked it up for about $20). 

It looks like you needed to use the ath5k driver. For me, I had to use the ath_pci (contains proprietary binary layer) driver.

Again, congrats. It is always good to hear things "just work" on a Linux machine :)

---

### Post by doas777 on 2009-05-03
I was amazed to find that after upgrading to jaunty (via clean install) that my Atheros card was working OOB. I've never been able to get it working correctly in past, but not for lack of trying.

anyway, I'm happy now.

---

