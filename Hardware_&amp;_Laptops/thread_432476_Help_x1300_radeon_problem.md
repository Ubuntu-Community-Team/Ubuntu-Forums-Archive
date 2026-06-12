---
title: "Help x1300 radeon problem"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by xenosyn on 2007-05-04
ok well the story goes like this I installed ubuntu 7.04 worked fine got my internet to work and then I wanted to get my ati X1300 radeon visiontec video card so without looking into anything about this matter I explore my desktop I find this menu under administrative I think or something like that called restricted drivers or something sooo I open it up and what do you know there is something saying something about drivers for my ati video card 
so I double click it and it installs like any other package under the package manager it installs with success and tells me I need to restart my computer for changes to take effect so I do  when it starts up the ubuntu start up splash screen pops up and loads as normal after loading it goes to a blank black screen or as people refer it to the black screen of death so as you can see im a newbie and have no clue on what to do. I'm aware that there are many topics like this one that offer things to do I tried a couple of them commands there and there and they didnt help none of the topics I found show my position soo plz help me if you can.

---

### Post by qrdl on 2007-05-04
Can you post your Xorg.0.log (can be found in /var/log directory)?

---

### Post by xenosyn on 2007-05-04
ya I will later I got to go to school now

ok here is the file

---

### Post by xenosyn on 2007-05-06
*bump*

---

### Post by eggdeng on 2007-05-06
Sounds like you updated from the bundled ati driver to the proprietary fglrx driver. To revert to using the original driver, type
```
sudo nano /etc/X11/xorg.conf
``` in a terminal. Edit the line ```
Driver      "fglrx"
``` to read ```
Driver      "ati"
```
Hit Ctrl+X, then Y to save changes. Reboot.

---

### Post by xenosyn on 2007-05-06
cool I'll go try that out and telll you the results

---

