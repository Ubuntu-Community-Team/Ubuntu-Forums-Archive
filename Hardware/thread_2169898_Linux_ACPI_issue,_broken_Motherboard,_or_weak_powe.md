---
title: "Linux ACPI issue, broken Motherboard, or weak power supply?"
date: 2013-08-23
forum: Hardware
---

### Post by SweetAurora on 2013-08-23
Hi, I seem to be having trouble with an Intel DG33BU Motherboard. For some reason, the ACPI functions, specifically sleep, restart and shutdown are broken. I'm not sure if it's a Linux issue, hardware device issue ( like the board), or a PSU issue. 

The OS being used is Ubuntu 13.04 64Bit

Hardware currently used in the machine: 
Intel Pentium Dual-Core E5500
6GB DDR2 800MHz 1.8v ram (6-6-6-18 timings)
80GB Velociraptor drive + a 300GB WD drive for storage
Nvidia Quadro 600
Soundblaster X-FI XtremeGamer
Generic FireWire card
Lite-On DVD/CD-RW drive
Sentry MIXX 2 Fan controller
7 Fans. 3x140mm, 4x120mm
and a Ultra LSP 450w PSU

So when the motherboard is installed in the PC:
First with the restart issue. The computer dosen't seem to be able to do a soft restart, but instead it has to actually shutdown, then a couple seconds later, on it's own, turns back on and boots.

Shutdown on occasion hangs, where it will get to the plymouth screen, then freezes and requires me to hold the power button to turn off and then sometimes I have to throw the switch on the PSU cause the button doesn't respond. The shutdown issue almost, always, happens when sleep mode has been done once on the Computer per boot. 

Sleep mode issue is a bit scary (for possible system damage) and perplexing to me. Even though the BIOS is set to S3, the setting seems to be ignored and the computer enters what is best described as S1. I say "best described" as it doesn't seem to be a true S1 state. For one, the drives "Hard drives, cd-rom, and a fan controller" are still on and operational durring "sleep mode" but it seems only the 5v rail is actually powered and the 12v rail off. So only the controllers lights are on, the cd-drive flashes it's lights when the button is pushed to open, but doesn't actually do so, and who knows what going on with the HD's. 

Also to note, when I installed a Core 2 Duo E8400, it litterally melted itself down. I had a heatsink rated for 75 watts on it and it was idleing a between 68-72c and the heatsink was mounted properly using a bolt through kit. In fact, after shutting the down after I saw the crazy temps, I had to wait a couple of minutes before removing the heatsink because it was so hot. The E5500 on the otherhand is perfectly happy, ideling at ~32c and at 58c durring full load using the same heatsink as on the C2D.

When it came to trouble shooting, I already tried the usual stuff, Tried different CPU's, ram, and drive orders. As well as tested the PCI cards and Graphics card. 

So what might be the problem? Can anyone give an opinion or advice on what it could be the source of these issues? Thanks.

---

### Post by SweetAurora on 2013-08-24
I also forgot to mention that according to Intel, the DG33BU needs 3 Amps on the 5VSB line, my PSU only provides 2.5 Amps. But I'm not sure to trust Intel's specs since almost all their boards say 3A on the 5VSB no matter how big or small the board is.

---

### Post by SweetAurora on 2013-08-27
Becasue of the overwelming amount of support I have had here in this thread, I was able to find out on my own that it was the PSU to blame. So thank you everyone for giving time to give your opinions on the matter, If anyone is interested, the PSU I bought was a Fractal Integra 650w.

---

