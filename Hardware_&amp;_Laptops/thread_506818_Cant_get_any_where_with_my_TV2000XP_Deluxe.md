---
title: "Cant get any where with my TV2000XP Deluxe"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by DriftShin on 2007-07-22
[SIZE="2"]I've been searching the net for info on how to install and configure my tuner card since i installed Ubuntu (started with Breezy now on Feisty). All the guides i have read are made for the RM and/or Expert cards. Mine is the Deluxe version which i bough in Australia (guess that should influence tuner type huh?). I've tried all the configurations that i have seen with no success. Soon as i open tvtime, it just flashes then closes. 

What am i doing wrong? Is the card not compatible with the kernel version (or just Feisty for that matter)? I had the same thing with the 2.6.20-15-generic version. I'm tired of PMing pple because its getting me nowhere. I love Ubuntu but i'm starting to get pissed off. [COLOR="Blue"]Win[/COLOR] XP looks so inviting right now!!!!

Heres my various outputs: (keep in mind i've tried various tuner types, 2, 5, 14.....)

```
driftshin@driftshin-desktop:~$ sudo rmmod bt878
Password:
ERROR: Module bt878 does not exist in /proc/modules
driftshin@driftshin-desktop:~$ sudo rmmod tuner
ERROR: Module tuner does not exist in /proc/modules
driftshin@driftshin-desktop:~$ sudo rmmod bttv
ERROR: Module bttv does not exist in /proc/modules

driftshin@driftshin-desktop:/etc/modprobe.d$ sudo modprobe bttv card=34 tuner=2
WARNING: /etc/modprobe.d/bttv line 1: ignoring bad line starting with 'modprobe'
FATAL: Error inserting bttv (/lib/modules/2.6.20-16-generic/kernel/drivers/media/video/bt8xx/bttv.ko): Invalid argument
```

```
01:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
Subsystem: LeadTek Research Inc. WinFast TV 2000
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 32 (4000ns min, 10000ns max)
Interrupt: pin A routed to IRQ 9
Region 0: Memory at d8100000 (32-bit, prefetchable) [size=4K]
Capabilities: <access denied>

01:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
Subsystem: LeadTek Research Inc. Unknown device 6606
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 32 (1000ns min, 63750ns max)
Interrupt: pin A routed to IRQ 18
Region 0: Memory at d8101000 (32-bit, prefetchable) [size=4K]
Capabilities: <access denied>
```[/SIZE]

---

