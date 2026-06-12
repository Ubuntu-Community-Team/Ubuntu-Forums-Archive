---
title: "[SOLVED] problems with nvidia GeForce 5200"
date: 2005-05-18
forum: Hardware &amp; Laptops
---

### Post by arnieboy on 2005-05-18
Problems:
My comp hardware:
P4 3.0 GHz (hyperthreading on)
RAM: 1 GB
Motherboard: PM800-M2
Video Card: GeForce 5200 (128MB)

I installed Hoary 5.04 "server" (base system) from the CD because the full install was freezing. 
I installed gdm with apt.
After that I followed the instructions on [www.ubuntuguide.org](www.ubuntuguide.org) to install the nvidia driver. I also installed xserver-xorg package.
After I rebooted, It tried to start X server and showed the Nvidia logo everytime (it tried thrice) and failed and then tried to show me the log file but then it froze (as in cold freeze.. nothing working) and I would have to do a cold reboot (by pressing the reset button on my computer).
Thats the status right now. I used the Ubuntu CD and went into rescue mode and removed the xserver-xorg package and then rebooted. This time expectedly, it could not start X and then threw me into init 3, from which I can do everything but cannot start X.
Please help!

---

### Post by HellSpawn on 2005-05-18
Are you sure you don't have any other hardware problems??
You have to much freezing!!!

Try installing 6229 drivers from the nvidia website with the patches from nvforums!!!

---

### Post by arnieboy on 2005-05-18
any other ideas?

---

