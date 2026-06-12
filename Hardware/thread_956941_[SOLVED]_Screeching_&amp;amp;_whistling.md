---
title: "[SOLVED] Screeching &amp;amp; whistling"
date: 2008-10-23
forum: Hardware
---

### Post by Patness on 2008-10-23
very, very high pitched (in some cases comparable to knowing there's a TV on in the house).

It varies with my PC load: if I put a screensaver as my desktop (using xwinwrap) then it gets worse. I am not kidding when I say I can hear it when I move my mouse over the scrollbar in firefox, scroll the wheel down, and I can hear every click going down the page). I hear every button pressed, every tab switched, everything.

I have disabled sound on my PC, unplugging my speakers; this did nothing.

My personal experience says the problem might be hard-drive, but this doesn't sound like an impending crash screech. I have been told this might also be a power supply issue (bad fan). 

Any other offers or suggestions on what needs to be done?

edit: I have noticed that if I restart X (CTRL-ALT-Bksp) things go quiet. When I log in again, I can still feintly hear strolling, tabbing, etc, etc. The whistle part comes back whenever I run the screensaver - even if I'm looking at the preview window. Running any games (Savage 2, Penny Arcade, Penumbra) doesn't produce nearly the same volume of screeching (!).

I'm confused as  -- I'm really confused. If anyone reads this, get back to me with some creative thoughts.

---

### Post by cariboo on 2008-10-23
What kind of monitor do have crt or lcd?

Jim

---

### Post by Patness on 2008-10-28
LCD - Acer 1715

---

### Post by cariboo on 2008-10-28
I have the same monitor, so that isn't the problem. Have you checked the power supply? If you can just exchange for another on and see if there is any difference.

Jim

---

### Post by Patness on 2008-10-28
unfortunately, I can't without taking my PC out of commission for a week.

I do appreciate it. At this point, it's purely diagnostic. My fans, hard drive, and power supply are my primary antagonists, here. I would, however, like to know if someone can justify others.

---

### Post by Patness on 2008-10-31
I put a delay on my startup and it stopped screeching - which makes me think disc thrashing.

Thanks!

```
#!/bin/bash
sleep 20 &&
nice -n 15 /usr/bin/xwinwrap -ni -o 0.25 -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/skyrocket -window-id WID &
```

---

