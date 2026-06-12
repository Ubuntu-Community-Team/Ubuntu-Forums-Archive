---
title: "help!"
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by raghav_p on 2005-08-09
Hi,

I need help installing the i855crt module to enable the external vga monitor.

I downloaded the tarball but can't do anything more.

I tried ```
sudo make
``` but it says > make: `i855crt' is up to date. 

I don't know what to do. Please help!

**EDIT:** 

I found a i810switch in the repositories that may help. Just need to try it out. I don't know how to enable it though?

---

### Post by blind0wl on 2005-08-10
Do you know if that module is the actual module name?  If it is, just try:

```
modprobe i855crt
```

in a console.

Also it might help if you actually give the subject a name, rather than just "help!"  Being descriptive is what makes ppl actually click to see what your problem is.

---

