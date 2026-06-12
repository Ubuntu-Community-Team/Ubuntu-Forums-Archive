---
title: "BT878 TV Tuner / no audio"
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by v-jmorri on 2007-02-09
Hi,
I am trying to get a Pinnacle TV tuner card working with Edgy.  This same hardware worked earlier this week on Fedora 2.  I can get video without a problem, but I don't get any audio.  I have plugged speakers into the audio out on the tuner card to rule out any sound card problems.  Here is the output of my dmesg  

```

[42949388.750000] bttv: driver version 0.9.16 loaded
[42949388.750000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[42949388.750000] bttv: Bt8xx card found (0).
[42949388.750000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 193
[42949388.750000] bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 193, latency: 32, mmio: 0xdddfe000
[42949388.750000] bttv0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012
[42949388.750000] bttv0: using: Pinnacle PCTV Studio Pro [card=52,insmod option]
[42949388.750000] bttv0: gpio: en=00000000, out=00000000 in=00ffefff [init]
[42949388.750000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[42949388.750000] bttv0: pinnacle/mt: id=5 info="NTSC / mono" radio=no
[42949388.750000] bttv0: using tuner=33
[42949388.750000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[42949388.760000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[42949388.760000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[42949388.820000] tda9887 1-0043: chip found @ 0x86 (bt878 #0 [sw])
[42949388.900000] tuner 1-0060: Chip ID is not zero. It is not a TEA5767
[42949388.900000] tuner 1-0060: chip found @ 0xc0 (bt878 #0 [sw])
[42949388.910000] tuner 1-0060: microtune: companycode=3cbf part=42 rev=99
[42949388.910000] tuner 1-0060: microtune MT2050 found, OK
[42949388.950000] bttv0: registered device video0
[42949388.950000] bttv0: registered device vbi0
[42949388.950000] bttv0: PLL: 28636363 => 35468950 .. ok
[42949389.030000] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 201
[42949389.030000] PCI: Via IRQ fixup for 0000:00:11.5, from 5 to 9
[42949389.030000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[42949389.080000] bt878: AUDIO driver version 0.0.0 loaded
[42949389.250000] NET: Registered protocol family 10
[42949389.250000] lo: Disabled Privacy Extensions
[42949389.250000] IPv6 over IPv4 tunneling driver
[42949389.560000] bt878: Bt878 AUDIO function found (0).
[42949389.560000] ACPI: PCI Interrupt 0000:00:09.1[A] -> GSI 17 (level, low) -> IRQ 193
[42949389.560000] bt878_probe: card id=[0x1211bd], Unknown card.
[42949389.560000] Exiting..
[42949389.560000] ACPI: PCI interrupt for device 0000:00:09.1 disabled
[42949389.560000] bt878: probe of 0000:00:09.1 failed with error -22

```

lspci shows that 0000:00:09.1 is the bt878 Audio Capture:
```

# lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
<snip>

```

Why is this failing, and any idea what error -22 means?  I am hoping to get this working by this weekend or I may have to put Fedora (shudder) back on.  My Freevo PVR system isn't able to record anything right now. :(

Thanks!
Jon

---

