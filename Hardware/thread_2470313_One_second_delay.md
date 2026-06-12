---
title: "One second delay"
date: 2021-12-25
forum: Hardware
---

### Post by triplemaya on 2021-12-25
New install of ubuntu mate 20.04
install goes fine

PROBLEM

When laptop is connected with Ultra slim docking station, key presses and mouse clicks take about one second to register. So the system is unusable.
Mouse movement is fine
(These are key presses and mouse clicks on the laptop itself, not through the dock.)

This problem only exists on my HP Elitebook 850 G1 which is an i7 with Radeon HD 8750M grapics. Elitebook i5 with only intel graphics has no problem with 20.04. 

Solution is to start with a working ubuntu mate 18.04 installation which has no problem. 

Run 
sudo apt-mark hold xserver-xorg-core 

Hope this helps someone. It drove me nuts!

---

