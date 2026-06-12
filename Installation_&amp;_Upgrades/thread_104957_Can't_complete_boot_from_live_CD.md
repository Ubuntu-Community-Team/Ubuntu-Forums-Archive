---
title: "Can't complete boot from live CD"
date: 2005-12-17
forum: Installation &amp; Upgrades
---

### Post by CyberPilgrim on 2005-12-17
I am brand spanking new to Linux. Maximum PC ran a piece on this distro, and I have been interested in trying Linux out for years, so....

I downloaded and burned a copy of the live CD. I am running an emachines T6524 (AMD 64). The CD boots, but not completely. A bunch of text scrolls across the screen, then it seems to freeze.

Can anyone help me? I tried finding this topic already, but was unsuccessful. 
:confused: 

Pilgrim

---

### Post by kapblp on 2005-12-17
I have an eMachines 6212 and have the same problem.  It seems to be hanging on the SATA controller.

---

### Post by aysiu on 2005-12-17
It could be a bad CD--possibly corrupted during download or burn.

---

### Post by CyberPilgrim on 2005-12-17
Is there a solution to this, or should I try a different distro?

CyberPilgrm

---

### Post by kevvyd on 2005-12-17
I had a similar problem just this week. It took me a bit of messing around and forced me to actually read my motherboard manual for the proper BIOS settings (gasp!), but it turned out that when I added the new SATA drive I didn't properly set up the BIOS. I would look to the BIOS settings to make sure your machine is reading the drives correctly.

---

### Post by taelmx on 2005-12-18
Make sure you downloaded the 64-bit edition of the live CD. Since code(hex) is different for mac, 64-bit, and regular processors, you need to have the right CD.

---

