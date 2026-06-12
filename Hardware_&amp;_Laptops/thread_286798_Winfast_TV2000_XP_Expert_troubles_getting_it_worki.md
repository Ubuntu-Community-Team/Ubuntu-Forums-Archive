---
title: "Winfast TV2000 XP Expert troubles getting it working"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by _francis on 2006-10-28
hey,

i've a pretty fresh edgy installation and after some troubles with my wireless card everything is working fine EXCEPT the winfast card!

i installed tvtime and xawtv with apt-get but both programms don't get any signal from the television source.

xawtv screen is black and tvtime-scanner finds nothing. 

lspci output is:

00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
00:06.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 0a)
00:08.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:0a.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)


so the card is recognised, isn't it?

'cause i'm pretty new to linux i don't 've any idea what to do. searched through the forum and googled the problem but found no clue.

anyone who got the card working?

Help appreciated...

thx

---

### Post by lazyart on 2006-10-28
I have one of these and didnt even know it was possible to use it... I might now.

Anyhow, it's a pretty involved process, outlined here: [http://64.233.187.104/search?q=cache:Hb28HqNQOFEJ:home.sch.bme.hu/~dss/+winfast+linux&hl=en&gl=us&ct=clnk&cd=2&client=firefox](http://64.233.187.104/search?q=cache:Hb28HqNQOFEJ:home.sch.bme.hu/~dss/+winfast+linux&hl=en&gl=us&ct=clnk&cd=2&client=firefox)

It involves recompiling the kernal.  Not for the faint of heart. :(

---

### Post by _francis on 2006-10-28
thanks a lot. i will work through that tomorrow (hopefully with some positive results)

---

### Post by chedabob on 2006-11-05
For me, I just installed xawtv and tvtime. Xawtv went fullscreen and crashed after a while, tvtime got all the channels straight away.

---

