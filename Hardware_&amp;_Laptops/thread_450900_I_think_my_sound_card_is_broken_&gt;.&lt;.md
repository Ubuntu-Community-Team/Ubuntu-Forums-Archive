---
title: "I think my sound card is broken &gt;.&lt;"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by Rumplesmigskin on 2007-05-21
<introductory stuff>
Hi all
Been using Linux a few years now, love it to bits. Dual-booting anyway, 'cause it's the smarter thing to do.
</introductory stuff>

Anyhow, I got a nasty surprise today - the sound on my laptop (a Dell Inspiron 1300) stopped working. Period. 
My guess is that the hardware is dead or something, since I usually plug the laptop's headphone jack into an amplifier (with added nummy speakers). 
Funny thing is, it never caused problems before though. I've been doing it for years. 
Even an internet cafe I do part-time work in has a 3.5mm jack to 2 phono going from the main computer to an amp. 

Hardware being dead is the worst-case scenario anyways, so I'm hoping it's just a stupid thing that I managed to miss.. ^^
So, lspci shows this:

```

rumple@deimos:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
**00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)**
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

No problems seem to be there; it detects my sound card fine.
Listing ALSA playback devices:

```

rumple@deimos:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Again, no problems seem evident here.

I have all the mixer volumes raised to max with alsamixer too. And they're not muted.
Still, no joy. Aplayer (or any audio player indeed for that matter) won't produce so much as a squeak.
Sound was working happily earlier on in the day, so this is definitely a strange occurrence.

Is this really a hardware problem? Can anyone give me some pointers here?

PS: Sound is dead on Windows 2000 as well. No amount of messing and fiddling around with *that* OS did any good either...

Cheers

---

### Post by onbongos on 2007-05-23
what bios? the A10 update from dell is supposed to fix alot of sound issues

---

