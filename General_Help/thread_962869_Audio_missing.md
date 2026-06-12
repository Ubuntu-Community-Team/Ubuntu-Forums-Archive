---
title: "Audio missing"
date: 2008-10-29
forum: General Help
---

### Post by rosa1 on 2008-10-29
Hello! I've just had Ubuntu installed into my PC. However, the sound seems to go shortly after re-start..i.e. switch the PC on , listen to Youtube (speakers and/or headphones) and, after five minutes, the sound slowly dies ...

My speakers were ok before Ubuntu was installed...it is very hard for me to find the cause of this...does anyone have any idea about this? Regards

Rose:KS****

---

### Post by Mark_in_Hollywood on 2008-10-29
Sound diminishing over time seems like a problem with the electronic hardware. Specifically the power supply capacitors. BUT, let us check Ubuntu, first

From the Applications menu (upper ribbon panel, top left), open that to Accessories, pull that down and find: Terminal. Select Terminal.

When the terminal screen is open type:

alsamixer

(you can cut & paste the above)

once the alsamixer is viewable, use the arrow (cursor) keys to move left and right to select various inputs/outputs, also, use the up/down keys to vary volumes, input levels, etc. If all those look OK, close the terminal.

Things to consider. How old is the sound system? How much use has it had? Without being in the same room your 'puter is in, this is a tough one.

---

