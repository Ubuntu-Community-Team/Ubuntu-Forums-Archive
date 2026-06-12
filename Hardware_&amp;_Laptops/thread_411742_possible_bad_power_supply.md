---
title: "possible bad power supply?"
date: 2007-04-17
forum: Hardware &amp; Laptops
---

### Post by milton1 on 2007-04-17
Hi everyone,

I am getting an intermittent flicker effect on some video intensive apps that was not there before a couple of days ago, and am trying to isolate the problem. I have tested the power supply, and find the -12v reads zero. Does this mean that my ps is toast? Will that lead only read under specific load circumstances?

Help will be greatly appreciated.

---

### Post by milton1 on 2007-04-17
It's wine! On a fresh boot, if I run neverwinter, graphics are fine. If I then attempt to run, say, Diablo 2 or Starcraft in wine (0.9.35, I think), fullscreen mode does not work (mouse will scroll past the screen edges, showing distorted portions of the desktop), and subsequntly, neverwinter loads with horrible flicker problems. I'll try downgrading to an earlier wine.

I'm still curious about that -12v, though, if anyone has any thoughts on it.

---

### Post by Bartender on 2007-04-17
I'm pretty sure I know the answer.  Older (at least 5 or 6 years back) PSU's actually supplied negative voltages.  I think these were for some ISA slotted parts.   Newer power supplies don't provide these voltages because nothing on the boards needs it.
However, you still see those negative values in some monitoring software.

---

### Post by milton1 on 2007-04-17
I'm not using monitoring software. I plugged my DMM directly into the power cables under load (attached to the mobo) and read good voltages on everything (including -5v) but the -12v lead.

---

### Post by milton1 on 2007-04-17
OK, more on the funny wine issue:

Switched back to wine 0.9.30. This rid me of the beyond-fullscreen issue, but I still get flickering graphics after running games in wine. Restarting X fixes it.

Thought? Opinions?

---

