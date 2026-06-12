---
title: "OpenPGP FSFE Smart Card"
date: 2005-12-03
forum: Hardware &amp; Laptops
---

### Post by easterndodo on 2005-12-03
Hello everybody: I searched through some forums, but I couldn't find anything so, Ubuntly affected, I post here my trouble:

I HAVE GOT AN OPENPGP SMART CARD: IT IS THE ONE SENT BY THE FREE SOFTWARE FOUNDATION EUROPE. I CAN'T MAKE PC/SC MIDDLEWARE WORK!

This is the problem: I got this Cryptography smart card for OpenPGP by doning some money to the European Free Software Foundation, and they sent me this nice smart card. I bought a PCMCIA smart card reader / writer for my laptop and tried to make it work: I installed the pc/sc libraries (for accessing the reader and the card), but when I run [FONT="Courier New"]gpg --card-status[/FONT] (or other smartcard-related gpg commands) I get this message:

[FONT="Courier New"]gpg: detected reader `SCR24x Smart Card Reader 00 00'
gpg: apdu_send_simple(0) failed: unknown status error
Please insert the card and hit return or enter 'c' to cancel:[/FONT]

So I can't use the card at all. The PCMCIA card reader is installed and working: I put here the information received by [FONT="Courier New"]pcsc_scan[/FONT] command:

[FONT="Courier New"]PC/SC device scanner
V 1.4.1 (c) 2001-2004, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.2.9-beta7
Scanning present readers
0: SCR24x Smart Card Reader 00 00

Sat Dec  3 14:58:53 2005
 Reader 0 (SCR24x Smart Card Reader 00 00)
        Card state: Card inserted,
        ATR: 3B FA 13 00 FF 81 31 80 45 00 31 C1 73 C0 01 00 00 90 00 B1

ATR: 3B FA 13 00 FF 81 31 80 45 00 31 C1 73 C0 01 00 00 90 00 B1
+ TS = 3B --> Direct Convention
+ T0 = FA, Y(1): 1111, K: 10 (historical bytes)
  TA(1) = 13 --> Fi=372, Di=4, 93.000 cycles/ETU
  TB(1) = 00 --> Programming Param P: 0 Volts, I: 0 milli-Amp\uffffres
  TC(1) = FF --> Extra guard time: 255
  TD(1) = 81 --> Y(i+1) = 1000, Protocol T = 1
-----
  TD(2) = 31 --> Y(i+1) = 0011, Protocol T = 1
-----
  TA(3) = 80 --> IFSC: 128
  TB(3) = 45 --> Block Waiting Integer: 4 - Character Waiting Integer: 5
+ Historical bytes: 00 31 C1 73 C0 01 00 00 90 00 B1

Possibly identified card (using /usr/lib/pcsc/smartcard_list.txt):
3B FA 13 00 FF 81 31 80 45 00 31 C1 73 C0 01 00 00 90 00 B1
        OpenPGP

[/FONT]

I put here the information about my system:
 - Ubuntu Dapper Drake development branch
 - pcsc-lite version 1.2.9-beta9
 - GnuPG version 1.4.2
 - Smart Card Reader SCM microsystems SCR243
 - PCMCIA bus information (obtained by lspci): 0000:01:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
 - Asus M2400Ne Series laptop with Intel Centrino 1.6Ghz.

Thank you all!!!!

---

### Post by prlewis on 2008-02-26
Hey!

Did you ever get the SCR243 PCMCIA card working with your FSFE cryptocard?

I'm thinking about buying the SCR243 and wondered if it would work.

Thanks!

Peter.

---

