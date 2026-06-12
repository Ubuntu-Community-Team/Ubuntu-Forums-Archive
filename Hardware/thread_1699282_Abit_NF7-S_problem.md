---
title: "Abit NF7-S problem"
date: 2011-03-03
forum: Hardware
---

### Post by TCMGO on 2011-03-03
[COLOR=black][FONT=Verdana]I am trying to rebuild an older computer with an Abit NF7-S motherboard.  To start, there are no hard drives installed, only a cd and dvd drive, which the motherboard detects.  My problem is that the MB cannot detect SATA drives, only IDE drives. I have the MB manual, but it says very little about the SATA setup, and it has no troubleshooting info for this problem.  I have searched the web for several hours and found no solutions.  I am hoping that perhaps somebody on the forum uses the NF7-S and can help me figure out the problem.  [/FONT][/COLOR]

---

### Post by befreetech on 2011-06-07
> **TCMGO said:**
> [COLOR=black][FONT=Verdana]I am trying to rebuild an older computer with an Abit NF7-S motherboard.  To start, there are no hard drives installed, only a cd and dvd drive, which the motherboard detects.  My problem is that the MB cannot detect SATA drives, only IDE drives. I have the MB manual, but it says very little about the SATA setup, and it has no troubleshooting info for this problem.  I have searched the web for several hours and found no solutions.  I am hoping that perhaps somebody on the forum uses the NF7-S and can help me figure out the problem.  [/FONT][/COLOR]

I have confirmed your problem.  When I attempt to install Ubuntu 11.4 on the NF7-S motherboard's SATA drive I get an unrecoverable message that indicates the grub installer failed on the sata device.  With the NF7-S this is also true with Windows.   The SATA ports require a driver to work with Windows so the same may be true with Linux.  If I learn more I'll let you know.

---

