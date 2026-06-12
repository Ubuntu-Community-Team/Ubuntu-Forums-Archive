---
title: "unkown character in hd uid?"
date: 2010-03-03
forum: Hardware
---

### Post by salviablue on 2010-03-03
HI,
When ever I call the uuid of the hard disk's, it shows the uuid, but with random characters inserted, question marks usually, or at the mount points..
Anyone know what this means?
I have done e2fsck -cc on all the partitions and all came back clean/ok (well one part has 10 badblocks and i think all the hd's where "modified" by e2fsck -cc).
Not sure whether its related, but everytime I e2fsck -cc on some partitions, the blocks used # increases, but not on others?

I usually run ubustu 9.10, but am checking the drives for errors since having some strange behaviour (usually associated with dying drives, drdy's etc, hence the checking). So this lshw is called from systemrescuecd, but i get the same kind of output from ubustu. This kind of output also occurred before e2fsck -cc'ing.

```
root@sysresccd / % lshw   
sysresccd                 
    description: Desktop Computer
    product: VT8363
    vendor: VIA Technologies, Inc.
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: 8363-686A
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 6.00 PG (03/08/2001)
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Socket A
          size: 2GHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous external write-back
     *-memory
          description: Flash Memory
          physical id: 20
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: BANK_0
             size: 256MiB
        *-bank:1
             description: DIMM
             physical id: 1
             slot: BANK_1
             size: 256MiB
        *-bank:2
             description: DIMM
             physical id: 2
             slot: BANK_2
             size: 512MiB
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: BANK_3
     *-pci
          description: Host bridge
          product: VT8363/8365 [KT133/KM133]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8
        *-pci
             description: PCI bridge
             product: VT8363/8365 [KT133/KM133 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
           *-display:0 UNCLAIMED
                description: VGA compatible controller
                product: RV280 [Radeon 9200 PRO]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
                configuration: latency=32 mingnt=8
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV280 [Radeon 9200 PRO] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32 mingnt=8
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: driver=parport_pc latency=0 module=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-disk:0
                description: ATA Disk
                product: SAMSUNG SV1021D
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: PE10
                serial: 0269J1DNA14192
                size: 9732MiB (10GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=6c0ecc90
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: 6f0cd715-73b8-4e66-a3ee-263a072d7439
                   size: 478MiB
                   capacity: 478MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2010-02-28 01:40:19 filesystem=ext3 lastmountpoint=/bootfNc&#65533;;&#65533;&#65533;p&#65533;&#65533;&#65533; :&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;?y&#65533;|&#65533;&#65533;&#65533;&#65533;&#65533;X&#65533;,&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;i&#65533;(i&#65533;&#65533;(i&#65533;&#65533;&#65533;;&#65533;&#65533; modified=2010-03-02 19:35:11 mounted=2010-03-02 17:30:49 state=clean
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1.0
                   serial: f93cbe6c-d5f3-4615-ac40-8427b2fef58f
                   size: 7153MiB
                   capacity: 7153MiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2010-02-28 01:40:21 filesystem=ext3 lastmountpoint=/I^ &#65533;&#65533;&#65533;&#65533;#&#65533;&#65533; >&#65533;&#65533;~&#65533;&#65533;?y&#65533;|~&#65533;&#65533;X&#65533;,&#65533;&#65533;~&#65533;&#65533;i&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;~&#65533;&#65533;&#65533;~ modified=2010-03-02 21:00:49 mounted=2010-03-02 18:04:05 state=clean
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 1.0
                   serial: 139266f6-1ccb-41b3-a157-e729ae214bf7
                   size: 478MiB
                   capacity: 478MiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2010-02-28 01:40:32 filesystem=ext3 lastmountpoint=/homeZ&#65533;[&#65533;&#65533;&#65533;/&#65533;h*&#65533;&#65533; ;&#65533;&#65533;>2&#65533;?y&#65533;|>2&#65533;X&#65533;,&#65533;&#65533;>2&#65533;i&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;/&#65533;&#65533;> modified=2010-03-02 22:25:17 mounted=2010-03-01 10:33:59 state=clean
              *-volume:3
                   description: Linux swap volume
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   version: 1
                   serial: 0ff31604-0dff-400d-8666-bf3f032f7b32
                   size: 1615MiB
                   capacity: 1615MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-disk:1
                description: ATA Disk
                product: ST340014A
                vendor: Seagate
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 3.06
                serial: 3JX4NG89
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=8ae18ae1
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   version: 1.0
                   serial: 5a9c1ad3-21cb-442c-b9f4-f9b6bab0f269
                   size: 956MiB
                   capacity: 956MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2010-02-26 00:32:52 filesystem=ext3 lastmountpoint=/media/5a9c1ad3-21cb-442c-b9f4-f9b6bab0f269&#65533;0&#65533;n&#65533;&#65533;@&#65533;&#65533;&#65533;&"&#65533;&#65533;&#65533;&#65533; modified=2010-03-02 23:16:27 mounted=2010-02-28 22:07:47 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sdb2
                   size: 1608MiB
                   capacity: 1608MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 1608MiB
                      capabilities: nofs
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.1.0,3
                   logical name: /dev/sdb3
                   version: 1.0
                   serial: bafc8cc8-18c0-4998-83d6-e3c88f070fb9
                   size: 18GiB
                   capacity: 18GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2010-02-26 00:32:53 filesystem=ext3 lastmountpoint=/targether*\&#65533;&#65533;8&#65533;_&#65533;&#335;&#65533;&#65533;&#65533;&#65533;&#65533;iW&#65533;&#65533;N&#65533;&#65533;N&#65533;\&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Y&#65533;\&#65533;&#65533; modified=2010-03-02 23:49:20 mounted=2010-02-28 22:08:20 state=clean
              *-volume:3
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 4
                   bus info: scsi@0:0.1.0,4
                   logical name: /dev/sdb4
                   version: 1.0
                   serial: 93a63617-977a-4a2d-87c3-9685b5a846c8
                   size: 16GiB
                   capacity: 16GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2010-02-26 08:43:39 filesystem=ext3 lastmountpoint=/media/93a63617-977a-4a2d-87c3-9685b5a846c88&#65533;`&#65533;&#65533;&#65533;@&#65533;"&#65533;&#65533;%"&#65533;&#65533;^&#65533; modified=2010-03-03 00:55:31 mounted=2010-02-28 22:08:30 state=clean
           *-cdrom
                description: DVD writer
                product: CD/DVDW TS-H552U
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /mnt/cdrom
                version: US02
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,relatime,mode=0644 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /mnt/cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,relatime,mode=0644 state=mounted
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 16
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.32.09-std140 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 16
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.32.09-std140 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12.0MB/s
              *-usb
                   description: Mass storage device
                   product: Flash Disk
                   vendor: Chipsbank Microelectronics Co., Ltd
                   physical id: 2
                   bus info: usb@2:2
                   logical name: scsi2
                   version: 1.00
                   serial: 0113170218193609
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB/s
                 *-disk
                      description: SCSI Disk
                      physical id: 0.0.0
                      bus info: scsi@2:0.0.0
                      logical name: /dev/sdc
                      size: 2015MiB (2112MB)
                      capabilities: partitioned partitioned:dos
                      configuration: signature=0221d798
                    *-volume
                         description: Windows FAT volume
                         vendor: @SWIN4.1
                         physical id: 1
                         bus info: scsi@2:0.0.0,1
                         logical name: /dev/sdc1
                         logical name: /flash
                         version: FAT16
                         serial: 0221-d798
                         size: 2014MiB
                         capacity: 2014MiB
                         capabilities: primary bootable fat initialized
                         configuration: FATs=2 filesystem=fat label=DISK_IMG mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=ascii,shortname=mixed,errors=remount-ro state=mounted
        *-bridge UNCLAIMED
             description: Bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 7.4
             bus info: pci@0000:00:07.4
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: bridge pm cap_list
             configuration: latency=0
        *-multimedia UNCLAIMED
             description: Multimedia audio controller
             product: SB Live! EMU10k1
             vendor: Creative Labs
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32 maxlatency=20 mingnt=2
        *-input UNCLAIMED
             description: Input device controller
             product: SB Live! Game Port
             vendor: Creative Labs
             physical id: a.1
             bus info: pci@0000:00:0a.1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: c
             bus info: pci@0000:00:0c.0
             logical name: eth0
             version: 10
             serial: 00:10:a7:21:16:e0
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.87 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

```

e2fsck:

```
root@sysresccd / % e2fsck -ccfkvy /dev/sda1
e2fsck 1.41.9 (22-Aug-2009)
Checking for bad blocks (non-destructive read-write test)
Testing with random pattern: done                                
/dev/sda1: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

     165 inodes used (0.13%)
       0 non-contiguous files (0.0%)
       0 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 155
   42625 blocks used (8.70%)
       0 bad blocks
       0 large files

     153 regular files
       3 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
     156 files
root@sysresccd / % e2fsck -ccfkvy /dev/sda2
e2fsck 1.41.9 (22-Aug-2009)
Checking for bad blocks (non-destructive read-write test)
Testing with random pattern: done                                
/dev/sda2: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes

Running additional passes to resolve blocks claimed by more than one inode...
Pass 1B: Rescanning for multiply-claimed blocks
Multiply-claimed block(s) in inode 185064: 1170432 1170479
Pass 1C: Scanning directories for inodes with multiply-claimed blocks
Pass 1D: Reconciling multiply-claimed blocks
(There are 1 inodes containing multiply-claimed blocks.)

File /var/cache/apt/archives/muse_0.8.1a-6.3ubuntu0.1_i386.deb (inode #185064, mod time Mon Nov 30 12:05:24 2009) 
  has 2 multiply-claimed block(s), shared with 1 file(s):
	<The bad blocks inode> (inode #1, mod time Tue Mar  2 19:45:41 2010)
Clone multiply-claimed blocks? yes

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong for group #0 (4946, counted=4944).
Fix? yes

Free blocks count wrong for group #35 (7969, counted=7971).
Fix? yes


/dev/sda2: ***** FILE SYSTEM WAS MODIFIED *****

  185654 inodes used (40.55%)
     197 non-contiguous files (0.1%)
     109 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 162991/18
 1042664 blocks used (56.93%)
      10 bad blocks
       1 large file

  140111 regular files
   17112 directories
      68 character device files
      26 block device files
       2 fifos
     525 links
   28290 symbolic links (22503 fast symbolic links)
      36 sockets
--------
  186170 files
root@sysresccd / % e2fsck -ccfkvy /dev/sda2
e2fsck 1.41.9 (22-Aug-2009)
Checking for bad blocks (non-destructive read-write test)
Testing with random pattern: done                                
/dev/sda2: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda2: ***** FILE SYSTEM WAS MODIFIED *****

  185654 inodes used (40.55%)
     197 non-contiguous files (0.1%)
     109 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 162990/19
 1042664 blocks used (56.93%)
      10 bad blocks
       1 large file

  140111 regular files
   17112 directories
      68 character device files
      26 block device files
       2 fifos
     525 links
   28290 symbolic links (22503 fast symbolic links)
      36 sockets
--------
  186170 files
root@sysresccd / % e2fsck -ccfkvy /dev/sda3
e2fsck 1.41.9 (22-Aug-2009)
Checking for bad blocks (non-destructive read-write test)
Testing with random pattern: done                                
/dev/sda3: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda3: ***** FILE SYSTEM WAS MODIFIED *****

     421 inodes used (0.34%)
      21 non-contiguous files (5.0%)
       3 non-contiguous directories (0.7%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 397/10
  336588 blocks used (68.69%)
       0 bad blocks
       0 large files

     270 regular files
     138 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       4 symbolic links (4 fast symbolic links)
       0 sockets
--------
     412 files

root@sysresccd / % mke2fs -c /dev/sda4 
mke2fs 1.41.9 (22-Aug-2009)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
103584 inodes, 413673 blocks
20683 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=423624704
13 block groups
32768 blocks per group, 32768 fragments per group
7968 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912

Checking for bad blocks (read-only test): done                                
Writing inode tables: done                            
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 25 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.


root@sysresccd / % mkswap /dev/sda4
Setting up swapspace version 1, size = 1654688 KiB
no label, UUID=0ff31604-0dff-400d-8666-bf3f032f7b32

root@sysresccd / % e2fsck -ccfkvy /dev/sdb1
e2fsck 1.41.9 (22-Aug-2009)
Checking for bad blocks (non-destructive read-write test)
Testing with random pattern: done                                
/dev/sdb1: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sdb1: ***** FILE SYSTEM WAS MODIFIED *****

     164 inodes used (0.27%)
       0 non-contiguous files (0.0%)
       0 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 154
   11991 blocks used (4.89%)
       0 bad blocks
       1 large file

     152 regular files
       3 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
     155 files

root@sysresccd / % e2fsck -ccfkvy /dev/sdb3
e2fsck 1.41.9 (22-Aug-2009)
Checking for bad blocks (non-destructive read-write test)
Testing with random pattern: done                                
/dev/sdb3: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sdb3: ***** FILE SYSTEM WAS MODIFIED *****

   31224 inodes used (2.55%)
      10 non-contiguous files (0.0%)
      23 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 29567/5
  207271 blocks used (4.24%)
       0 bad blocks
       1 large file

   24850 regular files
    4245 directories
      59 character device files
      26 block device files
       0 fifos
     406 links
    2035 symbolic links (1557 fast symbolic links)
       0 sockets
--------
   31621 files
root@sysresccd / % e2fsck -ccfkvy /dev/sdb4
e2fsck 1.41.9 (22-Aug-2009)
Checking for bad blocks (non-destructive read-write test)
Testing with random pattern: done                                
/dev/sdb4: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sdb4: ***** FILE SYSTEM WAS MODIFIED *****

      15 inodes used (0.00%)
       0 non-contiguous files (0.0%)
       0 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 5
  110483 blocks used (2.61%)
       0 bad blocks
       1 large file

       3 regular files
       3 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
       6 files
root@sysresccd / % mke2fs -c /dev/sdb2     
mke2fs 1.41.9 (22-Aug-2009)
mke2fs: inode_size (128) * inodes_count (0) too big for a
	filesystem with 0 blocks, specify higher inode_ratio (-i)
	or lower inode count (-N).

root@sysresccd / % mke2fs -c /dev/sdb5
mke2fs 1.41.9 (22-Aug-2009)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
102960 inodes, 411657 blocks
20582 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=423624704
13 block groups
32768 blocks per group, 32768 fragments per group
7920 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912

Checking for bad blocks (read-only test): done                                
Writing inode tables: done                            
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 30 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
root@sysresccd / % mkswap /dev/sdb5        
Setting up swapspace version 1, size = 1646624 KiB
no label, UUID=59c22b66-b88f-4e55-b6a0-77fe4f5dd9ee

```

anyhelp would be appreciated

---

