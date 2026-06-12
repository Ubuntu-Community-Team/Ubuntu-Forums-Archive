---
title: "10 year old Acer laptop with resolution problem"
date: 2015-12-01
forum: Hardware
---

### Post by Bathroom Humor on 2015-12-01
My cousin was wanting me to fix up her old (old) laptop for her, until she gets a more recent laptop, hopefully soon. I got a new charger cable that would work with it, But this bad boy was running XP, and is very likely unable to handle Windows 7, even if I could get a copy of it. So, no more support for the primary OS.

Lubuntu to the rescue! It was going fine, the live-DVD worked as well as I would hope. Wireless drivers will take some work, but that's pretty usual with broadcom. So, I installed it, which also worked fine. I did notice some graphical flickering, but that wasn't enough to deter me. Then, after the install, I booted it up and the resolution was now much smaller, I think it is stuck at 640x400, and I have no way to adjust it anymore. I installed some firmware from the "additional drivers" box, but it didn't work. I tried looking for drivers other drivers online, or other people who have this issue and I didn't find anything.

The CPU is an AMD Turion 64 ml-30. I do not think there is any gpu present but, like I said, the resolution was fine in the Live-DVD. Any help would be appreciated. Otherwise this thing will be a paperweight for good.

---

### Post by weatherman2 on 2015-12-01
Do a web search for the exact model of Acer laptop it is  + "Ubuntu."  You might find past examples where people were able to tweak it to get it working.

Your problem sounds much like the issue I had in the past with a Dell Inspiron 1100.  It took some tweaking to get the resolution beyond 640x480 - some Grub options or something, certainly not intuitive.

---

### Post by Bathroom Humor on 2015-12-01
I saw posts online about adding a xorg config file but I don't know enough about how to do that sort of thing and my attempt just cased it to stop loading altogether.

But yes I will keep looking around for information. I hope the solution isn't going to involve pulling out hair.

---

### Post by weatherman2 on 2015-12-01
I pulled out some hair over that old 1100, when it wasn't as old as it is now.  Even then it probably wasn't worth the effort for such an old thing.  I wouldn't waste my time on the 1100 today.  Yours seems to be slightly newer - maybe worth it, maybe not.

You might broaden your search to the graphics chipset.  For old Intel-based laptops, you can do stuff with the i915 driver but of course that's irrelevant with an AMD-based laptop.

---

### Post by mörgæs on 2015-12-02
Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by sudodus on 2015-12-02
Since the live session worked I would try with the following tweak:

Edit the file **/etc/default/grub**: remove the **#** character from the line **#GRUB_TERMINAL=console**

```
sudo nano /etc/default/grub
```

to make it like this

```
GRUB_TERMINAL=console
```

Save the file and run the following command to make the tweak active.

```
sudo update-grub
```

Reboot

---

### Post by Bathroom Humor on 2015-12-02
I found this thread a moment ago [http://ubuntuforums.org/showthread.php?t=2252413&page=3](http://ubuntuforums.org/showthread.php?t=2252413&page=3) (hey mörgæs you were there lol) and after checking Synaptic, it appears as though a dropped driver may also be the issue for me. That SIS driver seems to causing people issues.

I may try to do the Grub tweak if you think that may be a better work around, but if not, I will have to install 14.04 and/or compile the new driver.

I will post the output lshw in a moment, I'm typing this on another laptop while troubleshooting because that resolution makes me want to weep.

---

### Post by Bathroom Humor on 2015-12-02
```
computer
    description: Computer
    width: 32 bits
    capabilities: smbios-2.31 smp-1.4 smp
    configuration: cpus=1
  *-core
       description: Motherboard
       physical id: 0
     *-cpu
          product: AMD Turion(tm) 64 Mobile Technology ML-30
          vendor: Advanced Micro Devices [AMD]
          physical id: 0
          bus info: cpu@0
          version: 15.4.2
          size: 800MHz
          capacity: 1600MHz
          width: 64 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow rep_good pni lahf_lm 3dnowprefetch vmmcall cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 1MiB
     *-memory
          description: System memory
          physical id: 1
          size: 1019MiB
     *-pci:0
          description: Host bridge
          product: 760/M760 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-amd64 latency=64
          resources: irq:0 memory:e0000000-e1ffffff
        *-pci
             description: PCI bridge
             product: AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:a000(size=4096) memory:e2100000-e21fffff memory:e8000000-efffffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller cap_list
                configuration: latency=0
                resources: memory:e8000000-efffffff memory:e2100000-e211ffff ioport:a000(size=128)
        *-isa
             description: ISA bridge
             product: SiS963 [MuTIOL Media IO] LPC Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 25
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2/3 SMBus controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0
             resources: irq:0 ioport:8100(size=32)
        *-ide
             description: IDE interface
             product: 5513 IDE Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=pata_sis latency=128
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:2000(size=16)
        *-communication UNCLAIMED
             description: Modem
             product: AC'97 Modem Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.6
             bus info: pci@0000:00:02.6
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=173 maxlatency=11 mingnt=52
             resources: ioport:1000(size=256) ioport:1c00(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: SiS7012 AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=173 maxlatency=11 mingnt=52
             resources: irq:18 ioport:1400(size=256) ioport:1c80(size=128)
        *-usb:0
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64 maxlatency=80
             resources: irq:20 memory:e2002000-e2002fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.2.0-19-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=3 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64 maxlatency=80
             resources: irq:21 memory:e2003000-e2003fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.2.0-19-generic ohci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=3 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64 maxlatency=80
             resources: irq:23 memory:e2004000-e2004fff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.2.0-19-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.02
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
        *-network:0
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: enp0s4
             version: 91
             serial: [REMOVED]
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=[REMOVED] latency=173 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100Mbit/s
             resources: irq:19 ioport:1800(size=256) memory:e2005000-e2005fff memory:40020000-4003ffff
        *-pcmcia
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:19 memory:40000000-40000fff ioport:2400(size=256) ioport:2800(size=256) memory:44000000-47ffffff memory:48000000-4bffffff
        *-network:1
             description: Network controller
             product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=b43-pci-bridge latency=64
             resources: irq:17 memory:e2000000-e2001fff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA MK1031GA
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 4A
             serial: [REMOVED]
             size: 93GiB (100GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=a315a315
           *-volume:0
                description: Windows FAT volume
                vendor: MSWIN4.1
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: FAT32
                serial: [REMOVED]
                size: 3004MiB
                capacity: 3004MiB
                capabilities: primary boot fat initialized
                configuration: FATs=2 filesystem=fat label=PQSERVICE
           *-volume:1
                description: Windows FAT volume
                vendor: MSWIN4.1
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: FAT32
                serial: [REMOVED]
                size: 44GiB
                capacity: 45GiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat label=ACER
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                size: 45GiB
                capacity: 45GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2002MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /
                   capacity: 43GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVDRW SOSW-833S
             vendor: Slimtype
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             logical name: /media/heather/Lubuntu 15.10 i386
             version: VRS2
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /media/heather/Lubuntu 15.10 i386
                capabilities: partitioned partitioned:dos
                configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 signature=5803726b state=mounted
              *-volume UNCLAIMED
                   description: Hidden HPFS/NTFS partition
                   physical id: 1
                   capacity: 746MiB
                   capabilities: primary bootable hidden

```

---

### Post by sudodus on 2015-12-02
Yes, I think there can be problems with SIS graphics, and *mörgæs* is better than I to analyze such problems. Let us wait for his advice :-)

That thread you linked to in post #7 looks promising though.

---

### Post by Bathroom Humor on 2015-12-02
I jumped the gun a little and compiled the newest SIS driver, but after a reboot nothing has changed. I'm not sure if I would need to remove another video driver or how to check if it is even installed properly.

---

### Post by mörgæs on 2015-12-03
Thanks for the faith but I don't have more advice than what is written in the thread mentioned above and in 
[http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)

This is one if the few examples where I would suggest Lubuntu 14.04. Does it work better?

---

### Post by Bathroom Humor on 2015-12-03
I assume the compiling did not work or I needed to go through more steps in order to get the module to load. I don't know, but it really isn't worth the trouble in the event that 14.04 works as intended! The support window for security updates would be much longer than 15.10 anyway.

Hopefully the wireless will be more cooperative too but I'll cross that bridge when I get to it. I'm burning a Lubuntu 14.04 cd as I type this, but I will install it tomorrow when I wake up. I'll report back in after.
 Thank you for your time, guys.

---

### Post by Bathroom Humor on 2015-12-03
So far so good. I had to burn a 14.04 CD without any point releases because I didn't feel like using another DVD and the original 14.04 ISO is the only one that fits on a CD. So i'm doing the big updates now and no huge issues at the moment, aside from the Wireless not working :/ but it was expected to begin with. Resolution on and off the live media is fine though, so I'll be sticking with this.

---

### Post by mörgæs on 2015-12-05
Good, please mark the thread solved.
For the Broadcom problem see this:
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by Bathroom Humor on 2015-12-05
I actually did get my wireless sorted out mostly. I say mostly because it does work as far as I know after fiddling with modules and screwing up dpkg (I used this page eventually to set my driver straight [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)), but now I cannot suspend the laptop and when I reboot my machine it gives me warnings that mention the network manager, but these may be completely unrelated, and aren't related to this thread, in any case.
Thanks again!

---

### Post by mörgæs on 2015-12-06
This is the kind of small annoyances which are expected in old software like 14.04. Security related bugs are fixed but not minor ones like the one you described. 

If I read your posts right the suspend bug was not in 15.10, meaning that a fix has been released sometime after 14.04.

Have you tried the development version (16.04)? I expect it to behave like 15.10 but it's interesting to get a confirmation.

---

