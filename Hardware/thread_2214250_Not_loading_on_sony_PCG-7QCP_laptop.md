---
title: "Not loading on sony PCG-7QCP laptop"
date: 2014-03-31
forum: Hardware
---

### Post by micwit2 on 2014-03-31
I have an old Sony Vaio laptop, and I am trying to put Ubuntu on it. The CD boots to begin with (12.04 and 13.10 do the same thing), but before it even get to the stage where you choose live or install, it hangs (the 4 dots stop changing colors). It is 32-bit (only a 32-bit CPU), and because the loading screen is there, I cant even see the output to see what is causing it to die. Any ideas?

---

### Post by mörgæs on 2014-03-31
How does it work with Lubuntu 13.10?

---

### Post by micwit2 on 2014-03-31
OK, have tired lubuntu 12.04 and 14.04 beta 2.
12.04 can boot to live cd!!! But there is a bug in the install disk! If you go into verify (on any computer, and tried multiple burns), it fails verification! It also hangs while trying to install.
14.04 beta 2 hangs on boot, just like ubuntu does.

I have managed to get to the loading screen instead of the splash, and it seems to stop around the bluetooth daemon starting. Although in Ubuntu 13.10, it seems to hang randomly as its initializing things. I cant get anywhere near trying the live version. If I press esc as soon as the cd spins up, I can get to the language selection and select to install or try, but its just after there it hangs either way.

---

### Post by mörgæs on 2014-04-01
Random hangs could be caused by bad memory. 
Have you tried running memtest from the boot menu? Best to give it at least an hour.

---

### Post by micwit2 on 2014-04-01
Tried that, no errors or crashes. It was also up and running in windows 7 no problems.

---

### Post by micwit2 on 2014-04-01
WOOHOO!! Got Ubuntu 14.04 installed. Once I got into the advance menu, selected acpi=off, and it stopped whatever was causing the issue!

The issue I have now is that once booted, the CPU sits pretty much at 100% and it runs so slow! Its a celeron 1.6GHz (so way above the requirements of the 700mhz). Im wondering if its something to do with the video card (Intel Graphics Media Accelerator 900)? There are no additional drivers that show.

---

### Post by mörgæs on 2014-04-02
Good, have you tried Lubuntu 14.04 with the same boot option?

---

### Post by micwit2 on 2014-04-02
Yep, this option seems to work in any version. Now just trying to sort out the GMA 900 video card. Do you know what the system requirements are for Ubuntu? Im suspecting the 700mhz and 512mb ram is for lubuntu? I want to know what you need for the full ubuntu with unity.

This machine has 1GB ram (2 miss matched 512mb, but all I could find), 80GB hdd (I know thats fine), celeron 1.6GHz and an intel GMA 900 video card. Is this enough to run ubuntu 14.04?

---

### Post by micwit2 on 2014-04-02
OK, 12.04.4 installs, but fails as it boots. Normal mode, I see something about disabling IRQ 9, recovery mode I think gets to the same place (I can just see more) and stops after [7.067636] input: Sony Vaio Jogdial as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:13/SNY5001:00/input/input6

Edit: Fixed now, had to edit grub.

OK, ubuntu runs sooo fast in 12.04.4! Which makes me think that 13.10 and 14.04 have some kind of stability issue with some piece of hardware in my system! I expected to have to run Ubuntu in 2D, but its going fine in 3D. I would love to be able to get 14.04 running on it when it comes out, but this problem could be a very hard one to solve!

---

### Post by mörgæs on 2014-04-02
I don't use Ubuntu so I don't know in detail the difference between 12.04.4 and 14.04. 

If you want people to help it's best to begin with a hardware description. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by micwit2 on 2014-04-02
The result is:
```

computer
    description: Notebook
    product: VGN-FJ76GP_W
    vendor: Sony Corporation
    version: C1013BE6
    serial: [REMOVED]
    width: 32 bits
    configuration: boot=normal chassis=notebook uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Q-Project
       vendor: Sony Corporation
       physical id: 0
       version: 01
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: R0130X6
          date: 03/29/2006
          size: 114KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect socketedrom edd int9keyboard int10video acpi usb agp ieee1394boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor         1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: N/A
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx bts
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: burst external write-back data
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: SODIMM DDR
             physical id: 0
             slot: SODIMM1
             size: 512MiB
             width: 32 bits
        *-bank:1
             description: SODIMM DDR
             physical id: 1
             slot: SODIMM2
             size: 512MiB
             width: 32 bits
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller cap_list
             configuration: latency=0
             resources: memory:b0080000-b00fffff ioport:1800(size=8) memory:c0000000-cfffffff memory:b0040000-b007ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:44000000-4407ffff
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:16 memory:b0000000-b0003fff
        *-usb:0
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:5 ioport:1820(size=32)
        *-usb:1
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:10 ioport:1840(size=32)
        *-usb:2
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:5 memory:b0004000-b00043ff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:2000(size=4096) memory:b0100000-b01fffff ioport:40000000(size=67108864)
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 8
                bus info: pci@0000:06:08.0
                logical name: eth0
                version: 10
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=[REMOVED] latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
                resources: irq:10 ioport:2000(size=256) memory:b0114000-b01140ff
           *-pcmcia
                description: CardBus bridge
                product: PCI7420 CardBus Controller
                vendor: Texas Instruments
                physical id: 9
                bus info: pci@0000:06:09.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:10 memory:b0115000-b0115fff ioport:2400(size=256) ioport:2800(size=256) memory:40000000-43ffffff memory:48000000-4bffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
                vendor: Texas Instruments
                physical id: 9.2
                bus info: pci@0000:06:09.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=3
                resources: irq:7 memory:b0114800-b0114fff memory:b0110000-b0113fff
           *-storage
                description: Mass storage controller
                product: PCI7420/7620 SD/MS-Pro Controller
                vendor: Texas Instruments
                physical id: 9.3
                bus info: pci@0000:06:09.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7
                resources: irq:10 memory:b0116000-b0116fff
           *-network:1
                description: Wireless interface
                product: AR5212/AR5213 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: a
                bus info: pci@0000:06:0a.0
                logical name: wlan0
                version: 01
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k driverversion=3.11.0-15-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
                resources: irq:10 memory:b0100000-b010ffff
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801FBM (ICH6M) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1870(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18a0(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: HTS541080G9SA00
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: MB4O
             serial: [REMOVED]
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=0003b55d
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 73GiB
                capacity: 73GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-04-02 17:50:48 filesystem=ext4 lastmountpoint=/ modified=2014-04-02 18:16:25 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-04-02 21:32:58 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 1013MiB
                capacity: 1013MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1013MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVD RW DW-Q520A
             vendor: SONY
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: HFS2
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc

```
Anything stand out?

---

### Post by mörgæs on 2014-04-02
It all looks OK to me, but you will get a better performance with more memory.

If 12.04.4 is much faster than 14.04 (beta) then we have a conclusion. You could try 14.04 again in a separate partition a month or two after release and see if it's catching up.

---

### Post by micwit2 on 2014-04-02
Yeh, the memory isn't filling up anyhow (not that I have done much), its more the CPU usage. Not spending any money on this craptop anyhow.

I will keep it on 12.04.4 for now, and maybe give 14.04.1 a go once released (should have a lot of bug fixes). But then again, may be good to keep with 12.04.4 as it has the option of 2D login. Why they get rid of the 2d login? With 12.04.4, the cool thing is that the interface is pretty much the same as 14.04 anyhow, so will work in well with the rest of the machines once they are on 14.04.

I notice that even in previous versions, they only go back to the last supported LTS version. Is there anywhere that u can get older versions? Even once 12.04 is out of date, it could be handy to have for the 2D login.

---

### Post by mörgæs on 2014-04-02
Don't install old (if that means unsupported) versions. 12.04 is supported through 2017, so I guess you are safe.

If this solves the problem please mark the thread so.

---

### Post by micwit2 on 2014-04-02
By then I hope she has paid for a new laptop!! haha

OK, new problem, 12.04.4 doesn't want to power off the system. Just shows the ubuntu splash and the dots stop moving. Checked the syslog and doesn't seem to be anything unusual there. Sometimes this causes it to do a disk scan as it boots, so I would like a safe way to shut down.

---

### Post by micwit2 on 2014-04-02
Seems with ACPI=off, the wireless card says it runs, but it wont find networks unless the cable is plugged in! When the cable is plugged in, it finds them and connects etc! So maybe I have to find out why ACPI=off works and try to get around that issue??

---

### Post by mörgæs on 2014-04-03
For the shutdown prolem I don't think I can recommend more than I have already posted: Try more than one version of Buntu. Did X/Lubuntu 13.10 behave in the same way?

---

### Post by micwit2 on 2014-04-03
OK, for now the shutdown thing is minor, and I won't bother about it until I can sort the ACPI issue. From what I read, its a far greater issue than the wireless not working, as it can mean fans etc don't work when they are supposed to (which would explain the massive heat from the laptop before).

So, what I have found:

ACPI at default state (on)
Ubuntu 14.04 b2, 13.10, 12.04.4 and Lubuntu 14.04 b2, 13.10 All fail on boot, so cant install.
Lubuntu 12.04 Loads into live CD, and the wifi works. However, it fails reading a file when trying to install (did a disk check and it failed as well). Tried burning another copy and it did it as well.

ACPI set as off
All of the above will boot into the live CD, but the wireless will not work on any of them (Including Lubuntu where it works with ACPI on!!) So the wireless issue MUST be to do with the ACPI state.
When installed (tested Ubuntu 12.04.4, 13.10, 14.04 b2) the new install wont boot until grub sets the flag as ACPI off. None then work with wireless. Havn't tested the other Lubuntus for install, but 12.04 was the only one that worked live, and it wont install.

Once grub has ACPI=off, they all boot, but the wireless won't work unless the cable is plugged in.

So I guess one big question is whats different about ACPI in Lubuntu 12.04 compared to the rest??? I would have thought Lubuntu would have used the Ubuntu version for ACPI (isnt that part of the kernel)? If its different, whats the difference and does that mean there is a bug in all the others???

Oh, I have also updated the bios to the latest version. It sucks! Barely any options, so cant play with disabling things there :( Doesnt even boot off usb!

---

### Post by micwit2 on 2014-04-03
OK, this got me thinking.. Whats the difference between Lubuntu 12.04 and Ubuntu 12.04.4? Its the .4 at the end!!! I guess Lubuntu didn't upgrade when Ubuntu did, but waited until a future release (so by 13.10 they had upgraded the kernel). So I managed to find an old release, Ubuntu 12.04.3, and guess what, it worked!!! This tells me that there has been something changed in ACPI between the 12.04.3 and the 12.04.4 kernel, and whatever it is, it hasn't changed since! (Im guessing it only effects some computers, probably older ones). The issue now is that 12.04.3 is not supported, so how to find out what changed and just change that one thing back???

Im installing 12.04.3 now to test if the wireless works.

UPDATE: Installed, and it boots and wifi works (It even shuts down, Im suspecting the shutdown thing is something to do with acpi). The only thing I can see now that doesn't work is that there are no video drivers installed and none available in additional drivers.

---

### Post by mörgæs on 2014-04-03
Looks like a regression in the newer kernels. 
It would be great if you could report the bug, but maybe it's best first to discuss it with the people in the [development forum]("http://ubuntuforums.org/forumdisplay.php?f=427").

---

