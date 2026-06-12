---
title: "Requesting firmware, but it is there!"
date: 2010-10-14
forum: Hardware
---

### Post by tancrackers on 2010-10-14
So I am i686 Lucid Ubuntu on a Toshiba Satellite and my wireless randomly drops.
Wireless card: Intel wifi link 5100 (of course the millionth person!!!)
My wireless conncetion randomly drops!
I turned off hibernation, turned off sleep, turned off idle turn off display. So... ?

[PHP]john@john-laptop:~$ dmesg | grep iwl
[   19.006215] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   19.006217] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   19.006349] iwlagn 0000:03:00.0: power state changed by ACPI to D0
[   19.006432] iwlagn 0000:03:00.0: power state changed by ACPI to D0
[   19.006470] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.006506] iwlagn 0000:03:00.0: setting latency timer to 64
[   19.006582] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   19.029122] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   19.029407] iwlagn 0000:03:00.0: irq 30 for MSI/MSI-X
[   19.039394] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[   19.071224] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   43.831344] iwlagn 0000:03:00.0: iwl_tx_agg_start on ra = 58:bc:27:0e:d7:30 tid = 0
[/PHP]

I have the driver installed but is says that it is requesting the firmware. But the ucode blah -2 is in the folder lib/firmware ! So... Why isn't it seeing it?
before it said : firmware: requesting iwlwifi-5000-2.ucode
but i forgot which command, the above command might not be it...

---

