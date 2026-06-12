---
title: "Installing 1068E RAID Controller"
date: 2008-09-29
forum: Hardware
---

### Post by tiburcillo on 2008-09-29
Hello!

I'm fairly new to Linux and so far I've never had any problems when plugging in new hardware. For example, last year I plugged in a Promise IDE Controller and was suprised I didn't even had to install a driver to get it working. Now with a shortage on hard drives I've decided to buy an Intel SASMF8I card which has an LSI MegaRAID 1068E chip inside. My ubuntu 7.10 (2.6.22-14-generic) doesn't seem to recognize the card, when i do lspci -v I get this output:
Code:
```
02:00.0 RAID bus controller: LSI Logic / Symbios Logic Unknown device 0059 (rev 08)
        Subsystem: Intel Corporation Unknown device 3002
        Flags: bus master, fast devsel, latency 0, IRQ 10
        I/O ports at ee00 [size=256]
        Memory at fd9fc000 (64-bit, non-prefetchable) [size=16K]
        Memory at fd9e0000 (64-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at fd600000 [disabled] [size=2M]
        Capabilities: [50] Power Management version 2
        Capabilities: [68] Express Endpoint IRQ 0
        Capabilities: [98] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [b0] MSI-X: Enable- Mask- TabSize=1
```
Some searching on the net & this forum says that loading the megaraid_sas driver should get this working. My guess is that by doing "modprobe megaraid_sas" the driver is inserted in the kernel. Now my question is... how do i know this succeeded and how can I see (and then mount) the 4 SATA drives that are attached to the controller?

Is it also possible to compile a kernel module or something? :confused:

Thanks,
t

edit: I originally posted in the server platforms forum, but I think this is a better place...

---

