---
title: "hard drives switching logical names"
date: 2008-07-22
forum: Hardware
---

### Post by nduerr on 2008-07-22
Last weekend I loaded 8.04 and am using it as a Windows file server.  The problem I am having is with my hard drives during the boot up process.  For some reason the logical name (/dev/sda1 etc) are changing from boot to boot.  I have 3 SCSI and 2 serial ATA drives.  This is a list of what is on each disk. and how they booted in 2 consecutive boots
*_Boot 1_*
SCSI Disk 0 segate 68GB
/dev/sda1 = /boot  
/dev/sda2 = /

SCSI Disk 1 viking II 4.5GB
/dev/sdb1 = swap
/dev/sdb2 = swap
 
SCSI Disk 2 Atlas 34GB
/dev/sde1 = /media/_s1

ATA 0 Segate 110GB
/dev/sdc1 = /media/_h1

ATA 1 Segate 110GB 
/dev/sdd1 = /media/_h2

*_Boot 2_*
SCSI Disk 0 segate 68GB
/dev/sdc1 = /boot  
/dev/sdc2 = /  & /media/_h1

SCSI Disk 1 viking II 4.5GB
/dev/sdd1 = swap  & /media/_h2
/dev/sdd2 = swap
 
SCSI Disk 2 Atlas 34GB
/dev/sde1 = /media/_s1

ATA 0 Segate 110GB
/dev/sda1 = not mounted

ATA 1 Segate 110GB 
/dev/sdb1 = not mounted

As you can see the auto mounting does not come correctly during the second boot.  Is there something I can do to get these drive to come up in a static state?  :confused:

System info

    description: Desktop Computer
    product: PROD00000000
    vendor: OEM00000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: 8IK1100
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: FG (03/01/2004)
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.5
          slot: Socket 478
          size: 2800MHz
          capacity: 3600MHz
          width: 32 bits
          clock: 200MHz


          *-scsi
                description: SCSI storage controller
                product: AIC-7892A U160/m
                vendor: Adaptec
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: scsi2
                version: 02
                width: 64 bits
                clock: 66MHz
                capabilities: scsi pm bus_master cap_list scsi-host
                configuration: driver=aic7xxx latency=32 maxlatency=25 mingnt=40 module=aic7xxx
              *-disk:0
                   description: SCSI Disk
                   product: ST373455LW
                   vendor: SEAGATE
                   physical id: 0.0.0
                   bus info: scsi@2:0.0.0
                   logical name: /dev/sdc
                   version: 0003
                   serial: 3LQ2A1KD00009822ALLJ
                   size: 68GiB (73GB)
                   capacity: 69GiB (75GB)
                   capabilities: 15000rpm partitioned partitioned:dos
                   configuration: ansiversion=3 signature=0000256f
                 *-volume:0
                      description: EXT3 volume
                      vendor: Linux
                      physical id: 1
                      bus info: scsi@2:0.0.0,1
                      logical name: /dev/sdc1
                      version: 1.0
                      serial: e6e1a730-fbdf-48b1-8cd5-a8f34b5da124
                      size: 9766MiB
                      capacity: 9766MiB
                      capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                      configuration: created=2008-06-21 06:42:19 filesystem=ext3 modified=2008-07-22 05:57:34 mounted=2008-07-22 05:52:06 state=clean
                 *-volume:1
                      description: EXT3 volume
                      vendor: Linux
                      physical id: 2
                      bus info: scsi@2:0.0.0,2
                      logical name: /dev/sdc2
                      logical name: /
                      logical name: /dev/.static/dev
                      version: 1.0
                      serial: dc71aae3-bf1d-4db2-8398-5a49fc596d3e
                      size: 58GiB
                      capacity: 58GiB
                      capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                      configuration: created=2008-06-21 06:42:22 filesystem=ext3 modified=2008-07-22 05:58:47 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-07-22 05:58:47 state=mounted
              *-disk:1
                   description: SCSI Disk
                   product: VIKING II 4.5WLS
                   vendor: QUANTUM
                   physical id: 0.1.0
                   bus info: scsi@2:0.1.0
                   logical name: /dev/sdd
                   version: 4110
                   serial: 194816243233
                   size: 4350MiB (4562MB)
                   capacity: 5251MiB (5507MB)
                   capabilities: 7200rpm partitioned partitioned:dos
                   configuration: ansiversion=2 signature=ebd8ed5f
                 *-volume:0
                      description: Linux swap volume
                      physical id: 1
                      bus info: scsi@2:0.1.0,1
                      logical name: /dev/sdd1
                      version: 1
                      serial: b5cbb43a-814a-40e3-bebf-7b37cea4a954
                      size: 1996MiB
                      capacity: 1996MiB
                      capabilities: primary bootable nofs swap initialized
                      configuration: filesystem=swap label=SWAP-sdb1 pagesize=4096
                 *-volume:1
                      description: Linux swap volume
                      physical id: 2
                      bus info: scsi@2:0.1.0,2
                      logical name: /dev/sdd2
                      version: 1
                      serial: a5f4c181-65f3-4b2d-bd3c-6896847d9e92
                      size: 1996MiB
                      capacity: 1996MiB
                      capabilities: primary nofs swap initialized
                      configuration: filesystem=swap label=SWAP-sdb2 pagesize=4096
              *-disk:2
                   description: SCSI Disk
                   product: ATLAS10K3_36_WLS
                   vendor: QUANTUM
                   physical id: 0.2.0
                   bus info: scsi@2:0.2.0
                   logical name: /dev/sde
                   version: 020W
                   serial: 344212048127
                   size: 34GiB (36GB)
                   capacity: 34GiB (36GB)
                   capabilities: 10000rpm partitioned partitioned:dos
                   configuration: ansiversion=3 signature=2c53f30f
                 *-volume
                      description: EXT3 volume
                      vendor: Linux
                      physical id: 1
                      bus info: scsi@2:0.2.0,1
                      logical name: /dev/sde1
                      logical name: /media/_s1
                      version: 1.0
                      serial: 214a17e0-46a3-4a26-b37a-bc4a09b848c8
                      size: 34GiB
                      capacity: 34GiB
                      capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                      configuration: created=2004-06-16 05:12:13 filesystem=ext3 label=/s1 modified=2008-07-22 06:00:32 mount.fstype=ext3 mount.options=rw,relatime,data=ordered mounted=2008-07-22 06:00:32 state=mounted

        *-ide
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk:0
                description: ATA Disk
                product: ST3120026AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.18
                serial: 5JT2CLST
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=502c66f9
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/_h1
                   version: 1.0
                   serial: f942a5ed-320d-4d98-b675-54a2395c3c1a
                   size: 111GiB
                   capacity: 111GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2004-06-16 04:53:35 filesystem=ext3 label=/h1 modified=2008-07-22 06:04:14 mount.fstype=ext3 mount.options=rw,relatime,data=ordered mounted=2008-07-22 06:04:14 state=mounted
           *-disk:1
                description: ATA Disk
                product: ST3120026AS
                vendor: Seagate
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 3.18
                serial: 5JT2C0TR
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=502c66f8
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /media/_h2
                   version: 1.0
                   serial: 2d9b2c0f-94c3-4b55-8ced-7a17cd770aa0
                   size: 111GiB
                   capacity: 111GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2004-06-16 05:02:56 filesystem=ext3 label=/h2 modified=2008-07-22 06:01:34 mount.fstype=ext3 mount.options=rw,relatime,data=ordered mounted=2008-07-22 06:01:34 state=mounted

---

### Post by logos34 on 2008-07-22
> **nduerr said:**
> As you can see the auto mounting does not come correctly during the second boot.  Is there something I can do to get these drive to come up in a static state?  :confused:

It seems your /etc/fstab is not using UUIDs--if it were you wouldn't have this problem (because the disks would be identified by their uuid #'s and not block device name.  

i.e.:

                      serial: b5cbb43a-814a-40e3-bebf-7b37cea4a954

---

