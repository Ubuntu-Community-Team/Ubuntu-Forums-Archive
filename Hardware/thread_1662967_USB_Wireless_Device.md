---
title: "USB Wireless Device"
date: 2011-01-09
forum: Hardware
---

### Post by nova47 on 2011-01-09
I've got a ubiquiti srx 300 mw plugged in to a USB card reader and I've not been able to get Ubuntu to run it. When I type ifup eth0 to bring the ethernet up at the end of the output is 

if-up.d/mountnfs[eth0]: waiting for interface eth1 before doing NFS mounts
if-up.d/mountnfs[eth0]: waiting for interface eth2 before doing NFS mounts
if-up.d/mountnfs[eth0]: waiting for interface ath0 before doing NFS mounts
if-up.d/mountnfs[eth0]: waiting for interface wlan0 before doing NFS mounts

So it clearly detects that there is some sort of wireless card there. (It does not display ath0 or wlan0 if the card is not plugged in). However when I type ifconfig -a it doesn't show up and ifup ath0 and ifup wlan0 won't work. I can also tell the card reader is detected by typing lsusb which contains

Bus 002 Device 002: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter

Question is how do I get the wireless card working?

---

### Post by IcarusR on 2011-01-09
> Bus 002 Device 002: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter

That is an audio controller.
From  AK5370 datasheet

> The AK5370 is AD converter for USB audio, especially USB microphone

Remove wifi card then reinstall then run & post full results of these two

```
dmesg | tail -n 20
```

```
lsusb
```

---

### Post by nova47 on 2011-01-09
lol well don't I feel foolish. Anyway I'm not sure what I'm supposed to reinstall. The built in madwifi drivers cover the card should I reinstall those? Here's the output of the commands:

[PHP]

vgaarb: device changed decodes: PCI:0000:06:00.0,olddecodes=io+mem,decodes=none:owns=none
NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.29  Wed Dec  8 12:09:09 PST 2010
hda_codec: ALC1200: BIOS auto-probing.
lp: driver loaded but no devices found
Adding 1322964k swap on /dev/sda6.  Priority:-1 extents:1 across:1322964k
EXT3-fs (sda5): using internal journal
ip_tables: (C) 2000-2006 Netfilter Core Team
forcedeth 0000:00:11.0: irq 45 for MSI/MSI-X
NET: Registered protocol family 10
lo: Disabled Privacy Extensions
vmap allocation for size 16781312 failed: use vmalloc=<size> to increase size.
NVRM: RmInitAdapter failed! (0x26:0xffffffff:1029)
NVRM: rm_init_adapter(1) failed
vmap allocation for size 16781312 failed: use vmalloc=<size> to increase size.
NVRM: RmInitAdapter failed! (0x26:0xffffffff:1029)
NVRM: rm_init_adapter(1) failed
vmap allocation for size 16781312 failed: use vmalloc=<size> to increase size.
NVRM: RmInitAdapter failed! (0x26:0xffffffff:1029)
NVRM: rm_init_adapter(2) failed
eth0: no IPv6 routers present


Bus 002 Device 006: ID 1532:0102 Razer USA, Ltd Tarantula Keyboard
Bus 002 Device 005: ID 046d:c216 Logitech, Inc. Dual Action Gamepad
Bus 002 Device 004: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 002 Device 003: ID 1532:000c Razer USA, Ltd
Bus 002 Device 002: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

[/PHP]

I went ahead and booted to my windows partition to confirm that it was working. It shows up in device manager as a USB to Express card converter. It doesn't seem to be showing up with lsusb. I ran the command with and without it plugged in and the results are the same either way.

---

### Post by IcarusR on 2011-01-09
> Anyway I'm not sure what I'm supposed to reinstall

Sorry my fault, I meant remove then re-plug in the wireless card then run

```
dmesg | tail -n 20
```

To see if there is any mention of the wireless card, & to see weather ubuntu sees it.

---

### Post by nova47 on 2011-01-09
Ya I tried that a couple of time same result unfortunately. One can always hope. I also went back and ran ifup without it in there and ath0 still showed up. (I must just not have noticed it before. It works just fine on Windows but Ubuntu doesn't seem to be noticing that it's even there.

---

### Post by nova47 on 2011-01-30
Bump*

---

