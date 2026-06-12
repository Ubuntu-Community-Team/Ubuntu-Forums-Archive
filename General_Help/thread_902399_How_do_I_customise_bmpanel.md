---
title: "How do I customise bmpanel?"
date: 2008-08-27
forum: General Help
---

### Post by Alucard-sama on 2008-08-27
Okay been searching for a good lightweight panel for quite some time now but never being quite satisfied with the better known ones [fbpanel, pypanel, lxpanel, etc] and I happened to stumble across one called "bmpanel". 
Only problem is the documentation sucks balls [unless I've somehow missed the page that gives you all the prerequisite knowledge necessary for the few tutorials I did find] and I have no idea how to theme it. And since the website proudly proclaims that there are no configuration files and the only way to customise it is through themes this becomes a bit of an issue.
I seriously have no clue how to theme this thing. Anybody got any idea?
If not could somebody at least point me in the direction of some more lightweight panels.

---

### Post by mishathegoat on 2008-12-14
[Bump]

Same here.. There's almost no documentation.. I can't find how to configure/theme bmpanel

---

### Post by celtic426 on 2008-12-15
SAME, please help on this, thanks.

---

### Post by maxol on 2009-01-09
Same here. Want to use it but completely stumped by the lack of documentation.

---

### Post by Terraman on 2009-01-17
Same here! Does anyone know where we can find a good guide for this thread?

---

### Post by CC_Joe on 2009-03-12
Better late then never:


You need to create the folder ~/.bmpanel/themes

Then you need to download a theme file (there are some [here]("http://nsf.110mb.com/bmpanel/")) and extract it to the folder above. Then run ```
bmpanel theme
```



So for instance you can download arch.tar.gz from that site and extract it to home/joe/.bmpanel/themes and then type "bmpanel arch" in a terminal.

*arch's theme, btw, requires a compositing engine (ie xcompmgr) to run with transparency, FYI.

---

### Post by Alucard-sama on 2009-03-16
Thanks CC_Joe, worked perfectly. =]

---

### Post by CC_Joe on 2009-03-18
Not a problem. I was vexed by the lack of documentation too, until I stumbled across the solution in the Arch forum. 

It's a nice little panel, but I've already moved on to tint. I swear, I change panels almost as often as wallpaper =)

---

