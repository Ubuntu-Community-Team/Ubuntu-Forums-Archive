---
title: "[SOLVED] multi-window terminal"
date: 2008-08-24
forum: General Help
---

### Post by bryonak on 2008-08-24
Inspired by those side-by-side-panel file browsers, I've been looking for a way to do something similar with a terminal.
Take a look at the attached screenshot for a rough idea. My goal is to make those 4 terminals behave as one: open, close and minimize all of them with a single click. And there should be only one entry in the window list.

The ideal would be a normal gnome-terminal with it's "input surface" divided into four separate parts, but I can't find such a program.

The next best thing I can imagine is to use devilspie, i.e. take one terminal and make the other 3 behave relative to it. But this would get quite complex and I don't know if it's really feasible, since my own experience with devilspie is quite limited.

A simple solution is to embed the terminals into the desktop, but I want to open/close them at will, like any other application... and I need my desktop space for myself ;)

So... any other suggestions?


EDIT: solved because mcduck mentioned terminator [down here]("http://ubuntuforums.org/showthread.php?p=5659361#post5659361").


**

---

### Post by easybake on 2008-08-24
You could create a launcher and write a toggle script where it would launch all and close all of them at the same time.
Similar to the one I have in step 4 [http://ubuntuforums.org/showpost.php?p=5544134&postcount=1]("http://ubuntuforums.org/showpost.php?p=5544134&postcount=1")

 You could create a different profile for each Terminal. In CCSM you could set window rules, decoration and placement for each profile.

---

### Post by loboc on 2008-08-24
use screen

---

### Post by DaymItzJack on 2008-08-24
You can use compiz's "group and tabs" plugin.

---

### Post by bryonak on 2008-08-24
Thanks for your quick answers!

I tought I knew ccsm pretty well... obviously not, because this plugin completely slipped by me.
It looks very promising indeed.
Now I just need to figure out how to automatically group windows on launch and how to reduce the amount of items in the window list to 1 without collapsing (tabbing) the group. I'll try with different profiles later.

@easybake: The goal is to handle them in the window list like any other application window. Otherwise I'd be using a bash script with 4x "gnome-terminal --geometry..." and "killall gnome-terminal".
Btw: awesome layout you got there! I assume the lower right part is conky, but what about the calendar? And your launcher/dock is cairo or awn?

@loboc: You and me, we're obviously not on the same side of y2k ;P
Nah, I like screen, but why not use something similar in function but much more fancy (ok, sensationalist) in appearance on a machine that can easily support compiz?

---

### Post by easybake on 2008-08-24
> **bryonak said:**
> Thanks for your quick answers!
@easybake:Btw: awesome layout you got there! I assume the lower right part is conky, but what about the calendar? And your launcher/dock is cairo or awn?


Thanks. The calendar is [Rainledar]("http://www.rainlendar.net/cms/index.php?option=com_rny_download&Itemid=30"). With this [Skin]("http://customize.org/rainlendar/skins/57943"). The dock is Cairo Dock.

---

### Post by mcduck on 2008-08-25
Try Terminator. It does exactly what you asked for, a gnome-terminal that can be divided horizontally & vertically into separate terminals.

[http://www.tenshu.net/terminator/]("http://www.tenshu.net/terminator/")

If I remeber right the package should be in Hardy's repositories.

---

### Post by bryonak on 2008-08-25
Wohoo, thanks a lot mcduck!
I've been desperately trying to hook the close-event between my four gnome-terminals (close one -> all the others get closed), but now you showed me exactly what I needed...

*~$ sudo aptitude install terminator*


On a side note, I think there is clearly a need to improve the way we share knowledge about open source apps. I've been using Linux for a few years now, yet I missed out on the existence of terminator... and the same is happening in other threads in these forums.

---

