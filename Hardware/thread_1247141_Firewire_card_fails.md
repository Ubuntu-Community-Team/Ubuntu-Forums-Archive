---
title: "Firewire card fails"
date: 2009-08-22
forum: Hardware
---

### Post by hansson_14 on 2009-08-22
SOLUTION: See below, change the card.

I moved a working firewire card from one Linux computer to another. The card is a PCI and I use it to connect my FireDTV box. But it doesn't work in the new computer, a Shuttle K45 with Jaunty running.

lspci |grep 1394
03:09.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)

Outputs:

lsmod |grep 1394
dv1394                 17948  0 
video1394              15804  0 
raw1394                24636  0 
ohci1394               30460  2 dv1394,video1394
ieee1394               85908  4 dv1394,video1394,raw1394,ohci1394

dmesg | grep 1394
[    2.250562] ohci1394 0000:03:09.0: setting latency timer to 64
[    2.304512] ohci1394: Failed to allocate interrupt 0
[    2.304548] ohci1394: probe of 0000:03:09.0 failed with error -16
[    7.639897] ieee1394: raw1394: /dev/raw1394 device initialized
[    7.649722] video1394: Installed video1394 module

Anyone has a clue?

---

### Post by hansson_14 on 2009-08-31
Solution:

I replaced the firewire card with a new one. Apparently Shuttle K45 doesn't handle the chip from NEC. The card with VIA chip works ok.

---

