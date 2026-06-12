---
title: "Wrong graphics card name"
date: 2005-11-03
forum: Hardware &amp; Laptops
---

### Post by phanboy_iv on 2005-11-03
I have been in the process of trying to get 3D support in Breezy, and in my futile efforts to accomplish this, I noticed that Xorg identifies my laptop's ATI card as a "Mobility Radeon 9200". My card is actually a Mobility Radeon *9000 IGP*, though.

My question is: Should I file a bug report, or is Xorg just finding the closest supported card to my unsupported one as possible(a.k.a, not a flaw, just doing the best that it can do under the circumstances)?

---

### Post by insitu on 2005-11-03
When X starts up, it logs what it does in /var/log/Xorg.0.log (or equivalent). There you can check the id of your chip as far as X can tell. The marketted name of your card may very well hide some standard chip.
The question is : did you manage to configure X (and 3D) anyway ?

---

### Post by phanboy_iv on 2005-11-03
[QUOTE=insitu]When X starts up, it logs what it does in /var/log/Xorg.0.log (or equivalent). There you can check the id of your chip as far as X can tell. The marketted name of your card may very well hide some standard chip.
The question is : did you manage to configure X (and 3D) anyway ?[/QUOTE]

X worked fine out of the box, but no, I haven't gotten 3D to work. I just noticed this problem during Xorg reconfigures after failed attempts to get the new fglrx driver to work. Darn ATI.

I found hese strings in the log file : "Chipset ATI Radeon Mobility 9200 IGP 7835 found" and 
"(--) RADEON(0): Chipset: "ATI Radeon Mobility 9200 IGP 7835" (ChipID = 0x7835)"

I just wanted to know if this is something I should file a bug about, or just forget.

---

