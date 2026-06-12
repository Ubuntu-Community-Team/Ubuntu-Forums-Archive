---
title: "Should I upgrade the kernel"
date: 2005-12-31
forum: Installation &amp; Upgrades
---

### Post by Mikeynewbie on 2005-12-31
Hey all was wondering if I should upgrade my kernel to 686.  I am running breezy 386 i have an amd athlon xp processor and 1 gig ram.  I have noticed since upgrading the ram that the system monitor says i am using more ram than what is accounted for in the running processes didn't know if upgrading the kernel would make any difference.

Also are there any benefits to upgrading the kernel.

---

### Post by Perfect Storm on 2005-12-31
On an amd proccessor you properly want the k7 kernel, and yes you will see a diffrence. It will take the advance of your 1gb ram which i386 can't


```

sudo apt-get install linux-k7
```

reboot

---

