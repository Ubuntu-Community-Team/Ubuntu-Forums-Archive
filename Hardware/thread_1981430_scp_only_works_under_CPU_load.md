---
title: "scp only works under CPU load"
date: 2012-05-16
forum: Hardware
---

### Post by Nod51 on 2012-05-16
I bought an Asus K70AB laptop that has a AMD Turion X2 Dual-Core Mobile RM-75 / ATI RV710 from a friend that will white screen on and off randomly in Linux or Windows(XP/7), but I decided to use it as a server. Everything was working fine till I tried to scp from from my current server over at which point after about 1 second of transfer I get: 

Corrupted MAC on input.
Disconnecting: Packet corrupt
lost connection

Network wires are good, but if I run 1 or more CPU intensive tasks, say burnK7 or memtester, scp works fine. 

I tried: 
- running a 3 day memtest (all pass between the white screens)
- changing the ram (and moving around what it came with)
- disabled CPU scaling at 2200mhz (it's max) or 1ghz but no change. 

If I have it at 2200mhz and run 2 burnK7 it will shutdown in around a minute.

---

