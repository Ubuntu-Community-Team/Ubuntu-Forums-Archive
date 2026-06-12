---
title: "lenovo T400 heating up under load and shutshown"
date: 2010-12-25
forum: Hardware
---

### Post by abeep on 2010-12-25
hi, i am  using lenovo T400 laptop dual boot with Win-XP-32bit and Ubuntu-32bit 10.10(kernel Linux 2.6.35-24-generic-pae)
The problem is when i run stress load intensive process ,
the laptop gets heated and suddenly shuts down, and the whole work gets lost.
But with XP things work absolutely fine and have no heating issues when ran the same processes.
I am struggling to get any solution for this problem.
Any workarounds  or recommendation would be of great help, I don't want to give up ubuntu which I love, because of this reason

Thanks
abee

---

### Post by abeep on 2010-12-25
i am consistently able to reproduce the problem when i run the stress test
stress --cpu 16 --vm 2 --vm-bytes 128M --timeout 1000s
along with that if start eclipse or jboss server it goes down abruptly

---

