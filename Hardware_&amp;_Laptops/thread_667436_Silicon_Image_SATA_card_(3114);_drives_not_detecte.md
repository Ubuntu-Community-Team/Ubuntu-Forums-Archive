---
title: "Silicon Image SATA card (3114); drives not detected"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by makunouchi on 2008-01-14
Hello, recent Ubuntu convert here.

I am using the 7.10 Gutsy AMD64 server release and have run into a problem when hooking up my hard drives.

The motherboard (A8N-SLI vanilla) has 4 sata_nv ports which work fine. But I also have a Silicon Image 4-port SATA card (SiI3114) which I have the sata_sil module installed and loaded for. The card itself is detected and appears to be recognised by Ubuntu, but when i do an fdisk -l it only shows the drives connected to sata_nv (the mobo ports).

The drives are brand new and are unpartitioned, I haven't done anything besides plug them in. Have I overlooked something? The only threads I could find dealt with getting Ubuntu to see the drives as one RAID volume, which I don't need, I plan on using software RAID.

Quick summary: I want Ubuntu to be able to see my drives connected to my SiI3114 card.

Thank you for reading.

EDIT: After much aggrovation with Silicon Image's site (they are very unclear as to what files you actually need and half their utilities plain don't work) I finally managed to flash the card's BIOS to the latest version which fixed the problem. All drives are detected now. I had to make a DOS boot CD and flash from there as the windows flash utlity didn't work.

---

