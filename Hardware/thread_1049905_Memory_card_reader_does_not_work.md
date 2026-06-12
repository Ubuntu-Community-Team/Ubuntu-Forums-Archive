---
title: "Memory card reader does not work"
date: 2009-01-25
forum: Hardware
---

### Post by crazyfuturamanoob on 2009-01-25
I just upgraded my acer laptop to Ubuntu 8.10, and memory card reader doesn't work.

lspci gives me this along with other stuff:
> 
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)


But when I put any memory stick into it, nothing happens, no pop-ups. I can't even mount the drive manually.

---

### Post by Sam Lars on 2009-01-25
I have the same one, and I have the same problem.  The bug is here.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238208](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238208)
Basically they'll add the driver when they get around to it.

---

### Post by atropa on 2009-02-04
I'm using 8.10 on a HP 8530w Notebook with the R5C822 SD/MMC memory card controller.

In the bugreport they mention memory stick cards not beeing detected, while SD works fine.

However, when I plug in a SD card, nothing happens at all.

Information available on this topic is somewhat ambiguous and I'd be interested if SD cards (e.g. San Disk) are supposed to be working or if everyone is having the same problem.

---

### Post by crazyfuturamanoob on 2009-02-05
Why is it a "bug report"?

There reads this isn't a bug, just no driver at all.

---

### Post by atropa on 2009-02-05
Thank you for your expertise.

Do you also know if SD generally works or not with this controller?

---

