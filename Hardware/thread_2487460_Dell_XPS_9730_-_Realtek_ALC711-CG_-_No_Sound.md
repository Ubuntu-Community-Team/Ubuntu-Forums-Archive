---
title: "Dell XPS 9730 - Realtek ALC711-CG - No Sound"
date: 2023-06-05
forum: Hardware
---

### Post by raiinzen on 2023-06-05
Hello,
I've been attempting to get my audio working for about a week now, and nothing seems to do the trick.  Nothing is muted, and it is currently showing me 3 audio options under PulseAudio Volume Control, and none of them are working: : 
sof-hda-dsp Pro
sof-hda-dsp Pro 2
sof-hda-dsp Pro 3

From everything I can find on the subject, it looks like maybe it's impossible to get audio on this laptop?   
I've tried this tutorial [https://blog.fts.scot/2020/07/04/dell-xps-2020-how-to-get-audio-working-on-linux/](https://blog.fts.scot/2020/07/04/dell-xps-2020-how-to-get-audio-working-on-linux/) amongst many others, and always run nto a snag.  On this one, I can't utilize dkms.  

Thank you for any help!  I'd LOVE to get Linux up on this computer.  


Here's my lspci -v
```
[FONT=monospace]
0000:00:00.0 Host bridge: Intel Corporation Device a706 
        Subsystem: Dell Device 0bda 
        Flags: bus master, fast devsel, latency 0, IOMMU group 1 
        Capabilities: <access denied> 

0000:00:01.0 PCI bridge: Intel Corporation Device a70d (prog-if 00 [Normal decode]) 
        Subsystem: Dell Device 0bda 
        Flags: bus master, fast devsel, latency 0, IRQ 122, IOMMU group 2 
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0 
        I/O behind bridge: 3000-3fff [size=4K] [16-bit] 
        Memory behind bridge: ab000000-abffffff [size=16M] [32-bit] 
        Prefetchable memory behind bridge: 6000000000-6201ffffff [size=8224M] [32-bit] 
        Capabilities: <access denied> 
        Kernel driver in use: pcieport 

0000:00:02.0 VGA compatible controller: Intel Corporation Raptor Lake-P [Iris Xe Graphics] (rev 04) (prog-if 0
0 [VGA controller]) 
        Subsystem: Dell Device 0bda 
        Flags: bus master, fast devsel, latency 0, IRQ 202, IOMMU group 0 
        Memory at 628e000000 (64-bit, non-prefetchable) [size=16M] 
        Memory at 4000000000 (64-bit, prefetchable) [size=256M] 
        I/O ports at 4000 [size=64] 
        Expansion ROM at 000c0000 [virtual] [disabled] [size=128K] 
        Capabilities: <access denied> 
        Kernel driver in use: i915 
        Kernel modules: i915 

0000:00:04.0 Signal processing controller: Intel Corporation Device a71d 
        Subsystem: Dell Device 0bda 
        Flags: bus master, fast devsel, latency 0, IRQ 220, IOMMU group 3 
        Memory at 628f280000 (64-bit, non-prefetchable) [size=128K] 
        Capabilities: <access denied> 
        Kernel driver in use: proc_thermal_pci 
        Kernel modules: processor_thermal_device_pci 

0000:00:06.0 System peripheral: Intel Corporation RST VMD Managed Controller 
        Flags: fast devsel, IOMMU group 4 

0000:00:07.0 PCI bridge: Intel Corporation Device a76e (prog-if 00 [Normal decode]) 
        Subsystem: Dell Device 0bda 
        Flags: bus master, fast devsel, latency 0, IRQ 123, IOMMU group 5 
        Bus: primary=00, secondary=02, subordinate=2b, sec-latency=0 
        I/O behind bridge: 5000-5fff [size=4K] [16-bit] 
        Memory behind bridge: 9e000000-aa1fffff [size=194M] [32-bit] 
        Prefetchable memory behind bridge: 6210000000-622bffffff [size=448M] [32-bit] 
        Capabilities: <access denied> 
        Kernel driver in use: pcieport 

0000:00:07.1 PCI bridge: Intel Corporation Device a73f (prog-if 00 [Normal decode]) 
        Subsystem: Dell Device 0bda 
        Flags: bus master, fast devsel, latency 0, IRQ 124, IOMMU group 6 
        Bus: primary=00, secondary=2c, subordinate=55, sec-latency=0 
        I/O behind bridge: 6000-6fff [size=4K] [16-bit] 
        Memory behind bridge: 90000000-9c1fffff [size=194M] [32-bit] 
        Prefetchable memory behind bridge: 6230000000-624bffffff [size=448M] [32-bit] 
        Capabilities: <access denied> 
        Kernel driver in use: pcieport 

0000:00:07.2 PCI bridge: Intel Corporation Device a72f (prog-if 00 [Normal decode]) 
        Subsystem: Dell Device 0bda 
        Flags: bus master, fast devsel, latency 0, IRQ 125, IOMMU group 7 
        Bus: primary=00, secondary=56, subordinate=7f, sec-latency=0 
        I/O behind bridge: 7000-7fff [size=4K] [16-bit] 
        Memory behind bridge: 82000000-8e1fffff [size=194M] [32-bit] 
        Prefetchable memory behind bridge: 6250000000-626bffffff [size=448M] [32-bit] 
        Capabilities: <access denied> 
        Kernel driver in use: pcieport 

0000:00:07.3 PCI bridge: Intel Corporation Device a71f (prog-if 00 [Normal decode]) 
        Subsystem: Dell Device 0bda 
        Flags: bus master, fast devsel, latency 0, IRQ 126, IOMMU group 8 
        Bus: primary=00, secondary=80, subordinate=a9, sec-latency=0 
        I/O behind bridge: 8000-8fff [size=4K] [16-bit] 
        Memory behind bridge: 74000000-801fffff [size=194M] [32-bit] 
        Prefetchable memory behind bridge: 6270000000-628bffffff [size=448M] [32-bit] 
        Capabilities: <access denied> 
        Kernel driver in use: pcieport 

0000:00:08.0 System peripheral: Intel Corporation Device a74f 
        Subsystem: Dell Device 0bda 
        Flags: fast devsel, IRQ 255, IOMMU group 9 
        Memory at 628f2f3000 (64-bit, non-prefetchable) [disabled] [size=4K] 
        Capabilities: <access denied> 

0000:00:0a.0 Signal processing controller: Intel Corporation Device a77d (rev 01) 
        Subsystem: Dell Device 0bda 
        Flags: fast devsel, IOMMU group 10 
        Memory at 628f2d0000 (64-bit, non-prefetchable) [size=32K] 
        Capabilities: <access denied> 
        Kernel driver in use: intel_vsec 
        Kernel modules: intel_vsec 

0000:00:0d.0 USB controller: Intel Corporation Device a71e (prog-if 30 [XHCI]) 
        Subsystem: Dell Device 0bda 
        Flags: bus master, medium devsel, latency 0, IRQ 148, IOMMU group 11 
        Memory at 628f2c0000 (64-bit, non-prefetchable) [size=64K] 
        Capabilities: <access denied> 
        Kernel driver in use: xhci_hcd 
        Kernel modules: xhci_pci 

0000:00:0d.2 USB controller: Intel Corporation Device a73e (prog-if 40 [USB4 Host Interface]) 
        Subsystem: Dell Device 0bda 
        Flags: bus master, fast devsel, latency 0, IRQ 16, IOMMU group 11 
        Memory at 628f240000 (64-bit, non-prefetchable) [size=256K] 
        Memory at 628f2f2000 (64-bit, non-prefetchable) [size=4K] 
        Capabilities: <access denied> 
        Kernel driver in use: thunderbolt 
        Kernel modules: thunderbolt 

0000:00:0d.3 USB controller: Intel Corporation Device a76d (prog-if 40 [USB4 Host Interface]) 
        Subsystem: Dell Device 0bda 
        Flags: bus master, fast devsel, latency 0, IRQ 16, IOMMU group 11 
        Memory at 628f200000 (64-bit, non-prefetchable) [size=256K] 
        Memory at 628f2f1000 (64-bit, non-prefetchable) [size=4K] 
        Capabilities: <access denied> 
        Kernel driver in use: thunderbolt 
        Kernel modules: thunderbolt 

0000:00:0e.0 RAID bus controller: Intel Corporation Volume Management Device NVMe RAID Controller Intel Corpor
ation 
        Subsystem: Dell Volume Management Device NVMe RAID Controller Intel Corporation 
        Flags: bus master, fast devsel, latency 0, IOMMU group 12 
        Memory at 628c000000 (64-bit, non-prefetchable) [size=32M] 
        Memory at 72000000 (32-bit, non-prefetchable) [size=32M] 
        Memory at 628f100000 (64-bit, non-prefetchable) [size=1M] 
        Capabilities: <access denied> 
        Kernel driver in use: vmd 
        Kernel modules: vmd, ahci 

0000:00:12.0 Serial controller: Intel Corporation Alder Lake-P Integrated Sensor Hub (rev 01) (prog-if 00 [825
0]) 
        Subsystem: Dell Device 0bda 
        Flags: bus master, fast devsel, latency 0, IRQ 26, IOMMU group 13 
        Memory at 628f2b0000 (64-bit, non-prefetchable) [size=64K] 
        Capabilities: <access denied> 
        Kernel driver in use: intel_ish_ipc 
        Kernel modules: intel_ish_ipc 

0000:00:14.0 USB controller: Intel Corporation Alder Lake PCH USB 3.2 xHCI Host Controller (rev 01) (prog-if 3
0 [XHCI]) 
        Subsystem: Dell Alder Lake PCH USB 3.2 xHCI Host Controller 
        Flags: medium devsel, IRQ 149, IOMMU group 14 
        Memory at 628f2a0000 (64-bit, non-prefetchable) [size=64K] 
        Capabilities: <access denied> 
        Kernel driver in use: xhci_hcd 
        Kernel modules: xhci_pci 

0000:00:14.2 RAM memory: Intel Corporation Alder Lake PCH Shared SRAM (rev 01) 
        Subsystem: Dell Alder Lake PCH Shared SRAM 
        Flags: fast devsel, IOMMU group 14 
        Memory at 628f2e8000 (64-bit, non-prefetchable) [disabled] [size=16K] 
        Memory at 628f2f0000 (64-bit, non-prefetchable) [disabled] [size=4K] 
        Capabilities: <access denied> 

0000:00:14.3 Network controller: Intel Corporation Device 51f1 (rev 01) 
        Subsystem: Intel Corporation Device 4090 
        Flags: bus master, fast devsel, latency 0, IRQ 16, IOMMU group 15 
        Memory at 628f2e4000 (64-bit, non-prefetchable) [size=16K] 
        Capabilities: <access denied> 
        Kernel driver in use: iwlwifi 
        Kernel modules: iwlwifi 

0000:00:15.0 Serial bus controller: Intel Corporation Alder Lake PCH Serial IO I2C Controller #0 (rev 01) 
        Subsystem: Dell Alder Lake PCH Serial IO I2C Controller 
        Flags: bus master, fast devsel, latency 0, IRQ 27, IOMMU group 16 
        Memory at 4017000000 (64-bit, non-prefetchable) [size=4K] 
        Capabilities: <access denied> 
        Kernel driver in use: intel-lpss 
        Kernel modules: intel_lpss_pci 

0000:00:15.1 Serial bus controller: Intel Corporation Alder Lake PCH Serial IO I2C Controller #1 (rev 01) 
        Subsystem: Dell Alder Lake PCH Serial IO I2C Controller 
        Flags: bus master, fast devsel, latency 0, IRQ 40, IOMMU group 16 
        Memory at 4017001000 (64-bit, non-prefetchable) [size=4K] 
        Capabilities: <access denied> 
        Kernel driver in use: intel-lpss 
        Kernel modules: intel_lpss_pci 

0000:00:16.0 Communication controller: Intel Corporation Alder Lake PCH HECI Controller (rev 01) 
        Subsystem: Dell Alder Lake PCH HECI Controller 
        Flags: bus master, fast devsel, latency 0, IRQ 203, IOMMU group 17 
        Memory at 628f2ed000 (64-bit, non-prefetchable) [size=4K] 
        Capabilities: <access denied> 
        Kernel driver in use: mei_me 
        Kernel modules: mei_me 

0000:00:1c.0 PCI bridge: Intel Corporation Device 51bb (rev 01) (prog-if 00 [Normal decode]) 
        Subsystem: Dell Device 0bda 
        Flags: bus master, fast devsel, latency 0, IRQ 127, IOMMU group 18 
        Bus: primary=00, secondary=aa, subordinate=aa, sec-latency=0 
        I/O behind bridge: [disabled] [16-bit] 
        Memory behind bridge: ac000000-ac0fffff [size=1M] [32-bit] 
        Prefetchable memory behind bridge: [disabled] [64-bit] 
        Capabilities: <access denied> 
        Kernel driver in use: pcieport 

0000:00:1f.0 ISA bridge: Intel Corporation Device 519d (rev 01) 
        Subsystem: Dell Device 0bda 
        Flags: bus master, fast devsel, latency 0, IOMMU group 19 

0000:00:1f.3 Multimedia audio controller: Intel Corporation Device 51ca (rev 01) 
        Subsystem: Dell Device 0bda 
        Flags: bus master, fast devsel, latency 64, IRQ 223, IOMMU group 19 
        Memory at 628f2e0000 (64-bit, non-prefetchable) [size=16K] 
        Memory at 628f000000 (64-bit, non-prefetchable) [size=1M] 
        Capabilities: <access denied> 
        Kernel driver in use: sof-audio-pci-intel-tgl 
        Kernel modules: snd_hda_intel, snd_sof_pci_intel_tgl 

0000:00:1f.4 SMBus: Intel Corporation Alder Lake PCH-P SMBus Host Controller (rev 01) 
        Subsystem: Dell Alder Lake PCH-P SMBus Host Controller 
        Flags: medium devsel, IRQ 16, IOMMU group 19 
        Memory at 628f2ec000 (64-bit, non-prefetchable) [size=256] 
        I/O ports at efa0 [size=32] 
        Kernel driver in use: i801_smbus 
        Kernel modules: i2c_i801 

0000:00:1f.5 Serial bus controller: Intel Corporation Alder Lake-P PCH SPI Controller (rev 01) 
        Subsystem: Dell Alder Lake-P PCH SPI Controller 
        Flags: fast devsel, IOMMU group 19 
        Memory at 70800000 (32-bit, non-prefetchable) [size=4K] 
        Kernel driver in use: intel-spi 
        Kernel modules: spi_intel_pci 

0000:01:00.0 3D controller: NVIDIA Corporation AD106M [GeForce RTX 4070 Max-Q / Mobile] (rev a1) 
        Subsystem: Dell GN21-X6 
        Flags: bus master, fast devsel, latency 0, IRQ 16, IOMMU group 20 
        Memory at ab000000 (32-bit, non-prefetchable) [size=16M] 
        Memory at 6000000000 (64-bit, prefetchable) [size=8G] 
        Memory at 6200000000 (64-bit, prefetchable) [size=32M] 
        I/O ports at 3000 [size=128] 
        Expansion ROM at <ignored> [disabled] 
        Capabilities: <access denied> 
        Kernel modules: nvidiafb, nouveau 

0000:aa:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5260 PCI Express Card Reader (rev 01) 
        Subsystem: Dell RTS5260 PCI Express Card Reader 
        Flags: bus master, fast devsel, latency 0, IRQ 128, IOMMU group 21 
        Memory at ac000000 (32-bit, non-prefetchable) [size=4K] 
        Capabilities: <access denied> 
        Kernel driver in use: rtsx_pci 
        Kernel modules: rtsx_pci 

10000:e0:06.0 PCI bridge: Intel Corporation Device a74d (prog-if 00 [Normal decode]) 
        Subsystem: Dell Device 0bda 
        Flags: bus master, fast devsel, latency 0, IRQ 166, IOMMU group 12 
        Bus: primary=00, secondary=e1, subordinate=e1, sec-latency=0 
        I/O behind bridge: [disabled] [16-bit] 
        Memory behind bridge: 72000000-720fffff [size=1M] [32-bit] 
        Prefetchable memory behind bridge: [disabled] [64-bit] 
        Capabilities: <access denied> 
        Kernel driver in use: pcieport 

10000:e1:00.0 Non-Volatile memory controller: SK hynix Platinum P41 NVMe Solid State Drive 2TB (prog-if 02 [NV
M Express]) 
        Subsystem: SK hynix Platinum P41 NVMe Solid State Drive 2TB 
        Flags: bus master, fast devsel, latency 0, IRQ -2147483648, NUMA node 0, IOMMU group 12 
        Memory at 72000000 (64-bit, non-prefetchable) [size=16K] 
        Capabilities: <access denied> 
        Kernel driver in use: nvme 
        Kernel modules: nvme 
[/FONT]
```

Here's my aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: sofhdadsp [sof-hda-dsp], device 1: HDMI1 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: sofhdadsp [sof-hda-dsp], device 2: HDMI2 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: sofhdadsp [sof-hda-dsp], device 3: HDMI3 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

sudo lshw -c sound | grep driver=
```
       configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
       configuration: driver=sof-audio-pci-intel-tgl latency=64

```

lsmod | grep snd
```

[FONT=monospace][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_seq_dummy          16384  0 [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hrtimer            16384  1 [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_skl_hda_dsp    28672  1 [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_intel_hda_dsp_common    20480  1 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_skl_hda_dsp [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_probes         20480  0 [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_hdac_hdmi      45056  1 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_skl_hda_dsp [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_rt711_sdca     57344  0 [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_rt715_sdca     49152  0 [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_rt1316_sdw     28672  0 [/COLOR]
regmap_sdw_mbq         16384  2 [COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_rt715_sdca,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_rt711_sdca [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hda_codec_hdmi     94208  1 [/COLOR]
regmap_sdw             16384  3 [COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_rt715_sdca,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_rt1316_sdw,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_rt711_sdca [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_dmic           16384  1 [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_pci_intel_tgl    16384  0 [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_intel_hda_common   188416  1 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_pci_intel_tgl [/COLOR]
soundwire_intel        57344  1 [COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_intel_hda_common [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_intel_hda      24576  1 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_intel_hda_common [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_pci            24576  2 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_intel_hda_common,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_pci_intel_tgl [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_xtensa_dsp     16384  1 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_intel_hda_common [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof               311296  4 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_pci,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_intel_hda_common,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_probes,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_intel_hda [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_utils          20480  1 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_hdac_hda       24576  1 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_intel_hda_common [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hda_ext_core       36864  4 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_intel_hda_common,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_hdac_hdmi,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_hdac_hda,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_intel_hda [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_acpi_intel_match    77824  2 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_intel_hda_common,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_pci_intel_tgl [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_acpi           16384  2 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_acpi_intel_match,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_intel_hda_common [/COLOR]
soundwire_bus         110592  8 [COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_rt715_sdca,regmap_sdw,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_rt1316_sdw,regmap_sdw_mbq,soundwire_inte[/COLOR]
l,[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_rt711_sdca,soundwire_generic_allocation,soundwire_cadence [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_core          417792  11 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_rt715_sdca,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_rt1316_sdw,soundwire_intel,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_intel_h[/COLOR]
da_common,[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_hdac_hdmi,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_hdac_hda,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_rt711_sdca,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_probes,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_dmic,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_skl_hda_ds[/COLOR]
p 
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_compress           32768  2 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_core,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_probes [/COLOR]
ac97_bus               16384  1 [COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_core [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_pcm_dmaengine      20480  1 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_core [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hda_intel          61440  0 [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_intel_dspcfg       36864  3 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hda_intel,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_intel_hda_common [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_intel_sdw_acpi     20480  2 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_intel_hda_common,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_intel_dspcfg [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hda_codec         204800  6 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hda_codec_hdmi,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hda_intel,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_intel_hda_dsp_common,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_hdac_hda[/COLOR]
,[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_intel_hda,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_skl_hda_dsp [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hda_core          139264  9 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hda_codec_hdmi,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hda_intel,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hda_ext_core,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hda_codec,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_intel_[/COLOR]
hda_dsp_common,[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_intel_hda_common,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_hdac_hdmi,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_hdac_hda,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_intel_hda [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hwdep              20480  1 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hda_codec [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_pcm               192512  15 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_rt715_sdca,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hda_codec_hdmi,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_rt1316_sdw,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hda_intel,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hd[/COLOR]
a_codec,soundwire_intel,[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_intel_hda_common,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_hdac_hdmi,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_compress,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_rt711_sdca,[/COLOR][COLOR=#ff5454]**snd**[/COLOR]
[COLOR=#000000]_soc_core,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof_utils,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hda_core,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_pcm_dmaengine [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_seq_midi           20480  0 [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_seq_midi_event     16384  1 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_seq_midi [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_rawmidi            53248  1 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_seq_midi [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_seq                94208  9 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_seq_midi,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_seq_midi_event,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_seq_dummy [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_seq_device         16384  3 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_seq,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_seq_midi,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_rawmidi [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_timer              49152  3 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_seq,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hrtimer,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_pcm [/COLOR]
[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]                   135168  17 [/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_seq,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_seq_device,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hda_codec_hdmi,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hwdep,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hda_intel,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_hda_cod[/COLOR]
ec,[COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_sof,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_timer,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_hdac_hdmi,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_compress,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_soc_core,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_pcm,[/COLOR][COLOR=#ff5454]**snd**[/COLOR][COLOR=#000000]_rawmidi [/COLOR]
soundcore              16384  1 [COLOR=#ff5454]**snd**[/COLOR][/FONT]

```

---

### Post by kinddolphin8827 on 2023-06-06
Did  you check the download proprietary codecs and drivers option when you originally installed Ubuntu?

---

### Post by raiinzen on 2023-06-06
I believe I did, yes, but just in case, could you tell me how to go back and check that and add them if I didn't?

Update for reference as I try to puzzle this out.  
[https://launchpad.net/ubuntu/+source/firmware-sof](https://launchpad.net/ubuntu/+source/firmware-sof)  is already on my computer, and no updates are needed on that end.

---

### Post by mrproxis on 2023-07-21
Did you manage to resolve this? I'm seeing the same issue with PopOS 22.04 on my 9730. 

Been trying various OS on live usb and found out that the sound works fine on Kubuntu 22.04 (doesn't work on 23.04 though). Now need to work out what is the source of issue in Ubuntu/Pop.

---

### Post by tinysand on 2023-08-13
I've tried Fedora (+XFCE, KDE spins), Debian 12, openSUSE, Pop, Ubuntu, Mint, and Endeavour, but none of them works with the sound on the XPS 9730. The only OS that works with the sound on these devices is Windows which came pre-loaded.

---

### Post by mrproxis on 2023-08-21
> **tinysand said:**
> I've tried Fedora (+XFCE, KDE spins), Debian 12, openSUSE, Pop, Ubuntu, Mint, and Endeavour, but none of them works with the sound on the XPS 9730. The only OS that works with the sound on these devices is Windows which came pre-loaded.

Did you try Ubuntu 22.10 with linux kernel 5.19.0-32-generic? That seems to work on a live boot usb, but later linux kernels break the audio.

---

### Post by #&amp;thj^% on 2023-08-21
> **mrproxis said:**
> Did you try Ubuntu 22.10 with linux kernel 5.19.0-32-generic? That seems to work on a live boot usb, but later linux kernels break the audio.

I guess the OP could confirm but>>>>Ubuntu 22.10 (Kinetic Kudu) reaches End of Life on July 20 2023

---

