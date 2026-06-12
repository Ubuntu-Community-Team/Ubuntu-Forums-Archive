---
title: "Brightside (screen actions) not active on startup since upgrade"
date: 2008-11-13
forum: General Help
---

### Post by sambody on 2008-11-13
Hi everyone.

I'm using Brightside - which lets me have "screen actions" (or "hot corners"): starting applications or running commands just by placing my mouse cursor in a corner of my screen (eg. start Firefox, Nautilus). Works great.

The problem: since I upgraded to Ubuntu from 8.04 8.10, the screen actions don't work anymore when I start up the computer. 

Workaround: The simple act of going to System>Preferences>Screen actions suddenly the sreen actions work again. But when I reboot my computer, they are not active anymore. Not very practical. How do I make the screen actions work normally at computer startup automatically, like it worked on Ubuntu 8.04 ?

Thank you.

---

### Post by RolandFlagg on 2009-10-05
bump, i'm experiencing this problem too. Anyone with solutions?

---

### Post by karenyyng on 2009-10-07
You have to configure brightside to be launched on start up. 

Read the part on configuring start up programs: [http://thedailyubuntu.blogspot.com/2008/01/brightside-screen-corner-actions-and.html](http://thedailyubuntu.blogspot.com/2008/01/brightside-screen-corner-actions-and.html)

---

### Post by alphaamanitin on 2009-11-10
> **karenyyng said:**
> You have to configure brightside to be launched on start up. 

Read the part on configuring start up programs: [http://thedailyubuntu.blogspot.com/2008/01/brightside-screen-corner-actions-and.html](http://thedailyubuntu.blogspot.com/2008/01/brightside-screen-corner-actions-and.html)


Will this work in Ubuntu 9.10?  I installed Brightside, looked like it installed correctly, but I never found the new category in my preferences as I was supposed to, and I couldn't figure out any way to get it to run.  Reading the Read-Me did not help.  I think this is an awesome idea.  I really just want to be able to open all the windows at once and choose between them like you can in Macs.  I am not sure if Brightside does this but I am sure I can find other uses that would be just at good.

Thanks.

---

### Post by troll1602 on 2009-12-12
Okay, I had the same problem and I think I found a solution. First add brightside to the starting applications as the link above describes. Then open up terminal and type:
```

brightside-properties

```
This should open up configuration window. Then just setup your corner actions.

---

