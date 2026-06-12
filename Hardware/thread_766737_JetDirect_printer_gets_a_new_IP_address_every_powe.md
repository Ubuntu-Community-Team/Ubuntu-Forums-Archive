---
title: "JetDirect printer gets a new IP address every power up."
date: 2008-04-25
forum: Hardware
---

### Post by gusjones on 2008-04-25
Hello,

I recently got an old HP laserJet 4mv (with built in JetDirect network card) scrapped off from work, and I did a cold reset on it in order to allow it to 'get' an ip address from my broadband router when I power up. This is OK so I power up the PC, print out a test page to tell me its IP address, and I manually configure it using the HPLIP software (provided for Linux by HP here:[http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)) which then correctly allows me to detect and use the printer.

This is great so far, however next day is like ground hog day and I have to repeat the process all over again as my printer gets assigned a new IP address and is not automatically picked up by Ubuntu.

I have some ideas, but does anyone have experience of the best way to solve this problem???

---

### Post by gusjones on 2008-04-26
Bump

---

### Post by gusjones on 2008-04-28
bumpity bump, looks like I'll have to solve this one myself...

---

### Post by MiataMuc on 2008-04-28
Hi, maybe you have to configure the jetdirect not to obtain an address via dhcp, but to have a fixed IP-address, or (if possible) to configure your router to give the printer always the same address. 

hope this helps, Flo

---

### Post by gusjones on 2008-04-30
yup, looks like there were two ways to do it, I went for a fixed IP address on the jet direct card which lay outside the range issued by my router. I had to figure out how to use telnet in order to change the IP address of the Jetdirect card, but now everything works a treat, thanks.

---

