---
title: "Seperate hard drives"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by LUIWOMBAT on 2009-05-14
I'm installing a second hard drive for a friend of mine on his computer.He wants windows vista in one hard drive  and linux in  the other.Does anyone know how to do this.I will appreciate any help.Thank you.

---

### Post by alphacrucis2 on 2009-05-14
> **LUIWOMBAT said:**
> I'm installing a second hard drive for a friend of mine on his computer.He wants windows vista in one hard drive  and linux in  the other.Does anyone know how to do this.I will appreciate any help.Thank you.

Install Windows first on one drive. Then install Linux on the other. If you are installing UBUNTU then select manual partitioning and put the linux partitions (eg ext3 or ext4) on the second disk. It is a good idea to divide the second disk into two partitions plus maybe a swap partition. One that mounts as the root file system / and the second partition that mounts as /home. You don't specify a mount point for the swap partition.

---

### Post by rativid on 2009-05-14
Check out your bios boot menu, they must have choice which device use to boot. Then just install Win on one hard drive and Ubuntu on another. And after installation both systems you should be able to choose what system to boot from bios boot menu.

---

### Post by LUIWOMBAT on 2009-05-14
I thank you both for giving me good info on how to do this.):P:D

---

