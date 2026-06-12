---
title: "Unbuntu 8.10, HP LaserJet1100 Parallel Port Printer Hangs / Doesn't Work well"
date: 2008-11-22
forum: Hardware
---

### Post by Capa Pinbacker on 2008-11-22
I have a Sony Laptop (PCG-K33), and could not get my parallel port HP LaserJet 1100 printer to printer more than a page before getting stuck.  I found the following fix worked great:

1.  Set computer BIOS Parallel Port type to "EPP", or "Normal"
2.  Enter the following:
    sudo aptitude install hpoj hpijs cupsys
    sudo ptal-init setup
    sudo ptal-init start
    dpkg-reconfigure cupsys
3.  Goto System->Administartion->Printing, create the printer & select the following dirver:
    HP LaserJet 1100 Foomatic/hpijs [en]

I hope this helps other poor souls out there.

---

### Post by Capa Pinbacker on 2009-04-11
I should have mentioned that the following driver is fast and reliable... choose this one instead:
HP LaserJet 1100 - CUPS+Gutenprint v5.2.0-rc1 [en]

---

