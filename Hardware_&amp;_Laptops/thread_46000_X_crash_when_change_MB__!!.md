---
title: "X crash when change M/B  !!"
date: 2005-07-02
forum: Hardware &amp; Laptops
---

### Post by pnix on 2005-07-02
I change mainboard K7N2 Delta2 FSR to A7N8X-E deluxe. My box still can boot but Xwindows is not work and this is some part of Xorg.0.log   

(II) NVIDIA X Driver  1.0-7174  Tue Mar 22 06:48:37 PST 2005
(II) NVIDIA Unified Driver for all NVIDIA GPUs
(II) Primary Device is: PCI 03:00:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:3:0:0) found
(EE) No devices detected.

Fatal server error:
no screens found

anyway to reconfiguration X and network???  :-|

---

### Post by rama on 2005-09-28
[QUOTE=pnix]I change mainboard K7N2 Delta2 FSR to A7N8X-E deluxe. My box still can boot but Xwindows is not work and this is some part of Xorg.0.log   
(II) NVIDIA X Driver  1.0-7174  Tue Mar 22 06:48:37 PST 2005
(II) NVIDIA Unified Driver for all NVIDIA GPUs
(II) Primary Device is: PCI 03:00:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:3:0:0) found
(EE) No devices detected.
Fatal server error:
no screens found
anyway to reconfiguration X and network???  :-|[/QUOTE]

I have the exact same problem (except that my mb is A7N8X Deluxe - no 'e') and that the error descr says PCIID:2:0:0. Did you manage to solve the problem?

---

### Post by mlomker on 2005-09-28
Did you try running **dpkg-reconfigure xserver-xorg**?  The Nvidia driver specifies the slot that the card is in and if it doesn't find it then it'll die.

You could also **lscpi** and verify that your card is in the same slot as your config lists.

---

### Post by rama on 2005-09-29
Yeap! And it worked like a charm ... I found out about it a few minutes after I posted here. Thx anyway.

---

