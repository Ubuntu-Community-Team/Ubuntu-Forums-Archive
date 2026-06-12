---
title: "mount points partition"
date: 2008-10-08
forum: General Help
---

### Post by wilcan34 on 2008-10-08
Hi All, Have looked everywhere but not been able to find similar but not same fix.

Have 2 Drives and they do not deem to be mounted priperly.

Disk /dev/sda: 6488 MB, 6488294400 bytes
255 heads, 63 sectors/track, 788 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x86070c77

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         752     6040408+  83  Linux
/dev/sda2             753         788      289170    5  Extended
/dev/sda5             753         788      289138+  82  Linux swap / Solaris

Disk /dev/sdb: 30.0 GB, 30003240960 bytes
255 heads, 63 sectors/track, 3647 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005fe8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1826    14667313+  83  Linux
/dev/sdb2            3416        3647     1863540    5  Extended
/dev/sdb3   *        1827        3415    12763642+  83  Linux
/dev/sdb4            3648        3648           0    e  W95 FAT16 (LBA)
/dev/sdb5            3492        3647     1253038+  82  Linux swap / Solaris
/dev/sdb6            3416        3491      610407   82  Linux swap / Solaris

Partition table entries are not in disk order

looks all over the place.
Any help to get them all in order,under  / would be a big help.
Reguards
Greg

---

### Post by drs305 on 2008-10-08
I am not sure what you are asking. What you displayed is merely the partition structure of your drives. Mounting the partitions is accomplished with fstab.

As far as the "Partition table entries are not in disk order" message, it is common and is not really an issue. You can leave it the way it is without any worries. However, you can fix it if you really want to. In a terminal:

[COLOR="Red"]If you accomplish the following it may change partition designations which will need to be updated in fstab prior to rebooting. Additionally, reformatting or creating/deleting  partitions with gparted can change the UUIDs. Review the results of "sudo blkid" and compare the listings to those in /etc/fstab. Make sure the fstab listings reflect the blkid results or you  may have problems on rebooting.[/COLOR]

```
sudo fdisk /dev/sda1
at the prompt:
m (for help)
at the prompt:
x (extra functionality - experts only)
fix
w (write to disk and exit)

```

You may get a warning that devices are in use and the new table will be used at the next boot.
Repeat for other drives.

---

### Post by vanadium on 2008-10-08
@drs305, nice little secret to know!

@wilcan, if you also post the output of "mount" we will see which of the drives are not mounted. If in addition, you post "cat /etc/fstab", we will know if the partitions are properly set-up to mount at boot time. If then we see some partitions do not mount while they should, we can try to identify the cause.

---

### Post by wilcan34 on 2008-10-08
Thanks for your quick response.
What the prob. is is I get Blender freezing up.
Have a 6G and 27G drives.
How to mount the 27G drive to start at boot up so I have more memory.


greg@greg-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-386/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
greg@greg-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=88820ac8-c8a9-4c55-9803-1c1cea1e3a8d / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=81038d54-5b6a-42c8-ad63-df0cad141d87 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
greg@greg-desktop:~$ 

greg@greg-desktop:~$ sudo lshw 
[sudo] password for greg: 
greg-desktop              
    description: Desktop Computer
    product: KM266-8235
    vendor: VIA Technologies, Inc.
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: KM266-8235
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (02/21/2003)
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Duron(tm) processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.7.1
          slot: Socket A
          size: 1300MHz
          capacity: 2100MHz
          width: 32 bits
          clock: 100MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow ts
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 768MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 256MiB
        *-bank:1
             description: DIMM
             physical id: 1
             slot: A1
             size: 512MiB
     *-pci
          description: Host bridge
          product: VT8375 [KM266/KL266] Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8633 [Apollo Pro266 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: VT8375 [ProSavage8 KM266/KL266]
                vendor: S3 Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
                configuration: driver=prosavage_smbus latency=32 maxlatency=255 mingnt=4 module=i2c_prosavage
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-disk:0
                description: ATA Disk
                product: FUJITSU MPE3064A
                vendor: Fujitsu
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: ED-0
                serial: 01025102
                size: 6187MiB (6488MB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=86070c77
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 88820ac8-c8a9-4c55-9803-1c1cea1e3a8d
                   size: 5898MiB
                   capacity: 5898MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: filesystem=ext3 modified=2008-10-08 23:25:59 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-10-08 20:02:22 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 282MiB
                   capacity: 282MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 282MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: IC35L030AVV207-0
                vendor: Hitachi
                physical id: 1
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: V22O
                serial: VNVB30G8UVV1MH
                size: 27GiB (30GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0005fe8e
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   version: 1.0
                   serial: 0627fe3a-a957-4e50-bebf-c7931566bfb1
                   size: 13GiB
                   capacity: 13GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2007-06-17 16:42:55 filesystem=ext3 modified=2008-10-08 23:25:58 mounted=2008-10-08 20:19:58 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sdb2
                   size: 1819MiB
                   capacity: 1819MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 1223MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sdb6
                      capacity: 596MiB
                      capabilities: nofs
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.1.0,3
                   logical name: /dev/sdb3
                   version: 1.0
                   serial: 35125f22-828e-4715-a775-6c34b52a4ee2
                   size: 12GiB
                   capacity: 12GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2007-06-27 10:19:31 filesystem=ext3 modified=2008-10-08 20:01:05 mounted=2008-10-08 19:49:41 state=clean
           *-cdrom:0
                description: SCSI CD-ROM
                product: CD-ROM DRIVE-40X
                vendor: ATAPI
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: N0AP
                serial: ATAPI   CD-ROM DRIVE-40XN0AP
                capabilities: removable audio
                configuration: ansiversion=5 status=open
           *-cdrom:1
                description: DVD-RAM writer
                product: IDE H16X
                vendor: DVDRW
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: B02T
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-communication
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Modem latency=0 module=snd_via82xx_modem
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 74
             serial: 00:0a:e6:99:0a:13
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=10.1.1.5 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
     *-scsi
          physical id: 1
          bus info: usb@3:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: USB Storage-CFC
             vendor: IC
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdc
             version: 301b
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             product: USB Storage-SMC
             vendor: IC
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdd
             version: 301b
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             product: USB Storage-MMC
             vendor: IC
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sde
             version: 301b
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             product: USB Storage-MSC
             vendor: IC
             physical id: 0.0.3
             bus info: scsi@2:0.0.3
             logical name: /dev/sdf
             version: 301b
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdf
greg@greg-desktop:~$ 

some picts.

---

### Post by drs305 on 2008-10-08
/dev/sdb1 1 1826 14667313+ 83 Linux
/dev/sdb2 3416 3647 1863540 5 Extended
/dev/sdb3 * 1827 3415 12763642+ 83 Linux
/dev/sdb4 3648 3648 0 e W95 FAT16 (LBA)
[B]/dev/sdb5 3492 3647 1253038+ 82 Linux swap / Solaris
/dev/sdb6 3416 3491 610407 82 Linux swap / Solaris[/B]
Note you have two swap partitions. This isn't necessary.

Make mount points in /media for sdb1 and sdb3 (Name them what you wish) Bold requires user input. In this example I will simply call the mount points sdb1 and sdb3. I you wanted sdb1, for example, to be called 'myfiles', you would change every instance of /media/sdb1 with /media/myfiles  :

Make the mountpoint:
```
sudo mkdir /media/sdb1 /media/sdb3
```

Change ownership of mountpoints to yourself and set permissions. Replace *username* with your logon name:
```
sudo chown -R ***username:*** /media/sdb1 /media/sdb3
chmod -R 750 /media/sdb1 /media/sdb3

```

Backup fstab and open for editing (example uses gedit but you can use any text editor):
```
sudo cp /etc/fstab /etc/fstab.10-08.bak
gksudo gedit /etc/fstab
```

Add these lines:
```

/dev/sdb1 /media/sdb1 ext3 defaults,users 0 2 
/dev/sdb3 /media/sdb3 ext3 defaults,users 0 2 

```

Mount the new partition:
```

sudo mount -a

```

---

