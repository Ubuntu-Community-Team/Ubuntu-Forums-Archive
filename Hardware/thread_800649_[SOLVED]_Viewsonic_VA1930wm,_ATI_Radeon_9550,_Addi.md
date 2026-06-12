---
title: "[SOLVED] Viewsonic VA1930wm, ATI Radeon 9550, Adding Refresh Rates"
date: 2008-05-20
forum: Hardware
---

### Post by lefo on 2008-05-20
Luckily, Ubuntu Hardy is recognizing my ATI card, but it only shows the Generic display for the Viewsonic LCD.  It can be recognized using other ATI Catalyst, but Monitor Resolution Settings only shows the 60Hz refresh rate and not the 75Hz that I could use in WinXP.  It also shows it as an "unknown" monitor in the Screen Resolution panel.

So, any ideas on how to change this?

TIA

lefo

---

### Post by lefo on 2008-05-20
***Bump***

---

### Post by lefo on 2008-05-21
I've emailed Viewsonic Customer Support to see if they have any suggestions. Will post if/when they reply.

lefo

---

### Post by GregA on 2008-05-21
Most LCD's that I've used are designed to run best at 60 hertz.  

IF your LCD is not showing content the way you've been used to it, then you can adjust the video specs in /etc/x11/xorg.conf - - however, search and read about "xorg.conf" first, as there are a lot of options, and it's easy to hose your display entirely. 

Also, you can try changing your monitor type from generic to your actual monitor, or something close in number/series (system>preferences>screen resolution>scan for "")

---

### Post by lefo on 2008-05-22
LOL, boy!  Did I screw things up last night!  I think I hosed my config file.  Luckily, I've made a backup in my Documents folder.  When I get home, I'll replace it.  Got stuck in smaller resolutions, and I lost my mouse and Wacom Graphire settings.  Just glad I made a duplicate!

Thanks for the help.  60Hz is okay, but at 75 the imaging is really crisp and sharp.  Got used to that, but it's not bad at all at 60.  I'll stick with what works.  If Viewsonic comes up with anything, I'll try that...and, keep that dup config file in reserve!

lefo

---

