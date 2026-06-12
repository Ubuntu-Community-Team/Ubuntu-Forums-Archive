---
title: "intel hardware glitches  problem"
date: 2015-12-03
forum: Hardware
---

### Post by simo_kotbi on 2015-12-03
i installed ubuntu 14.04 x64 in my desktop 
my specs 
3gb ram 
256 gb rom
intel core 2 duo 1.87 

i have some glitches in the desktop

please help me with my problem

thanks 

here is a screenshoot
[ATTACH=CONFIG]265915[/ATTACH]

---

### Post by tripp98 on 2015-12-04
What type of video card do you have?

have you installed additional drivers under system settings / software and updates / additional drivers.

---

### Post by simo_kotbi on 2015-12-05
i have no additional drivers 

i have Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)

---

### Post by tgalati4 on 2015-12-05
Blow out the machine with compressed air; take out the RAM sticks and blow out the slots.  Change the order of the RAM sticks.  Run *memtest*, then see if the behavior changes.

---

### Post by mörgæs on 2015-12-06
There is no reason to suspect failing memory or other hardware, nor are there any additional drivers offered for Intel in the windows mentioned.

You have an Intel GMA 3000 with very limited hardware acceleration. It might be too weak for Ubuntu so I recommend that you try X/Lubuntu in stead.

---

### Post by tgalati4 on 2015-12-06
Distorted icons could be bad video RAM, which in the case of Intel on-board video, is shared static RAM, so checking RAM is important.

---

