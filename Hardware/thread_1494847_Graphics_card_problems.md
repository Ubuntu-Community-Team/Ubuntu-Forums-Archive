---
title: "Graphics card problems"
date: 2010-05-27
forum: Hardware
---

### Post by aaycumi on 2010-05-27
Toshiba Qozmio G20, have just upgraded to ubuntu 10.04 a couple of days ago and tried all the available NVidia hardware drivers (Nvidia Go 6600) in the admin but all start in low-graphics mode. Is there any tools that will help locate problem or should I just go back to XP?

---

### Post by dino99 on 2010-05-27
sudo rm -f /etc/X11/xorg.conf

need: nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings

---

### Post by aaycumi on 2010-05-27
Okay, after restarting after doing what you said, I tried enabling desktop effects but it just went straight to hardware drivers and asked to install vers. 173 of the Nvidia drivers. I restarted after getting low-graphics mode again and typed the command you said again and no more low-graphics mode warnings. But it wont let me enable desktop effects. But the graphics driver does appear to at least be installed properly.

---

### Post by aaycumi on 2010-05-27
No luck in the end, if I dont type the command in the comp starts in low-graphics mode and the graphics card keeps giving too many faults. Oh well.

---

