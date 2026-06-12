---
title: "How to get ethernet device data"
date: 2009-01-11
forum: Hardware
---

### Post by Ozzapoo on 2009-01-11
Hi, I was wondering how I would go about getting data from my ethernet device, namely the group that made it. For example, it could be a SiS or Realtek one, and I want to know. How would I do this in terminal or any other software natively on ubuntu.

---

### Post by glennzo on 2009-01-11
Does
```
lspci | grep -i ethernet
```
get you the results you're looking for?

---

