---
title: "HP Scanjet 2400 on Ubuntu Intrepid 64 bits"
date: 2009-03-01
forum: Hardware
---

### Post by Shoeman on 2009-03-01
Hey folks

Did anyone have sucess on making the hp scanjet 2400 scanner work on Ubuntu 64 bits? It's not supported by sane. I've found a driver os an indian company, but it only works for 32 bits systems. Any help would be appreciated.

---

### Post by geraldm on 2009-03-01
HP2400 has a developmental version only available in sane cvs as of yet.  
Expect that there will be basic or better support in a forthcoming release.
This was a notice to sane community from the developer:
[http://lists.alioth.debian.org/pipermail/sane-devel/2009-February/024125.html](http://lists.alioth.debian.org/pipermail/sane-devel/2009-February/024125.html)

regards,
Gerald

---

### Post by xzero1 on 2009-03-01
I had it working a while back, I think in hardy. I'm not sure if it ever worked in Intrepid. Lately, I tried to get it to work in Intrepid, but no go. Your best bet is to get an older version of sane (dated about the time of the driver), and compile it as per the install instructions.

---

