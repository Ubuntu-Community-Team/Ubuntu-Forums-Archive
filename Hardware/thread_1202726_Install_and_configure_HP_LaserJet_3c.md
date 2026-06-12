---
title: "Install and configure HP LaserJet 3c"
date: 2009-07-02
forum: Hardware
---

### Post by macheboy on 2009-07-02
I have very old HP ScanJet 3c scanner that connects to the computer throuth SCSI. I tried using it with xsane, but xsane starts using my TV card (Pinnacle). The scanner hasn't been used for a while (last time it was used with an ISO card), but I'm pretty sure that this Adaptec PCI  SCSI card works fine. When I turn the computer on, I can enter some kind of SCSI BIOS (or whatever it is).
I am not familiar with SCSI, so it might be that I configured something badly. (The card and the scanner are both on channel two.)
I don't even know how to check if Ubuntu sees the scanner or the card.

Please help

---

### Post by macheboy on 2009-07-03
bump

---

### Post by DellAnderson on 2009-11-02
I'm in the process of doing something similar.  Correct me if I'm wrong, but IIRC each device has to have a different ID number (in other words, I don't think you want both your host and your device set to 2)...of course I may have completely misunderstood what you were saying.   Customarily, I think 7 is the host card, 0 is a bootable SCSI drive etc.   My HP ScanJet 3c was set to "1" last time I used it on a PC.

Dell

> **macheboy said:**
> I have very old HP ScanJet 3c scanner that connects to the computer throuth SCSI. I tried using it with xsane, but xsane starts using my TV card (Pinnacle). The scanner hasn't been used for a while (last time it was used with an ISO card), but I'm pretty sure that this Adaptec PCI  SCSI card works fine. When I turn the computer on, I can enter some kind of SCSI BIOS (or whatever it is).
I am not familiar with SCSI, so it might be that I configured something badly. (The card and the scanner are both on channel two.)
I don't even know how to check if Ubuntu sees the scanner or the card.

Please help

---

### Post by macheboy on 2009-11-06
Thanks. I have set it the way you said, but Xsane still starts with pinnacle TV card as the scanning device.
how can i check if the scanner is working? (I do hear sounds from it :)

---

