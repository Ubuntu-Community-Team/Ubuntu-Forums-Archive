---
title: "Question regarding Ubuntu 12.04 LTS and Asus k53tk"
date: 2013-05-21
forum: Hardware
---

### Post by jrtarsoly on 2013-05-21
Hello,

I'm new to the forum, but I'm guessing this is where I should address my question. Please excuse me for my novice english (not a native speaker), or if I've made an error regarding where to place and if my question.

So, currently I'm dual-boot-ing Ubuntu 12.04 LTS alongside Windows 7, no problems here; I've made all the software updates, and also all the hardware-related driver upgrades - no problems here also.

My system seems to be stable, running smoothly, within parameters and stable temperature.

My question is, since my laptop has dual graphic cards (I have an APU with an integrated AMD HD 6520g 1 GB, along with a dedicated HD 7670M - 1GB dedicated RAM), how can I know which one of theese GPU is Ubuntu running ?

Better yet, how can I choose which one should the OS run on ? 

Thank you,

JrT

---

### Post by gordintoronto on 2013-05-21
Did you install a proprietary driver? If you do, I think Catalyst Control Center will help you.

---

### Post by jrtarsoly on 2013-05-22
Thanks for the reply, first of all.

I didn't knew there was a catalyst control center for linux/ubuntu. I'll get into this, and install a CCC hopefully.

JrT.

---

### Post by jrtarsoly on 2013-05-23
Bump.

I tried to open Catalyst Control Center by terminal through the "gksudo amdcccle" before trying to update to the new proprietary 13.4 stable Driver. Turns out I had a CCC already installed, but it detected only my discreete HD 6520g APU Card.

Later, I tried to update ... I did it by using --force command. The installer told me it was ok, a clean install. 

I've rebooted the system, and now when I try to open amdcccle using root priviledges, it just won't start; Trying to open the amdcccle by simply typing it's name into a terminal (no gksudo, no root privs) tells me "Command not found."

In other words, I'm stuck ...

Anyone, any ideas ?

JrT

---

