---
title: "nVidia proprietary drivers."
date: 2019-03-08
forum: Hardware
---

### Post by stepheny on 2019-03-08
I have a GeForce GT540M GPU and use it with Nouveaux because of problems with nVidia proprietary drivers in the past.

I am looking to buy a new laptop with a modern nVidia GPU such as the NVIDIA GeForce GTX 1060 6GB (GDDR5) and would like to know if anyone has experienced problems using modern nVidia proprietary drivers under Ubuntu 18.10.

---

### Post by ookgluk32 on 2019-03-08
I have. Whenever I switch to NVIDIA proprietary driver, after restarting, it endlessly hangs at "[OK] Starting GNOME Display Manager." I am using Ubuntu 18.10 with a Quadro 1000M.

---

### Post by Yellow Pasque on 2019-03-08
> **ookgluk32 said:**
> I have. Whenever I switch to NVIDIA proprietary driver, after restarting, it endlessly hangs at "[OK] Starting GNOME Display Manager." I am using Ubuntu 18.10 with a Quadro 1000M.

Maybe this: [https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1798790](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1798790)

---

### Post by CatKiller on 2019-03-08
For modern GPUs on the desktop, Nvidia cards are great. I would not buy a laptop with Nvidia graphics.

Mixed-mode graphics are just a pain. Intel is the best supported, most trouble-free, way to go for laptop graphics. Go for an AMD APU if you want a bit more performance.

---

