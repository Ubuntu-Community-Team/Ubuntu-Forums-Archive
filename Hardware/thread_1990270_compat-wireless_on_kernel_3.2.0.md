---
title: "compat-wireless on kernel 3.2.0?"
date: 2012-05-29
forum: Hardware
---

### Post by mvmacd on 2012-05-29
I downloaded compat-wireless the latest one [compat-wireless-2012-05-10] and patched it for zd1211rw driver [from [here]('http://www.aircrack-ng.org/doku.php?id=zd1211rw')].. and now when I try to insmod zd1211rw.ko, it says


**insmod: error inserting 'zd1211rw.ko': -1 Invalid parameters**

So I tried downloading linux-source [3.2.0 from synaptic], and tried to apply the patch for "Kernel 2.6.39+" but the patch was not there anymore.

Does anyone know how I can get the patched driver compiled on my kernel?

---

