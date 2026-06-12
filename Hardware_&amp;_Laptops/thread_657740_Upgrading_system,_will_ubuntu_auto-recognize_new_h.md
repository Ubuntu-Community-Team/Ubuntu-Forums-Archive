---
title: "Upgrading system, will ubuntu auto-recognize new hardware?"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by steve_d on 2008-01-03
I am currently running a P4 2.4 on an asus P4P800 board, ATI x800 AGP vid card, and 1gig of DDR ram. I am currently waiting on a New Asus socket 940 board, with a dual core 64x2 chip, a PCI-E ati card, and 2 gig of DDR2 ram.

Will Ubuntu automatically recognize that I have changed hardware and load new motherboard drivers PCI-E support ect, or should I take some steps ahead of time.

I have had some problems with XP with new hardware, just wondering if the same applies to ubuntu 7.1.

I am currently not going to switch to the 64bit ver. of ubuntu at this point so it will be the current system I am running.

I am new, so if anyone can provide help, please explain what the steps mean.

Thanks
-Steve

---

### Post by isaaca on 2008-01-04
I'm not quite sure what you indend to do here. If you mean to switch out your old hardware and plug your old hard drive into the new motherboard, the answer is no. You'd have to reinstall Ubuntu so it can configure itself to your new hardware. It is very rare that an operating system installed on one system will even boot if you move the hard drive to another computer with anything but identical hardware. (you can swap things like RAM without reinstalling the operating system, but you'll need to if you get a new motherboard).

Otherwise, the Ubuntu installer should recognize most if not all of your hardware. I think you'll need to use proprietary drivers via the restricted drivers manager for your video card, but I'm not a gamer, so I really don't know much about vid cards.

---

### Post by acron1 on 2008-01-04
I don't think it's going to work but you can save your Home folder so you don't loose everything. Good luck.

---

### Post by steve_d on 2008-01-04
Thanks guys, I was trying to avoid that issue, but I suppose it is somewhat expected.

FYI I have had success replacing motherboard/chip ect in xp. Its just somewhat of a 50/50 shot if it will auto load the new drivers or not.

---

### Post by Yellow Pasque on 2008-01-05
> I am currently waiting on a New Asus socket 940 board, with a dual core 64x2 chip, a PCI-E ati card, and 2 gig of DDR2 ramSocket 940 is a registered DDR/2 (ie Opteron/server) platform. I certainly hope you didn't get a Socket 940 board when you wanted an AM2 board. True, AM2 has 940 pins as well, but it's incompatible with Socket 940.

---

