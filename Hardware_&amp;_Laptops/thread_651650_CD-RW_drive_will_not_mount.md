---
title: "CD-RW drive will not mount"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by bwang on 2007-12-27
After upgrading from Feisty to Gutsy, my CD-RW drive will not mount. The error message is: /dev/scd1 does not exist. How do I fix this?

---

### Post by taurus on 2007-12-27
Look to see what is the device name now.

```
dmesg | more
```
Hit space bar for the next 24 lines.

---

### Post by bwang on 2007-12-27
The output of dmesg | more is huge. Which lines do I post?

---

### Post by taurus on 2007-12-27
Look in there until you see the line that has your CDROM in it.  Look to see what the name of the device, /dev/src0 or something like that.

---

