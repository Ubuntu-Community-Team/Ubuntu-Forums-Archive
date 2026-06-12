---
title: "Wireles in Fujitsu-Siemens"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by Rizzrat on 2007-10-19
Hi all, 

I have a Fujitsu-Siemens Amilo laptop (LI 1818 model i think). When i boot the liveCD for Gutsy i dont get any kind of wireless on it. I have done a bit of reading and apparently there are a few people who have this problem.

Can anyone help me get my wireless working. I wont install it over vista until i know its going to work. Vista btw, needs to repair my wireless every time i boot up :(. Maybe its a faulty killswitch or something.

Please help me get rid of windows. Help me get wireless on my laptop.

---

### Post by Barnable on 2007-10-22
Y'know, if you've got all the factory-restore discs for Vista, and a *recent* backup of your files, you could just bite the bullet - just go for it and install Ubuntu anyway.

I have a Fujitsu-Siemens Amilo PA1510 and - IIRC - the wireless didn't work under the LiveCD for Feisty, but once I installed it to hard disc it (presumably) puts the madwifi Atheros drivers in and lo-and-behold I had working wifi!

Not sure if that helps, upon reflection.

:)

---

### Post by Rizzrat on 2007-10-24
I would do that but knowing my luck the CDs Pcworld give you wont put vista on after a HDD wipe.. Probably why there is a partition on my drive with 6GB of tmp files.

I have raised this in the Amilo forums.

[http://www.amilo-forum.com/topic,1169,-LI1818-Wireless.html]("http://www.amilo-forum.com/topic,1169,-LI1818-Wireless.html")

Thats as far as we got. Would ndiswrapper work on the livecd? If so, how do i use it? (providing i can find the windows driver on my support cds)

---

### Post by John Mandrake on 2007-10-30
I managed to have it working, but there is no way I can turn on my wireless activity. I need a driver for the hotkey above the keybord to do that. iwconfig shows the interface, but the led is not lit. I used ndiswraper. You can find the step-by-step procedure in one of the threts. Search for AR5007EG on ubuntu forums, and you will surely find it. If you manage to get in working post, so I can use it myself.

---

### Post by Rizzrat on 2008-01-03
Alas no result.. Full of fail.
I got ndiswrapper to load the driver but it failed when it linked it to the hardware.. maybe it was the wrong driver i have no clue.

---

