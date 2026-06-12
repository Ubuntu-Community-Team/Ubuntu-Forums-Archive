---
title: "Lower power consumption after wakeup ?!?"
date: 2010-11-18
forum: Hardware
---

### Post by kapetr on 2010-11-18
Hello,

I'm running U10.10 - Athlon XP2000+ (not M - also without powernow cpuscaling (If I know)), VIA KT133A, ATI Radeon 7000 AGP, 2x PCI LAN rtl8139, VIA Audio embedded + PCI CMI audio, HD Maxtor 320GB, DVD+-RW.
> $ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0c.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QZ [Radeon 7000/VE]



My system takes 
-on idle          **70W**
-on 100% CPU load **82W**

Even if my system does not support Suspend To RAM:
> cat /proc/acpi/sleep 
S0 S1 S4 S5 


in new Ubuntu 10.10 I have the choice to **Suspend to RAM** (?!).

If I use it, the system goes down with

- on suspend       **40W**

**_And now the interesting:_**

After wake-up (with power button on case) the system has 
-on idle          **45W**
-on 100% CPU load **76-80W**

The difference in idle is _very high_!

I have test all my devices - both sound cards, video, USB ports, DVD, HDD power state - and all is working normal.

**So, from where could be the great difference ?**

I can't find nothing, what has stay sleeping after wakeup, my CPU does not support PowerNow - so it could not be turned on with sleep/wakeup code, ...

Any Idea ?

It would be very nice to have 45W instead of 70W in idle, but to make sleep+wakeup after every start of PC is probably not the right way (e.g. HDD spins down/up - not good).


[SIZE="5"]**Any Idea ?**[/SIZE]

Tank to all and sorry please my English.

--kapetr

---

### Post by kapetr on 2010-11-21
Nobody ?

---

### Post by kapetr on 2010-11-29
really nobody ?

---

