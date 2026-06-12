---
title: "CRYSTAL CS4235 sound problem"
date: 2005-08-04
forum: Hardware &amp; Laptops
---

### Post by rocktorrentz on 2005-08-04
I have just installed Ubuntu on an old P3 system, to see what I would make of it. After installing, all of my hardware was detected except for my sound card. The device manager program does not show my sound card which I have discovered from the net is a CRYSTAL CS4235 that is a chip on the motherboard. I am assuming that it is just a case of manually detecting it or installing a driver but I would not know how to go about it. 

On one guide it said to type lspci in terminal so here are the results (that don't appear to include my sound card):

> sam@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:10.0 Ethernet controller: Digital Equipment Corporation DECchip 21140 [FasterNet] (rev 22)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

If anyone on here can help I would be very greatful
cheers
rocktorrentz

---

### Post by rocktorrentz on 2005-08-05
Someone on here must have some idea of what to do? Or a tip for me to work it out myself? :-|

---

### Post by orev on 2005-08-05
Are you using ALSA?  If so, you may be able to find more information on the ALSA website.(?)

---

### Post by rocktorrentz on 2005-08-05
[QUOTE=orev]Are you using ALSA?  If so, you may be able to find more information on the ALSA website.(?)[/QUOTE]

I don't know. I am just using a standard ubuntu installation. I think it is a problem with the OS not realising the card is there rather than software not seeing it. However I don't know much about linux at all :p

---

### Post by wvslkr on 2005-08-05
[https://wiki.ubuntu.com/forum/hardware/OldSoundCard](https://wiki.ubuntu.com/forum/hardware/OldSoundCard) :)

---

### Post by Krank on 2006-08-12
Right, this looks familiar. Very familiar. Indeed, it seems like the exact same problem I have.

The computer I'm having trouble with is a Fujitsu something-or-other, with a Crystal CS4235 onboard sound chip. lspci gives me the exact same output as the original poster.

Windows has no trouble at all recognizing the card. Modprobing for snd-cs4236 (the recommended card) gives me "no such device".

...and yet - dmesg gives me:

[   29.148408] isapnp: Scanning for PnP cards...
[   29.247576] isapnp: Card 'CS4235'
[   29.247592] isapnp: 1 Plug & Play card detected total

...which suggests, at least, that SOMETHING (isapnp, whatever that is) recognizes the card.

This is beginning to annoy me. ,Whenever I try to get some older comp or soundcard working in Linux/Ubuntu, there's at least 10-40 hours of work to be done.


Oh, and I'm running Dapper, with blackbox as my window manager. Shouldn't matter, though... The comp is a PII 350 mhz with about 300 mb's of RAM.

---

