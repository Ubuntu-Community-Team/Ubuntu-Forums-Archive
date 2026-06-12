---
title: "Terratec Cinergy 2400i PCI-E"
date: 2011-03-29
forum: Hardware
---

### Post by nashant on 2011-03-29
Hi.  I've tried everything I can find to get this working. I've put ngene_15.fw as well as _16 and _17 in /lib/firmware. I've tried the following drivers:

[http://linuxtv.org/hg/v4l-dvb/](http://linuxtv.org/hg/v4l-dvb/)
[http://linuxtv.org/hg/~endriss/v4l-dvb/](http://linuxtv.org/hg/~endriss/v4l-dvb/)
[http://linuxtv.org/hg/~tlorenz/v4l-dvb/](http://linuxtv.org/hg/~tlorenz/v4l-dvb/)
[http://linuxtv.org/hg/~dougsland/v4l-dvb/](http://linuxtv.org/hg/~dougsland/v4l-dvb/)
and cinergy_2400i_ngene_treiber.zip from a german forum.

Absolutely none of these have done anything for me. The info on my card is as follows:


03:00.0 Multimedia video controller [0400]: Micronas Semiconductor Holding AG Device [18c3:0720]
        Subsystem: TERRATEC Electronic GmbH Device [153b:1167]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 16 bytes
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at cbff0000 (32-bit, non-prefetchable) [size=64K]
        Region 1: Memory at cbfe0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
                Address: 0000000000000000  Data: 0000
        Capabilities: [58] Express (v1) Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s, Latency L0 unlimited, L1 unlimited
                        ClockPM- Surprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-


The graphics card I'm using is a GeForce GT210. I don't know if this could be interfering with it, but that's giving me troubles too (not what this post is really about though).

If anyone could offer me any assistance it would be absolutely awesome!

Cheers in advance

---

### Post by m3mes on 2011-10-09
Hi Nashant

Have you had any luck with getting your TV card working?

I have it working with an ABIT KN9 motherboard. Still trying with another the ABIT IP43.
The drivers that worked for me can be found via the link below.

[http://translate.googleusercontent.com/translate_c?hl=en&ie=UTF8&prev=_t&rurl=translate.google.com&sl=de&tl=en&u=http://www.vdr-portal.de/index.php%3Fpage%3DThread%26postid%3D859477&usg=ALkJrhjsaxmJbAqRePrY581qURuGtcD-cA](http://translate.googleusercontent.com/translate_c?hl=en&ie=UTF8&prev=_t&rurl=translate.google.com&sl=de&tl=en&u=http://www.vdr-portal.de/index.php%3Fpage%3DThread%26postid%3D859477&usg=ALkJrhjsaxmJbAqRePrY581qURuGtcD-cA)

---

