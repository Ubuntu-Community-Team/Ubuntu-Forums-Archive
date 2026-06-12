---
title: "Enabling a LBA48 Drive even though driver is non-LBA48"
date: 2008-08-08
forum: Hardware
---

### Post by trekke20 on 2008-08-08
I am new to this forum so any help is appreciated.

I am trying to configure a server running Ubuntu server 8.04 and I am having trouble because the Kernal automaticly shuts off ata3 when it is booting up because the driver is not LBA48 compatible. I have read up on LBA48 and I want to use only 130GB of the 300GB drive attached to the controller currently.

I am using a SIIG SATA II-150 PCI RAID card in a machine, and I only have one drive connected to it operating in passthrough mode.

Is it possible to bypass the disabling of this drive by the kernal so I can use at least 130GB of the drive.

---

