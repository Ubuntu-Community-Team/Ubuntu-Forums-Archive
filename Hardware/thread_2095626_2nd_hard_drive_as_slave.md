---
title: "2nd hard drive as slave"
date: 2012-12-17
forum: Hardware
---

### Post by amber95 on 2012-12-17
I have tryed to set a 2nd hard drive as a slave and it will not allow me, i tryed the Gparted, I tryed the chown, i think it is, I got a 250 gb hard drive i use as the main, I want my 2nd 80 gb hard drive as a slave/Swap, i  got the swap part working i think, I just want it to be able to use the 80gb as storage

sudo lshw 
```
amber                     
    description: Desktop Computer
    product: ET1331G (To Be Filled By O.E.M.)
    vendor: eMachines
    serial: PTNBA02001949084852700
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=desktop family=eMachines Desktop power-on_password=disabled sku=To Be Filled By O.E.M. uuid=00251160-C882-2009-1203-014937000000
  *-core
       description: Motherboard
       product: MCP61PM-GM
       vendor: eMachines
       physical id: 0
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: AMI
          physical id: 0
          version: P01-A1
          date: 09/15/2009
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) II X2 235e Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) II X2 235e Processor
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1500MHz
          capacity: 2700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate npt lbrv svm_lock nrip_save cpufreq
          configuration: cores=2 enabledcores=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: pipeline-burst internal varies unified
     *-memory:0
          description: System Memory
          physical id: 2b
          slot: System board or motherboard
          size: 6GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 400 MHz (2.5 ns)
             vendor: Manufacturer00
             physical id: 0
             serial: 00000000
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 400 MHz (2.5 ns)
             vendor: Manufacturer01
             physical id: 1
             serial: 00000000
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM DDR2 Synchronous 400 MHz (2.5 ns)
             vendor: Manufacturer02
             physical id: 2
             serial: 00000000
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM DDR2 Synchronous 400 MHz (2.5 ns)
             vendor: Manufacturer03
             physical id: 3
             serial: 00000000
             slot: DIMM3
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:4f00(size=256)
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:11 ioport:4900(size=64) ioport:4d00(size=64) ioport:4e00(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB controller
          product: MCP61 USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:dff7f000-dff7ffff
     *-usb:1
          description: USB controller
          product: MCP61 USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:dff7ec00-dff7ecff
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:22 memory:dff78000-dff7bfff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:25:11:60:c8:82
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.2 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
          resources: irq:43 memory:dff7d000-dff7dfff ioport:e480(size=8)
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:e400(size=8) ioport:e080(size=4) ioport:e000(size=8) ioport:dc00(size=4) ioport:d880(size=16) memory:dff7c000-dff7cfff
     *-ide:2
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8.1
          bus info: pci@0000:00:08.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:20 ioport:d800(size=8) ioport:d480(size=4) ioport:d400(size=8) ioport:d080(size=4) ioport:d000(size=16) memory:dff77000-dff77fff
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:42
     *-display UNCLAIMED
          description: VGA compatible controller
          product: C61 [GeForce 6150SE nForce 430]
          vendor: NVIDIA Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list
          configuration: latency=0
          resources: memory:de000000-deffffff memory:c0000000-cfffffff memory:dd000000-ddffffff memory:dff40000-dff5ffff
     *-pci:4
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:8
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: a
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD2500BEVT-2
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: WD-WXK0A99C1830
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00069fa2
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: 5c23e48c-f483-41a9-8e25-f193d893d1bb
                size: 243MiB
                capacity: 243MiB
                capabilities: primary bootable ext2 initialized
                configuration: filesystem=ext2 modified=2012-12-17 08:14:52 mount.fstype=ext2 mount.options=rw,relatime,errors=continue state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 232GiB
                capacity: 232GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 232GiB
     *-scsi:1
          physical id: e
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD800JD-75MS
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: 10.0
             serial: WD-WMAM9LZ10386
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00075a50
           *-volume
                description: Extended partition
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                size: 74GiB
                capacity: 74GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sdb5
                   capacity: 12GiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sdb6
                   logical name: /media/tony/Slave
                   capacity: 62GiB
                   configuration: mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,data=ordered state=mounted
```

sudo lshw -C disk
```
  *-disk                  
       description: ATA Disk
       product: WDC WD2500BEVT-2
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WXK0A99C1830
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=00069fa2
  *-disk
       description: ATA Disk
       product: WDC WD800JD-75MS
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: 10.0
       serial: WD-WMAM9LZ10386
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=00075a50
```

---

### Post by ibjsb4 on 2012-12-17
Sounds like you just want a data partition.  For linux you just create an ext4 data partition.  For something that works with windows, I would guess fat partition.   Not sure though, I don't run windows.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=data+partition&as_qdr=all&sa=Google+Search&lang=en]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=data+partition&as_qdr=all&sa=Google+Search&lang=en")

---

### Post by amber95 on 2012-12-17
I just  want more space, And for it to use for SWAP to, I don't use windows at all ether. So i open Gparted and set it for a ext4 on a primary drive i tryed the slave option to and still nothing when i open the file it doesn't allow me to add folders and files to it, Nor does it or the SWAP mount automaticly. 
[IMG]http://i1079.photobucket.com/albums/w513/Tonywlo0/Screenshotfrom2012-12-17130636_zps5c883b77.png[/IMG][IMG]http://i1079.photobucket.com/albums/w513/Tonywlo0/Screenshotfrom2012-12-17130422_zps77e6750f.png[/IMG]

---

### Post by ibjsb4 on 2012-12-17
You do not need to set any slave option when creating a data partition on second HDD.  The slave jumper on the HDD itself may be required by your computer, but no software option is needed.  Just use gparted to create an ext4 partition on your second HDD and you will be able to mount it in nautilus.

---

### Post by ahallubuntu on 2012-12-17
In the context of hard drives, "slave" usually refers to a master/slave configuration on an old PATA (IDE) interface, where two drives are connected to the same flat ribbon cable and jumpers can be used to choose which drive is master and which is slave.

But it appears both of your hard drives are SATA drives, and no such thing applies to SATA.

So can you explain what you mean by "slave?"  That is probably confusing people.

You can create partitions on various hard drives and use them how you wish in Ubuntu.  In your computer's BIOS, you do have to choose the correct drive as your boot drive.

---

### Post by amber95 on 2012-12-17
Why won't it let me auto mount the swap, And why won't it like me make files in the slave drive? I have one set as slave and one as master, So  i figure it had to do with ubuntu.

---

### Post by amber95 on 2012-12-17
> **ahallubuntu said:**
> In the context of hard drives, "slave" usually refers to a master/slave configuration on an old PATA (IDE) interface, where two drives are connected to the same flat ribbon cable and jumpers can be used to choose which drive is master and which is slave.

But it appears both of your hard drives are SATA drives, and no such thing applies to SATA.

So can you explain what you mean by "slave?"  That is probably confusing people.

You can create partitions on various hard drives and use them how you wish in Ubuntu.  In your computer's BIOS, you do have to choose the correct drive as your boot drive.

i want the main hard drive to just stay it self, I want the 2nd hard drive for more space and SWAP for ram. But ubuntu will not auto mount nor will it let me make folders and files in the 2 hard drive, So even if i wanted i could not back anything up, or put files on the 2nd hard drive

---

### Post by irv on 2012-12-17
Let me get this straight. When you say slave drive, do you mean you set it as slave in your BIOS? And when you say swap do you mean you set it as swap in the install of Ubuntu? If you did that, and you used the whole 80gig for a swap, you won't be able to use it for anything else.
When using Linux it works different then Windows. Windows will see it as two different drives. Linux sees all the storage that is available and offers it all to you. From the OP you should be seeing something like 306gig total, that if you did use the whole 80gig as a swap drive.
Are you running Windows and Linux or just Linux?
When using gparted you will see the drive as a 250 and 80gig drive.
Maybe I should be asking if you have them formated differntly? Like ext4 and NTFS. If this is the case then you will see them differently.

EDIT:  OK I see you have the swap set at 12gig and the rest 62gib in gparted. So your 80 gig is sdb1 and sdb2. The swap being sdb1.

---

### Post by amber95 on 2012-12-17
Just linux, When i say slave i mean i can put files and folders on the 2nd hard drive, I put partition so that it would have 12 gb for swap and the rest i put as ext2 and its the same as my 1 hd format.

---

### Post by irv on 2012-12-17
> **amber95 said:**
> Just linux, When i say slave i mean i can put files and folders on the 2nd hard drive, I put partition so that it would have 12 gb for swap and the rest i put as ext2 and its the same as my 1 hd format.

Why don't you format it the same as the 250gig drive? If you have it formated as ext4 then make the sdb2 62gig the same.

EDIT:  I see you have it at ext4 already.

---

### Post by amber95 on 2012-12-17
> **irv said:**
> Why don't you format it the same as the 250gig drive? If you have it formated as ext4 then make the sdb2 62gig the same.

EDIT:  I see you have it at ext4 already.

I tryed making it the same format it will not allow me to make  files and folders or put files and folders in the 2nd hard drive. 



[ATTACH]228825[/ATTACH]

[ATTACH]228826[/ATTACH]

[ATTACH]228827[/ATTACH]

[ATTACH]228828[/ATTACH]

---

### Post by ibjsb4 on 2012-12-17
On a side note when posting a pic use the paperclip option.

[ATTACH]228815[/ATTACH]

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=swap&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=swap&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by oldfred on 2012-12-17
You are into permissions and ownership issues. And with a fixed internal drive it is best to auto mount with fstab so you set your permissions & ownership. Defaults may not be the best.

Backup fstab, list UUIDs, copy template into fstab and edit with your UUID, unmount if mounted, and test with mount -a. Details:
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
    
       [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
    
Lots of details:
       Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Yellow Pasque on 2012-12-17
> **amber95 said:**
> Just linux, When i say slave i mean i can put files and folders on the 2nd hard drive.

'Slave' doesn't make sense in that context. Even on the old PATA ribbon cable, which actually used master/slave on the bus, you could make the slave your primary drive and boot it, and just use the master as supplemental storage.

You can continue to think of an extra drive as the slave, but you should beware that the rest of the world doesn't use the word that way, especially when talking about SATA disks since they have their own cables.

---

### Post by amber95 on 2012-12-17
> **Temüjin said:**
> 'Slave' doesn't make sense in that context. Even on the old PATA ribbon cable, which actually used master/slave on the bus, you could make the slave your primary drive and boot it, and just use the master as supplemental storage.

You can continue to think of an extra drive as the slave, but you should beware that the rest of the world doesn't use the word that way, especially when talking about SATA disks since they have their own cables.

Well ok... I want my 2nd hard drive for SWAP and all of my wine programs to be installed on it, But it will not let me create files and folders on it nor will it kick in the swap automaticly make sense now?

---

### Post by oldfred on 2012-12-17
.wine is one of the more difficult things to move. It literally is the only thing I have not moved, that is data related,  out of my /home. The only things in my/home is the hidden user settings.

I have data partitions on other drives and link all the data back. But you first have to mount the data partition and give it correct ownership & permissions. Also better to format as ext4 or possibly ext3. But ext2 does not have a journal and is more difficult to recover from abnormal shutdown either by the user or power failure. 

Post these:

       sudo blkid -c /dev/null -o list
             sudo cat /etc/fstab

---

### Post by amber95 on 2012-12-17
sudo blkid -c /dev/null -o list
```
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext2             /boot          5c23e48c-f483-41a9-8e25-f193d893d1bb
/dev/sda5  crypto_LUKS      (in use)       1ba5c246-337c-4579-827b-e3d0bdf81a96
/dev/sdb1  swap             (not mounted)  188dcb8a-9749-47ea-b983-5dbb43417873
/dev/sdb2  ext2             (not mounted)  dbc955dc-8d91-4705-b537-ac53e4b018ff
/dev/mapper/sdb5_crypt
           LVM2_member      (in use)       f0bqWQ-t7rt-njm5-kdQd-whHv-ntmt-mwkcMo
/dev/mapper/ubuntu-root
           ext4             /              0672b6ae-976e-4bc3-a8f9-826266287372
/dev/mapper/cryptswap1
           swap             <swap>         9ac88c96-8f9a-49ab-a51b-b14127cf31c6
```

             sudo cat /etc/fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=5c23e48c-f483-41a9-8e25-f193d893d1bb /boot           ext2    defaults        0       2
/dev/mapper/ubuntu-swap_1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

---

### Post by oldfred on 2012-12-18
You are using full encryption with a separate /boot and LVM. I do not know LVM nor encryption.

I do not know if you can mount an unencrypted partition into your encrypted system or not.
I though one of the advantages of LVM is that you just add another partition and it becomes part of the LVM. But any damage to either drive destroys both making it impossible to recover data so a really good backup system is required with LVM.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
lvm info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)

---

### Post by amber95 on 2012-12-19
I just reinstalled ubuntu and did the advance LVM when installing, Does this look correct?

[ATTACH]228886[/ATTACH]

[ATTACH]228887[/ATTACH]

[ATTACH]228888[/ATTACH]

[ATTACH]228889[/ATTACH]

---

### Post by oldfred on 2012-12-19
It looks like you made sda1 the /boot partition. Normally I do not suggest a separate /boot, but it only needs to be 300MB if you want to have it. Is it the entire drive?

I also like to have entire system on one hard drive so if drive fails, I can boot other drive. And I usually have a full install on every drive in a 25GB partition.

Herman has everything in one partition.
       Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by amber95 on 2012-12-20
Wait... What? sorry im a noob... And i made that whole drive a boot and make the other one extend and swap.

---

### Post by oldfred on 2012-12-20
With Desktops we normally keep the /boot folder in the / (root) partition. With servers many of the system folders may be on separate partitions to control sizes, uses, security of the server.

I prefer for both Windows & Linux smaller system partitions and separate data partitions. It makes it easier to update system or use data in more than one system.

       Install options, Do not use erase entire drive unless that is really what you want.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

