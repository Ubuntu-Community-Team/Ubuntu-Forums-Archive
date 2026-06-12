---
title: "[SOLVED] no gui, vesa error"
date: 2008-07-18
forum: General Help
---

### Post by leetrefz on 2008-07-18
shocked by the increase in size of xubuntu 8.04, I tried to use deboprphan as much as possible. I removed something necessary to run the gui. When I do startx now, it says something like error, can't find vesa and driver. I left a driver for Via Unicrome which should be ok i think, unless it needs other drivers in conjunction. I thought atp-get install vesa might magically work, but it said it couldn't find module. please help! People are scoffing at my use of Linux! 

And whatever I took away was obviously no orphaned package, so shame on you, deborphan.

---

### Post by jimv on 2008-07-18
sudo apt-get install xserver-xorg-video-vesa

---

