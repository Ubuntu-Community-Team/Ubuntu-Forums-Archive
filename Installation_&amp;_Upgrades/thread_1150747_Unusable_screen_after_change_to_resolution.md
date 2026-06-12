---
title: "Unusable screen after change to resolution"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by currywuss on 2009-05-06
I updated to Jaunty the other day, all seemed well at the time but then I restarted the laptop. I found various problems, including not being able to see the bottom bar/windows that were minimized 'disappearing'. I thought this might be a resolution issue, so I changed this, only to wish I hadn't.... :oops:

The screen is now divided vertically into four sections, so that every icon on the desktop/top bar appear four times. I can just about make out what the icons are, but I can't read the results of any commands I type into a terminal window. ](*,) So I guess I need to be able to sort this out in the recovery mode menu? Via the root shell promt. Oh dear. Any ideas welcome.

---

### Post by Kareeser on 2009-05-06
Press Ctrl-Alt-F1 to drop down into a terminal prompt.

Log in, and try the command "xrandr". It'll probe your video outputs and mark the ideal resolution with a "+" next to the mode.

Change your resolution with the command:
```
xrandr --output VGA --mode "1280x768"
```
But replace the resolution with the proper one. Also make sure "VGA" is the name of your device. It varies from computer to computer.

---

### Post by currywuss on 2009-05-06
Thanks. The problem is, I can't read what the terminal says, my screen (after typing xrandr into a terminal) looks like this:
BTW I'm using a different machine to write at the moment.

---

### Post by Mark Phelps on 2009-05-07
The suggestion of CTRL-Alt-F1 will drop you into a text-mode console, not an xterm window.  Try what was suggested.

---

