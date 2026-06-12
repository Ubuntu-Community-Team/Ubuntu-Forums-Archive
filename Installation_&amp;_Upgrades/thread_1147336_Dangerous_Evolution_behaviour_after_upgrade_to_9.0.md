---
title: "Dangerous Evolution behaviour after upgrade to 9.04"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by Rehdon on 2009-05-03
Hi all,
I recently upgraded to Ubuntu 9.04, but I left my old 8.10 installation untouched on a different partition, 8.10 and 9.04 share the /home partition. This morning I booted in 8.10 to test the wireless connection and I misclicked on a send mail: because of that Evolution was launched, and I guess it tried to fetch mail. Well, to my horror and disbelief about 20-30 messages that were visible through my web-mail page first were marked as read, then simply **vanished** from my inbox. I didn't understand what happened at first, so some time later I checked my mail starting Evolution again: and again the messages on the server were deleted forever.

I wonder if anyone else experienced this, and if it's worth to point the Evo devs to it. In any case, be warned: sharing the Evolution mail base between version is currently **unsafe**, to say the least!

Rehdon

---

