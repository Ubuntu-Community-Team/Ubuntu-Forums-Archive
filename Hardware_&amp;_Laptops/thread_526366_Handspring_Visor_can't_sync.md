---
title: "Handspring Visor can't sync"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by likpok on 2007-08-15
I recently got a second hand Handspring Visor, and am trying to sync it with my amd64 Kubuntu laptop.

Currently (as in, out of the box) coldsync can sync. However, I would like some way to sync with the Kontact calender and the various KDE organizer stuff. I have tried both jpilot and kpilot, neither can sync successfully. Kpilot crashes almost immediately, and jpilot immediately looses the connection (as in, when i press the sync button in jpilot, the visor soon beeps and complains that the connection has been lost), and then never connects with the visor afterwards.

I have properly loaded the visor module into the kernel.

---

### Post by g4c9z on 2007-08-18
Hi,

I was having the exact problem with my Handspring Visor, which only appeared after upgrading to Ubuntu 7.04.  From Googling around, I found someone who suggested that I change the Serial Rate of the connection to 115200 (you can do this in the JPilot preferences, I don't know about KPilot) and suddenly the problem was fixed.  That's probably worth a try.

I don't understand why that should fix it, though, because in the JPilot dialog it says that the Serial Rate does not affect USB.  I think it's a bug, but I don't know if it's an Ubuntu bug or a J-Pilot bug.

---

### Post by Skeptibuntu on 2007-08-18
You need to add "visor" to the list in  /etc/modules

---

### Post by likpok on 2007-08-21
g4c9z:
Thank you. That setting of the speed worked perfectly. Both with Jpilot and Kpilot. Thank you very much.

---

