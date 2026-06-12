---
title: "Ubuntu 12.04 Graphic card not installed"
date: 2012-09-19
forum: Hardware
---

### Post by TheVamPiRe on 2012-09-19
My graphic card in ubuntu 12.04 has not installed. Can someone help me on install?

---

### Post by cmont899 on 2012-09-19
What graphics card do you have? 

You can list PCI devices with:

```
lspci
```

---

### Post by deadflowr on 2012-09-19
A little more nuanced:

```
lspci | grep VGA
```

Anyway, in what way is it not installed?
Are you getting a blank screen?
Are the graphics choppy?
Please elaborate, so as we can give you the most relevant help possible.

---

### Post by TheVamPiRe on 2012-09-20
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
This is the GRAPHIC CARD yee my graphics are not going good :(

---

