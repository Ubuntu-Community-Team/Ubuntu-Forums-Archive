---
title: "Looking for a PCI/PCI-e parallel port card which will work out-of-the-box with Linux"
date: 2016-03-05
forum: Hardware
---

### Post by delta410 on 2016-03-05
I just checked out the driver page for the parallel-port card card in my machine (Oxford Semiconductor Ltd OX16PCI952).

The Linux drivers for this designed-for-Windows card are six years old. They likely won't work properly with the latest versions of Ubuntu.

Furthermore, you can't just install the drivers automatically. They require* a lot* of command-line voodoo, that is, manually placing files here, there and elsewhere.

Is there a parallel-port PCI or PCIe card that will work *out-of-the-box* with Ubuntu 14.04 LTS? 

If so, where can I purchase it?

---

### Post by houstonbofh on 2016-03-08
Most of this stuff just works automatically on install.  Does your card not work without CLI-fu?

---

### Post by delta410 on 2016-03-09
As I said above, no, it requires A LOT of CLI-fu. It was designed to work under Windows. The fact that the Linux "drivers" are over 6 years old tells me that the manufacturer isn't interested in supporting Linux users.

---

### Post by delta410 on 2016-03-14
(Bump)

Any further info about this issue?

---

### Post by delta410 on 2016-03-18
Since no one here appears to have an answer to my problem, I took the matter to a local electronics dealer. They sold me a LAVA PCI parallel port card. They weren't exactly competitive, price-wise, but if it didn't work, I wanted to be able the bring the thing back the next day, and not have to wait days or *weeks* for an RMA and a product exchange. 

The short version - I removed the worthless Oxford parallel-port card (no Linux support whatsoever), installed the LAVA card, powered up my machine, deleted the printer I'd installed and then reinstalled it. Tried printing a test page. No result. Switched the printer from LPT 1 to LPT 2. Tried printing a test page again. This time, success!

I hope that my experience will help out other Linux users who need parallel-port capability.

---

