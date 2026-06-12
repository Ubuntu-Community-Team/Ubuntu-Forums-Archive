---
title: "hibernate disables udma5 mode!"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by dc. on 2007-05-08
Hi!

I noticed that after a fresh boot hdparm -I /dev/sda
shows me correctly udma5-mode for my harddisk:
DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5

However, after hibernate and resume, the disk runs only in udma2!

DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 udma5


What can I do? This affects system performance!

---

### Post by dc. on 2007-05-16
hi, anybod got the same problem?

---

### Post by dc. on 2007-05-28
Solved with 2.6.20-16-generic

---

