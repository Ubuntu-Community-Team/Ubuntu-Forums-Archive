---
title: "Docking station working with Live CD, not with installed system"
date: 2012-01-23
forum: Hardware
---

### Post by pbean on 2012-01-23
Hello!

I've installed Ubuntu 11.10 on my laptop and most of it is working great. However, I have one small problem, which is kind of annoying.

When I put my laptop in my docking station, the attached screen is not detected at all. The rest is detected properly (ie. the charger, wired networking, keyboard and mouse). The Display Settings just shows one 'Unknown Display'.

However, when I boot from the Live CD, it detects the external display normally. In addition, it also detects the laptop's own display (listed as 'Unknown Display' in the installed system). In fact, the Live CD detects it immediately when I plug it in. With the Display Settings pane open, I first see my laptop's display (AU Optronics) and as soon as I plug it in, the external display pops up there and the screen is extended to the display.

This is rather annoying, because as my day-to-day work flow I really want to put my laptop in and take my laptop out of my docking station occasionally.

As a side note, my desktop PC had one display attached and when I attached a second, it recognized it without problems.

The laptop is a Dell Latitude E6410. As far as I can see, the docking station doesn't have a model number, but it's a Dell branded, fully compatible docking station (it works with Windows, and as noted above, works with the Live CD).

Any suggestions? :)

---

### Post by Althorax on 2012-03-21
I have the exact same issue.  Can someone provide some feedback please?

---

### Post by Althorax on 2012-03-21
So, I figured it out.  You need to modify the "Power Management" not to hibernate when the lid is closed and then you need to have it detect the displays once you are on the docking station.  I chose to "Mirror" the displays.  

As a side note, I had to lift the lid of my laptop open slightly to get the display to register until the process was completed.

Works like I would expect it to now!

---

