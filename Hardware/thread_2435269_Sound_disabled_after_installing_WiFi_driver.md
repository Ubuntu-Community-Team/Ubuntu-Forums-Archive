---
title: "Sound disabled after installing WiFi driver"
date: 2020-01-18
forum: Hardware
---

### Post by subhechhu on 2020-01-18
When installed, I did notice the sound working pretty well on Ubuntu 18.04 installed on Dell Inspiron 14 5490.
It couldn't find WiFi driver though.

I checked my hardware with `lspci -nn` and found out it to be:

[B]     Network controller [0280]: Intel Corporation Device [8086:02f0]


[/B]When I installed the Wifi driver with the help of Ubuntu community, the sound stopped working.

**aplay -l :**
```

aplay: device_list:270: no soundcards found...
```


**sudo apt-get install linux-restricted-modules-`uname -r` linux-generic** gives me list of items so I believe the sound module has been installed

**lspci -v | grep -A7 -i "audio":**

```

00:1f.3 Multimedia audio controller: Intel Corporation Device 02c8
    Subsystem: Dell Device 0955
    Flags: bus master, fast devsel, latency 64, IRQ 146
    Memory at a121c000 (64-bit, non-prefetchable) [size=16K]
    Memory at a1000000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: sof-audio-pci
    Kernel modules: snd_hda_intel, sof_pci_dev

00:1f.4 SMBus: Intel Corporation Device 02a3
    Subsystem: Dell Device 0955
    Flags: medium devsel, IRQ 255
    Memory at a122b000 (64-bit, non-prefetchable) [disabled] [size=256]
    I/O ports at efa0 [disabled] [size=32]
```


But the sound setting still shows **Dummy Output **as in the attachment.
I am clueless what to do to fix sound now.

---

