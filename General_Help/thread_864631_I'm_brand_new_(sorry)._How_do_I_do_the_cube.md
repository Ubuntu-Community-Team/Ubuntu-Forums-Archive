---
title: "I'm brand new (sorry). How do I do the cube?"
date: 2008-07-19
forum: General Help
---

### Post by nickolas on 2008-07-19
Hello. I've never used Linux before, but I'm trying to learn it. I just installed it on my machine and I want to use the infamous Desktop Cube. However, I don't know how :(. I looked online but the tutorials would always end up assuming I knew how to do something basic, but I really know nothing. Is anyone willing to tell me what to do, step by step?


I have an AMD 64 Athlon with an ATI Radeon Express 200 on my eMachine T6212; I heard that might be a problem. And I'm apparently using Ubuntu 8.04, and GNOME (whatever that is) 2.22.2.


Also, any other suggestions on how to have a great Ubuntu experience would be appreciated. I also have a Macbook so any synchronicity advice would be interesting. I'm also using Vista on this eMachine. 

Thanks,
Nick

---

### Post by YaroMan86 on 2008-07-19
> **nickolas said:**
> Hello. I've never used Linux before, but I'm trying to learn it. I just installed it on my machine and I want to use the infamous Desktop Cube. However, I don't know how :(. I looked online but the tutorials would always end up assuming I knew how to do something basic, but I really know nothing. Is anyone willing to tell me what to do, step by step?


I have an AMD 64 Athlon with an ATI Radeon Express 200 on my eMachine T6212; I heard that might be a problem. And I'm apparently using Ubuntu 8.04, and GNOME (whatever that is) 2.22.2.


Also, any other suggestions on how to have a great Ubuntu experience would be appreciated. I also have a Macbook so any synchronicity advice would be interesting. I'm also using Vista on this eMachine. 

Thanks,
Nick

I'm going to take a wild guess, since I don't use ATI.

1. Click **System -> Administration -> Hardware Drivers**
2. Enable the proprietary ATI drivers.
3. Restart Ubuntu if needed.
4. Open Synaptic Package Manager
5. Search for compizconfig-settings-manager
6. Select it and click Install
7. Acknowledge that you also want all the dependencies installed.
8. Click Apply
9. Confirm that you want it all installed.
10. exit Synaptic.
11. **System -> Preferences -> Advanced Desktop Effects Settings**
12. Check all the boxes that have to do with the Desktop Cube. If it tells you its conflicting with another plugin (Like Desktop Wall) confirm that YES you do want to disable the old plugin so Desktop Cube can run.
13. Press CTRL + ALT + Left Click and, while holding that left mouse button... drag the cursor around. You're now rotating your cube.

You might want at least 512 MiB of RAM before you attempt visual effects, since they can be pretty RAM-heavy.

---

### Post by Portable_Jim on 2008-07-20
> **YaroMan86 said:**
> I'm going to take a wild guess, since I don't use ATI.

1. Click **System -> Administration -> Hardware Drivers**
2. Enable the proprietary ATI drivers.
3. Restart Ubuntu if needed.
4. Open Synaptic Package Manager
5. Search for compizconfig-settings-manager
6. Select it and click Install
7. Acknowledge that you also want all the dependencies installed.
8. Click Apply
9. Confirm that you want it all installed.
10. exit Synaptic.
11. **System -> Preferences -> Advanced Desktop Effects Settings**
12. Check all the boxes that have to do with the Desktop Cube. If it tells you its conflicting with another plugin (Like Desktop Wall) confirm that YES you do want to disable the old plugin so Desktop Cube can run.
13. Press CTRL + ALT + Left Click and, while holding that left mouse button... drag the cursor around. You're now rotating your cube.

You might want at least 512 MiB of RAM before you attempt visual effects, since they can be pretty RAM-heavy.
Good advice (even though I don't use an ATI card either).

If it still does not work you might have to go to System => Preferences => Appearance => Visual Effects and choose either "Normal" or "Extra".

---

### Post by nickolas on 2008-07-20
YaroMan86 - Thank you. I did everything up to check "Desktop Cube". However, CTRL + ALT + Left Click did nothing. I also checked Wobbly Windows, but my windows are not wobbly.

Portable_Jim - Good call, when I went to Visual Effects "None" was ticked. When I tried to change it, "The Composite extension is not available" popped up, and that window would freeze. 

What should I do now?

Also, how do I close this frozen "Appearance Preferences" window? How do I force quit windows with this Ubuntu thing?

---

### Post by jkyahoo101 on 2008-07-20
Is everything installed properly? Did you try restarting? And don't pay too much attention to what I say because I am new to Linux too. But my effects do work perfectly with no lag. And they only take up about 200 some Mb or my ram. (I have 2Gb anyway)

---

### Post by Vadi on 2008-07-20
It looks like desktop effects couldn't be activated on your computer for some reason. Do you know what video card does your computer have?

---

### Post by nickolas on 2008-07-20
Here's all the specs on my computer:

nicholas-ubuntu           
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1406MiB
     *-cpu
          product: AMD Athlon(tm) 64 Processor 3200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up rep_good lahf_lm cpufreq
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 64 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: RS480 [Radeon Xpress 200G Series]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list
                configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_sil latency=64 module=sata_sil
        *-ide:1
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_sil latency=64 module=sata_sil
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide:2
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ATIIXP_IDE latency=64 module=atiixp
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk
                   product: ST3160021A
                   vendor: Seagate
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   capacity: 149GiB (160GB)
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom:0
                   product: TSSTcorpCD/DVDW TS-H552B
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
              *-cdrom:1
                   product: LITE-ON CD-ROM LTN-489S
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   capabilities: packet
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k Data/Fax Modem
                vendor: Conexant
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth0
                version: 10
                serial: 00:11:09:05:bd:61
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.105 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: VIA Technologies, Inc.
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2 module=snd_atiixp
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-scsi
       physical id: 1
       bus info: scsi@5
       logical name: scsi5
       capabilities: scsi-host
       configuration: driver=usb-storage

---

### Post by nickolas on 2008-07-20
So to answer the graphics card question:

01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]

---

### Post by Vadi on 2008-07-20
Okay. Click [here to install Envy]("apt:envyng-gtk"), and then got Applications - System tools - Envy and install the latest ATI driver.

Then try to enable Desktop Effects again. Does it work now?

---

