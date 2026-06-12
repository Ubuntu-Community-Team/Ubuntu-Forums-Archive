---
title: "System monitor applet or something like this?"
date: 2009-05-03
forum: Hardware
---

### Post by VictorR on 2009-05-03
Can anybody suggest how to get System Monitor applet, or similar on the screen for Netbook mode? I used to have GKRellM on my desktop, but it has 22" display. For 7" EEE PC screen System Monitor on the taskbar with CPU and Network graphs would be sufficient, but I don't see any ways to get it there.

Thanks for any help.

---

### Post by SLEEPER_V on 2009-05-03
screenlets are what you are looking for.  Go into synaptic and type in screenlets in the search box.  They have several different system monitors

---

### Post by hansdown on 2009-05-03
Hi VictorR.

Right-click an empty space in the top toolbar.

Click add to panel.

Scroll down to system monitor, and click add.

If you want more, look in system> administration> synaptic package manager.

---

### Post by VictorR on 2009-05-03
Thanks guys, but I am asking about Ubuntu Netbook Remix in its Netbook mode. I don't want to occupy any place on a 7 inch screen except a small part of the taskbar.
To hansdown: this is a standard way to add an applet, but it does not work for UNR.

Thanks anyway. Any more ideas?

---

### Post by mfsnoeij on 2009-05-15
I struggled with this issue too for an hour, because I wanted to add some sensor monitoring applets to the panel. The problem is that netbook remix is using the 'window picker' applet to merge the title bar of any program with the top toolbar, thus saving space. This applet automatically fills up any empty space left in the toolbar, so you cannot click on an empty part of the toolbar to add new applets. To solve this issue, do the following:

1) remove the 'window-picker' applet. To do this, close all open programs, then right click on it and say remove. Note that if there are no programs open, this applet is basically invisible, but it is still there!

2) Add whatever applet you want in the taskbar, by clicking right again and say 'add to panel', as mentioned in previous answers.

3) After adding the applets you want, add the 'window-picker' applet in the same way as above, then move it all the way to the left so it lines up.

BTW, NBR by default has the clock not only display time but also day of the week and date - quite wasteful. you can change this by clicking right of it, then 'preferences'. Saves a lot of space to add some cool applets

---

### Post by VictorR on 2009-05-15
Thanks, mfsnoeij,

That was very helpful, your trick works perfectly.

> BTW, NBR by default has the clock not only display time but also day of the week and date - quite wasteful. you can change this by clicking right of it, then 'preferences'. Saves a lot of space to add some cool applets

I set the clock applet to show time and weather, the rest is visible when the mouse hovers above it.

Thanks again.

---

