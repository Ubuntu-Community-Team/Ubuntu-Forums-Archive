---
title: "iwlwifi-6000g2a-4.ucode"
date: 2011-04-21
forum: Hardware
---

### Post by tooqui on 2011-04-21
Hi all,
I am an experienced linux (and google) user but this issue is driving me crazy...

Yesterday i received my brand new laptop dell 5520
4gb ram
intel i7-2620M
and wifi intel (my nightmare)

Installed maverick amd_64
the interface is not show on network management of in ifconfig. iwconfig is empty...

```
*-network UNCLAIMED
                description: Network controller
                product: 6000 Series Gen2
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 34
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress cap_list
                configuration: latency=0
                resources: memory:e3c00000-e3c01fff

```So starting to look around on internet saw that i needed to install a package for linux backports and i did:
```
sudo apt-get install linux-backports-modules-wireless-maverick-generic
```rebooted the system (yes I know... but i am an old windows user)

and on dmesg shows

```
jacobourdiales@jacobo-laptop:~$ dmesg |grep wla
[   11.403760] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   11.403763] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   11.403885] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.403924] iwlagn 0000:02:00.0: setting latency timer to 64
[   11.404010] iwlagn 0000:02:00.0: Detected 6000 Series 2x2 AGN Gen2a, REV=0xB0
[   11.420938] iwlagn 0000:02:00.0: device EEPROM VER=0x715, CALIB=0x6
[   11.421064] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   11.421301] iwlagn 0000:02:00.0: irq 48 for MSI/MSI-X
[   13.054025] iwlagn 0000:02:00.0: [COLOR=Red]request for firmware file 'iwlwifi-6000g2a-4.ucode' failed.[/COLOR]
[   13.054067] iwlagn 0000:02:00.0: [COLOR=Red]no suitable firmware found![/COLOR]
[   13.054317] iwlagn 0000:02:00.0: PCI INT A disabled
jacobourdiales@jacobo-laptop:~$ uname -r
2.6.35-29-generic

```gone to /lib/firmware and found this 
```
iwlwifi-6000-4.ucode   i[COLOR=Red]wlwifi-6000g2a-5.ucode[/COLOR]  iwlwifi-6000g2b-5.ucode
```man!! kernel is looking for a file and there is installed a higher version one.

Tried to remane and does not work (seems the version is hardcoded on file also) 

gone to [http://intellinuxwireless.org/?n=Downloads](http://intellinuxwireless.org/?n=Downloads) but there is the same version as on my laptop...

How can i solve this mess??  


Best regards and thanks in advance for you help!

---

### Post by tooqui on 2011-04-22
Finally I solved my own problem!
But i decided to post the solution in case somebody need help abut this.

The answer is that the kernel in maverick does not correctly support the driver and upgrading the kernell is the solution.

now i am working with kernell 2.6.38-8-generic

Finally decided to upgrade to ubuntu 11.4 as this was the simplest solution.

---

