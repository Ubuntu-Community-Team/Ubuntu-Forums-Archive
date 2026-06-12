---
title: "Broadcom 4138 wireless card on HP nx6110"
date: 2009-05-15
forum: Hardware
---

### Post by eggzenbeanz on 2009-05-15
Hi,

I’ve recently installed jaunty jackalope on my HP laptop (model: nx6110) – Everything works very well and im luving using ubuntu. However I can’t get my wireless card working.

I’ve tried to follow a few guides of what I can find on line but no success. None of the guides seem to talk about jaunty jackalope release, rather 3-4 versino back. So im not sure its intended for 9.04. My Broadcom wireless card is a BCM4138 and the light is on, but I cannot see where its active.

I am a very big linux noob, and I only want to really use it on my HP laptop to surf and email nothing more than that. Can someone assist me with setting up my wireless card? At the moment I have a network cable trailing halfway across my flat!

Thanks

Mark

---

### Post by scrooge_74 on 2009-05-18
Hi, by version 8.04 that card was being recognize as restricted driver. You probably need to enable the other repositories in Admin>Software Origins

then in Admin>Restricted Drivers, the wireless and the modem should show up once you give a few clicks the system should go fetch them (provided you have internet using the ethernet card)

I have that same laptop model and it being working pretty good for me since Dapper and even back using Debian.

Good luck and have fun

---

