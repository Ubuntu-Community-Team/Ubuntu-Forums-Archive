---
title: "I disabled or fried my sound card?"
date: 2008-09-25
forum: Hardware
---

### Post by treehouse on 2008-09-25
So I was messing around trying to record off my guitar into my computer. I had done so before, plugging my electric into a combo amp, then the amp into the soundcard (I forget which plug) and it distorted it all to hell. I tried again this time with my acoustic/electric after my friend told me he got his to work with Audacity on his Windoze box straight into the card.

When I plugged into line in (straight from guitar) I got no response. I switch to mic input and immediately I got this chopped buzzing sound and everything locked up.

I rebooted and now there's no sound. If I try to open the volume control I get: "No volume control GStreamer plugins and/or devices found." Sound preferences shows no audio device. "cat /proc/interrupts" doesn't list my soundcard. "lspci -v" actually shows it, saying:
```

00:0d.0 Class ffff: Creative Labs SB Live! EMU10k1 (rev 08)
	Subsystem: Creative Labs CT4832 SBLive! Value
	Flags: medium devsel, IRQ 11
	I/O ports at <unassigned> [disabled]
	Capabilities: [dc] Power Management version 1

```

Can I just re-enable it? I'm at a complete loss.


EDIT: I just realised, I've had onboard sound, as well as this PCI card, but I don't see it anywhere as a valid device either. I'm not sure if I've ever seen it as a device.

---

### Post by treehouse on 2008-09-25
bump (sorry)

---

### Post by treehouse on 2008-09-26
Or possibly someone knows where I could look for more help on this? I'm completely stuck. I don't really know why it would be listed in lspci but as disabled. The OS obviously can tell that it's there, and it's operating enough to list what brand it is and all manner of info about it, but for some reason I can't use it for anything.

EDIT: "asoundconf list" shows no soundcards, neither the soundblaster or the onboard

---

### Post by kostkon on 2008-09-26
> **treehouse said:**
> Or possibly someone knows where I could look for more help on this? I'm completely stuck. I don't really know why it would be listed in lspci but as disabled. The OS obviously can tell that it's there, and it's operating enough to list what brand it is and all manner of info about it, but for some reason I can't use it for anything.

EDIT: "asoundconf list" shows no soundcards, neither the soundblaster or the onboard
Yes, it seems that you may have fried your card. As fas as the onboard one, make sure that it is enabled from the BIOS.

---

### Post by treehouse on 2008-09-26
Thanks :(

---

### Post by nautaforever on 2009-06-23
I happened to do the same stunt and fried my onboard speakers a well. it is still able to list the sound card devices and there is some kind of a crackling sound when i try to play any sound. 

here is the output i got :


bharath@bharath-laptop:~$ asoundconf list
Names of available sound cards:
SB
bharath@bharath-laptop:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
	Subsystem: Acer Incorporated [ALI] Device 010f
	Flags: bus master, 66MHz, medium devsel, latency 64
	Kernel modules: ati-agp

// omitted other lists 

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
	Subsystem: Acer Incorporated [ALI] Device 010f
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Acer Incorporated [ALI] Device 010f
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at a000 [size=256]
	Memory at b0301c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp

bharath@bharath-laptop:~$ 





can somebody help me please? i think it is a hardware problem but is there any other fixes somebody can suggest ?


I have an ACER Aspire 5050

---

### Post by nautaforever on 2009-06-24
Hey the sound came back on after i reinstalled Ubuntu. guess it was a software problem afterall.

Im a total newbie but ive seen that after most screwups a fresh install is the best thing to do

---

