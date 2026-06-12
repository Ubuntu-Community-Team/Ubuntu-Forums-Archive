---
title: "DVD Recorder Too Slow"
date: 2008-08-19
forum: General Help
---

### Post by NeoAndersen on 2008-08-19
I've tried to record with cd/dvd Creator and using Brasero too, but in both cases it spent about 1 hour to finish. I have two drives installed, one ide and the other sata...

In nero and xp I use to record a dvd in just 10 minutes...

How can I solve this?

---

### Post by gobbles414 on 2008-08-21
> **NeoAndersen said:**
> I've tried to record with cd/dvd Creator and using Brasero too, but in both cases it spent about 1 hour to finish. I have two drives installed, one ide and the other sata...

In nero and xp I use to record a dvd in just 10 minutes...

How can I solve this? More information would be helpful. Which version of Ubuntu are you using? What are your EXACT system specs? Please include as much info on brands and model numbers as possible.

---

### Post by NeoAndersen on 2008-08-24
Are there any commands to get a list with my system specification?

---

### Post by NeoAndersen on 2008-08-24
I am using Ubuntu 8.04.1 amd64

---

### Post by cariboo on 2008-08-24
You can use:

```
sudo lshw > hardware.txt
```

This will create a text file with your hardware specifications.

Jim

---

### Post by NeoAndersen on 2008-08-24
That's what I've got:

neoandersen@neoandersen-desktop:~$ sudo lshw > hardware.txt
[sudo] password for neoandersen: 
neoandersen@neoandersen-desktop:~$ lshw
WARNING: you should run this program as super-user.
neoandersen-desktop       
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2047MiB
     *-cpu
          product: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2394MHz
          capacity: 2394MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display UNCLAIMED
                description: VGA compatible controller
                product: G71 [GeForce 7950 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list
                configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-storage
                description: SATA controller
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: storage ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0 module=ahci
           *-ide
                description: IDE interface
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                logical name: scsi2
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: ide bus_master cap_list emulated
                configuration: driver=pata_jmicron latency=0 module=pata_jmicron
              *-cdrom
                   description: DVD-RAM writer
                   product: DVD-RAM GSA-H55N
                   vendor: HL-DT-ST
                   physical id: 0.0.0
                   bus info: scsi@2:0.0.0
                   logical name: /dev/cdrom
                   logical name: /dev/dvd
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   version: 1.00
                   serial: [HL-DT-STDVD-RAM GSA-H55N1.0007/03/21 7U02
                   capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: ansiversion=5 status=open
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8056 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: 12
                serial: 00:1b:fc:ed:bf:91
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=10.1.1.4 latency=0 module=sky2 multicast=yes
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW323
                vendor: Agere Systems
                physical id: 3
                bus info: pci@0000:05:03.0
                version: 70
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=24 mingnt=12 module=ohci1394
           *-network
                description: Ethernet interface
                product: RTL-8110SC/8169SC Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 4
                bus info: pci@0000:05:04.0
                logical name: eth0
                version: 10
                serial: 00:1b:fc:ed:be:21
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes
        *-isa
             description: ISA bridge
             product: 82801IR (ICH9R) LPC Interface Controller
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
             product: 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
        *-ide:1
             description: IDE interface
             product: 82801I (ICH9 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:22:ca:35
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
neoandersen@neoandersen-desktop:~$ sudo lshw > hardware.txt
neoandersen@neoandersen-desktop:~$ hardware.txt
bash: hardware.txt: command not found
neoandersen@neoandersen-desktop:~$

---

### Post by NeoAndersen on 2008-08-24
Seems to me that just the IDE DVD recorder appeared in the list... The SATA don't...

---

### Post by gobbles414 on 2008-08-25
I assume that you've tried selecting several different burning speeds when burning in Ubuntu? Sometimes the "Fastest" setting doesn't work correctly with some DVD burners. Try selecting the SECOND FASTEST burning speed in a Ubuntu burning program -- for example 8x instead of 16x.

> **NeoAndersen said:**
> Seems to me that just the IDE DVD recorder appeared in the list... The SATA don't... I could be wrong, but I think that Ubuntu reports IDE technology as ATA, and SATA technology as SCSI. This would mean that your "DVD-RAM GSA-H55N" burner is actually SATA, and that your IDE-based DVD burner is missing from the list. It might be worth your time to go inside your computer tower, and unplug the SATA-based DVD burner from your computer's motherboard. Then test the burning speed of the IDE-based burner in Ubuntu, and see if the IDE-based DVD recorder now appears in Ubuntu's report of your computer specs. Similarly, you may wish to disconnect the IDE-based burner in order to test your SATA-based burner in Ubuntu.

PS: Could you please provide the brand names of your DVD recorders, as well as the brand & model number of your computer? For DVD burner brands, look on the front of each DVD recorder's disc tray. Examples of computer brands & model numbers include HP Pavilion a6500z, Dell INSPIRON 530, and Apple Mac Pro. This will help us to better research your problem.

---

### Post by NeoAndersen on 2008-08-25
Hello!!

The speed I can choose in the SATA recorder are 1x, 3x and Max Speed; and in the IDE, 1x, 3x, 5x, 7x and Max Speed. All that in the Brasero while in the CD/DVD Creator the maximum I can choose are 6,2x...

The brand of both is LG... 

I have mounted my pc following instructions of a magazine...
The motherboard is a P5k Deluxe. The processor is a Core 2 Duo 6600.
The graphics processor is GeForce7950 GT.
RAM 2GB dimm Kingston...

---

### Post by NeoAndersen on 2008-08-26
Using the CD/DVD Creator I could record a dvd in the IDE recorder in just 13 min in the Max Possible speed... In the Sata it took me 34 min in the maximum speed...
I am sure the one appearing in the list are the IDE recorder... Then the problem are just with the SATA that, seems to me, are not appearing in the list.
To choose between the drivers the IDE appears as DVD-RAM GSA-H55N and the SATA appears as DVDRAM GH20NS10...

---

### Post by gobbles414 on 2008-08-27
> I have mounted my pc following instructions of a magazine... I don't understand! You shouldn't need to follow any instructions to "mount" Ubuntu. It should start automatically when your turn on your computer. How did you install Ubuntu? Is it installed on a USB flash drive, internal hard drive, something else?

---

### Post by NeoAndersen on 2008-08-27
I mean I bought the motherboard and all the parts separately and then at home I connected  all the hardware I bought... I installed ubuntu from a cd...

---

### Post by gobbles414 on 2008-08-28
> **NeoAndersen said:**
> I mean I bought the motherboard and all the parts separately and then at home I connected  all the hardware I bought... I installed ubuntu from a cd... I see. In that case, I recommend that you do the following.

1. Use Google to search the internet for known compatibility issues between your hardware and Ubuntu. For example, since you own a GeForce 7950 graphics card, you'd enter *geforce 7950 AND ubuntu* into Google. Do this search for your DVD burners (using model numbers), and all other major components of your computer.

2. Go into your computer's BIOS, and reload your computer's default settings. Some computers have both "optimized settings" and "failsafe settings". Try both, and also try manually tweaking so of the settings.

3. Backup your data, erase your hard drive, and install Ubuntu 8.0.4.1 32-bit instead of the 64-bit version.

---

