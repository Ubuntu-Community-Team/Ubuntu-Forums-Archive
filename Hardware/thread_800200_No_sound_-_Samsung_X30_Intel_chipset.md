---
title: "No sound - Samsung X30 Intel chipset"
date: 2008-05-19
forum: Hardware
---

### Post by alexjhill on 2008-05-19
HI all,

I had sound last time i ran ubuntu 7.10 wonder why i don't now.. can you help? total newbie! 

ran lspci -v


this is my sound device.


Ran 00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Samsung Electronics Co Ltd Unknown device c00f
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at c0000c00 (32-bit, non-prefetchable) [size=512]
        Memory at c0000800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

---

### Post by nicedude on 2008-05-20
First you might try the command below and see if your sound volume levels are turned up as well as check under the top menu bar SYstem -then-> Prefferences -then-> sound , and see if you have alsa mixer chosen for your sound system as that is what works for my laptop and there are test buttons there as well. The following command lets you open the alsa mixer control panel to turn up your volumes.

command 
alsamixer

Hope this gets your sound going and welcome to Ubuntu :-)

---

