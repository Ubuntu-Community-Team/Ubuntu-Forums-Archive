---
title: "ram detection problems"
date: 2005-12-04
forum: Hardware &amp; Laptops
---

### Post by frootstripe on 2005-12-04
Hi, I have 2G of ram on my system, but Kbuntu only detected 1G. I've run Knoppix 3.6 on it and it detected both sticks. suggestions?

---

### Post by heimo on 2005-12-04
Default kernel in (x/k/edu/u)buntu supports ~900MB RAM. You need to install linux-686 (for Intel processors) or linux-k7 (for AMD processors). Use Synaptic or Kynaptic - or run:
```
sudo apt-get install linux-686 (or linux-k7)
``` And reboot. Do not uninstall linux-386. If anything goes wrong, you can choose your old version of kernel at grub menu (at the beginning of boot process).

---

### Post by frootstripe on 2005-12-04
thanks for the quick reply, much appreciated.

---

### Post by frootstripe on 2005-12-04
Solution worked. sweet.

thanks again.

---

