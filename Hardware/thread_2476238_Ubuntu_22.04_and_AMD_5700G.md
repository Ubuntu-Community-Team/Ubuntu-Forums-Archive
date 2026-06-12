---
title: "Ubuntu 22.04 and AMD 5700G"
date: 2022-06-20
forum: Hardware
---

### Post by agentl074 on 2022-06-20
Has anyone tested the AMD Ryzen 7 5700G (or the Ryzen 5 5600G for that matter) on Ubuntu 22.04? In looking at the 5.15 kernel, all of the newer Ryzen chips with integrated graphics should be fairly well supported, but I am not completely sure.

---

### Post by TheFu on 2022-06-20
Not running 22.04, but I do have 5.11.x kernels on my Ryzen 5600G and an Asus B450 motherboard.  I didn't want to deal with B550 Intel 2.5Gbps NIC issues and didn't care about pcie 4-gen.
It runs a few virtual machines and media center stuff.  The only reason I put 5.11 onto it was for the iGPU support.  I was happy with prior kernels 4.15+, except the F/LOSS iGPU driver was running poorly.

The system is due for a fresh install, but I won't subject myself to 22.04. It is just too new for my tastes.

---

