---
title: "HP Laser 1020; USB Hub Issues"
date: 2009-10-26
forum: Hardware
---

### Post by CovenStine on 2009-10-26
I installed ubuntu, and plugged in my HP LaserJet1020 using an extension, worked fine.  Wanted to add a PhotoSmart c3100, needed a hub, moved the 1020 to the hub alongside the c3100, and plugged the hub into the mobo where the extension had been.
Problem arises here: autodetect found the c3100, but can no longer find the 1020. I've tried moving around the printers on the hub, disconnecting the 3100, moving around the hub on the mobo, with various and sundry restarts thrown in for good measure.
I found a thread that talked about a simlar issue, and the 1020 would only disover with lsusb run as root, but the solution failed for me.
I also tried HPLIP, to attempt to get the drivers to work correctly, also to no avail.
As a rookie, I'm out of ideas... and am getting quite frustrated with what should be a plug and play issue (I believe...)
Any suggestions?

---

### Post by CovenStine on 2009-10-31
<bump> Anyone?  Should this be in a different category?  </bump>

---

### Post by CovenStine on 2009-11-16
Any suggestions at all?
I've upgraded to 9.10 and still there is no perceptible improvement.

---

### Post by oldsoundguy on 2009-11-16
My personal experience is that most HP printers don't like living on a hub, even a powered hub. (Especially 3 in 1 and 4 in 1 units.)  None of mine are wired so and all 4 of them work including their scanners. 
I had to install a usb PCI card in order to eliminate the hub for the printers. (cheap enough on eBay)

---

