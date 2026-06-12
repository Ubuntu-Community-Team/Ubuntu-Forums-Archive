---
title: "Is driver NVIDIA-Linux-x86-180.22 work in Ubuntu 9.04 ?"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by hairulazami on 2009-05-24
I used Ubuntu 8.10 before. In Ubuntu 8.10, I use NVIDIA-Linux-x86-180.22-pkg1.run as nVidia Driver for GeForce 9500 GT and it work. Today, I install fresh Ubuntu 9.04. but I got error after restart X Server.

```

(EE) Failed to load "type1" (module doesn't exist)
(EE) Failed to load "freetype" (module doesn't exist)
NVIDIA: use the -ignoreABI option to override this check
(EE) Failed to load "nvidia" (module requirement)
(EE no drivers available)

```

Is driver NVIDIA-Linux-x86-180.22 work in Ubuntu 9.04 ?

---

### Post by 73ckn797 on 2009-05-24
I am using the Nvidia 180 driver "recommended" in System/Administration/Hardware Drivers with no problems. It appears you are installing the driver from their site.

I am running 9.04 64bit ext3 and 9.04 32bit with server kernel (for PAE capability) on ext4 and the "recommended" Nvidia driver works perfectly.

---

### Post by hairulazami on 2009-05-25
so you think I use not recomended download site ?

No, I download it from nVIDIA.

I will try to download newest driver:
[http://www.nvidia.com/object/linux_display_ia32_180.51.html](http://www.nvidia.com/object/linux_display_ia32_180.51.html)

I will back :)

---

### Post by 73ckn797 on 2009-05-25
Use what is provided for in Synaptic. Those usually will work just fine and will do all the work for you when installing.

---

### Post by Catalyst2Death on 2009-05-25
I don't know how recently nvidia has released those drivers, but when I upgraded Jaunty, the ones that I got from nvidia's site worked fine.  Unfortunately, the computer that has the nvidia drivers is ~1500 mi away at the moment, so I can't really check.  I've never had a problem in the past though.

---

### Post by hairulazami on 2009-05-25
@73ckn797

Synaptic provide me nVIDIA 180.44 .....
Then I try to install it, I remove 180.22 before, and it WORKS ! :popcorn:

Sory for my Bad, Thanks friends :)

---

### Post by Bearly Able on 2009-05-25
Sorry if I'm posting this in the wrong place.

I have a GeForce 7900 GS graphics card, which worked perfectly under Hardy.  Since I upgraded to Jaunty a couple of weeks ago, we have twice had error messages telling us to restart the system, followed by a message stating the X server could not be started.  I'm using the "recommended" NVIDIA 180 driver.

I know how to recover from the problem; I want to know why it's happening and how to prevent it.  Can anybody help?  Thank you.

---

### Post by 73ckn797 on 2009-05-25
> **Lesley Lutomski said:**
> Sorry if I'm posting this in the wrong place.

I have a GeForce 7900 GS graphics card, which worked perfectly under Hardy.  Since I upgraded to Jaunty a couple of weeks ago, we have twice had error messages telling us to restart the system, followed by a message stating the X server could not be started.  I'm using the "recommended" NVIDIA 180 driver.

I know how to recover from the problem; I want to know why it's happening and how to prevent it.  Can anybody help?  Thank you.

You appear to use the same video card I have. The 180 from Ubuntu works perfectly in 9.04 32 and 64 bit versions. The only problem I encountered was when trying to install the server kernel to enable PAE so the system could read all memory over 4gigs. I have 6gigs of memory. I would get the same error on every reboot, fix it following the prompts and run fine until a next reboot. I do not know what setup you have.

What are your computer specs?

---

### Post by Bearly Able on 2009-05-25
Hi, and thanks for your reply.

Now I'm embarrassed to admit I'm not sure about the specs.  The system was built to order a couple of years ago, and as far as I can recall, has an Intel Core Duo 3.4GHz processor.  It definitely has 2GB RAM.  What else do you need to know, and where can I find the information?

Thanks again for your help.

---

### Post by 73ckn797 on 2009-05-25
> **Lesley Lutomski said:**
> Hi, and thanks for your reply.

Now I'm embarrassed to admit I'm not sure about the specs.  The system was built to order a couple of years ago, and as far as I can recall, has an Intel Core Duo 3.4GHz processor.  It definitely has 2GB RAM.  What else do you need to know, and where can I find the information?

Thanks again for your help.

Open a terminal and type:
```
sudo lshw
```That will list all hardware info.

A short list would be shown by entering:
```
 sudo lshw -short
```

---

### Post by mount_evans on 2009-05-26
> **hairulazami said:**
> I used Ubuntu 8.10 before. In Ubuntu 8.10, I use NVIDIA-Linux-x86-180.22-pkg1.run as nVidia Driver for GeForce 9500 GT and it work. Today, I install fresh Ubuntu 9.04. but I got error after restart X Server.

```

(EE) Failed to load "type1" (module doesn't exist)
(EE) Failed to load "freetype" (module doesn't exist)
NVIDIA: use the -ignoreABI option to override this check
(EE) Failed to load "nvidia" (module requirement)
(EE no drivers available)

```

Is driver NVIDIA-Linux-x86-180.22 work in Ubuntu 9.04 ?

I am in the same boat.  When I go to "Hardware Drivers" and select the option:
```
NVIDIA accelerated graphics driver (version 180) [Recommended]
```
...and click "Activate", Ubuntu goes through the motions of downloading and installing the driver, but does not activate it.  I checked in Synaptic, and the driver appears to be there, along with all of the modaliases, but Ubuntu can't seem to use it.  I have run:
```
sudo nvidia-xconfig
```
many, many times, and get the result:
```
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```
and yet NVIDIA X Server Settings still tells me:
```
You do not appear to be using the NVIDIA X driver.
Please edit your X configuration file (just run `nvidia-xconfig` as root),
 and restart the X server.
```
Does "Restart the X server" mean something other than close and open NVIDIA Server Settings again?  I have no idea where the "X server" may be found, other than that.
For what its worth, I have a GeForce 8200 display.

---

### Post by Bearly Able on 2009-05-26
73ckn797: Thanks again.  My system specs:
```

mandela                   
    description: Desktop Computer
    product: PROD00000000
    vendor: OEM00000
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2
  *-core
       description: Motherboard
       product: P965T-A
       vendor: ELITEGROUP COMPUTER SYSTEM CO.,LTD.
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (09/15/2006)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) D CPU 3.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.6.4
          serial: 0000-0F64-0000-0000-0000-0000
          slot: Socket 775
          size: 2400MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous
             physical id: 0
             slot: A0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR Synchronous [empty]
             physical id: 1
             slot: A1
             width: 24832 bits
        *-bank:2
             description: DIMM DDR Synchronous
             physical id: 2
             slot: A2
             size: 1GiB
             width: 64 bits
        *-bank:3
             description: DIMM DDR Synchronous [empty]
             physical id: 3
             slot: A3
             width: 24832 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.6.4
          serial: 0000-0F64-0000-0000-0000-0000
          size: 2400MHz
          capacity: 2400MHz
          capabilities: ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82P965/G965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82P965/G965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: G71 [GeForce 7900 GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-storage
                description: SATA controller
                product: JMB361 AHCI/IDE
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress bus_master cap_list
                configuration: driver=ahci latency=0 module=ahci
           *-ide
                description: IDE interface
                product: JMB361 AHCI/IDE
                vendor: JMicron Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                logical name: scsi6
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list emulated
                configuration: driver=pata_jmicron latency=0
              *-cdrom
                   description: DVD-RAM writer
                   product: DVDRW LH-20A1H
                   vendor: LITE-ON
                   physical id: 0.0.0
                   bus info: scsi@6:0.0.0
                   logical name: /dev/cdrom
                   logical name: /dev/cdrw
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   version: LL06
                   capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: ansiversion=5 status=nodisc
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-network
                description: Ethernet interface
                product: RTL-8110SC/8169SC Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:04:05.0
                logical name: eth0
                version: 10
                serial: 00:19:21:3d:cd:dd
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.64 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=MII speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801HB/HR (ICH8/R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-ide:1
             description: IDE interface
             product: 82801H (ICH8 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             logical name: scsi4
             logical name: scsi5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
           *-disk:0
                description: ATA Disk
                product: WDC WD1600JS-00N
                vendor: Western Digital
                physical id: 0
                bus info: scsi@4:0.0.0
                logical name: /dev/sda
                version: 10.0
                serial: WD-WCANMD777519
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=fbc4fbc4
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@4:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 92730b41-38cb-dd4c-ae3f-06d071c6a031
                   size: 34GiB
                   capacity: 34GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2007-04-04 19:08:23 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@4:0.0.0,2
                   logical name: /dev/sda2
                   size: 114GiB
                   capacity: 114GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 29GiB
                 *-logicalvolume:1
                      description: HPFS/NTFS partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /media/disk
                      capacity: 31GiB
                      configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
                 *-logicalvolume:2
                      description: HPFS/NTFS partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 32GiB
                 *-logicalvolume:3
                      description: HPFS/NTFS partition
                      physical id: 8
                      logical name: /dev/sda8
                      capacity: 21GiB
           *-disk:1
                description: ATA Disk
                product: WDC WD1600AAJS-0
                vendor: Western Digital
                physical id: 1
                bus info: scsi@5:0.0.0
                logical name: /dev/sdb
                version: 01.0
                serial: WD-WMAV30402278
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000ec031
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@5:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   version: 1.0
                   serial: 5fd01ebc-10f0-404f-9c20-35fb88570be0
                   size: 143GiB
                   capacity: 143GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-02-03 19:58:49 filesystem=ext3 modified=2009-05-25 21:08:38 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-05-25 12:17:37 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@5:0.0.0,2
                   logical name: /dev/sdb2
                   size: 5930MiB
                   capacity: 5930MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 5930MiB
                      capabilities: nofs
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 52:66:c7:d6:a3:04
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

I don't know how much this helps.

mount_evans: I can activate the driver and it seems to be running fine, but having had the same type of crash twice in just over a week, then clearly it isn't.

On both occasions, when I've recovered from the problem and gone to Hardware Drivers, it shows version 180 as the recommended version, and has a message at the bottom that "A different version of this driver is in use".  Do I have an earlier version which is causing a conflict, and if so, how can I find it and remove it?

---

### Post by 73ckn797 on 2009-05-26
> **Lesley Lutomski said:**
> 
mount_evans: I can activate the driver and it seems to be running fine, but having had the same type of crash twice in just over a week, then clearly it isn't.

On both occasions, when I've recovered from the problem and gone to Hardware Drivers, it shows version 180 as the recommended version, and has a message at the bottom that "A different version of this driver is in use".  Do I have an earlier version which is causing a conflict, and if so, how can I find it and remove it?

You may need to uninstall all drivers and start from scratch with the recommended 180.

---

### Post by Bearly Able on 2009-05-26
That's what I was wondering, but I'm not sure how to go about it.  If I use the "remove" button on the Hardware Drivers window, won't that just remove the latest version?  I don't know how to go about finding and removing earlier versions.  Presumably I need to do it from the terminal, but as I don't know what I'm doing, I'm afraid of screwing things up completely.

---

### Post by 73ckn797 on 2009-05-26
Look in Synaptic for any video drivers that are installed. You may be able to remove those and start fresh. I have not had to do this so you may want to see what others have to say. I figure on reboot after removing the installed ones that you will have resolution issues until you install the recommended one.

---

### Post by Bearly Able on 2009-05-26
Thanks again.  I had tried looking in Synaptic, but the only entry I can find (assuming I'm looking for the right thing) is nvidia-180-kernel-source, and it's showing the latest version (180.44) as installed.  I can't find any other version listed as installed.  Am I looking at the wrong thing?

Since my last post, my entire system has frozen and I had to restart in recovery mode.  I used the autofix for graphics problems, which has got me back to the same display I get when running from the Live CD - fine, apart from being shifted almost 1cm to the right.  I'm loathe to try installing the nvidia driver again without sorting out any conflict problems, as I think this will just keep happening.

---

### Post by 73ckn797 on 2009-05-26
> **Lesley Lutomski said:**
> Thanks again.  I had tried looking in Synaptic, but the only entry I can find (assuming I'm looking for the right thing) is nvidia-180-kernel-source, and it's showing the latest version (180.44) as installed.  I can't find any other version listed as installed.  Am I looking at the wrong thing?

Since my last post, my entire system has frozen and I had to restart in recovery mode.  I used the autofix for graphics problems, which has got me back to the same display I get when running from the Live CD - fine, apart from being shifted almost 1cm to the right.  I'm loathe to try installing the nvidia driver again without sorting out any conflict problems, as I think this will just keep happening.

Won't know till you try.

---

### Post by Bearly Able on 2009-05-26
Sorry, I don't think I explained myself very well.  Installing the nvidia driver from Hardware Drivers is what I've done every time so far, and there's clearly a problem with that.  What I meant was that I don't want to just do the same thing again.  I'm quite happy to try uninstalling earlier versions and then doing a fresh install of the latest one, as you suggested, but I don't know how or where to find what versions are installed.  Synaptic shows only the latest one, but Hardware Drivers is again telling me "A different version of this driver is in use", so surely I must have more than one version somewhere?

[Edit] I've just checked the NVIDIA X Server Settings, which say ```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
```That seems to conflict with the message from the Hardware Drivers.  Now I'm really confused.

---

### Post by Bearly Able on 2009-05-27
OK.  I'd left things as they were and not reinstalled the nvidia driver, and I've just had the same crash and error messages as before.

I have no idea how to diagnose the problem, far less fix it, and I should be most grateful for any assistance from someone more knowledgeable.

Thanks in advance.

---

### Post by Bearly Able on 2009-05-30
Well, I've spent a couple of days with a system which was freezing at ever more frequent intervals.  It had reached the point where I was lucky if it would run for more than five minutes at a time.  I decided to completely remove the nvidia driver and see what happened.  Hardware Drivers is now reporting "This driver is not activated" and so far, the system seems stable.  (It's been about an hour since I removed the driver.)

One thing I did notice: when I removed the driver, Synaptic was showing one package to remain unchanged.  This is something called gstreamer0.10-plugins-bad.  When I upgraded to Jaunty, this package showed up with updates available, but then I had a message to say it was unable to install updates (or something like that).  Could this be causing problems now, and if so, should I try again to update it or can I safely remove it?  I'm not sure what it does.

---

### Post by 73ckn797 on 2009-05-30
Looking over your hardware info your video settings appear identical to mine. We are using the same video card.

I do not see anything else that is video related.

One question that comes to mind is whether this has on-board graphics in addition to an add-in video card. I would wonder if disabling the on-board video in bios for changing the way the system recognizes which video device to start up with. I do not have the info in front of me now but check that out.

I assume by the description of what is happening that after making any video changes you log-out or restart the system. 

Which 9.04 are you using: 32 or 64 with ext3 or ext4?

I was having similar video issues and discovered a failing hard drive. Since fixing that I am having no other problems.

Also enter this in terminal:

```
sudo lshw -class VIDEO
```
It will isolate any video info.

---

### Post by Bearly Able on 2009-05-30
Hi 73ckn797, and thanks for your help again.

I originally installed Hardy 32bit on a brand new hard drive about four months ago, so I don't think the problem is with the hard drive.  I upgraded from there, so this will be 32bit and as far as I know is still ext3; I've never knowingly done anything to change that.

The output from the terminal is```
:*-display               
       description: VGA compatible controller
       product: G71 [GeForce 7900 GS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia 
```

I'm afraid I don't really understand your remark about disabling the onboard video in BIOS, although I'm game to try most things if given clear instructions.  However, the machine is a dual-boot with XP, and while I mostly use Ubuntu, I occasionally need access to XP and don't want to do anything which will cause me problems there.

At the moment, things are still running fine, which is the best it's been for a few days, but of course I've lost the right-hand edge of the desktop again.

[Edit] Sorry, I nearly forgot to add that yes, I do log out or restart after making the changes.

---

### Post by 73ckn797 on 2009-05-30
The bios idea is due to the fact that some motherboards have a built-in video and also can have a separate card slot (AGP or PCIe). In the bios there is a switch to boot from either the on-board or the slot. I do not see anything to indicate another driver is installed. The system can also figure out whether there is a card or on-board video being used so that may not make any difference. I personnally switch it to the slot. My current mother board did not come with on-board video but all the other computers here (3) do have it and I have designated in bios to use the slot.

You said you upgraded from 8.04. Was that a fresh install or via update manager? It is possible that if you upgraded over the 8.04 via update and not with a LiveCD fresh install that somewhere the old info is still being seen.

I am no expert on all of this but questions and my experience can not be completely bad.

You may want to post a new thread in the "Multimedia & Video" forum where it could get more response than just from myself.

---

### Post by Bearly Able on 2009-05-30
Thanks for the explanation about the bios, 73ckn797.

I upgraded using update manager (via Intrepid).  I'm really reluctant to do a fresh install if it's not absolutely necessary.

I'll take your advice and try posting in "Multimedia and Video".  I started off here as the problem only arose after the upgrade.

Thanks again for your help.

---

### Post by 73ckn797 on 2009-05-30
> **Lesley Lutomski said:**
> Thanks for the explanation about the bios, 73ckn797.

I upgraded using update manager (via Intrepid).  I'm really reluctant to do a fresh install if it's not absolutely necessary.

I'll take your advice and try posting in "Multimedia and Video".  I started off here as the problem only arose after the upgrade.

Thanks again for your help.

Sounds good. I do hope something was useful.

---

