---
title: "What command can I use to check my systems specs"
date: 2013-12-29
forum: Hardware
---

### Post by michael-piziak on 2013-12-29
What command can I use to check my systems specs - such as my memory, etc...

Or is there a utility in the "dash home" that I can use to check it

---

### Post by deadflowr on 2013-12-29
There are several commands you could try
```
sudo lshw
```
several other as well, I would think.
you could also look at installing something like the program "system profile and benchmark", which I believe does all that, and more, in a gui.

---

### Post by michael-piziak on 2013-12-29
Please tell me why "sudo lsw" shows 332 giB (250 GB)  but "system monitor" only shows 39.9 total giB with 32.8 giB available.  See the screenshot attached.

My understanding when I got this computer is that it had 250 gig hard drive.  I partitioned it so that most of it is Ubuntu and only small amout is Windows Vista

The "sudo lsw" is closer to what I thought it should be.  Why is System Monitor showing such small amount?

see attachment screenshot

---

### Post by deadflowr on 2013-12-29
The lshw output you posted shows you the whole disk.System monitor is only showing you the mounted partitions.
Towards the end of the lshw output should be where the output for the partition you have is.
The parts should be listed as volumes. Starting with volume 0.
So the output should list first the whole disk, then the volumes.

---

### Post by michael-piziak on 2013-12-29
I'm afraid I did the partition wrong from installing from the Ubuntu CD.  I thought I had given Ubuntu most of the HD space, but why does "system monitor" only show 39.9 gigs ?  Does it think only that much is for Ubuntu.  
Please look at this below and tell me what you think.  I will do a reinstall if Windoes Vista is getting the majority of my HD !


     *-disk
                description: ATA Disk
                product: ST3250410AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 6RY4HMH2
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ccfd1447
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 4e3eabaa-7a78-d845-89f2-a80e22f8e63a
                   size: 186GiB
                   capacity: 186GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2013-12-14 22:23:21 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 40ad3eef-fc7f-4e4f-aaf1-c361d9510689
                   size: 1973MiB
                   capacity: 2000MiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2013-12-14 22:49:40 filesystem=ntfs label=OS_TOOLS state=clean
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 44GiB
                   capacity: 44GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 40GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 4015MiB
                      capabilities: nofs
        *-ide:1
             description: IDE interface
             product: 82801I (ICH9 Family) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1258(size=8) ioport:1270(size=4) ioport:1260(size=8) ioport:1274(size=4) ioport:1220(size=16) ioport:1230(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: CD/DVDW TS-H653L
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: HA03
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
     *-scsi
          physical id: 4
          bus info: usb@2:1
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0

---

### Post by deadflowr on 2013-12-29
I think the installer just gave you the space it saw as best fit for the install.
Resizing windows parts(ntfs) can cause harm to the windows install if not done right.
Linux tools aren't so great when it comes to this, so the system allocated as much space as it felt it could without damaging the existing system.IMHO.
Here's some idea
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Edit: You can resize during the initial install, when you get to the how/where to install section.
toggle the slider bar at top.
But I will restate that I think the installer gave you as much as it felt safe.

---

### Post by michael-piziak on 2013-12-29
I took care of the problem.  I reinstalled Ubuntu and now it's on 100% of my HD.

---

### Post by mörgæs on 2013-12-30
I have to remind you - again - that it's a polite gesture to mark your threads 'solved' using 'thread tools' when you don't need more assistance.

---

