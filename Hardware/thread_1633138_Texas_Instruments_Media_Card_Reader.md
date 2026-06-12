---
title: "Texas Instruments Media Card Reader"
date: 2010-11-28
forum: Hardware
---

### Post by tacoman359 on 2010-11-28
I have an HP dv4000 with Jolicloud installed, which I believe is based off of Ubuntu 9.04 Jaunty Jackalope.  I can't find my SD card in the list of drives when I put it in the internal reader that the computer has.  The two things related to what I need (from lspci) are:
1. Texas Instruments PCIxx21 Integrated FlashMedia Controller
2. Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

I have minimal knowledge of Ubuntu and Linux in general... can anyone point me in the right direction?  Or tell me if drivers even exist for this card reader?

Thank you.

---

### Post by sandy8925 on 2011-08-18
try the command "dmesg|grep tifm|less" in a terminal and see if the output shows anything about a card reader.

---

