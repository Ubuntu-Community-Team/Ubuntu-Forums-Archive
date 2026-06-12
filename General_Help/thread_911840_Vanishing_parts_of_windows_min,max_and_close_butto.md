---
title: "Vanishing parts of windows: min,max and close button gone"
date: 2008-09-06
forum: General Help
---

### Post by Unlearned on 2008-09-06
i am new to ubuntu....hmm you could guess that i think

i was turning on the cube effect for fun and i had firefox open when the top part of the browser disappeared. the window now starts with the menu bar with file edit etc(like i have to say that :) ) when i opened another window it was the same. i have to minimize by right clicking on the window list on the panel. i also cannot move a window because where i normally click to move it is no longer there.

can someone help me fix this. i would reinstall but its a pain and i would have to reinstall some things the way i want and they are almost too much trouble to deal with

---

### Post by cpetercarter on 2008-09-06
Sometimes the top orange bar on Firefox gets stuck underneath the panel at the top of the screen.
You can drag and drop the top panel temporarily to the side of the screen - the top Firefox bar should then be visible. Unmaximise it, and adjust its size so that it will fit below the panel, then move the panel back.

---

### Post by zxscooby on 2008-09-06
re-enable your window decorations in the compiz settings manager

---

### Post by Unlearned on 2008-09-06
> **zxscooby said:**
> re-enable your window decorations in the compiz settings manager

how do i do that or should i say what exactly do i turn back on

---

### Post by Unlearned on 2008-09-06
hahaha thanks found the right one....i hate when you look for something and cannot find it then after you ask you can see it.....now i will go and sell my computer and move to a cave somewhere remote and contemplate my shame.

---

### Post by zxscooby on 2008-09-09
I did the same thing :lolflag: 
I think it hides.

---

### Post by Lizard_King on 2008-09-12
If you can't explain how to do something keep your comments to yourself. Telling us noobs to "fix it" doesn't help. Sometimes we need a "how to" explanation.

---

### Post by gldearman on 2008-09-12
> **Unlearned said:**
> i am new to ubuntu....hmm you could guess that i think

i was turning on the cube effect for fun and i had firefox open when the top part of the browser disappeared. the window now starts with the menu bar with file edit etc(like i have to say that :) ) when i opened another window it was the same. i have to minimize by right clicking on the window list on the panel. i also cannot move a window because where i normally click to move it is no longer there.

can someone help me fix this. i would reinstall but its a pain and i would have to reinstall some things the way i want and they are almost too much trouble to deal with

I think I know what is going on; it happened to me.

Do you have an NVIDIA graphics card?  When I enabled desktop effects, my min/max/close window buttons also disappeared -- I think this may be a bug with the NVIDIA drivers.  I ended up having to muck about in the xorg.conf file to fix it.  Glad you found an easier solution.

---

### Post by bunnsnow on 2010-10-11
The easiest way around this is to:

[LIST=1]
[*]Navigate to 'System>Preferences>Appearance'
[*]Then, Select the 'Visual Effects' tab and change the setting to 'None'
[*]Finally, revert back to the original settings (Extra?) and all will be OK
[/LIST]
*Sudo apt-get install the-best-operating-system-in-the-world*

---

### Post by Bluebearbevis on 2010-10-15
Hello all,

I've reached this point in the discussion, including an attempt to remove/activate the nVidia driver when visual effects said extras could not be activated. When restart said I was installing an upgraded driver I was hopeful.  Again the "not."  The min, max, close buttons are back, but I can't enable visual effects.  I have a System76 panp6, maybe it has something to do with their driver?  I'll check on an update.  I'll also check the forum for can't enable visual effects which now is really my issue.  If anyone knows where I'm headed and can give some direction?

Thanks everyone,  Richard

---

