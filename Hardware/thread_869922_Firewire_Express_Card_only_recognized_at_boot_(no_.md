---
title: "Firewire Express Card only recognized at boot (no hotplugging)"
date: 2008-07-25
forum: Hardware
---

### Post by scotty64 on 2008-07-25
I got myself a Lindy 2 Port Firewire 1394a Express Card. The card works fine when I plug it into the slot before booting.
lscpi is giving the proper output:
0e:00.0 FireWire (IEEE 1394): Texas Instruments XIO2200(A) IEEE-1394a-2000 Controller (PHY/Link) (rev ff)
The problem is that hotplugging does not work at all:
- If I put the card into the slot AFTER system startup lspci is showing nothing.
- On the other hand the card is still listed by lspci, even when I remove it.
I found another thread with someone having a similar problem and I wonder if there is a solution, or if this is a kernel bug.

---

