---
title: "mouse not working at startup"
date: 2008-09-11
forum: Hardware
---

### Post by Trailriderdan on 2008-09-11
So when I boot into linux or windows (dual booting) the light on my mouse is on but it doesnt work. Replugging the mouse fixes the problem. Its a USB razer copperhead mouse and im running hardy heron version of ubunutu. This problem only occurs when ubuntu is installed and not when the only OS is windows. I was able to find a solution on the internet that involved adding a boot command but I forgot what it was and cant find what it is again. Although that solution only worked booting into ubuntu. Does anybody have a solution for this? Maybe even one for windows too?

---

### Post by Crafty Kisses on 2008-09-11
When you're at the login screen, do the following:
```
Cntrl+Alt+F1
```
Login from there, and after that do this:
```
lsusb
```
Look and see if your mouse is on that list.

---

### Post by Trailriderdan on 2008-09-11
nope but when i plug a different mouse in, that mouse does come up on the list. maybe time for a different mouse, or is there a fix?

---

### Post by arch0njw on 2009-02-28
> **Trailriderdan said:**
> nope but when i plug a different mouse in, that mouse does come up on the list. maybe time for a different mouse, or is there a fix?

Did you find a fix to this yet?  I have discovered that the copperhead is VERY power hungry.   You need to figure out the order of your USB ports on the bus and plug it into the "first" one -- or have it be on the "first one" compared to the others.

For example, let's say you have 4 USB slots.  If you figure out the order and plug the mouse into #3, then your keyboard (assuming it is USB) should go in #4.  Of course, ideally you would plug it into the very first on the bus and that solves the problem.

Now... maybe I have an overall hardware issue going on.  Since my machine seems stable otherwise, I'm tempted to think not.  I was very disappointed with this mouse at first until by trial-and-error I figured that out.

---

