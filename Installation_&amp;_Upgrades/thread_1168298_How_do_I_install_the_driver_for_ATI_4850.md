---
title: "How do I install the driver for ATI 4850?"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by nemesisinfinity on 2009-05-23
well ive tried everything i can figure out from envy to cmd lines to the proprietary drivers in ubuntu installed to get my pc to run WoW...wine's installed and when i launch it i get a garbled screen with like 1fpm...I just can't figure out how to install the driver for my ati 4850.   i do like using linux just cant get it to work...I always a black screen at where i should boot after i do it and If i do 
libgl1-mesa-dri
and 
libgl1-mesa-glf
updates in the manager i get the same thing. Ive done multiple installs and its getting frustrated so im gonna stop trying for a while and maybe come back. If anyone has gotten this card to work i'd love to know how, and also im using ubuntu 64bit if that matters ](*,)

---

### Post by bpayne71 on 2009-05-25
nemesisinfinity:

I am currently attempting to install this on my new Ubuntu box. I will let you know how it goes.  I am using Wine to try and see if I can get it to go.  If I do, I will post here how I got it done. I am using ATI X1650 card.  Let's keep our fingers crossed.

---

### Post by nemesisinfinity on 2009-05-25
cool thanks lemme know

---

### Post by Mark Phelps on 2009-05-25
I would be utterly astounded if this works -- because Wine is written to run Windows applications in Linux, not to use Windows drivers.  Wine runs in user mode; drivers run in kernel mode.  In Ubuntu (or any other Linux version), you're running a Linux kernel, not a Windows kernel.  So, basically, there is simply no way this can work.

---

