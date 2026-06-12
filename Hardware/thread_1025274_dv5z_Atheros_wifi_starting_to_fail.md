---
title: "dv5z Atheros wifi starting to fail"
date: 2008-12-29
forum: Hardware
---

### Post by highlandsun on 2008-12-29
I also posted this on forum.notebookreview.com...

I've had my dv5z since late August. It generally worked OK, but now the wifi card is failing frequently. Sometimes on a bootup it's not even detected. Generally it stops working within a few minutes of bootup, when it actually gets detected. Has anyone else seen this? I have a feeling it's related to the overall high operating temperature of the machine, baking the card...

When the card starts to fail, the driver is no longer able to initialize it: (using Linux)

Dec 29 18:34:59 violino kernel: [ 1522.478531] ath9k: driver unloaded
Dec 29 18:35:25 violino kernel: [ 1548.212047] ath9k: 0.1
Dec 29 18:35:25 violino kernel: [ 1548.212047] ath9k 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 29 18:35:25 violino kernel: [ 1548.322439] ath_init: unable to attach hardware; HAL status 4294967291
Dec 29 18:35:25 violino kernel: [ 1548.322535] ath9k 0000:08:00.0: PCI INT A disabled

Googling for the HAL status message only gets 1 hit, on this Norwegian site.

[http://www.diskusjon.no/lofiversion/.../t1035581.html](http://www.diskusjon.no/lofiversion/.../t1035581.html)

I'm also running Ubuntu 8.10...

When it's operating, the failures start like so:
Dec 27 12:15:47 violino kernel: [14099.310748] ForceXPAon: 0
Dec 27 12:17:21 violino kernel: [14193.479020] wlan0: No ProbeResp from current AP 00:12:17:26:56:10 - assume out of range
Dec 27 12:17:23 violino kernel: [14195.062940] ath_drain_txdataq: unable to reset hardware; hal status 4294936576
Dec 27 12:17:23 violino kernel: [14195.386940] ath_set_channel: unable to reset channel 1 (2412Mhz) flags 0x300e2 hal status 4294936577
Dec 27 12:17:23 violino kernel: [14195.387769] ath9k_config: Unable to set channel
Dec 27 12:17:24 violino kernel: [14196.862940] ath_drain_txdataq: unable to reset hardware; hal status 4294936576
Dec 27 12:17:25 violino kernel: [14197.190941] ath_set_channel: unable to reset channel 2 (2417Mhz) flags 0x300e2 hal status 4294936577
Dec 27 12:17:25 violino kernel: [14197.190941] ath9k_config: Unable to set channel

Has anyone else seen this? If not, I suspect you're going to soon... I don't think it's a driver issue, since things were working fine before and the software hasn't changed. It just looks like the hardware is dying in use.

Some more info... When the card is working, Linux sees it as:

lspci -v
...
08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
Subsystem: Hewlett-Packard Company Device 1381
Flags: bus master, fast devsel, latency 0, IRQ 17
Memory at d1200000 (64-bit, non-prefetchable) [size=64K]
Capabilities: [40] Power Management version 2
Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
Capabilities: [60] Express Legacy Endpoint, MSI 00
Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
Capabilities: [100] Advanced Error Reporting
Capabilities: [140] Virtual Channel
Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
Kernel driver in use: ath9k
Kernel modules: ath9k

When it starts failing, the card's PCI config space is corrupted:
lspci -v
...
08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev ff) (prog-if ff)
!!! Unknown header type 7f
Kernel driver in use: ath9k
Kernel modules: ath9k

---

