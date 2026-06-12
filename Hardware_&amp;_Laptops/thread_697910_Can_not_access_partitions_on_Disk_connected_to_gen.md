---
title: "Can not access partitions on Disk connected to generic card with VIA VT6421 chipset"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by noamik on 2008-02-15
Hi,

I just installed a new generic PCI-card with VIA VT6421 chipset. I just want to access a harddrive using the IDE-channel offered by this card. I already googled quite a bit and I searched the forum, so please don't reply to do so without a hint for the proper query.

Output of "lspci" is:
> 
 01:06.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)


Output of "lshw" is:
> 
 *-storage
                description: RAID bus controller
                product: VT6421 IDE RAID Controller
                vendor: VIA Technologies, Inc.
                physical id: 6
                bus info: pci@0000:01:06.0
                logical name: scsi2
                version: 50
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list emulated
                configuration: driver=sata_via latency=32 module=sata_via
              *-disk
                   description: SCSI Disk
                   product: SAMSUNG HD400LD
                   vendor: ATA
                   physical id: 0.0.0
                   bus info: scsi@2:0.0.0
                   logical name: /dev/sda
                   version: WQ10
                   serial: S0AXJ12LA00438
                   size: 372GB
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5
                 *-volume:0 UNCLAIMED
                      description: W95 FAT32 (LBA) partition
                      physical id: 1
                      bus info: scsi@2:0.0.0,1
                      capacity: 191GB
                      capabilities: primary
                 *-volume:1 UNCLAIMED
                      description: W95 FAT32 (LBA) partition
                      physical id: 2
                      bus info: scsi@2:0.0.0,2
                      capacity: 180GB
                      capabilities: primary


Output of "lsmod | grep sata_via" is:
> 
sata_via               12548  0 
libata                125168  2 ata_generic,sata_via


Output of "fdisk -l /dev/sda" is:
> Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22a61811

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       25063   201318516    c  W95 FAT32 (LBA)
/dev/sda2           25064       48641   189390285    c  W95 FAT32 (LBA)

With qtparted I am also able to see the partitions.

The problem is, /dev/sda1 and /dev/sda2 do not exist, the same is true for /dev/.static/dev/sda1 and sda2

I already tried to stop udev and to create sda1 and so on with ./MAKEDEV sda and to mount the partitions manually, but it just tells me, it would not be a block device. Same is true for ./MAKEDEV sda without stoping udev.

What am I doing wrong? Any idea why sda1 and sda2 are not created?

Just in case: I'm using xubuntu 7.10 ...

---

### Post by noamik on 2008-02-17
I just looked into what dmesg tells me right on boot. Thought it might help you help me :-D
As it's quite long, I attach it as a text-file.

---

### Post by noamik on 2008-02-20
Somebody told me, it could be a cable issue, but how could this setup work with windows, if there was a hardware problem?
I tried a second cable anyway. Problem stays the same.

Another funny problem: if I switch this damn harddrive with my DVD-Drive, xubuntu won't even boot.

---

### Post by noamik on 2008-02-20
I just tried to connect a SATA-Drive. It works as expected.

I have no idea why I can read the partition table with fdisk, but the kernel doesn't get it? I'll try another PATA-Disk later. If any of you happens to have an idea, i'd be happy to hear it.

---

### Post by noamik on 2008-02-21
A friend of mine helped me to access the disk.
> 
sudo blockdev -v --rereadpt /dev/sda

forces the kernel to reread the partition table. This proves the driver to be at least functional. As it is not really elegant, to type or start this each time after boot: could anyone track down the problem and tell me what I would have to do to the controller to
[LIST]
[*]use this disk with dma
[*]let the kernel read the partition table on boot, not to make him reread it later
[/LIST]

---

### Post by noamik on 2008-02-29
Still nobody who knows what really happens here and why?

Any idea how i could force the drive to use DMA? PIO4 is not really cool to access a hard drive.

---

### Post by noamik on 2008-05-06
Problem got solved by updating to hardy, suppose it was a kernel driver bug ...

---

