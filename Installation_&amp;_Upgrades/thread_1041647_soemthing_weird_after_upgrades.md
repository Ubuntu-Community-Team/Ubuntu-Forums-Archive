---
title: "soemthing weird after upgrades"
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by gd6noob on 2009-01-16
i have updated ubuntu 8.10 with updated via update manager and also check synaptic package manager, after i rebooted theres more lines in grub

8.10 kernel 2-6-27-9
8.10 kernel 2-6-27-9 (recovery mode)
8.10 kernel 2-6-27-7
8.10 kernel 2-6-27-7 (recovery mode)
windows

i dont get this??? the different between 8.10 kernel 2-6-27-9 and 8.10 kernel 2-6-27-7?

---

### Post by taurus on 2009-01-16
> **gd6noob said:**
> i have updated ubuntu 8.10 with updated via update manager and also check synaptic package manager, after i rebooted theres more lines in grub

[B]8.10 kernel 2-6-27-9
8.10 kernel 2-6-27-9 (recovery mode)[/B]
8.10 kernel 2-6-27-7
8.10 kernel 2-6-27-7 (recovery mode)
windows

i dont get this??? the different between 8.10 kernel 2-6-27-9 and 8.10 kernel 2-6-27-7?

Those two lines are from your new kernel (one for normal boot and one for recovery mode).  It's a good idea to leave an older kernel on your machine just in case there is something wrong with the new one.  BUT if you are sure everything is fine with the latest one, you can use synaptic to remove the old one, kernel 2-6-27-7.

---

