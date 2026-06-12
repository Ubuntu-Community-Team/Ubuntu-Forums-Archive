---
title: "Sata &amp; Sataii ?"
date: 2008-04-02
forum: Hardware &amp; Laptops
---

### Post by ShodanjoDM on 2008-04-02
I'm planning to buy a new hard drive soon. It'll be either Western Digital or Seagate SATAII 200 - 300gb class hd.

But since my motherboard (ASUS P5GPL-X) doesn't has SATAII specification (only SATA), I wonder if there's any compatibility issues between a SATAII hd and SATA controller on the motherboard?

I assume that there will be no issues, but since I'm not completely sure, I thought of asking here first.

Thanks in advance :)

Edit: lol, I forgot the forum changed the uppercase in the title. So it's Sataii now :lolflag:

---

### Post by logos34 on 2008-04-02
Shouldn't be any problem--all sataII drives I've seen are backward compatible with sata I.  Might need to set the jumper on the back of the drive, that's all.

---

### Post by ShodanjoDM on 2008-04-02
Thank you. Now I'm feeling confident to buy the hard drive.

Anyway, since my current setup has a 80gb PATA drive, do you think it's wise to mix the two? I'm thinking of using the SATA as my main hd and the PATA as my backup drive.

---

### Post by logos34 on 2008-04-02
> **ShodanjoDM said:**
> Thank you. Now I'm feeling confident to buy the hard drive.

Anyway, since my current setup has a 80gb PATA drive, do you think it's wise to mix the two? I'm thinking of using the SATA as my main hd and the PATA as my backup drive.

Again, should be no problem.  Except if you (re)install ubuntu on a sata in a mixed sata/pata machine, grub usually ends up on the the mbr of the pata drive, so you'll need to continue booting from it or else specify in step 7 (Advanced button) that grub go on the sata.

---

### Post by ShodanjoDM on 2008-04-02
Alright, thanks again :)

---

