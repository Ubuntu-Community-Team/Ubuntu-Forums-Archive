---
title: "just for information"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by rudi009 on 2009-02-27
i've recently installed ubuntu and upgraded it.noe it's showing two ubuntus(different numbers in front of them) in the boot menu along with windows(duel boot).not a big problem but why two  ubuntus????

---

### Post by smani on 2009-02-27
There aren't to different versions of ubuntu, just two kernels. When you update the kernel, the old one is usually kept, though you can remove it with system-cleaner-gtk (sudo apt-get install it). Usually old kernels are kept in order to let you boot back into it if the new one does not work or has problems.

---

### Post by rudi009 on 2009-02-27
thanks.

---

### Post by wangsuda on 2009-02-27
> **smani said:**
> There aren't to different versions of ubuntu, just two kernels. When you update the kernel, the old one is usually kept, though you can remove it with system-cleaner-gtk (sudo apt-get install it). Usually old kernels are kept in order to let you boot back into it if the new one does not work or has problems.According to Synaptic, I have this. So how do I run it?

---

### Post by smani on 2009-02-27
> **wangsuda said:**
> According to Synaptic, I have this. So how do I run it?

System -> Administration -> Cruft remover or from terminal cruft-remover-gtk

Note: they have renamed the package in jaunty to computer-janitor-gtk, just to know for the future;)

---

