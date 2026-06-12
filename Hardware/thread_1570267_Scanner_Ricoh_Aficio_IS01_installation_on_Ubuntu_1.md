---
title: "Scanner Ricoh Aficio IS01 installation on Ubuntu 10.04.1 ?"
date: 2010-09-07
forum: Hardware
---

### Post by l1n0x on 2010-09-07
Hi,

Is there anyway to install a scanner RICOH Aficio IS01 (SCSI) on Ubuntu 10.04.1 ?

Here is what I get with lshw:

[COLOR=Blue][I]*-scsi
                description: SCSI storage controller
                product: 53c810
                vendor: LSI Logic / Symbios Logic
                physical id: b
                bus info: pci@0000:02:0b.0
                logical name: scsi0
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: scsi bus_master scsi-host
                configuration: driver=sym53c8xx latency=64 maxlatency=64 mingnt=8
                resources: irq:23 ioport:d000(size=256) memory:feaffc00-feaffcff

*-scanner   UNCLAIMED
                   description: SCSI Scanner
                   physical id: 0.5.0
                   bus info: scsi@0:0.5.0[/I][/COLOR]

TIA ;)

---

