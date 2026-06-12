---
title: "RocketRaid 2310"
date: 2013-07-14
forum: Hardware
---

### Post by TLD98541 on 2013-07-14
I have a RocketRaid 2310 with 4 1T sataII HDs set up in raid 5 as a storage drive full of movies that i need to be able to access as this computer is my HTPC. 
I have Ubuntu 12.04LTS and Windows Vista on different partitions set up as duel boot on a different drive.

I have found a driver for the RocketRaid 2310 card here [http://man.sourcentral.org/ubuntu1204/4+hptrr](http://man.sourcentral.org/ubuntu1204/4+hptrr) but when i read the notes on the driver page it states "[COLOR=#000000][FONT=arial]The [/FONT][/COLOR][B]hptrr[COLOR=#000000] driver does [/COLOR][I]not work on i386 with [pae(4)]("http://man.sourcentral.org/ubuntu1204/4+pae") enabled."
[/I][/B]
In grub my version is identified as - Linux Ubuntu 3.2.0 - 49 [lowlatency] pae. Does that mean that this driver will not work on this OS or is pae different that pae(4)?

If this driver will work, how do i install it?

---

### Post by CinTUX on 2013-07-14
How much RAM does your PC have and are you running a 32-bit or 64-bit OS?

If you have more than 4GB RAM and are using a 64-bit OS, then it will work.

**[COLOR=#000000][COLOR=#000000][FONT=arial]The [/FONT][/COLOR][/COLOR]**[B]hptrr[COLOR=#000000] driver does [/COLOR][I]not work on i386 with [pae(4)]("http://man.sourcentral.org/ubuntu1204/4+pae") enabled.
[/I][/B]This means that the driver won't work if you have a 32-bit OS and have more
than 4GB RAM.

- Don't hit me if I'm wrong.. :)

---

### Post by TLD98541 on 2013-07-14
I have a 32 bit OS with 3GB ram.

---

### Post by CinTUX on 2013-07-14
The driver should work then. But why do you want to install this driver? Do you just want to access the Windows partitions from your Ubuntu
environment?

If so, take a look at this: [http://www.wikihow.com/Access-Windows-Files-in-Ubuntu](http://www.wikihow.com/Access-Windows-Files-in-Ubuntu)
I hope this leads you to the right way, it's time to sleep for me now. :)

---

### Post by TLD98541 on 2013-07-14
The 4 drives hooked to the [COLOR=#000000]RocketRaid 2310 card are configured to raid 5, doesn't Linux have to have a driver to mount the raid 5 as a single [/COLOR][COLOR=#000000]drive[/COLOR][COLOR=#000000]?

[/COLOR][COLOR=#000000]I have Ubuntu 12.04LTS and Windows Vista on different partitions set up as duel boot on a different drive.[/COLOR]

---

### Post by CharlesA on 2013-07-14
FWIW, the site hosting the driver linked above sounds fishy - it could be fine, but I would not use it.

You would need to build the driver for Linux (or Windows, for that matter) to see the array as the Linux kernel does not include modules to access HighPoint tech hardware by default.

The driver is found here:
[http://www.highpoint-tech.com/USA_new/rr2300_download.htm](http://www.highpoint-tech.com/USA_new/rr2300_download.htm)

Download the open source driver.

The drive needs to be recompiled whenever you update the kernel, so I would recommend setting up DKMS for that.

As far as building the driver goes, read the wiki page here:
[https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid)

EDIT: That driver won't build on 3.0 kernel's without some haxxing. I'll see if I can get it working as the instructions on the wiki are pretty confusing.

---

### Post by TLD98541 on 2013-07-14
Thank you very much charlesA.

I downloaded the driver from HighPoint.

I have installed DKMS and the driver is sitting on the desktop on the Linux computer.

The driver has a .tgz extension if that makes a difference.

---

### Post by CharlesA on 2013-07-14
Alright, download this: [http://charlesa.net/files/rr231x-2.5.tar.gz](http://charlesa.net/files/rr231x-2.5.tar.gz)

Extract it to your home folder and follow the instructions in the install file.

---

### Post by TLD98541 on 2013-07-14
Well it went ok until i did the build command then there was an error so i rebooted and tried again and still an error. it said there was a log so i copied the content of the log.

DKMS make.log for rr231x-2.5 for kernel 3.2.0-49-lowlatency-pae (i686)
Sun Jul 14 19:27:59 PDT 2013
make: *** product/rr3210pm/linux: No such file or directory.  Stop.

That i686 does that mean its a 64 bit OS, I wanted the 32bit OS.

I extracted the folder to the folder with my user name i hope that's what you meant by home folder.
it wouldn't let me paste it in the home folder, or should i have used the ```
 sudo -i 
``` first to get it into the home folder?

---

### Post by CharlesA on 2013-07-14
Bah, typo. Run this:

```
sed -i 's/3210/2310/' /usr/src/rr231x-2.5/dkms.conf
```

And try the build again.

i686 is 32-bit. x86_64 is 64-bit.

---

### Post by TLD98541 on 2013-07-15
Well that built the driver and install seemed to work but i can not see the HD on the desktop like i see the other HDs and partitions and i couldn't find it in any of the folders in /dev/disk or /dev/media after i rebooted. 

It's getting late here so a big thanks for the help CharlesA i'll be back on tomorrow to see if anybody can help me figure out whats going on. and i still have to get one of the Ethernet cards to work, so its boot back to windows till i get this figured out.

---

### Post by CharlesA on 2013-07-15
Run this:

```
sudo fdisk -l
```

```
gksu gparted
```

See if it shows up.

---

### Post by TLD98541 on 2013-07-15
```
 sudo fdisk -l 
``` showed the partitions on the 500 GB drive that has windows on the first 80 GB partition (NTFS)  then Ubuntu on the second 30 GB ext4 Partition then a 3 GB SWAP for Ubuntu then a 47 GB ext3 partition for /home and the rest of the disk partitioned in (NTFS).
The second HD has 1 1.8 TB partition formatted in (NTFS).
But the raid drive didn't show up its 1 partition of 1.8 TB formatted in (NTFS) with a spare drive attached as backup.

```
 gksu gparted 
``` didn't didn't show anything and jusy went back yo a prompt. i don't think it's installed. I'll install it tomorrow and see if it sees the raid drive.

Thanks again CharlesA

---

### Post by TLD98541 on 2013-07-15
Ok i installed gparted and ran ```
 gksu gparted 
``` and in the gui i can see the 4 1 TB drives that make the raid 5, it said unallocated with a red explanation point next to each drive as i looked at them.

---

### Post by CharlesA on 2013-07-15
That's odd. Does the card detect the RAID 5 before you boot into an OS?

As it stands, I would not recommend storing a RAID5 array between Windows and Linux on the same machine.

Your best bet would be to boot into Vista and backup the array so you don't lose any data if things go pear shaped with *nix.

---

### Post by TLD98541 on 2013-07-15
When the BIOs for the card load it shows the raid array, in windows the array works fine.
I have over 800 movies on the array and not enough space to back it up that's why i have a spare disk attached to the array so if there is a HD failure the spare will automatically be added to rebuild the array. 
I plan on sharing this array as read only for now with Ubuntu as it only need to play movies from it. This computer is a HTPC and internet gateway for the other computers in my house.

Don't give up, i am determined to switch from windows to Linux and if i lose my movies i will not blame you or anyone trying to help me, I have been warned,

I have tried to switch to Linux a couple time in the past 10 years and i in going to succeeded this time. Or blow everything up trying. HA HA.

I am running the duel boot with windows so i can take as long as it takes to get this done, all i have to do is boot back to windows and everything is back to normal. I do have Disk images of the windows install on 1 of the other machines so if that gets messed up i can easily put the image back on the partition and i'm back in business.

---

### Post by TLD98541 on 2013-07-15
The controler shows up on this list when i run ```
 [COLOR=#000000][FONT=Ubuntu Mono]sudo lshw 
```

```
 [/FONT][/COLOR]tld@US1:~$ sudo lshw[sudo] password for tld: 
us1                       
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=6018F6FA-5E1D-D711-9018-0013D477ED8C
  *-core
       description: Motherboard
       product: A8N-SLI Premium
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: 1.02
       serial: 123456789000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: ASUS A8N-SLI Premium ACPI BIOS Revision 1009
          date: 10/21/2005
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 3
          bus info: cpu@0
          version: 15.3.2
          slot: Socket 939
          size: 2200MHz
          capacity: 3700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni lahf_lm cmp_legacy
        *-cache:0
             description: L1 cache
             physical id: a
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: b
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-memory:0
          description: System Memory
          physical id: 43
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM 400 MHz (2.5 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM 400 MHz (2.5 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM 400 MHz (2.5 ns)
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM 400 MHz (2.5 ns)
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-cpu:1
          physical id: 4
          bus info: cpu@1
          version: 15.3.2
          size: 2200MHz
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 1MiB
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: CK804 ISA Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: CK804 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
          resources: irq:255 ioport:e400(size=32) ioport:4c00(size=64) ioport:4c40(size=64)
     *-usb:0
          description: USB controller
          product: CK804 USB Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:d8004000-d8004fff
     *-usb:1
          description: USB controller
          product: CK804 USB Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:d8005000-d80050ff
     *-multimedia
          description: Multimedia audio controller
          product: CK804 AC'97 Audio Controller
          vendor: NVIDIA Corporation
          physical id: f
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=snd_intel8x0 latency=0 maxlatency=5 mingnt=2
          resources: irq:22 ioport:dc00(size=256) ioport:e000(size=256) memory:d8003000-d8003fff
     *-ide:0
          description: IDE interface
          product: CK804 IDE
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: f2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:d800(size=16) memory:d8002000-d8002fff
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi5
          logical name: scsi7
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:20 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:c400(size=16) memory:d8001000-d8001fff
        *-disk:0
             description: ATA Disk
             product: ST3500320AS
             vendor: Seagate
             physical id: 0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdf
             version: SD15
             serial: 5QM1QXC4
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=e1143743
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@5:0.0.0,1
                logical name: /dev/sdf1
                version: 3.1
                serial: 2c1d4698-8490-c34b-b4af-88c67957ca83
                size: 79GiB
                capacity: 79GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2010-05-08 03:09:11 filesystem=ntfs label=WinVista state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@5:0.0.0,2
                logical name: /dev/sdf2
                version: 3.1
                serial: aa8f-f85b
                size: 305GiB
                capacity: 305GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2013-07-09 11:10:13 filesystem=ntfs label=NAS state=clean
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@5:0.0.0,3
                logical name: /dev/sdf3
                size: 79GiB
                capacity: 79GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sdf5
                   logical name: /
                   capacity: 33GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sdf6
                   capacity: 2929MiB
                   capabilities: nofs
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sdf7
                   logical name: /home
                   capacity: 43GiB
                   configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,user_xattr,acl,barrier=1,data=ordered state=mounted
        *-disk:1
             description: ATA Disk
             product: WDC WD2002FAEX-0
             vendor: Western Digital
             physical id: 1
             bus info: scsi@7:0.0.0
             logical name: /dev/sdg
             version: 05.0
             serial: WD-WMAY01654284
             size: 1863GiB (2TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=46697619
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@7:0.0.0,1
                logical name: /dev/sdg1
                version: 3.1
                serial: 22793d75-75e4-8442-ae9f-9e6fdd913635
                size: 1863GiB
                capacity: 1863GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2012-09-29 22:30:16 filesystem=ntfs label=2TCav state=clean
     *-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master
          resources: ioport:a000(size=4096) memory:d6000000-d7ffffff memory:d8100000-d81fffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
             vendor: Texas Instruments
             physical id: b
             bus info: pci@0000:05:0b.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
             resources: irq:16 memory:d7008000-d70087ff memory:d7004000-d7007fff
        *-network
             description: Ethernet interface
             product: 88E8001 Gigabit Ethernet Controller
             vendor: Marvell Technology Group Ltd.
             physical id: c
             bus info: pci@0000:05:0c.0
             logical name: eth0
             version: 13
             serial: 00:13:d4:77:fc:00
             size: 100Mbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.14 duplex=full firmware=N/A ip=98.237.219.196 latency=32 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:17 memory:d7000000-d7003fff ioport:a000(size=256) memory:d8100000-d811ffff
     *-bridge
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: NVIDIA Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth1
          version: a3
          serial: 00:13:d4:77:ed:8c
          size: 1000000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=1Gbit/s
          resources: irq:23 memory:d8000000-d8000fff ioport:b000(size=8)
     *-pci:1
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: NVIDIA Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:9000(size=4096) memory:d4000000-d5ffffff ioport:d8200000(size=1048576)
        *-scsi
             description: SCSI storage controller
             product: RocketRAID 2310 4 Port SATA-II Controller
             vendor: HighPoint Technologies, Inc.
             physical id: 0
             bus info: pci@0000:04:00.0
             logical name: scsi0
             logical name: scsi2
             logical name: scsi4
             logical name: scsi6
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: scsi pm msi pciexpress bus_master cap_list rom emulated
             configuration: driver=sata_mv latency=0
             resources: irq:17 memory:d5000000-d50fffff ioport:9000(size=256) memory:d8200000-d827ffff
           *-disk:0
                description: ATA Disk
                product: WDC WD1002FAEX-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WCATR7223053
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=47dce5c3
              *-volume
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 1862GiB
                   capabilities: primary
           *-disk:1
                description: ATA Disk
                product: WDC WD1002FAEX-0
                vendor: Western Digital
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                version: 05.0
                serial: WD-WCATR7237105
                size: 931GiB (1TB)
                configuration: ansiversion=5
           *-disk:2
                description: ATA Disk
                product: WDC WD1002FAEX-0
                vendor: Western Digital
                physical id: 2
                bus info: scsi@4:0.0.0
                logical name: /dev/sdd
                version: 05.0
                serial: WD-WCATR7259587
                size: 931GiB (1TB)
                configuration: ansiversion=5
           *-disk:3
                description: ATA Disk
                product: WDC WD1002FAEX-0
                vendor: Western Digital
                physical id: 3
                bus info: scsi@6:0.0.0
                logical name: /dev/sde
                version: 05.0
                serial: WD-WCATR7168257
                size: 931GiB (1TB)
                configuration: ansiversion=5
     *-pci:2
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: NVIDIA Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41
     *-pci:3
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: NVIDIA Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:42
     *-pci:4
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: NVIDIA Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:43 ioport:8000(size=4096) memory:d0000000-d3ffffff ioport:c0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: G84 [GeForce 8600 GT]
             vendor: NVIDIA Corporation
             physical id: 0
             bus info: pci@0000:01:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:18 memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:8000(size=128) memory:d3000000-d301ffff
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi
          physical id: 10
          bus info: usb@1:3
          logical name: scsi10
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@10:0.0.0
             logical name: /dev/sdc
             size: 3824MiB (4009MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=fdf8b019
           *-volume
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@10:0.0.0,1
                logical name: /dev/sdc1
                version: FAT32
                serial: 802e-e198
                size: 3820MiB
                capacity: 3820MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat
tld@US1:~$ 

```

---

### Post by CharlesA on 2013-07-15
It sounds like you might have to rebuild the array, but if it is showing up at 4 x 1TB drives, something isn't right unless you used Windows disk management to create the RAID5 array.

I only have experience with the rr2640x1 card, and am basing my advice off that one, but i never ran that one in Windows.

Can you take a picture of what the array looks like in before the OS boots?

---

### Post by TLD98541 on 2013-07-15
I built the array in the card BIOS when it was booting. 
I'm don't know how to get a screen shot during the boot, any suggestions?

---

### Post by TLD98541 on 2013-07-15
Here's i picture i took with a camera.

[IMG]http://img27.imageshack.us/img27/53/6wsm.jpg[/IMG]

---

### Post by CharlesA on 2013-07-15
Camera works, if you have one.

I wonder if there is a different driver for the RAID functionality of that card. Have you tried contacting HighPoint Tech's support?

EDIT: That looks right. It's pretty puzzled.

---

### Post by TLD98541 on 2013-07-15
No i haven't tried contacting HighPoint Tech's support, i really don't want to go that route if i don't have to as i am really a novice at Linux and they would lose me very quickly with jargon.

I still think it a driver issue as i read in one of the dozens of post about this issue that the HighPoint driver wasn't working anymore for 231x cards i just need to find that post again, I think that where i got the link to the driver that's in the first post.

But its getting late and i have work tomorrow so it will have to wait for another day, probably next weekend.

Thanks again.

---

### Post by CharlesA on 2013-07-16
Heh, last person I helped with that driver didn't get back to me. =/

Maybe this will help (but I doubt it):
[http://ubuntuforums.org/showthread.php?t=1625289](http://ubuntuforums.org/showthread.php?t=1625289)

This might help too:
[https://bbs.archlinux.org/viewtopic.php?id=113464](https://bbs.archlinux.org/viewtopic.php?id=113464)

Mostly the whole "The windows and linux driver seem to not want to play nice together" kinda deal. I wonder what would happen if you broke the array and recreated it, but then you'd lose your data, so make a backup of anything you value.

---

### Post by TLD98541 on 2013-08-02
OK i took the spare HD from the raid array and deleted some files here and there and got enough room to move all the movies.
So do you want me to delete the raid array in the BIOs and recreate it again in the BIOs or create it in Linux.

If you want me to make the array in Linux how do i go about doing that?

---

### Post by CharlesA on 2013-08-02
> **TLD98541 said:**
> OK i took the spare HD from the raid array and deleted some files here and there and got enough room to move all the movies.
So do you want me to delete the raid array in the BIOs and recreate it again in the BIOs or create it in Linux.

If you want me to make the array in Linux how do i go about doing that?

You should be able to download the management software from the HighPoint tech site if you need it.

As far as creating the array goes, I just created it with the raid card's bios program. If should be picked up by the OS as one large drive with fdisk as long as the driver is loaded.

---

### Post by TLD98541 on 2013-08-03
The driver you gave me a couple weeks ago is there, so will it work, I guess we'll find out. It will be next weekend before i will be able to try it. I'm to busy the rest of this weekend.

---

### Post by CharlesA on 2013-08-03
Good luck!

---

### Post by TLD98541 on 2013-08-09
Well i deleted the array and created another array with the same disks in the bios and it didn't work, i am still seeing each disk as i single disk and not i big one.

Does Linux software raid work well?
I need a raid 5 array (it needs to be able to be written to from windows as a SMB share) for data (movies) that can be expanded with more disks as needed, i need to be able to have a spare disk so if the array has a hardware failure it will automatically rebuild with the spare disk.

I tried installing the highpoint array management software but i think the installation is frozen as it started the Ubuntu software center and started to install and is still grinding away an hour later, I'll be closing that down and rebooting soon, hopefully that doesn't screw something up.

---

### Post by CharlesA on 2013-08-09
Linux software RAID should work fine for you. I'm a bit puzzled by why the drives aren't showing up as a single disk, but it might be a quirk with the driver.

As far as Software RAID goes, check this post out:
[http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm](http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm)

I used it to create the RAID5 I use on my backup server.

---

### Post by TLD98541 on 2013-08-10
Well i think i hosed my setup i tried to start Synaptic Package Manager and got an error. 
It said to run ```
 dpkg --configure -a 
``` to fix the problem, when i did i got this: ```
 tld@us1:~$ dpkg --configure -adpkg: error: requested operation requires superuser privilege
tld@us1:~$ sudo dpkg --configure -a
[sudo] password for tld: 
Setting up hptsvr (3.13-7) ...
Can't detect any supported driver automatically.
hptmv6 is used by default.

```
hptsvr is the highpoint array management software that got stuck when i tried to install it, I ended up rebooting but it looks like it is still trying to install.

EDIT: I am also getting this error

"'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running"

when trying to share a folder,

---

### Post by CharlesA on 2013-08-10
Strange, the management software thinks there isn't a driver for your card loaded (????).

I'm not really sure how you have your shares setup, but that sounds like a definite problem. Did you do the right-click > share method?

---

### Post by TLD98541 on 2013-08-10
I booted into recovery mode and ran the dpkg package repair which showed that the highpoint array management software is causing a error. It re-installed some stuff and i have my [COLOR=#000000]Synaptic Package Manager back, but it could not fix the [/COLOR]highpoint array management software and i still can't share any new folders however the folders that were already shares still work. I rebooted back to recovery mode and ran the cleanup which did remove a couple of packages that i had installed that were not being used but could not remove the highpoint array management software.

To setup sharing i edited the samba.conf file and changed the workgroup to the windows workgroup i use also i changed it so it only works with eth1 and changed the authorization from guest to share. i also downloaded the package nautilus-share. So i open nautilus and right click on the file i want to share then set the folder to be shared and nautilus automatically sets the permissions.

Do you think i should try re-installing the driver package you made for me?

---

### Post by TLD98541 on 2013-08-11
Well software raid isn't going to be an option while i do have 4 empty sata II connections they can only be used for raid arrays and if i use that chip i would not be able to move the array to another board when necessary plus it is limited to 4 disks so i would not be able to expand the array when needed. 
So i need to get this raid card working or go back to windows.

---

### Post by TLD98541 on 2013-08-11
Sense Ubuntu can't use my raid card i'm just going to install Ubuntu in VirtualBox and let windows take care of the drivers.

---

### Post by TLD98541 on 2013-08-12
Well in [COLOR=#000000]VirtualBox i can't use my remote control so i'll have the get a sata port multiplier i guess.[/COLOR]

---

### Post by METDeath on 2014-06-26
Found this thread, I'm in a similar boat of getting tired of dealing with Windows crap on my file server... except I have a 2310 and a 2300. Tried following your posted directions earlier... here's the result:

```
sudo dkms build -m rr231x -v 2.5

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....(bad exit status: 2)
make KERNELRELEASE=3.13.0-24-generic -C product/rr2310pm/linux KERNDIR=/lib/modules/3.13.0-24-generic/build....(bad exit status: 2)
ERROR (dkms apport): binary package for rr231x: 2.5 not found
Error! Bad return status for module build on kernel: 3.13.0-24-generic (x86_64)
Consult /var/lib/dkms/rr231x/2.5/build/make.log for more information.
```

If I add 3.13 to the list of okay kernels and the extra endif, I get this:
```
DKMS make.log for rr231x-2.5 for kernel 3.13.0-24-generic (x86_64)
Fri Jun 27 00:00:29 UTC 2014
make: Entering directory `/var/lib/dkms/rr231x/2.5/build/product/rr2310pm/linux'
[CC] /var/lib/dkms/rr231x/2.5/build/osm/linux/os_linux.c
In file included from /lib/modules/3.13.0-24-generic/build/include/linux/kernel.h:6:0,
                 from /lib/modules/3.13.0-24-generic/build/include/linux/cache.h:4,
                 from /lib/modules/3.13.0-24-generic/build/include/linux/time.h:4,
                 from /lib/modules/3.13.0-24-generic/build/include/linux/stat.h:18,
                 from /lib/modules/3.13.0-24-generic/build/include/linux/module.h:10,
                 from /var/lib/dkms/rr231x/2.5/build/osm/linux/osm_linux.h:17,
                 from /var/lib/dkms/rr231x/2.5/build/osm/linux/os_linux.c:6:
/lib/modules/3.13.0-24-generic/build/include/linux/linkage.h:7:25: fatal error: asm/linkage.h: No such file or directory
 #include <asm/linkage.h>
                         ^
compilation terminated.
make: *** [os_linux.o] Error 1
make: Leaving directory `/var/lib/dkms/rr231x/2.5/build/product/rr2310pm/linux'
```

Any advice?

---

### Post by CharlesA on 2014-06-26
Try running make manually and see where it fails. 

See here too, it might help:
[https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid)

I got sick of running into problems, so I moved away from RocketRaid and started using an LSI card. Having the kernel models requires in the mainline kernel is a hell of a nice thing.

---

### Post by METDeath on 2014-06-27
> **CharlesA said:**
> Try running make manually and see where it fails. 

See here too, it might help:
[https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid)

I got sick of running into problems, so I moved away from RocketRaid and started using an LSI card. Having the kernel models requires in the mainline kernel is a hell of a nice thing.

Well, changing cards is certainly something to consider for my next server build. However, I will probably switch to plain controller cards and let the OS handle the RAID. Maybe ZFS, or something.

However, after reading that using the cards in Windows then trying to convert directly to Linux may kill my data (15 TB on the two arrays). I'm waiting to see if Highpoint comes back with a worth wile solution.

---

### Post by lukeiamyourfather on 2014-07-01
> **CharlesA said:**
> I got sick of running into problems, so I moved away from RocketRaid and started using an LSI card. Having the kernel models requires in the mainline kernel is a hell of a nice thing.

Yes, HighPoint's support for Linux is awful which is too bad because they have some intriguing products like the Rocket 750, oh well.

> **METDeath said:**
> Maybe ZFS, or something.

This is what I have done for machines that will mostly be serving files. Not sure if I'd do it on a workstation though since ZFS is a memory hog.

> **METDeath said:**
> However, after reading that using the cards in Windows then trying to convert directly to Linux may kill my data (15 TB on the two arrays). I'm waiting to see if Highpoint comes back with a worth wile solution.

I have a RocketRAID 2320 with a RAID 5 array formatted as NTFS that is accessible from both Windows and Ubuntu, but it's an older version of Ubuntu that the HighPoint open source driver still supports. So it's possible to do assuming the driver supports the version of Ubuntu you want to use.

---

### Post by CharlesA on 2014-07-01
> **lukeiamyourfather said:**
> Yes, HighPoint's support for Linux is awful which is too bad because they have some intriguing products like the Rocket 750, oh well.

It was mostly me having to fudge with the make file or source to get the modules to actually compile. I was using DKMS for a time, but it would blow up any time there was a new kernel pushed out and even though DKMS ran and compiled the modules for the new kernel, they wouldn't load without redoing them. Quite annoying when the machine would hang at boot due to being unable to mount the array because the device was not there.

---

