---
title: "No /dev/video0"
date: 2009-04-12
forum: Hardware
---

### Post by tazthecat on 2009-04-12
I'm trying to watch tv on my pc but it doesn't work.

all seems ok but no /dev/video0 is created.

lsmod | grep tv
tveeprom               20100  1 cx23885

[   12.770927] CORE cx23885[0]: subsystem: 0070:71d3, board: Hauppauge WinTV-HVR1200 [card=7,autodetected]
[   12.792139] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   12.792343] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   12.792345] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   12.792347] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   12.936450] tveeprom 2-0050: Hauppauge model 71949, rev H2E9, serial# 3064431
[   12.936454] tveeprom 2-0050: MAC address is 00-0D-FE-2E-C2-6F
[   12.936457] tveeprom 2-0050: tuner model is Philips 18271_8295 (idx 149, type 54)
[   12.936460] tveeprom 2-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[   12.936463] tveeprom 2-0050: audio processor is CX23885 (idx 39)
[   12.936465] tveeprom 2-0050: decoder processor is CX23885 (idx 33)
[   12.936466] tveeprom 2-0050: has no radio
[   12.936468] cx23885[0]: hauppauge eeprom: model=71949
[   12.936471] cx23885_dvb_register() allocating 1 frontend(s)
[   12.936474] cx23885[0]: cx23885 based dvb card
[   13.050416] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   13.050422] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[   13.050528] HDA Intel 0000:00:05.0: setting latency timer to 64
[   13.098232] tda829x 3-0042: type set to tda8295
[   13.145140] tda18271 3-0060: creating new instance
[   13.180351] TDA18271HD/C1 detected @ 3-0060
[   13.440016] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   14.229965] DVB: registering new adapter (cx23885[0])
[   14.229971] DVB: registering adapter 0 frontend -1 (NXP TDA10048HN DVB-T)...
[   14.230434] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   14.230442] cx23885[0]/0: found at 0000:04:00.0, rev: 2, irq: 16, latency: 0, mmio: 0xfd800000
[   14.230449] cx23885 0000:04:00.0: setting latency timer to 64

If you need more info just ask.

I just want to watch cable tv.

thanks

---

