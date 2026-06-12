---
title: "Screen is to smal........"
date: 2006-01-10
forum: Hardware &amp; Laptops
---

### Post by pinkpanther_bc on 2006-01-10
[FONT="System"][/FONT]
Hello I am a new ubuntu user, have installed it (brezzy B) on 2 laptops and one tower.

It is working fine, untill i to day installed it on my nighbours old laptop.

The problem is that the laptop has a 12inch screen, but i can only see it as a 8 inch screen.(there is a 2.5 inche black boarder around)

How do i fix this problem...thanx

---

### Post by Qrk on 2006-01-10
The easy way is to go to System-->Preferences-->Screen Resolution 

But most likely there won't be a higher resolution listed in the drop down menu.

If that is the case, fire up a terminal and type:

```
sudo dpkg-reconfigure xserver-xorg
```

This will take you through a set of steps. The first step is choosing a driver. The most probable reason the resolution wasn't set right automatically is because Ubuntu chose the wrong driver by default. Change the driver on the first screen.

Depending on your graphics card, there are many choices. If you have an nvidia card, read the guide on installing the nvidia-glx (its in Help-->5.10 starter guide) and then reconfigure x.org, choosing "nvidia." 

Others to try are vga and vesa, but they won't have great performance

---

### Post by pinkpanther_bc on 2006-01-12
thanx for your help..got it working now

---

