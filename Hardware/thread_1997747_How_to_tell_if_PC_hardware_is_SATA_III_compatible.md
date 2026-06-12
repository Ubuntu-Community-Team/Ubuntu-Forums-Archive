---
title: "How to tell if PC hardware is SATA III compatible?"
date: 2012-06-05
forum: Hardware
---

### Post by gencon on 2012-06-05
Running: Ubuntu Lucid.

How do I determine if my desktop PC can have a SATA III hard disk plugged into it?

I'm pretty sure my current drives are SATA II (but not sure).

Thanks.

---

### Post by gordintoronto on 2012-06-05
Open Terminal. Enter this command:

sudo lshw -html > Desktop/config.htm

Enter your password when prompted.

A file should appear on your desktop. Double-click on it, it should open in your browser. The third line should say "product," that is your motherboard. You can Google it to get the specs.

If your computer is running Lucid, it probably does not support SATA III. I think a SATA III hard drive will work, but it won't deliver a performance advantage over SATA II.

---

### Post by gencon on 2012-06-07
Ok thanks. I didn't realize the only way to tell was to look up the hardware specs.

Cheers.

---

