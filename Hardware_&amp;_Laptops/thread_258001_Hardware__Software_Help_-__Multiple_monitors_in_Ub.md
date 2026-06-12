---
title: "Hardware / Software Help -  Multiple monitors in Ubuntu"
date: 2006-09-15
forum: Hardware &amp; Laptops
---

### Post by Brendt2 on 2006-09-15
Hello,

I have a simple question that I will leave open ended:  What is the best way for me to have 2 or 3 monitors attached to my Ubuntu computer (in a usable fashion!)?

---

### Post by uDanimal on 2006-09-15
I don't know if its the best way, but I have 2 monitors plugged to my nvidia 6800 card.  Ubuntu/nvidia drivers don't recognize both with configuration, but the changes were not too bad.  

I can drag windows from 1 monitor to the other without problems.  The only problem I have is that for fullscreen games, they try to split across both monitors.  I made a workaround hack, though.  I just made a copy of my xorg.conf file that is setup for just 1 monitor, and wrote a shellscript to swap them out and restart x to single monitor so I can play a game.  It's not perfect, but its a small price to pay for dual monitors.

---

