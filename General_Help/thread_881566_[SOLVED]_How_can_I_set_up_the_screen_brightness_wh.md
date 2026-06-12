---
title: "[SOLVED] How can I set up the screen brightness when runningon battery"
date: 2008-08-06
forum: General Help
---

### Post by Friccy on 2008-08-06
Hi!

I have installed the Hardy on a new HP laptop and when I am running it on battery, the screen has not enough brightness. After several minutes of working it can be very painful for my eyes.
I have tried to adjust it from the Power Management (like in Windows), but there is no way to do it from there.
How can I adjust the brightness? 
Thanks!

---

### Post by pro003 on 2008-08-06
try this:

```
sudo aptitude update
```

```
sudo aptitude install ddccontrol
```

also there is a gddccontrol:

```
sudo aptitude install gddccontrol
```


hpe it help... let me know

---

### Post by Friccy on 2008-08-06
Hello!
I have tried what you have suggested, but nothing happened.
Can't see anything that lets me control or setup the brightness.
The display of the laptop is still "dim" like it is on power saving.
Whit the gddccontrol, the Monitor Settings apeared but was unable to detect my display.

---

### Post by pro003 on 2008-08-06
What can I say? Get a new laptop?! 

Sorry.

---

### Post by Friccy on 2008-08-06
Hope not to!
This one is brand new.
Probably it's just a setting problem and will find out!

---

### Post by TheCarNinja on 2008-08-06
Friccy: (I'm assuming Gnome) Right click on your panel and click add to panel. Now select the brightness applet. Now you can control your brightness.

---

### Post by pro003 on 2008-08-06
> **Friccy said:**
> Hope not to!
This one is brand new.
Probably it's just a setting problem and will find out!

I missed that part somehow. How about ms windows? Do you have it installed and is there too problem with the brightness?

---

### Post by Friccy on 2008-08-07
> **pro003 said:**
> I missed that part somehow. How about ms windows? Do you have it installed and is there too problem with the brightness?

Yes, the laptop came with installed Vista. But I have no problem with it (I mean with the brightness).
I can adjust now the brightness with the applet, but have to do it every time I start the laptop.

---

### Post by sayakb on 2008-08-07
Press Alt+F2 and type in [B]gconf_editor
[/B]Navigate to **/apps/gnome-power-manager/backlight **and change the brightness_battery and idle_brightness values and see if it works.

---

