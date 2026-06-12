---
title: "Boot: 10 seconds delay to init console?"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by Markus72 on 2008-12-06
Hi,

I experience a strange behavior when bootin my kubuntu.
It seems that there is some delay of 10 seconds before intializing the console I cannot explain.
Any idea what's going wrong?

```

[    0.000000] Kernel command line: root=UUID=0835473c-d34a-4356-a44d-7485cb4e4d7a ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2194.584 MHz processor.
[    9.994503] Console: colour VGA+ 80x25
[    9.994507] console [tty0] enabled
[    9.994817] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    9.995194] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   10.119525] Memory: 2066432k/2096768k available (2177k kernel code, 29116k reserved, 1005k data, 368k init, 1179264k highmem)
[   10.119534] virtual kernel memory layout:
[   10.119536]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   10.119537]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   10.119539]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   10.119540]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   10.119541]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   10.119543]       .data : 0xc0320704 - 0xc041bdc4   (1005 kB)
[   10.119544]       .text : 0xc0100000 - 0xc0320704   (2177 kB)

```

My kernel: Linux linus 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux

Helps very appreciated.

Thanks
Markus

---

### Post by Markus72 on 2008-12-07
no idea? I've read I'm not the only one with these effects

---

