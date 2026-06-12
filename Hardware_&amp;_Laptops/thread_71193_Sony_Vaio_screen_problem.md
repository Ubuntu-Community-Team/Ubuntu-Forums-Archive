---
title: "Sony Vaio screen problem"
date: 2005-10-02
forum: Hardware &amp; Laptops
---

### Post by i-tech on 2005-10-02
Hello 
in some threads i noticed that people has the same problem with me. When using  ubuntu screen corrupts and you have to relog to get rid of it. Anything else can be done? 
Thanx

---

### Post by daglta on 2005-10-14
Yes, install the restricted nvidia driver.   It works a lot better at least with the newer nvidia device that's present in the Sony VAIOs.   To use it, go into synaptic and search for 'restricted'.   You should see the restricted linux kernels module - load the one for your CPU.   You don't want the legacy module - you want the one that doesn't say it's the legacy drivers module.

Once you've installed that, hack /etc/X11/xorg.conf: instead of the "nv" driver, you want the "nvidia" driver.

Best of luck!

---

### Post by daglta on 2005-10-14
By the way, with the "nv" driver, if you change the screen resolution and change it back, it'll clear up the snow for a while.

---

### Post by i-tech on 2005-10-14
Great thanx!
but with the restricted driver it corrupts again? but not that often?

---

