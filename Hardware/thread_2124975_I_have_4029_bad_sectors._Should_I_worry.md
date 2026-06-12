---
title: "I have 4029 bad sectors. Should I worry?"
date: 2013-03-12
forum: Hardware
---

### Post by Juniorr on 2013-03-12
My SATA drive is from 2009 and has been under some circumstances where it's not "Pleasant" for the drive, such as blackouts (lots of them).
On Ubuntu 12.04 SMART reported 4029 bad sectors. I often do a zero-fill on the drive and I read that it reallocates those bad sectors. So, if it do a reallocate, why "a failure is imminent"? Why should I worry?

---

### Post by deadflowr on 2013-03-12
Replace the drive.
My guess is with over 4000 bad sectors, you've already maxed out the spare sectors, which normally sit around only a couple hundred.
Meaning anything you write that will be placed in a bad sector, would be moved into the ether as no spare sectors are available.

---

### Post by joebow1991 on 2013-03-12
Yea deadflowr is right, that drive is dying I mean you may be able to squeeze a little more out of it but I wouldn't recommend it due to the risk of data loss. Good luck!

---

### Post by tgalati4 on 2013-03-12
I see an UPS in your future.

---

