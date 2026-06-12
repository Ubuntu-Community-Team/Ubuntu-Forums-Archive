---
title: "Install trend on ubuntu?"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by vwlinux on 2009-04-07
I want to install Trend Micro Officescan on our ubuntu servers.
Cant seam to find many people that knows how to do it right.

Do you have a guide or tip?

We use the 8.04 LTS version with kernel 2.6.24-16

---

### Post by cariboo on 2009-04-07
Trend Micro Officescan is a Windows only product, you may want to have a look [here]("http://us.trendmicro.com/us/products/enterprise/serverprotect-for-linux/") fo a linux version. From the way it looks, they only have versions for Red Hat Suse, if you want to use them you would need to convert the rpm to deb.

Jim

---

### Post by vwlinux on 2009-04-07
Thanx.

I can just use alien to convert rpm to deb right?

---

### Post by cariboo on 2009-04-07
Yes the command to use is:

```
alien -d *rpm
```

Make sure you have alien installed, as it is not installed by default.

Jim

---

