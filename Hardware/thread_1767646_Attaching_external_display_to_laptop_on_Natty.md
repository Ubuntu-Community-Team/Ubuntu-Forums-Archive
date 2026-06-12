---
title: "Attaching external display to laptop on Natty"
date: 2011-05-26
forum: Hardware
---

### Post by greencookie on 2011-05-26
I usually connect my Thinkpad with an external screen and keyboard (when I'm at my desk) and I ran into a problem with Natty 64.

I let my laptop boot and once logged in, I connect my VGA cable and see my monitor come to life. Great!

Now I want to turn off my laptop's internal monitor so that my mouse is confined to just my external monitor. Problems arise. 

When I fire up 'Monitors' from the settings, I see that it lists both my internal and external monitors in their correct resolutions. But when I check my internal (primary) monitor to off, everything goes blank on both screens. There is an erratic flicker on my external drive. I usually have to reboot to restore display to my laptop (even disconnecting the VGA cable wont bring it back on).

I have found a temporary solution to this problem, but I do want to know if there's a better way.

So I boot up my laptop and attach VGA cable. At this point it sometimes gets the resolution on my ext monitor correct and extends it, or it mirrors it at the internal monitor's resolution.

My fix is to fire up terminal, and execute 
```
xrandr --output LVDS1 --off
``` which switches the Laptop screen off and puts all the stuff that was there onto my external monitor :P. (if you execute just 'xrandr' it will list your monitor names). When its time to disconnect, I re-type that xrandr command but with 'auto' instead of 'off'. 

This works fine for me, but I'm wondering if anyone has a less troublesome solution.

Thanks!

---

### Post by svast on 2011-05-31
what is your graphic card, and which driver are you using? Do you have integrated and/or discrete card?

---

