---
title: "SATA2 hdd doesn't work!"
date: 2006-10-01
forum: Hardware &amp; Laptops
---

### Post by olgias on 2006-10-01
I have an Asrock ALiveSATA"-GLAN and a MAXTOR SATA2 hdd 250Gb.

If I connect the hdd to the SATA2 connector on the motherboard,
the ubuntu installation cd can't see the hdd.

But if I connect it to the SATA connector it works fine.

Is really a kernel problem??

So do I have to install 2.6.18 kernel?

Thanks.

---

### Post by SonnyBonds on 2006-10-02
Hello there,

i had the exact same problem. Seems like the Asrock jMicron sataII chip is not recognized by Ubuntu. (I had to put it in SATAI too)

However, after the installation i updated the kernel, and every other thing that was outdated and SATAII worked fine!

---

