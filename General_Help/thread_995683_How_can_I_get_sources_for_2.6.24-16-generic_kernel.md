---
title: "How can I get sources for 2.6.24-16-generic kernel?"
date: 2008-11-28
forum: General Help
---

### Post by nite_man on 2008-11-28
Hi,

I try to build a kernel module for the kernel 2.6.24-16-generic (Kubuntu Hardy). But I cannot find appropriate kernel sources. I installed sources with apt-get:
```
apt-get install linux-source
```
But instead of linux-source-2.6.24-16-generic I got linux-source-2.6.24. The headers are corrects - linux-headers-2.6.24-16-generic. As result when the built module is loaded it gives that error:
```
fix_eeprom: disagrees about version of symbol struct_module
```
Could somebody tell me, please, how can I get appropriate kernel sources for the kernel 2.6.24-16-generic?

TIA

---

