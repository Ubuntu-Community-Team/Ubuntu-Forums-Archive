---
title: "screen resolution"
date: 2008-09-17
forum: General Help
---

### Post by fboxall on 2008-09-17
I have ubuntu inside windows xp pro.  I have done something really stupid.  I set the Ubuntu screen resolution to very low numbers and now I can see only a small portion (the upper right corner) of the Ubuntu desktop on my monitor.  I need to set the screen resolution to higher numbers but I can't get to System->preferences->screen resolution to make the change.  I have locked myself out of Ubuntu and I don't know how to get in.  I hope some kind soul can tell me what to do.

---

### Post by leef on 2008-09-18
If you can get to a terminal try the command "xrandr" then choose a resolution from the list and type "xrandr -s <number>" where <number> corresponds to the resoltion your want (starting from zero). If you can't get to a terminal use ALT + F2 to get the run dialog and enter the command xrandr -s 0

---

### Post by fboxall on 2008-09-19
> **leef said:**
> If you can get to a terminal try the command "xrandr" then choose a resolution from the list and type "xrandr -s <number>" where <number> corresponds to the resoltion your want (starting from zero). If you can't get to a terminal use ALT + F2 to get the run dialog and enter the command xrandr -s 0
Thanks for response, but apparently I have managed to make things worse. Now Ubuntu won't boot. I can't get to terminal and Alt+F2 doesnt't bring up run dialog.  I think I will have to uninstall Ubuntu and then reinstall from CD.   Any suggestions?

---

