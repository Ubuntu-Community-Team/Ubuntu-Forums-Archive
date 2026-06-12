---
title: "help with xorg"
date: 2006-04-17
forum: Hardware &amp; Laptops
---

### Post by slipk487 on 2006-04-17
i need to install my radeon 9250 graphics card and i dont understand the bus id for my graphics card on this motherboard because on my old one it was different here is the outcome of lspci for ati

```
0000:01:0a.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
0000:01:0a.1 Display controller: ATI Technologies Inc: Unknown device 5940 (rev 01)

```

---

### Post by taurus on 2006-04-18
I don't think you have to put in the Bus ID because I don't have that in my /etc/X11/xorg.conf!  See if X works without declaring the Bus ID...

---

### Post by slipk487 on 2006-04-18
i have to because i have an intergrated and if i dont it will just use the intergrated

---

