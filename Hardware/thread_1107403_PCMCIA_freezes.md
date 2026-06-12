---
title: "PCMCIA freezes"
date: 2009-03-26
forum: Hardware
---

### Post by Chico25 on 2009-03-26
Hi,

I saw similar issues have been brought up multiple times, I have a bad feeling in my guts that this problem is really cardbus-driver related...

My problem relates to 4x USB 2.0 PCMCIA card; my laptop (Fujitsu Siemens 3505) is quite cheap on USB ports and i ran out of these recently, so i gave YENTA PCMCIA USB controller a chance. Unfortunately, the controller freezes the whole system shortly after i initiate transfer.

I tried to unplug the controller once the system freezes as well as checking if kernel prints anything out when the crash occurs. Sadly, there's no recovery and no log on the console. Everything is just mute. The system never recovers and the only way to get it back up is to power off the laptop and start it up again.

I'm running Ubuntu x86_64 8.04 with kernel 2.6.24-23; the problem is 100% reproducible, yet there's little chance to collect the kern log as the freeze locks up everything, including io, so it's not really dumped.

I attached the log i figured most people ask about. It would be really fantastic if somebody could at least suggest where to go with it, if i should seek help elsewhere. I have a feeling this issue is really connected with all these network card freezes other people mentioned..

Thank you so much,
Tomek

---

### Post by Chico25 on 2009-03-27
[Bumping the thread...]

---

