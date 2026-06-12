---
title: "ATA &amp; SATA on RAID"
date: 2008-06-22
forum: Hardware
---

### Post by pki on 2008-06-22
Hello.

I'm not sure if this is the right category for my question, if not please move to the right.


I have installed ubuntu server 8.04 x64 on an ASrock K8Upgrade VM800 mainboard.

On ATA are two disks, 300GB each for / as RAID5 (software), this are primary master and slave.

On SATA are two disks, 500GB each for /home as RAID5 (software).

Everything works fine. The drives are detected as /dev/sda-sdd. I installed GRUB on both boot drives (the 300GB drives).

The problem begins then i remove one of the 300GB drives (simulating failure). If i remove the slave the system goes up in degraded mode, this is ok. The second raid (500GB) dont work.

If i remove the master drive the system won't boot. /dev/sdb is then moved to /dev/sda, sdc becomes sdb and so on.

How can i prevent the drives changing there names (sdb->sda)?

The controler is
        *-ide:0
             description: IDE interface
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_via latency=32 module=sata_via
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_via latency=32 module=pata_via


I dmesg i can see

sdb:<4>Driver 'sr' needs updating - please use bus_type methods

What can I do?

Best regards.

Piotr

---

