---
title: "enabling visual effects?"
date: 2008-08-23
forum: General Help
---

### Post by shresthanator on 2008-08-23
I cannot enable the visual effects on my desktop. Im using a very good graphics card, Ati's HD 4870. Note that I was not able to install the drivers for the card. Im new to ubuntu, so can someone could please tell me how to install the drivers (on the box of the card it says that its certified for vista, so does that mean it can't be installed on ubuntu?) or how to enable the visual effects?

---

### Post by fenian on 2008-08-23
Use [Envy]("http://albertomilone.com/envyngfaq.html") to install the ATI drivers,open a terminal and enter...

> sudo apt-get install envyng-gtk

if you are using kubuntu use this command instead...

> sudo apt-get install envyng-qt

You can launch Envy from the menu Applications>System Tools>EnvyNG
Select ATI and Automatic Hardware Detection
Envy should then install the pproper driver.

---

