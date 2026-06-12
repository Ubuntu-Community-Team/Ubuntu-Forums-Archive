---
title: "HELP! Cant get audio working on laptop!"
date: 2007-10-13
forum: Hardware &amp; Laptops
---

### Post by TemLeaf on 2007-10-13
Hi everyone, I'm an absolute newbie.

I have just loaded Xubuntu Fiesty Fawn onto my old Compaq Presario 1925.  Things are going well with it, I just can't seem to get my sound working no matter how many different guides I read through.  I have tried unsuccessfully to install the Alsa driver, lib, utils by following the sound troubleshooting guide on this forum.

Here's some of the troubles I've come across:
- When I put an audio cd in, it doesnt automount and i get an error when I try to mount it.
- When I try to play an audio cd in Rhytmbox, Banshee, etc, the program just crashes with no response whatsoever.
- When I try to open up Gxine, i get the splash screen and then its just crashes.
- When I open up Mixer Settings it only lists "default" under Device and has no other options
- I type alsamixer in the terminal and get this:
alsamixer: funtion snd_ctl_open failed for default: No such device

when i type in lspci -vvnn i get this:

01:00.1 Multimedia audio controller [0401]:  Neomagic Corporation NM2200 [MagicMedia 256AV Audio] [10c8:8005] (rev 20)
Subsystem: Compaq Computer Corporation Unknown device [0ell:b0d1]
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B+
Status: Cap+ 66MHz- UDF- Fast B2b+ ParErr- DEVSEL=medium >TAbort- <MAbort- >SERR- <PERR-
Interrupt: pin B routed to IRQ 10
Region 0: Memory at f4800000 (32 bit, prefetchable) [size=4M]
Region 0: Memory at f4200000 (32 bit, non-prefetchable) [size=1M]
Capabilities: <access denied>

I installed VLC and was able to play some .mov files, however without sound

I would appreciate greatly anyone that could help me get this baby firing with sound!  I REALLY dont want to cross back to the dark side of Windows!! :grin:

cheers

---

