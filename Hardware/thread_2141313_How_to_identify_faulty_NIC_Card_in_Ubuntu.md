---
title: "How to identify faulty NIC Card in Ubuntu?"
date: 2013-05-02
forum: Hardware
---

### Post by karthick87 on 2013-05-02
We are using ubuntu 12.10 operating system. In a particular system network is not working. I suspect that this may be due to faulty onboard NIC card. Instead of blindly buying a new NIC card, is it possible to confirm or find out whether the issue is with OS or with NIC card. I have checked with my network settings and the settings are good. I hope someone can guide me to get this problem fixed.

---

### Post by dabl on 2013-05-02
The fastest test I can think of, assuming you have a known-good Live CD (or Live USB stick) of some OS, is to boot that instead of the installed OS.  Two different Live CDs would be even better.  For example, if networking doesn't work with a recent Parted Magic or Ubuntu Live CD or USB stick, then I would declare it "broken".

Another approach, if someone has a wifi USB dongle available, is to try networking wirelessly.  If wireless works, but ethernet doesn't, then the ethernet transceiver is probably broken.

---

### Post by karthick87 on 2013-05-03
thankyou dabl will have check @ it.

---

