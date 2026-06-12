---
title: "Ferrari 4005 WLMi black screen on boot"
date: 2009-06-05
forum: Hardware
---

### Post by abbec on 2009-06-05
Hi!

I installed Jaunty on a Ferrari 4005 WLMi. It was a fresh install because earlier it had been dual-booting with XP so I decided to do a fresh install. 

The problem is that about 1/3 of the time, the xserver startup hangs (during boot) and the screen becomes black. The only thing to do is to restart the computer, and after a few restarts it may start working.

The problem is also mentioned ([here]("https://wiki.ubuntu.com/LaptopTestingTeam/AcerFerrari4005WLMi")), but I havent found a fix. I use the open source ati driver.

---

### Post by abbec on 2009-06-05
BUMP! this is really irritating... someone else has got to have the same problem...

---

### Post by abbec on 2009-06-06
Anyone???

---

### Post by abbec on 2009-06-08
Bump!

---

### Post by abbec on 2009-06-20
c'mon someone else has got to have the same problem?????

---

### Post by moewe2 on 2009-06-22
Yeah I had a similar problem, but it never workes - even not after a few attempts of reboot (and what should a reboot change??). So I reinstalled an older Ubuntu version. :(

It has something to do with the new handling of the connectors (LVDS, CDRT, DVI), that is done with randr now instead of setting it at xorg.conf. I don't know how to teach randr the correct setting and I'm waiting for a solution, too.

Greetings,
moewe2

---

### Post by abbec on 2009-06-22
Finally someone replies :D. I'm used to fast replies on this forum but since noone replies maybe there is no solution right now? Someone please correct me if I'm wrong...

---

### Post by abbec on 2009-10-06
BUMP! I have uploaded last part of Xorg.0.log in my original post! Please help with this...

---

### Post by tdp on 2009-11-12
Hi - I had the same problem with 9.04. I fixed by installing 9.10 64-bit. All is good now. I believe 9.10 is running a newer version of X.org. Plus using the 64-bit version gives a noticable performance hike (especially when using the lastest Adobe Flash 64-bit).

I have had the old wobbly screen once (quickly fixed by selecting System->Preference->Display->select rotation upside down, and then restore the display.

Install 9.10 64-bit - you'll love it.

---

