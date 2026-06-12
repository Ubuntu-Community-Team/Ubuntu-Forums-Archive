---
title: "Can't get eSata disk working"
date: 2008-08-01
forum: Hardware
---

### Post by mauri kanter on 2008-08-01
Hi:

I'm a newbie to Ubuntu and Linux ... So I'm grateful a-priori for your patience.

I'm facing aproblem using an eSata disk.

I'm running Ubuntu on an MSI PR-600 Laptop. I'm quite happy with it.

I bought for it a new 500 GB hard disk FreeAgent from Seagate
which includes support fo USB, FireWire and eSata.

I bought an eSata card for the laptop and an eSata cable.

The eSata card seems to be properly recognized, if I understand correctly.
The hard disk works also properly with the USB connection  but does not with eSata.

See some lines of the lshw an dmesg below.

P.S. I tried in my previous PC (IBM t42 with win XP) ... It 
does not recognize it either ... Even though Windows auomatically
recognized a new hardware and downloaded a driver for Sil 3512 ...

Mauri.

root@msii-laptop:/home/mauri# uname -r
2.6.24-19-generic


     *-storage
          description: Mass storage controller
          product: SiI 3512 [SATALink/SATARaid] Serial ATA Controller
          vendor: Silicon Image, Inc.
          physical id: 2
          bus info: pci@0000:02:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          capabilities: storage pm bus_master cap_list
          configuration: driver=sata_sil latency=64 module=sata_sil
     *-scsi
          physical id: 3
          bus info: usb@7:2
          logical name: scsi10
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: FreeAgent Pro
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@10:0.0.0
             logical name: /dev/sdb
             version: 4109
             serial: 9QM245PA
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=a4b57300
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@10:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/FreeAgent Drive
                version: 3.1
                serial: d04b-ed16
                size: 465GiB
                capacity: 465GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2008-05-05 05:54:05 filesystem=ntfs label=FreeAgent Drive mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other state=mounted


[151263.974644] ata11: SATA link down (SStatus 0 SControl 310)
root@msii-laptop:/home/mauri# dmesg | tail -30
[150989.728612] usb-storage: device scan complete
[150989.730242] scsi 10:0:0:0: Direct-Access     Seagate  FreeAgent Pro    4109 PQ: 0 ANSI: 4
[150989.735057] sd 10:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[150989.736695] sd 10:0:0:0: [sdb] Write Protect is off
[150989.736706] sd 10:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[150989.736711] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[150989.739925] sd 10:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[150989.741424] sd 10:0:0:0: [sdb] Write Protect is off
[150989.741431] sd 10:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[150989.741435] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[150989.741443]  sdb: sdb1
[150989.756587] sd 10:0:0:0: [sdb] Attached SCSI disk
[150989.756683] sd 10:0:0:0: Attached scsi generic sg2 type 0
[151015.619806] cs: warning: no high memory space available!
[151209.069177] usb 7-2: USB disconnect, address 4
[151246.286753] cs: warning: no high memory space available!
[151259.266833] pccard: card ejected from slot 0
[151259.299857] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[151261.453015] pccard: CardBus card inserted into slot 0
[151261.453414] PCI: Enabling device 0000:02:00.0 (0000 -> 0003)
[151261.453431] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 22 (level, low) -> IRQ 19
[151261.453466] sata_sil 0000:02:00.0: cache line size not set.  Driver may not function
[151261.453474] sata_sil 0000:02:00.0: Applying R_ERR on DMA activate FIS errata fix
[151261.453491] PCI: Setting latency timer of device 0000:02:00.0 to 64
[151261.453696] scsi11 : sata_sil
[151261.453795] scsi12 : sata_sil
[151261.453858] ata10: SATA max UDMA/100 mmio m512@0x44000000 tf 0x44000080 irq 19
[151261.453866] ata11: SATA max UDMA/100 mmio m512@0x44000000 tf 0x440000c0 irq 19
[151263.662937] ata10: SATA link down (SStatus 1 SControl 310)
[151263.974644] ata11: SATA link down (SStatus 0 SControl 310)

---

### Post by flatline on 2008-08-01
Mauri:

I am not an expert, but I was told that for some reason, at least in Linux, eSATA is **not** hot-swappable.  Have you tried connecting & powering up the hard drive before you turn on the computer?

---

### Post by mauri kanter on 2008-08-01
> **flatline said:**
> Mauri:

I am not an expert, but I was told that for some reason, at least in Linux, eSATA is **not** hot-swappable.  Have you tried connecting & powering up the hard drive before you turn on the computer?

Yep I tried ... May be the problem is the connector ?

---

### Post by rmjohnson144 on 2008-08-02
> **mauri kanter said:**
> Yep I tried ... May be the problem is the connector ?

This could be the problem.  I recently bought an external eSATA DVD and External 500GB hard drive.  I first hook up the hard drive to sata port and preformat it and get it ready.  I then put it in my eSATA case and hook it up and nothing.  Not even recognized at all, not even bios.

I then try the eSATA DVD case and all is fine.  I figure it was the case.  Then I moved it to my other computer for another test and all is fine.  Then I left the eSATA cable on the other machine and used my hard drive's eSATA cable to the DVD eSATA box and nothing.  

I look at the cables and one is longer than the other.  I then look at the eSATA connector and plug in the long cables and notice the plug sticks out on all the ports excapy my main computer which was failing.

so definately there are two different sizes of eSATA connector.

Good luck
-=Mark=-

---

### Post by mauri kanter on 2008-08-02
Bad luck ... I finally broke the eSata connector on the Seagate side while trying to insert it ... This happend after I noticed that there is like a "click" when I inserted it on the controller card side ...

So this is the end of my eSata intent ... I'm back on the USB :-(

Thank you all for your willingness to help.

Mauri.

---

