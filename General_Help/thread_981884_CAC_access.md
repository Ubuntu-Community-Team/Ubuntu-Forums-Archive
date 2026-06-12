---
title: "CAC access"
date: 2008-11-14
forum: General Help
---

### Post by carterw65 on 2008-11-14
Hey all,

I tried to post this in one of the already present threads but it wouldn't let me for some reason. 

I followed all the instructions for using a CAC with AKO and I got it working one time. I logged into AKO with user/pass and registered the CAC and logged out then back in. But I could only get it to do it once.

I keep getting a popup wanting my "Master Password" or one wanting a user name and password.

I have restarted pcsc to no avail Here is my output on pcsc_scan:

PC/SC device scanner
V 1.4.14 (c) 2001-2008, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.99
Scanning present readers
0: SCM SCR 3311 00 00

Fri Nov 14 06:43:04 2008
 Reader 0: SCM SCR 3311 00 00
  Card state: Card inserted, 
  ATR: XX XX XX XX XX XX XX XX XX XX

ATR: XX XX XX XX XX XX XX XX XX XX
+ TS = 3B --> Direct Convention
+ T0 = 95, Y(1): 1001, K: 5 (historical bytes)
  TA(1) = 95 --> Fi=512, Di=16, 32 cycles/ETU (111600 bits/s at 3.57 MHz)
  TD(1) = 40 --> Y(i+1) = 0100, Protocol T = 0 
-----
  TC(2) = FF --> Work waiting time: 960 x 255 x (Fi/F)
+ Historical bytes: AE 01 03 00 00
  Category indicator byte: AE (proprietary format)

Possibly identified card (using /usr/share/pcsc/smartcard_list.txt):
3B 95 95 40 FF AE 01 03 00 00
	Axalto - Cyberflex 64K
	Gemalto TOP IM FIPS CY2 (product code HWP115291A)

Thanks to anyone who can help. After all.....I'm a nooB with a capital B!

Bill   ](*,)

---

