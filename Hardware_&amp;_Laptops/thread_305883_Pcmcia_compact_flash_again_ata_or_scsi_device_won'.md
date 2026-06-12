---
title: "Pcmcia compact flash again: ata or scsi device won't appear."
date: 2006-11-24
forum: Hardware &amp; Laptops
---

### Post by leon_ti on 2006-11-24
Hi guys.
I've got some problem with PCMCIA-to-CompactFlash adaptor.
It stopped working at one moment.
Dmesg output is put below:
```
[17183164.340000] pccard: PCMCIA card inserted into slot 0
[17183164.340000] pcmcia: registering new device pcmcia0.0
[17183164.380000] ata2: PATA max PIO0 cmd 0x110 ctl 0x11E bmdma 0x0 irq 3
[17183194.544000] ata2: qc timeout (cmd 0x91)
[17183194.544000] ata2: dev 0 failed to IDENTIFY (INIT_DEV_PARAMS failed)
[17183194.544000] scsi1 : pata_pcmcia

```
Neither /dev/hd? nor /dev/sd? (i.e. scsi or ide) devices appeared.

Where is a bug?..

---

