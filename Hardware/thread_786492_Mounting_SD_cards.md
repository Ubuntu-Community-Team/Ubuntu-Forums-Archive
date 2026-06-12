---
title: "Mounting SD cards"
date: 2008-05-08
forum: Hardware
---

### Post by ibnpaul on 2008-05-08
Hi all,

I am running Kubuntu 8.04 on a Dell D630 and recently purchased a Sony Vaio PCMCIA card reader for my SD cards.  When I insert a card, I get this from dmesg:

```

May  8 06:07:08 kubuntop kernel: [ 2717.510836] pccard: PCMCIA card inserted into slot 0
May  8 06:07:08 kubuntop kernel: [ 2717.512128] pcmcia: registering new device pcmcia0.0
May  8 06:07:08 kubuntop kernel: [ 2717.553304] scsi8 : pata_pcmcia
May  8 06:07:08 kubuntop kernel: [ 2717.553386] ata9: PATA max PIO0 cmd 0x100 ctl 0x10e irq 19

```

And I see the reader when doing an lspci -v:

```
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
        Subsystem: Dell Unknown device 01f9
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device 01f9
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 6fa0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Dell Unknown device 01f9
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
        I/O ports at 6eb0 [size=8]
        I/O ports at 6eb8 [size=4]
        I/O ports at 6ec0 [size=8]
        I/O ports at 6ec8 [size=4]
        I/O ports at 6ee0 [size=16]
        I/O ports at eff0 [size=16]
        Capabilities: [70] Power Management version 3

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
        Subsystem: Dell Unknown device 01f9
        Flags: medium devsel, IRQ 10
        Memory at febfbf00 (32-bit, non-prefetchable) [size=256]
        I/O ports at 10c0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 135M (rev a1) (prog-if 00 [VGA controller])
        Subsystem: Dell Unknown device 01f9
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at df00 [size=128]
        [virtual] Expansion ROM at fc000000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint IRQ 0

03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
        Subsystem: Dell Unknown device 01f9
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 19
        Memory at f9d00000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
        Memory window 0: 88000000-8bfff000 (prefetchable)
        Memory window 1: 8c000000-8ffff000
        I/O window 0: 00001400-000014ff
        I/O window 1: 00001800-000018ff
        16-bit legacy interface ports at 0001


```

However, there is no device created for the card and it does not mount.  Does anyone have any ideas?  Thank you!

---

