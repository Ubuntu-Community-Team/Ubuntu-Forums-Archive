---
title: "Network Boot Failure"
date: 2010-02-12
forum: Hardware
---

### Post by bluefox815 on 2010-02-12
So because my laptop's CD drive is broken, I'm trying to do a network boot to get linux running on my system.

I followed tutorials for gPXE like these:
[http://polishlinux.org/installation/installing-linux-over-network-no-cd-drive/](http://polishlinux.org/installation/installing-linux-over-network-no-cd-drive/)
[http://forums.remote-exploit.org/tutorials-guides/4625-howto-pxe-netboot.html](http://forums.remote-exploit.org/tutorials-guides/4625-howto-pxe-netboot.html)

And out of those I've come up with a TFTP + DHCP server, and my linux ISO is extracted to a USB drive. However, the problem I'm getting can be seen in the output below, I don't know how to explain it. My first thoughts after some research are that my wired network card is not compatible with gPXE, which I really hope is not the case.

My laptop is an Averatec 6240 with a SiS 900-Based PCI Fast Ethernet Adapter. The currently installed operating system is Windows XP Home Edition.

Output:
```

Intel UNDI, PXE-2.0 (build 082)
Copyright 1997-2000 Intel Corporation

SiS900 PXE BootROM v1.09  Hook Int19

CLIENT MAC ADDR: (*output omitted*)
PXE->EB: !PXE at 9D57:0060, entry point at 9D57:0104
         UNDI code segment 9D57:2442, data segment 8D33:0240 (564-639kB)
         UNDI device is PCI 00:04.0
         525kB free base memory after PXE unload
gPXE initialising devices...



gPXE 0.9.7 -- Open Source Boot Firmware -- http://etherboot.org
Features FTP HTTP HTTPS DNS FTFP AoE iSCSI bsImage COMBOOT ELF Multiboot PXE PX
EXT

DHCP (net0 (*my mac address*))............. Connection timed out (0x4c106035)
Could not configure net0: Connection timed out (0x4c106035)

PXE-M0F; Exiting Intel PXE ROM.

PXE-E06: Option ROM requires DDIM support.
(*blinking cursor, I have to push power at this point*)

```

Notes:  in the omitted output, it's just a bunch of basic NIC information such as MAC and IP address, which were all set exactly as they were on the DHCP server.

---

