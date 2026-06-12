---
title: "LightDM Freezes on Resume"
date: 2012-08-06
forum: Hardware
---

### Post by slc2015 on 2012-08-06
Hi,
I have an HP Pavilion G6 laptop on which I installed Ubuntu yesterday. When I put it to sleep and wake it back up, 70% of the time LightDM will freeze. The mouse moves, and I am able to switch to TTY1-6. I can get LightDM back by running:
```
sudo service lightdm --full-restart
```
I'll upload any needed logs or supply any other info needed.
Specs:
Intel® Core™ i3 CPU M 370 @ 2.40GHz
Intel® Ironlake Mobile  
4 GB RAM
320 GB HDD 
Ubuntu 12.04 Precise Pangolin 64 bit

---

### Post by apienk01 on 2012-08-08
Have you tried in Ctrl-Alt-F1 console:

> sudo service bluetooth restart

---

