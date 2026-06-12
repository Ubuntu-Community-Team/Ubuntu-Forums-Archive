---
title: "How to setup dual boot with xp pro and ubuntu 6.06 on an IBM Thinkpad R40 2681 C8U"
date: 2007-04-15
forum: Hardware &amp; Laptops
---

### Post by geercom on 2007-04-15
How does one setup dual boot with xp pro and ubuntu 6.06 on an IBM Thinkpad R40 2681 C8U?

When will there be an Ubuntu 6.06 or later version install CD with instructions specifically for laptops?

D.

---

### Post by crouton on 2007-07-23
> **geercom said:**
> How does one setup dual boot with xp pro and ubuntu 6.06 on an IBM Thinkpad R40 2681 C8U?

When will there be an Ubuntu 6.06 or later version install CD with instructions specifically for laptops?

D.

1) Install Windows XP Pro with appropriate partition sizing to ensure Ubuntu has enough space.
2) Install Ubuntu 6.06.  Edit /boot/grub/menu.lst to fit your particular preferences for boot order, timeout, etc.

I've done this with XP Pro and Xubuntu 7.04 on an older R40 (1.5 P4M) and it works great.

---

