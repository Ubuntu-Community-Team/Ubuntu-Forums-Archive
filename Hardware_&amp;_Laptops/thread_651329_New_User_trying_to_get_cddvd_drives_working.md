---
title: "New User trying to get cd/dvd drives working"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by ragashiwala on 2007-12-27
I'm a new user, and am trying to get Ubuntu to read my cds or dvds.  Here is my setup:

I am using 7.10 and have it installed as a vmx using vmware.  I'm pretty sure that the cd drives are set correctly in there, but just in case, below is the part of the vmx for the cd drives:

# Settings for physical CDROM drive
ide1:0.present = "TRUE"
ide1:0.deviceType = "cdrom-raw"
ide1:0.startConnected = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.autodetect = "TRUE"

# Settings for physical CDROM drive
ide1:1.present = "TRUE"
ide1:1.deviceType = "cdrom-raw"
ide1:1.startConnected = "TRUE"
ide1:1.fileName = "auto detect"
ide1:1.autodetect = "TRUE"

I have tried setting the auto detect to the actual drive letters, but it keeps going back to autodetect.

I installed the OS by liveCD using an iso.  Now, no matter what cd i insert into the drives, they do not show up as icons nor are they accessable in other ways.  I know the drives work well.  They are both IDE drives 0 and 1 on the secondary channel.

I ran sudo lshw to try and get some information about this and I am pasting the ide and scsi info here:

        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=64 module=ata_piix
           *-disk
                description: SCSI Disk
                product: VMware Virtual I
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0000
                serial: 00000000000000000001
                size: 4800MB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 4533MB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 258MB
                   capacity: 258MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 258MB
                      capabilities: nofs
           *-cdrom:0
                description: DVD reader
                product: DVD-ROM MAGIC 62
                vendor: OBVIOUS
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 6.00
                serial: NECVMWarVMware IDE CDR101.00
                capabilities: removable audio dvd
                configuration: ansiversion=2 status=open
           *-cdrom:1
                description: DVD reader
                product: DVD-ROM MAGIC 62
                vendor: OBVIOUS
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 6.00
                serial: NECVMWarVMware IDE CDR111.00
                capabilities: removable audio dvd
                configuration: ansiversion=2 status=open

Any help to make my drives work would be appreciated.

Raj

---

