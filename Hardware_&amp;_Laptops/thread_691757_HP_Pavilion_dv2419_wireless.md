---
title: "HP Pavilion dv2419 wireless??????"
date: 2008-02-08
forum: Hardware &amp; Laptops
---

### Post by rittenbachstock on 2008-02-08
I just installed 7.10 on my HP. The wireless is not seen, but the blue tooth shows up just fine. Is their anyone out there that has a newer HP laptop that has gotten their wireless to work, and if so, how did you do it? 

  Thanks, rittenba

---

### Post by mikewhatever on 2008-02-09
HP laptops use various wireless cards, so you should specify your model. In my case, the [PRO/Wireless 3945ABG Network Connection] worked out of the box. In short, post the output of <sudo lshw -C network>.

---

### Post by gnelson on 2008-02-09
I was able to get mine (Broadcomm 4311 chipset) through the Restricted Drivers Manager, but the performance was poor.  I now use ndiswrapper and have much better results.  My laptop is a HP dv6324us.

Have you tried the Restricted Drivers Manger yet?

---

### Post by rittenbachstock on 2008-02-09
My wireless card is a Broadcom 4321AG. Has anyone heard of this card working?

   Thanks

---

