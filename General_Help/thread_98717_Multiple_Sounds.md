---
title: "Multiple Sounds"
date: 2005-12-04
forum: General Help
---

### Post by MrJHazelton on 2005-12-04
Hi Ubuntu Users!

Quick question for anyone willing to help. I been using ubuntu now for over a month and various distros before ubuntu for a couple years now.

My question is though, I am on a Toshiba Satellite laptop with a generic sound blaster sound card with ALSA drivers. My sound works fine but only one sound at a time. If I have XMMS open, my gAIM for instance, wont make any sounds when getting an instant messaged. And than, If I get instant messaged between songs on XMMS my gAIM will ding but XMMS will stop working (because my card is apparently being used) and wont work until I reboot my laptop. 

So my question is, how is it possible, if at all, to get multiple sounds playing at once.

Thanks everyone.

---

### Post by ewdp on 2005-12-04
This may not be the best solution, but i use esd.

type "esd -nobeeps &" in your terminal.

if you're in gnome-session simply enable the sound server.
System -> Preferences -> Sound

all the best.

---

