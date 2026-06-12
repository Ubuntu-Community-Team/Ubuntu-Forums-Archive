---
title: "High CPU usage and evince?"
date: 2008-08-08
forum: General Help
---

### Post by djsroknrol on 2008-08-08
Well, even someone who's been around Ubuntu for any amount of time needs help once in a while. :)

I downloaded the last PCLOS E-zine the other night to catch up on things and noticed that I was running at 100% processor while trying to look at a 44 page pdf...amazing, huh? here are to screenshots to show what I was dealing with. Top confirms what system monitor is saying. The strangest thing of all was that Sysmon was reporting that evence was sleeping when in fact, it was trying to load a page.

Anyone have any idea why this would be happening?

---

### Post by ibuclaw on 2008-08-08
Nope, probably not totally evince. It's the gnome-system-monitor...

There is currently a long-standing bug in the app which causes it to run at anomalously high CPU levels (on my machine it uses 50% when idle, but then drops back down to 2% when I close the app).

For CPU readings, use **top** or **htop** instead. They are runnable from the commandline.

Regards
Iain

---

### Post by djsroknrol on 2008-08-08
Well, I'm running 0% with nothing but firefox open. I am starting to suspect that it might be a video problem as I can read up to 15 page pdf's with no problem but large ones with color or many graphics just take forever to load and doesn't show more than 4 or 5 pages at a time.

Here's a shot of top:

---

