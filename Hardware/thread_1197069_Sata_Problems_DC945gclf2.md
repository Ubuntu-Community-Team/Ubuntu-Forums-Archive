---
title: "Sata Problems DC945gclf2"
date: 2009-06-25
forum: Hardware
---

### Post by gfblock on 2009-06-25
Hi there,

I'm having problems with the sata controller of this Intel Atom Board.

This error keeps repeating : 

[INDENT][84342.772272] ata3.00: configured for UDMA/33
[84342.772293] ata3: EH complete
[84342.796969] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[84342.796979] ata3.00: BMDMA stat 0x26
[84342.796995] ata3.00: cmd 25/00:00:97:61:68/00:01:4e:00:00/e0 tag 0 dma 131072 in
[84342.796999]          res 51/84:b0:e7:61:68/84:00:4e:00:00/e0 Emask 0x30 (host bus error)
[84342.797006] ata3.00: status: { DRDY ERR }
[84342.797011] ata3.00: error: { ICRC ABRT }
[84342.797027] ata3: soft resetting link[/INDENT]

I decided to install 2.6.30 kernel and tried several kernel options, but the problem is not solved.

Sata controller is :

[INDENT]00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Intel Corporation Device 464c
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 20c8 [size=8]
        I/O ports at 20ec [size=4]
        I/O ports at 20c0 [size=8]
        I/O ports at 20e8 [size=4]
        I/O ports at 20a0 [size=16]
        Capabilities: [70] Power Management version 2
        Kernel driver in use: ata_piix[/INDENT]

I don't know if ata_piix could be the right choice, and I don't know how to force AHCI.

Any help will be highly regarded.

---

### Post by gfblock on 2009-06-25
Extra info about the device and disk :

        *-ide:1                                                                                                                   
             description: IDE interface                                                                                           
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller                                                             
             vendor: Intel Corporation                                                                                            
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
           *-disk
                description: ATA Disk
                product: ST31000528AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                version: CC34
                serial: 6VP0CPNP
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0008f93c
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /media/Tera
                   version: 1.0
                   serial: e38cc2e7-53d9-4a77-8a39-ee82186891e1
                   size: 931GiB
                   capacity: 931GiB
                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2009-06-20 15:45:39 filesystem=ext3 label=tera modified=2009-06-24 23:53:18 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=writeback mounted=2009-06-24 23:53:18 state=mounted

---

