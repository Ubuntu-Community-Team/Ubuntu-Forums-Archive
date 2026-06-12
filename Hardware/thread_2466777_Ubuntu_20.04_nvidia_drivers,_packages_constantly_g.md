---
title: "Ubuntu 20.04 nvidia drivers, packages constantly getting stuck in held back"
date: 2021-09-05
forum: Hardware
---

### Post by spacecats on 2021-09-05
Hello,

I'm wanting to know if anyone else running Ubuntu 20.04 using the proprietary Nvidia drivers is constantly getting video related packages randomly stuck in "held back" in apt? Mostly it's the driver packages that get stuck in held back. When the problem occurs, I'm normally able to fix it but the fix is very tedious. I've also tried completely reinstalling Ubuntu 20.04 but eventually I start getting the problems again. I'm using the following method to fix the problem: [https://askubuntu.com/questions/1278688/the-following-packages-have-been-kept-back-safe-to-force-install#comment2192385_1278688](https://askubuntu.com/questions/1278688/the-following-packages-have-been-kept-back-safe-to-force-install#comment2192385_1278688)

I'm also getting other video-related packages besides the drivers themselves stuck in held back, e.g. mesa-va-drivers mesa-va-drivers:i386 mesa-vdpau-drivers mesa-vdpau-drivers:i386.

I'm not doing a lot of crazy stuff with apt either, mainly a small amount of manual .deb package installation (e.g. zoom, Nvidia .deb files for Tensorflow).

Graphics card is a GTX 960.

---

### Post by mikewhatever on 2021-09-05
Nope, not me. 
Try "full-upgrade" instead of "upgrade":
> sudo apt full-upgrade

---

### Post by spacecats on 2021-09-05
Thanks. In my current state of the held back mesa packages I'm not able to upgrade them. I will try this for future upgrades.

---

