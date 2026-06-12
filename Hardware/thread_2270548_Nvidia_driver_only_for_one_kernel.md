---
title: "Nvidia driver only for one kernel"
date: 2015-03-23
forum: Hardware
---

### Post by radhakrishna12 on 2015-03-23
I keep trying out new kernels for my projects. I install in a traditional way -> make, make modules_install install.
The problem is I have installed nvidia proprietary driver with the default ubuntu kernel 3.16+. And I want to disable nvidia and use opensource nouveau only for new 4.0rc+ kernels while still making sure nvidia driver works when I boot 3.16 kernel.

How do I do that?

Thanks

---

### Post by Tsepo_Joshua on 2015-03-24
sudo apt-get purge nvidia-current to remove nvdia drivers

---

