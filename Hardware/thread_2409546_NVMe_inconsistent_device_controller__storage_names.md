---
title: "NVMe inconsistent device controller / storage namespace between reboots"
date: 2019-01-03
forum: Hardware
---

### Post by zaurian on 2019-01-03
Thank you for reading my question.  I've looked for similar inquiries across multiple forums to no avail.

This is strange indeed.  I have two 1 Tb NVMe drives.  However, between reboots the device controller name seems to randomly fluctuate and swap between the two.  I never know which NVMe drive will be represented by which of the two device controllers: /dev/nvme0 or /dev/nvme1

You can see here the drives and partitions as listed by lsblk:
```
steve@Threadripper-U3:~$ lsblk
NAME                                         MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
nvme1n1                                      259:0    0 931.5G  0 disk 
|-nvme1n1p1                                  259:5    0   512M  0 part /boot/efi
|-nvme1n1p2                                  259:6    0  59.6G  0 part /
|-nvme1n1p3                                  259:7    0 405.8G  0 part /media/steve/NVMe0n1p3-Ext4
|-nvme1n1p4                                  259:8    0 465.7G  0 part 
  |-LVM--VolGroup01-LVM--NVMe1n1p4--VolGrp01 253:0    0 465.7G  0 lvm  
nvme0n1                                      259:1    0 931.5G  0 disk 
|-nvme0n1p1                                  259:2    0  10.5G  0 part [SWAP]
|-nvme0n1p3                                  259:4    0   860G  0 part /media/steve/NVMe1n1p3-Ext41
steve@Threadripper-U3:~$ 



```

I could reboot until I get the drives swapped, but it will undoubtedly eventually happen. Here is what I would see (I have manually edited this, but it will give you the idea):

```
steve@Threadripper-U3:~$ lsblk
NAME                                         MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
nvme0n1                                      259:0    0 931.5G  0 disk 
|-nvme0n1p1                                  259:5    0   512M  0 part /boot/efi
|-nvme0n1p2                                  259:6    0  59.6G  0 part /
|-nvme0n1p3                                  259:7    0 405.8G  0 part /media/steve/NVMe0n1p3-Ext4
|-nvme0n1p4                                  259:8    0 465.7G  0 part 
  |-LVM--VolGroup01-LVM--NVMe1n1p4--VolGrp01 253:0    0 465.7G  0 lvm  
nvme1n1                                      259:1    0 931.5G  0 disk 
|-nvme1n1p1                                  259:2    0  10.5G  0 part [SWAP]
|-nvme1n1p3                                  259:4    0   860G  0 part /media/steve/NVMe1n1p3-Ext41
steve@Threadripper-U3:~$ 



```

Note that the storage namespace / mount point is consistent.  I named these mount points when the nvme drives mapped one way.  I assume they mount properly no matter what due to the UUID not changing even though the device controller (/dev) name changes?  Here is another example - a screenshot showing the swapped drives mapping appropriately to their mount points even though the device controller name has been swapped:


[ATTACH=CONFIG]282089[/ATTACH]

The partitions and mountings seem to work fine even with the device controllers swapping.  Therefore, it doesn't seem like it's a big issue overall - everything seems to be working fine between boots, regardless of which identifier (0 or 1) each NVMe drive boots with.  It still makes me uneasy though... what am I missing here?

Any ideas?

> System Details:
ASUSTek ROG Zenith Extreme X399 E-ATX HEDT Motherboard
    BIOS American Megatrends Inc. v1601 (10/26/2018)
AMD Ryzen Threadripper 1950X 16-Core Processor 3.39 GHz
Corsair Vengeance RGB 8 x 16GB DDR4 DRAM 3200MHz C16 Memory (128GB) (CMR32GX4M2C3200C16)
Corsair AX1600i Digital ATX Power Supply (1600w)

Storage:
2 x Samsung 1TB PM961 Single Sided 80mm (2280/2280SS) M.2 PCI Express 3.0 x4 (PCIe Gen3 x4) OEM NVMe SSD (MZVLW1T0HMLH)
WDMyCloudDL4100 with 4 x 3 Tb HDD (12 Tb NAS)

Network:
Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (Motherboard)
Wilocity Ltd Wil6200 802.11ad Wireless Network Adapter (Motherboard)
Intel I211 Gigabit Network Ethernet Controller (Motherboard)
Aquantia Corp AQC107 NBase-T/IEEE 802.3bz Ethernet Controller (10G PCI card)

Graphics:
NVIDIA GeForce GTX 1080 Ti Gaming X 11G  - Windows 10 Guest Graphics (PCI Passthrough)
MSI AMD Radeon R7 240 (Oland PRO) - Ubuntu Host Graphics

Case and Cooling:
Corsair Crystal Series 570X RBG Mid-Tower Case
Thermaltake Floe Riing RGB 360 TT Premium Edition Cooling System with CPU Water Block

Display:
LG OLED65C7P 65" 4K UHD Smart OLED TV (2017 Model)

---

### Post by CatKiller on 2019-01-03
That always happens. It happened with SATA drives, and PATA and SCSI drives before that. There's absolutely no guarantee about which drive will prick up its ears first at boot time. That's why UUIDs or labels are used instead for anything important.

---

### Post by zaurian on 2019-01-03
No kidding!  Thank you for the reply.  This is good to know.  I suppose I should now stop naming my mount points based on the name of the device controller!

---

### Post by QIII on 2019-01-03
I name my mount points after Norse, Irish and German mythological characters (which are also used as the device labels) and use those with the UUID in my fstab.

---

