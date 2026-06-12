---
title: "X505 wierd messages in dmesg"
date: 2010-11-04
forum: Hardware
---

### Post by vdubhack on 2010-11-04
I have been searching for awhile on some messages I have never seen during boot until my new laptop which is a Toshiba x505-887. I am running 10.10 64bit with kernel 2.6.35-23

Here are the messages in question
```

[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000 
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1027692
[    0.000000] No AGP bridge found
[    1.762638] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.763633] \_SB_.PCI0:_OSC invalid UUID
[    1.765179] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    1.765183] pci 0000:00:03.0: PME# disabled
[    1.765501] pci 0000:00:1a.0: reg 10: [mem 0xf0906000-0xf09063ff]
[    1.765566] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.765575] pci 0000:00:1a.0: PME# disabled
[    1.765626] pci 0000:00:1b.0: reg 10: [mem 0xf0900000-0xf0903fff 64bit]
[    1.765678] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.765687] pci 0000:00:1b.0: PME# disabled
[    1.765767] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.765776] pci 0000:00:1c.0: PME# disabled
[    1.765859] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    1.765868] pci 0000:00:1c.3: PME# disabled
[    1.765948] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    1.765957] pci 0000:00:1c.4: PME# disabled
[    1.766039] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    1.766048] pci 0000:00:1c.6: PME# disabled
[    1.766104] pci 0000:00:1d.0: reg 10: [mem 0xf0907000-0xf09073ff]
[    1.766169] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.766178] pci 0000:00:1d.0: PME# disabled
[    1.829258] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP07._PRT]
[    1.829563] \_SB_.PCI0:_OSC invalid UUID
[    1.829565] _OSC request data:1 1f 1f 
[    1.956772] pcieport 0000:00:1c.6: irq 49 for MSI/MSI-X
[    1.957005] \_SB_.PCI0:_OSC invalid UUID
[    1.957007] _OSC request data:1 0 1f 
```There are more repeats of the same messages and tried to keep this actual post as small as possible. 
My Questions are basically is what I posted normal? I wouldnt think so since there are invlaid messages and report a bug, which I reported that bug but have had no response on it. I also tried the boot option it suggested but all that did was give me a message to booth with the reverse option. Is ACPI not recognizing everything on my computer properly? I know the SD card I had to do a work around just to get it to work. Thanks for any help and or info on this

The full dmesg in case this will help more [http://pastebin.com/B335VBWs](http://pastebin.com/B335VBWs)

---

### Post by vdubhack on 2010-11-06
Anyone have any ideas and or suggestions on this ?

---

