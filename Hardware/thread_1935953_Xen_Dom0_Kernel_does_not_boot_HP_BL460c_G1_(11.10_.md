---
title: "Xen Dom0 Kernel does not boot HP BL460c G1 (11.10 and 12.04-beta1 - server edition)"
date: 2012-03-05
forum: Hardware
---

### Post by harenber on 2012-03-05
Dear all,

I have several HP Blades BL460c G1 which do not boot the new 3.x kernel introduced in 11.10. With 12.04-beta1 I can install the blade and the kernel boots, but after installing the Xen hypervisor and trying to boot the same kernel as Dom0, the problem re-appears. The error message looks like the screen shot attached.

I already tried several kernel options as described on some forums (esp. pcie_aspm=force), but nothing helped. The machine stays "un-bootable". Without Xen, 12.04-beta1 boots and I attached the dmesg (dmesg.txt.bz2) to this post. 

I used to run RHEL 5.x on that machines and these boot fine, however I want to switch as Ubuntu supports Xen out-of-the box. 

Maybe someone has a clue. Thanks a lot!

---

