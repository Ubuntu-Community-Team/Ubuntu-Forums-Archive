---
title: "PCMCIA card not recognized"
date: 2014-06-29
forum: Hardware
---

### Post by natem2 on 2014-06-29
Hi All,

I am having some trouble getting a PCMCIA card to work. The card in question is a Startech Parallel Port PCMCIA card which I am hoping will work with my HP Pavilion laptop. I am currently running Ubuntu 10.04 LTS. When I unplug the card and plug it back in I get the following response when I run the command: dmesg | tail -n 20

[   94.214660] parport_pc 0000:07:00.1: device not available because of BAR 0 [0x00-0x07] collisions
[   94.214669] parport_pc: probe of 0000:07:00.1 failed with error -22


Can anyone give me any pointers for what is causing the problem? I haven't been able to find any information on this online.

Thanks!

---

### Post by natem2 on 2014-06-30
I know it's a long shot but if anyone has any advice that would be seriously helpful.

Thanks,

Nate

---

