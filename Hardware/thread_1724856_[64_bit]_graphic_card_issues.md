---
title: "[64 bit] graphic card issues"
date: 2011-04-08
forum: Hardware
---

### Post by bmoreno on 2011-04-08
Every time i install the drivers for my ATI Mobility Radeon HD 5650 graphics card my computer stops working. Either it wont boot or when it does boot my mouse cursor turns into a "X" and i lose the title bar to all programs. Is their any way around this?

some computer specs: Hp Envy 14, 50 gb ocz vertex2 ssd, intel i5 580m, 4 gigs ram, ATI Mobility Radeon HD 5650 graphics card. On my 4th installation of ubuntu 10.10 64-bit.

---

### Post by Yellow Pasque on 2011-04-09
You have switchable graphics (an Intel IGP as well as the Radeon). You either need to disable the Intel video in the BIOS if possible or find some way to switch between open-source intel drivers and binary ATI drivers. There may be better support for that in Natty: [http://www.phoronix.com/scan.php?page=news_item&px=OTI3Mg](http://www.phoronix.com/scan.php?page=news_item&px=OTI3Mg)

---

### Post by bmoreno on 2011-04-09
Thanks for the information. Not 100% sure what it means but its better then no information at all.

---

### Post by Yellow Pasque on 2011-04-09
> Not 100% sure what it means
Bluntly, it means you're screwed as far as using your RadeonHD with Catalyst/fglrx unless there are major improvements made to Xserver or you have a BIOS switch to disable the Intel integrated graphics.

---

### Post by bmoreno on 2011-04-10
lol ok i understand now. thanks for the info.

---

