---
title: "Kubuntu 20.04 Freezes AMD Ryzen 5 1600"
date: 2020-05-11
forum: Hardware
---

### Post by lazy-coyote on 2020-05-11
Hi there. I've got intermittent freezes on my Kubuntu 20.04 desktop. When they happen, my DE just freezes, I cannot move mouse pointer or do Alt-Ctrl-F to go to a console.
Could you help me to find out where I should dig into to solve this issue?
I had these freezes for about a year using Debian 10 with Linux 4.19 and Cinnamon DE, and now I'm using Kubuntu's default 5.4.0 kernel.
When I switched from Cinnamon to KDE on Debian, I noticed that I'm getting these freezes more frequently. And the same is now, when I'm on Kubuntu, I get them more frequently.

My hardware is as follows:

[LIST]
[*]AMD Ryzen 5 1600
[*]Motherboard: Asus Prime A320M-K
[*]RAM: 2x A-Data XPG Flame 8GB set to 2400 MHz
[*]Video: Nvidia GeForce GT 1030 with proprietary driver
[*]2x SSD: Samsung SSD 860 EVO 250GB, Samsung SSD 850 120 GB
[/LIST]

**UPD**. I don't think that it can be a overheating problem. I have a Windows install in a dualboot and play games, these frezes never happened during that time.

---

### Post by CelticWarrior on 2020-05-11
Welcome.

First thing to do is to update UEFI and SSD's firmware even if everything seems to work fine in Windows.
And please describe which Nvidia driver are you using and how was it installed?

---

### Post by lazy-coyote on 2020-05-11
Hello, thanks for reply. I'm using  ```
nvidia-driver-440
``` which I've downloaded from official repos

---

### Post by CelticWarrior on 2020-05-11
> **lazy-coyote said:**
> Hello, thanks for reply. I'm using  ```
nvidia-driver-440
``` which I've downloaded from official repos

Have you used command line or Additional -or- instead downloaded from Nvidia?

---

### Post by lazy-coyote on 2020-05-11
I've used the command line way through apt

---

### Post by CelticWarrior on 2020-05-11
Should be fine then.
Firmware updates, as mentioned before, are often needed regardless of the correct drivers version and installation.

---

