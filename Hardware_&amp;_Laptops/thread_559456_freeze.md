---
title: "freeze"
date: 2007-09-25
forum: Hardware &amp; Laptops
---

### Post by rgrig on 2007-09-25
A few weeks ago the computer started to randomly freeze. It happens very rarely and, so far, only while I was scrolling in firefox using the mouse wheel. Once the screen went black for a few seconds and then everything started working normally. The second time the computer stopped responding to any key press or mouse button, although I could move the mouse (alt-ctrl-backsp, alt-ctrl-f1, etc. didn't do anything). The last two times the screen went black (as if the computer was turned off) and all I could do was to keep the power button pressed.

I have no idea what it is. Any help?

In case it is something related to the video drivers, here is what I have:
                product: RV370 5B60 [Radeon X300 (PCIE)]
                vendor: ATI Technologies Inc

---

### Post by aashay on 2007-09-25
Not a solution.. but next time it freezes try 
(ALT+Print Screen ) REISUB. (Keep alt and prnt scr pressed as you type it)
It will restart the PC in a much cleaner way
EDIT: My ATI 9600xt + Compiz Fusion + Firefox tends to hang. Rarely though

---

### Post by PmDematagoda on 2007-09-25
I've had the same problem as well, my feisty would occasionally freeze during startup and even during my sessions, I thought this was the "Feisty Freezes" I've read about, but the freezes escalated, even Win XP started crashing at startup(Shouldn't be surprised). I was very confused, as even my BIOS froze on startup, then a few days later after starting my computer and tried to get to the bottom of the problem by disabling "Silent Boot" and "Intel Rapid Boot", I was faced with a warning that my RAM was not properly distributed, which I knew couldn't be unless there was a fault with the memory modules themselves.

So I opened up my CPU, took all my memory modules out, cleaned them carefully along with the slots, and re-installed them. Then guess what, the problem vanished all on it's own. It might be the same with you as well, so clean up your RAM a bit and see if that makes a difference.

---

### Post by aashay on 2007-09-26
XP Crashing at startup... happens to me all the time. Though Feisty only crashes when swiftfox decides to stop responding. Crashed 3 times this way, dint ever crash due to any other reason.

---

### Post by rgrig on 2007-09-27
I'll try to clean the RAM but somehow I doubt that is the problem. I run programs like "while (true) malloc(1)" all the time and that does *not* make it crash. Instead, it crashed everytime while scrolling down in firefox using the mouse wheel. Moreover, I forgot to mention that the driver I use for the graphic card is `restricted' (ATI accelerated graphics driver). At the time when I installed it the Ubuntu default only allowed me to use very low resolutions.

---

