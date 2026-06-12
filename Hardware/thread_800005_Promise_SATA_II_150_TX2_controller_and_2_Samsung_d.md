---
title: "Promise SATA II 150 TX2 controller and 2 Samsung drives"
date: 2008-05-19
forum: Hardware
---

### Post by masonfoley on 2008-05-19
I have a Promise controller card with two Samsung drives on it.  I'm in a dual boot configuration with XP successfully expressing the two drives in Raid 0 (striped).

However in my 8.04 Hardy install, the controller card is listed in the Device info however to the two samsung drives show up separately.  There is no volume that can be mounted currently.

Is there a How-To troubleshooting guide out there that would allow me to configure Ubuntu to manage these two as one volume?

---

### Post by fuzzieza on 2008-05-20
Hi,

It sounds like you're experiencing a similar problem to mine.  I have an Intel motherboard with onboard VIA 6410 ATA RAID (which I believe is similar to the one used on the Promise RAID cards).  I've got it set up with two 120G Seagate drives in a mirrored configuration.  Ubuntu sees the drives, but they also show up as separate drives.

I'm too scared to try and mount either lest I end up corrupting the mirror and losing the data.  The mdadm utilities don't recognise the mirror setup and all info I've found on the net point me to creating a new mirror in Linux.  I'm pretty sure I won't be able to see that on the Windows side, so I'm between a rock and a hard place there in terms of having a reliable volume that I can share between WinXP and Linux.

Andries

---

