---
title: "New gfx card, black screen"
date: 2005-05-13
forum: Hardware &amp; Laptops
---

### Post by apoc on 2005-05-13
A few weeks ago my old nvidia card died on me...

so I switched to mainboard grafics and all was good in windows..
then I needed something from my linux formated drive, and I booted ubuntu.. it could not load gnome, but I got a login screen. and luckely I could get the stuff I needed at the time..

now I have my new nvida card and now I just get a black screen.

anyone know how to fix this, I'm along way from doing anything usefull from comandline alone unless I have a howto printed or open on the laptop..  :?

---

### Post by cowbud on 2005-05-13
I had the same issue with an older version of the Nvidia driver. Are you running the latest? 

If so I am stumped with the amount of information. 

If you aren't update and see if the issue persists.

---

### Post by apoc on 2005-05-13
I don't think its the latest, I installed everything a few months ago..

So I plug the screen to the motherboard grafic, then

sudo apt-get install nvidia ?

---

### Post by cowbud on 2005-05-13
Are you running hoary or are you running warty? 

If you are running warty you should read: 

[http://www.ubuntulinux.org/wiki/UpgradingFromWartyWarthogToHoaryHedgehog](http://www.ubuntulinux.org/wiki/UpgradingFromWartyWarthogToHoaryHedgehog)

and do that. 

Warty does not have the latest drivers.

If you are running Hoary just 

apt-get update 

apt-get upgrade 

and it should update you

---

