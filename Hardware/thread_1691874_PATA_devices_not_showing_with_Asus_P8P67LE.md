---
title: "PATA devices not showing with Asus P8P67LE"
date: 2011-02-20
forum: Hardware
---

### Post by Artemis3 on 2011-02-20
[img]http://www.csv-direct.de/artpics/picA0581013.jpg[/img]

I'm bringing this to its own thread. Please note the P8P67**LE** is the only Asus p67 model with a pata port.

Before anyone mentions, the sata bug affects only the intel controlled sata3 ports, not the sata6 ports (which I'm using), or the marvell controlled pata/sata6 ports.

> **Jay1234 said:**
> Do you have a link or more info on this? I'm using 10.10 + Marvell, and it seems to work ok, but only after disabling ncq.

J.

No link, a hd and dvd i have attached to the pata cable are not seen by linux, dmesg doesn't even list the devices... They show/work in bios/windows xp64 just fine.

Disabling ncq? can't find that option in the bios. Is there a way to get into the marvell controller bios?

---

### Post by Artemis3 on 2011-02-21
lshw shows:
```

  *-storage               
       description: SATA controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 12
       width: 32 bits
       clock: 33MHz
       capabilities: storage pm msi pciexpress ahci_1.0 bus_master cap_list rom
       configuration: driver=ahci latency=0
       resources: irq:49 ioport:c090(size=8) ioport:c080(size=4) ioport:c070(size=8) ioport:c060(size=4) ioport:c050(size=16) memory:fa215000-fa2157ff memory:fa200000-fa20ffff
  *-ide UNCLAIMED
       description: IDE interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0.1
       bus info: pci@0000:08:00.1
       version: 12
       width: 32 bits
       clock: 33MHz
       capabilities: ide pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:c040(size=8) ioport:c030(size=4) ioport:c020(size=8) ioport:c010(size=4) ioport:c000(size=16) memory:fa214000-fa21400f memory:fa210000-fa213fff

```

lspci shows:
```

08:00.0 SATA controller: Marvell Technology Group Ltd. Device 9120 (rev 12) (prog-if 01 [AHCI 1.0])
	Subsystem: ASUSTeK Computer Inc. Device 83ba
	Flags: bus master, fast devsel, latency 0, IRQ 49
	I/O ports at c090 [size=8]
	I/O ports at c080 [size=4]
	I/O ports at c070 [size=8]
	I/O ports at c060 [size=4]
	I/O ports at c050 [size=16]
	Memory at fa215000 (32-bit, non-prefetchable) [size=2K]
	Expansion ROM at fa200000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [70] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Kernel driver in use: ahci
	Kernel modules: ahci

08:00.1 IDE interface: Marvell Technology Group Ltd. Device 91a4 (rev 12) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Marvell Technology Group Ltd. Device 91a4
	Flags: fast devsel, IRQ 19
	I/O ports at c040 [size=8]
	I/O ports at c030 [size=4]
	I/O ports at c020 [size=8]
	I/O ports at c010 [size=4]
	I/O ports at c000 [size=16]
	Memory at fa214000 (32-bit, non-prefetchable) [size=16]
	Expansion ROM at fa210000 [disabled] [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [70] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting

```

dmesg shows:
```

[    1.256410] ata7: SATA max UDMA/133 abar m2048@0xfa215000 port 0xfa215100 irq 49
[    1.256414] ata8: SATA max UDMA/133 abar m2048@0xfa215000 port 0xfa215180 irq 49

```

---

### Post by Artemis3 on 2011-03-16
Bump

Tested with kernel:

Linux 2.6.38-020638-generic #201103151303 SMP Tue Mar 15 13:08:09 UTC 2011 x86_64 GNU/Linux

Same result, no ide/pata.

---

### Post by Wug on 2011-03-23
I'm having a vaguely similar problem with a p6x58d-e, which uses some sort of pata emulation for the SATA 6Gb/s ports (I can't for the life of me figure out why).  In any case, the problem is that emulated pata devices aren't recognized by linux, where they work just fine with windows.

I'm not sure we have the same problem, but the fact that the SATA 6Gb/s ports use IDE emulation and the fact that you only have the problem with your IDE port jumped out at me.

---

### Post by Maliron on 2011-04-20
It's been four weeks and nothing else on this? I am having the same problem with a Marvell IDE controller. My IDE DVD burner is not showing up in Linux on my ASRock P55 Extreme4 mother board. I have been fighting the issue trying everything I could think of, and finally stumbled on this thread. I hope someone makes some progress soon.



```
   *-ide UNCLAIMED
        description: IDE interface
        product: Marvell Technology Group Ltd.
        vendor: Marvell Technology Group Ltd.
        physical id: 0.1
        bus info: pci@0000:04:00.1
        version: 11
        width: 32 bits
        clock: 33MHz
        capabilities: ide cap_list
        configuration: latency=0
        resources: ioport:b080(size=8) ioport:b000(size=4) ioport:ac00(size=8) ioport:a880(size=4) ioport:a800(size=16) memory:f5eff400-f5eff40f memory:c4010000-c401ffff


04:00.1 IDE interface: Marvell Technology Group Ltd. Device 91a4 (rev 11)

```Bump?

I have to wonder, with drag0nfur mentioning that the SATA6 controller is using some sort of emulation mode, my drive is plugged into that port, am I getting the performance I should be out of it, or is Linux treating this as a SATA3 port? Regardless it would be nice to burn again.

---

### Post by Yellow Pasque on 2011-04-20
The only thing I can suggest is:
```
sudo update-pciids
sudo modprobe -v pata_marvell.ko
```

Side note:
I had a SATA drive running off a PATA-emulated port and I found out that the port was detecting a 40-pin PATA cable and limiting the drive to UDMA/33. I used this command to find that:
```
dmesg | grep ata
```
I was able to force 80-pin detection with a boot argument, but eventually, I just used another port.

---

### Post by Maliron on 2011-04-22
Thanks for the reply, I will have to give it a shot,  and post the results. I have a feeling I am just going to have to buy a SATA burner though. LOL

---

### Post by Maliron on 2011-04-25
No difference at all. Still shows up as unclaimed in an 'lshw'

```
              bus info: scsi@13:0.0.0
      *-ide UNCLAIMED
           description: IDE interface
           product: Marvell Technology Group Ltd.
           vendor: Marvell Technology Group Ltd.
           physical id: 0.1
           bus info: pci@0000:04:00.1
           version: 11
           width: 32 bits
           clock: 33MHz
           capabilities: ide pm msi pciexpress cap_list
           configuration: latency=0
           resources: ioport:b080(size=8) ioport:b000(size=4) ioport:ac00(size=8) ioport:a880(size=4) ioport:a800(size=16) memory:f5eff400-f5eff40f memory:c4010000-c401ffff
```

Thanks for the suggestion though. I guess I'm going to just have to buy a SATA burner.

---

### Post by Artemis3 on 2011-05-25
Yes we are having the same issue, i hope enough people keep coming; we need a way address this with the linux developers (the kernel), or whoever maintains the marvell module.

---

### Post by novinick on 2011-05-25
try to boot using boot parameter:

```

pci=nomsi

```pray,and see what hapens /may be beter may be not beter/

backup important files

[http://ubuntuforums.org/showthread.php?t=1054476](http://ubuntuforums.org/showthread.php?t=1054476)
[http://www.fedoraforum.org/forum/archive/index.php/t-168929.html](http://www.fedoraforum.org/forum/archive/index.php/t-168929.html)

>         nomsi        [MSI] If the PCI_MSI kernel config parameter is
                enabled, this kernel boot option can be used to

                disable the use of MSI interrupts system-wide.
[http://www.fogproject.org/wiki/index.php?title=Kernel_Parameters](http://www.fogproject.org/wiki/index.php?title=Kernel_Parameters)
[http://www.mjmwired.net/kernel/Documentation/PCI/MSI-HOWTO.txt](http://www.mjmwired.net/kernel/Documentation/PCI/MSI-HOWTO.txt)

rationale: marvell pata driver may not support msi-type-of intrupts properly
which are per default enabled in new kernels if exists and suported by motherboard

---

### Post by Artemis3 on 2011-05-26
Still unclaimed...

```
        *-pci:6
             description: PCI bridge
             product: 6 Series Chipset Family PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:c000(size=4096) memory:fa200000-fa2fffff
           *-storage
                description: SATA controller
                product: Marvell Technology Group Ltd.
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress ahci_1.0 bus_master cap_list rom
                configuration: latency=0
                resources: irq:18 ioport:c090(size=8) ioport:c080(size=4) ioport:c070(size=8) ioport:c060(size=4) ioport:c050(size=16) memory:fa215000-fa2157ff memory:fa200000-fa20ffff
           *-ide UNCLAIMED
                description: IDE interface
                product: 88SE91A4 SATA 6Gb/s Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0.1
                bus info: pci@0000:08:00.1
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm msi pciexpress cap_list
                configuration: latency=0
                resources: ioport:c040(size=8) ioport:c030(size=4) ioport:c020(size=8) ioport:c010(size=4) ioport:c000(size=16) memory:fa214000-fa21400f memory:fa210000-fa213fff

```
```
08:00.0 IDE interface: Marvell Technology Group Ltd. 88SE91A0 SATA 6Gb/s Controller (rev 12) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device 83ba
	Flags: fast devsel, IRQ 18
	I/O ports at c090 [size=8]
	I/O ports at c080 [size=4]
	I/O ports at c070 [size=8]
	I/O ports at c060 [size=4]
	I/O ports at c050 [size=16]
	Memory at fa215000 (32-bit, non-prefetchable) [size=2K]
	Expansion ROM at fa200000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [70] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting

08:00.1 IDE interface: Marvell Technology Group Ltd. 88SE91A4 SATA 6Gb/s Controller (rev 12) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Marvell Technology Group Ltd. 88SE91A4 SATA 6Gb/s Controller
	Flags: fast devsel, IRQ 19
	I/O ports at c040 [size=8]
	I/O ports at c030 [size=4]
	I/O ports at c020 [size=8]
	I/O ports at c010 [size=4]
	I/O ports at c000 [size=16]
	Memory at fa214000 (32-bit, non-prefetchable) [size=16]
	Expansion ROM at fa210000 [disabled] [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [70] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting

```

Makes no difference with changing mode ahci/ide in the bios, i also did sudo modprobe -v pata_marvell but dmesg shows nothing and the device remains unclaimed.

---

### Post by Artemis3 on 2011-06-19
Ok this little patch from May 18 (v2 Jun 14) seems to fix it (finally): [http://lkml.org/lkml/2011/6/14/231](http://lkml.org/lkml/2011/6/14/231)

This is the launchpad #: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325)

And the bugzilla.kernel.org # [https://bugzilla.kernel.org/show_bug.cgi?id=34832](https://bugzilla.kernel.org/show_bug.cgi?id=34832)

I wish somebody had told me... Anyway, kernel compile time ^_^

---

