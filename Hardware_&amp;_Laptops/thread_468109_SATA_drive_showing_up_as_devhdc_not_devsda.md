---
title: "SATA drive showing up as /dev/hdc not /dev/sda ??"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by xenblend on 2007-06-08
Hello all,

Can someone tell me why my former /dev/sda sata drive is now showing up as /dev/hdc?  I upgraded from 6.10 to 7.04 and that was pretty much the only thing I changed (I now use the default 2.6.20 kernel of course.)  If you need more info please ask me I will gladly tell all.

xb

---

### Post by Megatog615 on 2007-06-08
I believe this is a change in libata.

---

### Post by xenblend on 2007-06-08
What do you mean a change in libata?  What could have changed?  And how?

---

### Post by Megatog615 on 2007-06-09
libata is the library that defines the names of drives.

---

