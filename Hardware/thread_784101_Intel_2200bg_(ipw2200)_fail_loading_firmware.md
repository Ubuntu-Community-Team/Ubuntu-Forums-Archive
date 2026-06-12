---
title: "Intel 2200bg (ipw2200) fail loading firmware"
date: 2008-05-06
forum: Hardware
---

### Post by krazyd on 2008-05-06
This is the relevant section of the system log output:> 06/05/08 19:22:16	lappy	kernel	[   29.102039] ieee80211_crypt: registered algorithm 'NULL'
06/05/08 19:22:16	lappy	kernel	[   29.135189] ieee80211: 802.11 data/management/control stack, git-1.1.13
06/05/08 19:22:16	lappy	kernel	[   29.135193] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
06/05/08 19:22:16	lappy	kernel	[   29.205006] nvidia: module license 'NVIDIA' taints kernel.
06/05/08 19:22:16	lappy	kernel	[   29.619706] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
06/05/08 19:22:16	lappy	kernel	[   29.619710] ipw2200: Copyright(c) 2003-2006 Intel Corporation
06/05/08 19:22:16	lappy	kernel	[   29.619789] PCI: Enabling device 0000:02:05.0 (0000 -> 0002)
06/05/08 19:22:16	lappy	kernel	[   29.619800] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 21 (level, low) -> IRQ 22
06/05/08 19:22:16	lappy	kernel	[   29.619809] PCI: Setting latency timer of device 0000:02:05.0 to 64
06/05/08 19:22:16	lappy	kernel	[   29.624443] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
06/05/08 19:22:16	lappy	kernel	[   29.673657] sdhci: Secure Digital Host Controller Interface driver
06/05/08 19:22:16	lappy	kernel	[   29.673661] sdhci: Copyright(c) Pierre Ossman
06/05/08 19:22:16	lappy	kernel	[   30.378259] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x3aa0b4, caps: 0xa04713/0x200000
06/05/08 19:22:16	lappy	kernel	[   30.421232] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio3/input/input7
06/05/08 19:22:16	lappy	kernel	[   30.974011] ipw2200: Unable to load ucode: -22
06/05/08 19:22:16	lappy	kernel	[   30.974032] ipw2200: Unable to load firmware: -22
06/05/08 19:22:16	lappy	kernel	[   30.974827] ipw2200: failed to register network device
06/05/08 19:22:16	lappy	kernel	[   30.974882] ACPI: PCI interrupt for device 0000:02:05.0 disabled
06/05/08 19:22:16	lappy	kernel	[   30.974898] ipw2200: probe of 0000:02:05.0 failed with error -5The last five lines are the most relevant, but I've included the others for context. 

I have not had any luck finding any info on this error.. google has some info but nothing recent.

The correct firmware is in /lib/firmware/2.6.24-17-generic.

This is a common chip so I find it strange that I haven't found anyone else with this issue. I thought that Intel wireless was out-of-the-box these days with linux. Can anyone point me in the right direction?
Thanks.

---

### Post by krazyd on 2008-05-07
found the bug report relating to my issue.. but no resolution:
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/180544](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/180544)

If anyone can help out, please let me know!

---

