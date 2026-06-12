---
title: "STB Tuner Card"
date: 2007-01-18
forum: Hardware &amp; Laptops
---

### Post by rueherman on 2007-01-18
I'm new to linux so be gentle  ](*,)   I start by a little preface - I'm building a MythTV backend server on an asus PR-DLSW Board with 2.4 Xeon and at the moment 1 gb ram.  I have an Air2PC HD Card coming at any time and plan to add one to two more HD Cards that are proven to work with Linux.   But I currently also already owned an older STB PCI Tuner card I would like to use to feed plain analog signals into also.

From my research so far I believe I have an STB TVPCI, STV TV PCI and a few other models for the name but basically a BT848KPF Frontend is a 4032 FY5 with a Temic 3X 7004

From pictures I have determine it best matchs Card=40 and Tuner=6  But I am still unable to get the card to be set correctly.   Here is some output I know will be useful

Myth-Backend:~$ dmesg | grep bttv && dmesg | grep tuner
[17179581.612000] bttv: driver version 0.9.16 loaded
[17179581.612000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179581.612000] bttv: Bt8xx card found (0).
[17179581.612000] bttv0: Bt848 (rev 18) at 0000:00:04.0, irq: 201, latency: 30, mmio: 0xfa800000
[17179581.612000] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[17179581.612000] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[17179581.620000] bttv0: using tuner=-1
[17179581.620000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179581.620000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179581.624000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179581.624000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179581.628000] bttv0: registered device video0
[17179581.628000] bttv0: registered device vbi0
[17179581.620000] bttv0: using tuner=-1


I've read in a few places that the kernal by default supports cards 0-19 and bttv-0.6.4h contains support for types 20 through 27  But what about above 27?

Thanks for the help!!
Rueben

---

