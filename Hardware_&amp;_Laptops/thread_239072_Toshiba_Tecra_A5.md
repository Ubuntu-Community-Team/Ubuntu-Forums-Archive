---
title: "Toshiba Tecra A5"
date: 2006-08-18
forum: Hardware &amp; Laptops
---

### Post by GoldBuggie on 2006-08-18
Just a very short help for Marvel Ethernet Controller usage...I'll probably make this into a nicer howto this weekend

anyway...

in short....the new driver for the Marvel chipset doesn't work. Internet hangs when bandwidth gets to high.
Solution: dl the syskonnect patch and apply it to kernel 2.6.15.7 and use the pci=routeirq kernel parameter. Then use the sk98lin driver instead of sky2.

Again this is just a short post for ppl in need. I'll write a better one soon but my firefox crashed while I was 98% finished with writing such a howto and now i'm not in the mood.

---

