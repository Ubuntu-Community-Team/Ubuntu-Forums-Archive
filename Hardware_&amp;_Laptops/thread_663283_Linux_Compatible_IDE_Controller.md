---
title: "Linux Compatible IDE Controller"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by mkzimms on 2008-01-10
Looking for a 100% linux compatible PCI IDE controller.  Im trying to increase the storage on my server and I have like 6 100G IDE drives to work with and only 2 IDE channels on my current rig.  Its going to be used to house a logical drive for my FTP.  i dont have PCI-X so its not going to be used boot and work of off,  I assume anything will saturate a 100Mb connection, correct me if im wrong.  Much thanks.

---

### Post by stalker145 on 2008-01-10
> **mkzimms said:**
> Looking for a 100% linux compatible PCI IDE controller.  Im trying to increase the storage on my server and I have like 6 100G IDE drives to work with and only 2 IDE channels on my current rig.  Its going to be used to house a logical drive for my FTP.  i dont have PCI-X so its not going to be used boot and work of off,  I assume anything will saturate a 100Mb connection, correct me if im wrong.  Much thanks.

I'll have to look when I get home to be sure. Until then, I can offer you what is in **lshw** for my server which uses *some* card like what you're looking for.
```
        *-storage
             description: Mass storage controller
             product: PCI0680 Ultra ATA-133 Host Controller
             vendor: Silicon Image, Inc.
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=pata_sil680 latency=32 module=pata_sil680
```
No configuration needed, hangs an extra 4 devices on your system, and runs without issue through Dapper. Edgy, Feisty, and now Gutsy. I had to install drivers for Windows (when I used it), but that was pretty easy. 
I don't recall the price, but I know I got it at BestBuy.

---

