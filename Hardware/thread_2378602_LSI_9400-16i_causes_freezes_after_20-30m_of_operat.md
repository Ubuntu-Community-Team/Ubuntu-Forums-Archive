---
title: "LSI 9400-16i causes freezes after 20-30m of operation"
date: 2017-11-25
forum: Hardware
---

### Post by jgrevich on 2017-11-25
I recently purchased the [Avago (Broadcom) 9400-16i HBA]("https://www.broadcom.com/products/storage/host-bus-adapters/sas-nvme-9400-16i#overview") after being pleased with their [9305-16i model]("https://www.broadcom.com/products/storage/host-bus-adapters/sas-9305-16i") in another of my systems. I updated the BIOS, driver, and firmware of the card to the latest versions:

```
# /opt/MegaRAID/storcli/storcli64 /c0 show
Controller = 0
Status = Success
Description = None


Product Name = HBA 9400-16i
Serial Number = SP732198472
SAS Address =  500605b00d3bb810
PCI Address = 00:04:00:00
System Time = 11/24/2017 21:27:39
FW Package Build = 04.00.00.00
FW Version = 04.00.04.00
BIOS Version = 09.07.00.00_04.00.00.00
NVDATA Version = 04.03.00.12
Firmware Product ID = 0x2231
Driver Name = mpt3sas
Driver Version = 23.00.00.00
Bus Number = 4
Device Number = 0
Function Number = 0
Vendor Id = 0x1000
Device Id = 0xAC
SubVendor Id = 0x1000
SubDevice Id = 0x3000
Board Name = HBA 9400-16i
Board Assembly = 03-50008-15003
Board Tracer Number = SP732198472
Physical Drives = 16

```

Everything seemed to load fine aside from the kernel being tainted due to the unsigned 3rd party driver and the odd repeating messages at the end of this snippet:
```
Nov 24 14:46:55 jn kernel: [    4.428320] mpt3sas: module verification failed: signature and/or required key missing - tainting kernel
Nov 24 14:46:55 jn kernel: [    4.476103] mpt3sas version 23.00.00.00 loaded
Nov 24 14:46:55 jn kernel: [    4.488596] mpt3sas_cm0: 64 BIT PCI BUS DMA ADDRESSING SUPPORTED, total mem (131929720 kB)
Nov 24 14:46:55 jn kernel: [    4.708245] mpt3sas_cm0: IOC Number : 0
Nov 24 14:46:55 jn kernel: [    4.717270] mpt3sas0-msix0: PCI-MSI-X enabled: IRQ 44
...
Nov 24 14:46:55 jn kernel: [    4.717349] mpt3sas_cm0: iomem(0x00000000f9f00000), mapped(0xffffc9000d600000), size(1048576)
Nov 24 14:46:55 jn kernel: [    4.717350] mpt3sas_cm0: ioport(0x000000000000e000), size(256)
Nov 24 14:46:55 jn kernel: [    4.832235] mpt3sas_cm0: IOC Number : 0
Nov 24 14:46:55 jn kernel: [    4.832236] mpt3sas_cm0: sending message unit reset !!
Nov 24 14:46:55 jn kernel: [    4.844225] mpt3sas_cm0: message unit reset: SUCCESS
Nov 24 14:46:55 jn kernel: [    5.783957] mpt3sas_cm0: Allocated physical memory: size(76659 kB)
Nov 24 14:46:55 jn kernel: [    5.783988] mpt3sas_cm0: Current Controller Queue Depth(8072), Max Controller Queue Depth(8192)
Nov 24 14:46:55 jn kernel: [    5.784019] mpt3sas_cm0: Scatter Gather Elements per IO(128)
Nov 24 14:46:55 jn kernel: [    6.016435] mpt3sas_cm0: SAS3416: FWVersion(04.00.04.00), ChipRevision(0x01), BiosVersion(09.07.00.00)
Nov 24 14:46:55 jn kernel: [    6.016471] mpt3sas_cm0: Protocol=(Initiator,Target,NVMe), Capabilities=(TLR,EEDP,Diag Trace Buffer,Task Set Full,NCQ)
Nov 24 14:46:55 jn kernel: [    6.016589] mpt3sas_cm0: : host protection capabilities enabled  DIF1 DIF2 DIF3 DIX0 DIX1 DIX2 DIX3
Nov 24 14:46:55 jn kernel: [    6.016959] mpt3sas_cm0: sending port enable !!
Nov 24 14:46:55 jn kernel: [    6.017414] mpt3sas_cm0: hba_port entry: ffff881fe7e804c0, port: 255 is added to hba_port list
Nov 24 14:46:55 jn kernel: [    6.019625] mpt3sas_cm0: host_add: handle(0x0001), sas_addr(0x500605b00d3bb810), phys(17)
Nov 24 14:46:55 jn kernel: [    6.032146] mpt3sas_cm0: port enable: SUCCESS
Nov 24 21:19:28 jn kernel: [    6.570423] mpt3sas_cm0: log_info(0x31200205): originator(PL), code(0x20), sub_code(0x0205)
Nov 24 21:19:28 jn kernel: [    6.572153] scsi 6:0:16:0: Wrong diagnostic page; asked for 7 got 0
Nov 24 21:19:28 jn kernel: [    6.576255] mpt3sas_cm0: log_info(0x31200205): originator(PL), code(0x20), sub_code(0x0205)
Nov 24 21:19:28 jn kernel: [    6.577978] scsi 6:0:16:0: Wrong diagnostic page; asked for 7 got 0
...

```

Unfortunately, the server freezes after ~30m of operation. By freeze I mean that the display goes completely black and the server is inaccessible via SSH. This message appears in the kernel log a few minutes before the freeze:

```
Nov 24 21:12:39 jn kernel: [ 1670.981651] perf interrupt took too long (2514 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
```

I think it's a red herring because I also saw the same message in the kern.log before the addition of this card.

I don't see any other helpful log messages. Does anyone have any suggestions as to how I can further debug this problem?

---

