---
title: "Hardware problems - HDD, fan, ...?"
date: 2005-10-27
forum: Hardware &amp; Laptops
---

### Post by teevee on 2005-10-27
My PC ([iDeq 210V](http://www.biostar.com.tw/products/barebone/ideq/210v/index.php3) with an Athlon XP 3000+, Samsung 80GB SATA HDD, 1x 512MB Corsair ValueSelect, GeForce FX 5200, SB Digital Live something soundcard) is behaving weird in the last days. First there are sounds as if the fan stops spinning and then restarts immediately. Or like a power reset perhaps. My system becomes unusable at this point. Nothing works, no Ctrl+Alt+Backspace and stuff, have to do a hard reset. Yesterday this happened all few minutes, today it already happened twice *during* the Ubuntu boot. There's no error messages in /var/log/* which could be related to this! A few weeks ago (before those problems) my HDD remounted to read-only all of a sudden, could this be happening here too? But before Ubuntu is able to write to the log files? (errors=remount-ro is in my fstab)

I also had to do 2 fsck's from Knoppix due to a faulty FS, which could be caused by the resets, or because the HDD is to blame in the first place...?

Cleaned the case and CPU fans now, they were a bit dusty, seeing if that helps.

To rule out a HDD problem I have to see if it happens from Puppy Linux on my USB pendrive too. So far it only happened while running from HDD.

Any ideas?

---

### Post by Ramses on 2005-10-27
Just guessing: could it be power supply?

---

### Post by teevee on 2005-10-27
Hmm, since I cleaned the fans there were no more hang-ups until now. Maybe this was the problem. It's a small form factor system with a small fan and little free room inside, if that can't blow air properly it's probably a bit more serious than with some multi-fan tower. :-)

Oh btw, posted this in Community Chat since it didn't seem related to Ubuntu.

---

