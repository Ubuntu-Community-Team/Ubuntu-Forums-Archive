---
title: "Hd Radeon 5770 Help Plz"
date: 2010-11-04
forum: Hardware
---

### Post by kulocka on 2010-11-04
my current setup up is a dual boot of windows 7 and ubuntu 10.10..i have amd phenom 2 x3 720 BE

In ubuntu my Hd Radeon will not install properly, there have been two instances where playing around with the Flgrx seems to work, but then stops working as soon as i log on or off. At the time i cant get it to work. I have installed it through ubuntu with system - administration - hardware, ive done that and it didnt work. Ive also installed them from the Ati website as well downloading the latest drivers and CCC. that got me close. and also i used this link 

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)  

this link has helped also the couple times i got it to work properly. doing the remove and reinstall of ati.
When it works properly of course i can use all the effects. But most of the time after installing these, i get the resolution i need, but everything is extremely choppy and i cannot enable any visual effects. Everytime i move a window around its very slow and choppy. also scrolling in web pages is choppy.............

Plz help hopefully theres a simple fix, or maybe a tutorial anyone can link me to, that would be awesome ..thank a lot guys
Kulocka

---

### Post by urosg3 on 2010-11-04
Try in Terminal
```
sudo aticonfig --inital -f
```

in order to generate xorg.conf file and reboot in order to force OS to using it, and try to enable effects.

---

