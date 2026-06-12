---
title: "Pentium Mobile - No cpu scaling in Lucid"
date: 2010-06-21
forum: Hardware
---

### Post by kpkeerthi on 2010-06-21
I'm stuck at 800Mhz in Lucid. Had this problem with Arch. Tried my luck with Lucid. No hope. 

For details on my configuration, please refer to the original bug I reported:
[https://bugs.archlinux.org/task/18901](https://bugs.archlinux.org/task/18901)

Please note: I tried with the cpu scaling applet. Although I could select a different governor or frequency from the applet, nothing changes (kernel does not seem to recognize the change). Indefinitely stuck at 800Mhz.

---

### Post by dino99 on 2010-06-21
i've not met this issue but thats let me thinking about a conflict between previous config settings and new kernel. The actual kernel(s) directly deals with powersaving: so better to remove/purge ALL the powersaving packages, install hwinfo, gconf-cleaner and bleachbit to clean the system, check that you dont use untrusted repo and reboot

---

### Post by kpkeerthi on 2010-06-23
Mmm... actually this is on a clean/fresh install of Lucid - all partitions new.

---

