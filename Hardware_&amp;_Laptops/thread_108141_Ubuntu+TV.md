---
title: "Ubuntu+TV"
date: 2005-12-25
forum: Hardware &amp; Laptops
---

### Post by abrovink on 2005-12-25
Hello!
I am very pleased with ubuntu and have recently replaced two XP installations with Ubuntu.

I have one issue left to resolve before i am 100% happy.

Its my TV (DVB) card. I cant get it to work.
Pinnacle PCTV 300i DVB-T + PAL

Dmesg reports:
[4294696.513000] saa7134[0]: subsystem: 11bd:002d, board: Pinnacle PCTV 300i DVB-T + PAL [card=50,autodetected]

But i still cant get any applications to work...

All help is appreciated.

TIA!

---

### Post by Domie on 2005-12-27
I have the samen problem. They told me to rebuild the kernel, something I'm doing right now

---

### Post by abrovink on 2005-12-29
[QUOTE=Domie]I have the samen problem. They told me to rebuild the kernel, something I'm doing right now[/QUOTE]

Hello!

What did you do, and did it work out?
Would be cool to get some feedback.

I tried to load some other modules and finally have the card working in Antenna mode, but not DVB-T.

---

### Post by colsinc on 2006-02-24
Hi.  I have a Twinhan DTV MiniTER, which is a DVB-T card.  I had a bit of trouble getting it going, but most of my problems were solved when I installed the dvb-utils package (check with Synaptic that it's installed, I'm sure what repos you need, but add the ones it says to in the wiki and it should be there)  I then used Kaffeine to search for channels - I had to restart after installing dvb-utils to let kaffeine detect the card.  hope this helps!

abrovink, I didn't have to rebuild the kernel, but maybe it's different for your card.  what is antenna mode?

---

