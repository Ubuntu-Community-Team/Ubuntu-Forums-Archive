---
title: "Help dim laptop screen"
date: 2008-11-30
forum: General Help
---

### Post by steve101101 on 2008-11-30
I cannot figure out how to dim my laptop's screen. I have a sony vaio VGN CR120E and the dim and brighten keys on the keyboard don't seem to work as they do in windows. Is there a way to fix these keys or a program that will do this. THanks for all the help.

---

### Post by blackened on 2008-11-30
Have you tried switching your backlight control to native or combination? This seems to work well on Sony laptops.

```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```

This won't last through a reboot, but you can add a script to session manager to check whether or not it's set. Let me know if the command works and I'll whip you up a script. Try setting it to native first, though setting it to combination seems to work better for me.

---

### Post by b3n0 on 2008-11-30
I'm using a laptop as well. To controll the brightness use 'fn + F8' for brighter and 'fn + F7' to dim it down. If you haven't tried it yet, well its simpler than doing it through the terminal. I think the shortcut on the Sony laptops are 'fn + F5' to dim the display.
You should find the fn key between the super and the left ctrl key.

---

### Post by blackened on 2008-11-30
> **b3n0 said:**
> I'm using a laptop as well. To controll the brightness use 'fn + F8' for brighter and 'fn + F7' to dim it down. If you haven't tried it yet, well its simpler than doing it through the terminal. I think the shortcut on the Sony laptops are 'fn + F5' to dim the display.
You should find the fn key between the super and the left ctrl key.

He knows where the keys are, just that they don't work like they should.

---

### Post by b3n0 on 2008-11-30
You could go system > preferences > keyboard shortcuts and re-assign the shortcut keys. When I upgraded to 8.10 I had a simalar problem but with my volume controls. Doing this fixed it for me. :D

---

### Post by steve101101 on 2008-11-30
> **b3n0 said:**
> You could go system > preferences > keyboard shortcuts and re-assign the shortcut keys. When I upgraded to 8.10 I had a simalar problem but with my volume controls. Doing this fixed it for me. :D

i cant find the section in the keyboard shortcuts that dims / brighrtens the screen. where is it?

---

### Post by steve101101 on 2008-11-30
> **blackened said:**
> Have you tried switching your backlight control to native or combination? This seems to work well on Sony laptops.

```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```

This won't last through a reboot, but you can add a script to session manager to check whether or not it's set. Let me know if the command works and I'll whip you up a script. Try setting it to native first, though setting it to combination seems to work better for me.

ran that in the terminal with both native and combination and neither worked. Any other ideals.

---

### Post by b3n0 on 2008-11-30
> **steve101101 said:**
> i cant find the section in the keyboard shortcuts that dims / brighrtens the screen. where is it?

Sorry mate, that was just an idea I had while I was on a train. I sent it from my phone. Now I'm at my computer I can see that there isn't an option for that. :S sorry buddy my bad.

---

### Post by steve101101 on 2008-11-30
> **b3n0 said:**
> Sorry mate, that was just an idea I had while I was on a train. I sent it from my phone. Now I'm at my computer I can see that there isn't an option for that. :S sorry buddy my bad.

its all good. I installed xbacklight from the synaptic package manager and that works. Can anyone create a program where I can just type a value into a box to change the brightness when i click on an icon. I can program in C++,C#, and basic but not sure how to do that. THanks for any help.

---

### Post by steve101101 on 2008-11-30
Right now I have two buttons on my panel. One increases Brightness by 10% the other deccreases Brightness by 10%. I think these will be pretty good.

---

### Post by fragos on 2008-11-30
You might try <Fn><up-arrow> or <down-arrow>.

---

### Post by hihihi on 2008-12-11
for those who happen to have a sony VAIO FZ or with an Nvidia-card in it, try this how to:

[http://ubuntuforums.org/showthread.php?t=1004568&highlight=Sony+FZ+brightness](http://ubuntuforums.org/showthread.php?t=1004568&highlight=Sony+FZ+brightness)

works very well on mine!
byebye

---

### Post by steve101101 on 2008-12-11
> **fragos said:**
> You might try <Fn><up-arrow> or <down-arrow>.

okay ill have to try that. thanks.

---

### Post by steve101101 on 2008-12-11
doesn't work. any other ideals.

---

### Post by blackened on 2008-12-12
You might also try xbacklight. Don't remember whether or not it's installed by default, but you can get it from the repos. Use it like:

```
xbacklight -set 50
```

will give you 50% brightness. You could make a couple scripts with hotkeys if it works.

---

