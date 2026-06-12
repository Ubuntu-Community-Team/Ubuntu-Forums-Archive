---
title: "Nvidia Quadro FX 770M on Ubuntu 10.04 LTS beta 1"
date: 2010-03-24
forum: Hardware
---

### Post by petersohn on 2010-03-24
I have installed Lucid on a machine with said video card. It runs with the free driver well, but it doesn't support 3D acceleration. If I try any of the non-free drivers, it runs very slowly and doesn't work at full resolution (I have 1580x1050). I googled for it, and there seems to be a "nvidia-graphics-drivers-177" driver for Intrepid, which is not in Lucid.

Which driver should I use with this video card?

---

### Post by petersohn on 2010-03-25
bump

---

### Post by cascade9 on 2010-03-25
It should use the 190.53 drivers.

---

### Post by petersohn on 2010-03-25
How to install it?

---

### Post by cascade9 on 2010-03-25
System-> Administration-> Restricted Drivers Manager.

---

### Post by petersohn on 2010-03-25
I use KDE, and under the K-menu, there is System->Hardware drivers, but it doesn't start. Is this because this bug?
> Because of the new alternatives system used for nvidia driver packages, the nvidia installer from NVIDIA's website currently doesn't work.
Or is something else wrong?

---

