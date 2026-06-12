---
title: "I have a new laptop, but can't figure out power settings."
date: 2008-07-04
forum: Hardware
---

### Post by kaldor on 2008-07-04
I have a new HP Pavilion dv2000. In vista, I can select power settings (extend battery life, etc)

I can't figure out how to in Ubuntu. I will be needing to bring my laptop around places, and I really don't want to use Vista. 

Any ideas?

---

### Post by sergiom99 on 2008-07-04
In Kubuntu, I can configure it by double-clicking over the battery icon.

---

### Post by kaldor on 2008-07-04
I'll try that out in a bit. I have KDE installed :)

Currently on vista :<

---

### Post by kaldor on 2008-07-05
Tried on both Gnome and KDE. Nothing useful. 

My situation is this: My laptop can only run about an hour on battery power. On vista, I can select it so that the battery power is extended, but the laptop performance is lower.

I want to be able to bring my laptop places without having to recharge it all the time.

---

### Post by sergiom99 on 2008-07-06
When you single-click on the battery icon, you get the power manager or something like that (my Kubuntu is in spanish) there you can choose your screen brightness when on battery and choose the CPU scaling policy. (both for AC and battery power)
And if you right-click the icon, you can also select your CPU policy:
Performance (full power), Dynamic or Powersave

good luck.

PS: HP recommends to drain your battery charge every 3 other months. I do it by setting 'Do nothing' in the forementioned place, under the battery section when it ask what to do when battery time fells under X mins.
I did it yesterday and it took 2.5 hr to poweroff with a full charge. I was only playing mp3s in Amarok and browsing this forum, nothing pretty power-intensive but a good time anyway.

---

### Post by ibuclaw on 2008-07-06
First, I advice strongly to recalibrate the battery.
My battery gained a good 50-100% extra life from it.

Run:
```
 gconftool-2 -t string -s /apps/gnome-power-manager/actions/critical_battery nothing
```
in the terminal, then close all apps and leave your Laptop on until it powers off. When you hit the power button, nothing should happed (because the battery is completely drained).

Now, recharge the battery for a good 2/3 hours to ensure that it is full.
And you should get a slightly better battery life (I went from 1hr 20mins to 2hr 30mins on a 6 cell battery life).

To set it back, run
```
 gconftool-2 -t string -s /apps/gnome-power-manager/actions/critical_battery shutdown
```

There are other tweaks and switches you can use, have a look around the Laptop Power Saving threads. (I managed to get 4 hours of life out of my battery).

I am in the middle of writing one myself currently, but I will be sure to post when I have it finalised.

[EDIT]
Oh, and what specific model is your laptop?
```
sudo lshw | head -n8
```
Paste the output of that.

Regards
Iain

---

