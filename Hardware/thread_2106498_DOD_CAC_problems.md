---
title: "DOD CAC problems"
date: 2013-01-19
forum: Hardware
---

### Post by rasmukri on 2013-01-19
i have installed all kinds of stuff for the freaking cac reader to include cackey and pcsc tools. my problem is when i put in my card or anybodys card and in terminal tryp pcsc_scan it tells me my card is unresponsive. and naturally if i try to log into my ako or anything that requires the cac it does not work. But if i got to another computer a work computer or the MWR computer it works fine.  any ideas on how to fix this? i am running ubuntu 12.04 x86 on a toshiba satelitte laptop with a stanley global 111-6 usb cac reader

```
kristoffer@kristoffer:~$ pcsc_scan
PC/SC device scanner
V 1.4.18 (c) 2001-2011, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.7.4
Using reader plug'n play mechanism
Scanning present readers...
0: Dectel CI692 [Smart Card Reader Interface] (20070818000000000) 00 00

Sat Jan 19 16:49:34 2013
Reader 0: Dectel CI692 [Smart Card Reader Interface] (20070818000000000) 00 00
  Card state: Card removed, 

Sat Jan 19 16:49:37 2013
Reader 0: Dectel CI692 [Smart Card Reader Interface] (20070818000000000) 00 00
  Card state: Card inserted, Shared Mode, Unresponsive card, 



```

---

