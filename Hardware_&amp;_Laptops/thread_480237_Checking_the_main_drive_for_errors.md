---
title: "Checking the main drive for errors"
date: 2007-06-21
forum: Hardware &amp; Laptops
---

### Post by SteffJay on 2007-06-21
Can someone tell me if there is a facility for checking the main hard drive for errors ?

---

### Post by neptho on 2007-06-21
It's called fsck.  It's tuned to run whenever it sees a problem.  If you want to run it manually, make sure you are in single user mode.

Reboot the machine, and when the GRUB screen comes up, press 'ESC' really fast.  Choose the 'Recovery Mode' option.

Finally,  login with your password, and run:

```
fsck -A
```

to check all filesystems in /etc/fstab

---

### Post by SteffJay on 2007-06-21
Thank you for the quick reply **neptho**. I'll give that a burst...  ;)

---

