---
title: "Nvidia won't go widescreen..."
date: 2008-10-03
forum: Hardware
---

### Post by zoomiest on 2008-10-03
I just installed Ubuntu 8.04.1 and can't seem to get things adjusted for a LG widescreen.

Have Nvidia GeForce Series 7 card 
Have AMD 64 box
Have LG L194 WTX screen (Flatron Wide)

[LIST]
[*]Tried to install the newly downloaded drivers from Nvidia, but I can't figure out how to stop the x server and keep everything else up. I tried sudo /etc/init.d/gdm stop
[*]Tried displayconfig-gtk 
[*]Tried reading other non-specific forum posts...
[/LIST]

Any suggestions? Thanx

---

### Post by zoomiest on 2008-10-03
I fixed my own issue... in an unusual way...

I went to the desktop, rightclicked > Change Desktop Background > Visual Effects (tab) > Extra. I was informed that I would need a special proprietary driver from Nvidia. It was automatically downloaded.

When I rebooted... it was activated, and my screen was automatically adjusted for 1440 x 900 (wide) was picked automatically. Presto!

Just forced a new update - by accident. Hope this helps someone.

---

