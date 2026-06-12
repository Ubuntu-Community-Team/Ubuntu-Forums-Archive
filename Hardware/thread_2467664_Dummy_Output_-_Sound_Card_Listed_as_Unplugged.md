---
title: "Dummy Output - Sound Card Listed as Unplugged"
date: 2021-10-03
forum: Hardware
---

### Post by grudgemonkey on 2021-10-03
In the Sound settings the audio output  is listed as Dummy Output. If i try pavucontrol, i can see my audio  cards listed as "(unplugged) (unavailable)"
I  have an amd radeon rx 550 graphics card (doubles as my sound card since  I use headphones plugged into my monitor). There's also the audio bus  in my case, which broke some months ago, so I don't use it. My processor  is an AMD® Fx(tm)-6300 six-core and i'm currently running Ubuntu 21.04.


Also no matter what distro I try the problem is the same. I've tried mint, ubuntu, and manjaro.


Here's some terminal output:

```
***hwinfo --sound***
```

28: PCI 100.1: 0403 Audio device                                
  [Created at pci.386]
  Unique ID: NXNs.7IS0FEaF4_0
  Parent ID: 8otl.1zYaSjlK1pF
  SysFS ID: /devices/pci0000:00/0000:00:04.0/0000:01:00.1
  SysFS BusID: 0000:01:00.1
  Hardware Class: sound
  Model: "ATI Baffin HDMI/DP Audio [Radeon RX 550 640SP / RX 560/560X]"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0xaae0 "Baffin HDMI/DP Audio [Radeon RX 550 640SP / RX 560/560X]"
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd. [MSI]"
  SubDevice: pci 0xaae0 
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfea60000-0xfea63fff (rw,non-prefetchable)
  IRQ: 36 (219 events)
  Module Alias: "pci:v00001002d0000AAE0sv00001462sd0000AAE0bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #13 (PCI bridge)

29: PCI 14.2: 0403 Audio device
  [Created at pci.386]
  Unique ID: 5Dex.c8pPfvNvCx4
  SysFS ID: /devices/pci0000:00/0000:00:14.2
  SysFS BusID: 0000:00:14.2
  Hardware Class: sound
  Model: "ATI SBx00 Azalia (Intel HDA)"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4383 "SBx00 Azalia (Intel HDA)"
  SubVendor: pci 0x1849 "ASRock Incorporation"
  SubDevice: pci 0x5892 
  Revision: 0x40
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfeb00000-0xfeb03fff (rw,non-prefetchable)
  IRQ: 16 (12184 events)
  Module Alias: "pci:v00001002d00004383sv00001849sd00005892bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


```
***cat /proc/asound/cards***
```

```
0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfeb00000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfea60000 irq 36
```


[I][B]lspci -v

01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Baffin HDMI/DP Audio [Radeon RX 550 640SP / RX 560/560X]
    Subsystem: Micro-Star International Co., Ltd. [MSI] Baffin HDMI/DP Audio [Radeon RX 550 640SP / RX 560/560X]
    Flags: bus master, fast devsel, latency 0, IRQ 36, NUMA node 0
    Memory at fea60000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

[/B][/I]Any clues as to what I can do or what's wrong here are appreciated. Thank you.

---

