---
title: "Audio card detected, no sound from speakers but earphones work fine"
date: 2023-09-27
forum: Hardware
---

### Post by Poleh on 2023-09-27
Hi 

similar to [this thread]("https://ubuntuforums.org/showthread.php?t=2441749") I have no sound from my speakers, however I have sound when plugging in my earphones.

Output on devices info etc. below. I have confirmed ALSA settings are good as well. I do have to select the correct device in alsamixer though - it defaults to a generic looking device per screenshots below.

Running Ubuntu 23.04, UEFI. Any help appreciated.

```

sudo lspci -vk |perl -lne 'print if /Audio/ .. /^[\w]*$/'
73:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Rembrandt Radeon High Definition Audio Controller
	Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Rembrandt Radeon High Definition Audio Controller
	Flags: bus master, fast devsel, latency 0, IRQ 91, IOMMU group 14
	Memory at dc4c8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [48] Vendor Specific Information: Len=08 <?>
	Capabilities: [50] Power Management version 3
	Capabilities: [64] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [2a0] Access Control Services
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

73:00.5 Multimedia controller: Advanced Micro Devices, Inc. [AMD] ACP/ACP3X/ACP6x Audio Coprocessor (rev 60)
	Subsystem: ASUSTeK Computer Inc. ACP/ACP3X/ACP6x Audio Coprocessor
	Flags: bus master, fast devsel, latency 0, IRQ 88, IOMMU group 18
	Memory at dc480000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: [48] Vendor Specific Information: Len=08 <?>
	Capabilities: [50] Power Management version 3
	Capabilities: [64] Express Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [2a0] Access Control Services
	Kernel driver in use: snd_pci_acp6x
	Kernel modules: snd_pci_acp3x, snd_rn_pci_acp3x, snd_pci_acp5x, snd_pci_acp6x, snd_acp_pci, snd_rpl_pci_acp6x, snd_pci_ps, snd_sof_amd_renoir, snd_sof_amd_rembrandt

73:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h/19h HD Audio Controller
	Subsystem: ASUSTeK Computer Inc. Family 17h/19h HD Audio Controller
	Flags: bus master, fast devsel, latency 0, IRQ 92, IOMMU group 19
	Memory at dc4c0000 (32-bit, non-prefetchable) [size=32K]
	Capabilities: [48] Vendor Specific Information: Len=08 <?>
	Capabilities: [50] Power Management version 3
	Capabilities: [64] Express Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [2a0] Access Control Services
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

```

```
sudo lshw -C multimedia
  *-multimedia:0            
       description: Audio device
       product: Rembrandt Radeon High Definition Audio Controller
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0.1
       bus info: pci@0000:73:00.1
       logical name: card0
       logical name: /dev/snd/controlC0
       logical name: /dev/snd/hwC0D0
       logical name: /dev/snd/pcmC0D3p
       logical name: /dev/snd/pcmC0D7p
       logical name: /dev/snd/pcmC0D8p
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:91 memory:dc4c8000-dc4cbfff
  *-multimedia:1
       description: Multimedia controller
       product: ACP/ACP3X/ACP6x Audio Coprocessor
       vendor: Advanced Micro Devices, Inc. [AMD]
       physical id: 0.5
       bus info: pci@0000:73:00.5
       version: 60
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=snd_pci_acp6x latency=0
       resources: irq:88 memory:dc480000-dc4bffff
  *-multimedia:2
       description: Audio device
       product: Family 17h/19h HD Audio Controller
       vendor: Advanced Micro Devices, Inc. [AMD]
       physical id: 0.6
       bus info: pci@0000:73:00.6
       logical name: card1
       logical name: /dev/snd/controlC1
       logical name: /dev/snd/hwC1D0
       logical name: /dev/snd/pcmC1D0c
       logical name: /dev/snd/pcmC1D0p
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:92 memory:dc4c0000-dc4c7fff
  *-usb
       description: Video
       product: USB2.0 FHD UVC WebCam: USB2.0 F
       vendor: Shinetech
       physical id: 1
       bus info: usb@5:1
       logical name: input10
       logical name: /dev/input/event8
       logical name: input9
       logical name: /dev/input/event7
       version: 0.03
       serial: 200901010001
       capabilities: usb-2.01 usb
       configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s

```

[ATTACH=CONFIG]292798[/ATTACH][ATTACH=CONFIG]292799[/ATTACH]

---

### Post by Poleh on 2023-11-17
*bump* still having this issue with no luck on latest releases and updates. wondering if anyone has any bright ideas...

---

