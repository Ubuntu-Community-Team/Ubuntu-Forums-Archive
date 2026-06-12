---
title: "No Video, GeForce 6200, 7.04, Help!"
date: 2007-09-24
forum: Hardware &amp; Laptops
---

### Post by Ubunme2 on 2007-09-24
Help, we love Ubuntu 7.04, but it won't install.

The process starts fine but just when it's ready to load the monitor flash is a series of random colors and lines.

HP media Center Pentium 4, 1 GB of RAM, GeForce 6200.

Must have installed ubuntu a dozen times, never had a problem before.

---

### Post by w4ett on 2007-09-24
I'd start by reconfiguring your xorg.conf.....boot into recovery mode.

From the command line type:


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Red"]"vesa"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:


```
startx
```

This should  get you to a GUI desktop.

There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

---

### Post by Ubunme2 on 2007-09-24
W4ett,

Thank you so much for your help!

This sounds like a lot of good information here,
 my first question would be: how do I get to the command line to enter the information if 7.04 won't even load as a live CD?

I am using a 21 inch wide monitor 1600 x 1200, should I try to find a smaller one for installation?

I hope this is good news, I tried to install the older version 6.06 and at least it plays as a live CD.  Would it be easier to install 6.06 and then upgrade to 7.04?

A sincere thanks for your help!

---

### Post by w4ett on 2007-09-24
If you can get to the initial main menu....try using the safe graphics mode...it that will not work....I would suggest using the Alternate Install CD which uses a text based installer.

While using 6.06 and then doing a stepped upgrade will work, it's kinda messy and time consuming and generally not recommended.

---

### Post by Ubunme2 on 2007-09-24
Thank you for your help,

I took your advice and installed the alternate CD,
The same problem exists with flashing colors and lines.
Tried rebooting into the recovery mode:
sudo dpkg-reconfigure -phigh xserver-xorg
just comes up with a postinst warning: over writing possibly customized configuration file; backup in /ext/X11/xord.conf 20070924162953


And there is no way to get to possible resolutions and drivers.

---

### Post by w4ett on 2007-09-24
> **Ubunme2 said:**
> Thank you for your help,

I took your advice and installed the alternate CD,
The same problem exists with flashing colors and lines.
Tried rebooting into the recovery mode:
sudo dpkg-reconfigure -phigh xserver-xorg
just comes up with a postinst warning: over writing possibly customized configuration file; backup in /ext/X11/xord.conf 20070924162953


And there is no way to get to possible resolutions and drivers.

That is a normal warning....we are trying to overwrite the file because we are reconfiguring it......Go ahead and ```
sudo dpkg-reconfigure -phigh xserver-xorg 
```
again...and select vesa as the driver and then startx again......lets see if we can get you into a GUI.

---

### Post by Ubunme2 on 2007-09-24
Yes, how can I get past that warning,
the up and down cursor keys just add or remove the last command.

---

### Post by w4ett on 2007-09-24
<enter>

---

### Post by Ubunme2 on 2007-09-24
Yes, "Enter" just reinserts the command prompt.
And the "spacebar" just add spaces.

---

### Post by w4ett on 2007-09-24
now type ```
startx
```
This should start your Graphic Display Manager.

---

### Post by Ubunme2 on 2007-09-24
When I type:

"startx"

It just makes the monitor flash colors and lines, I still can't get past the warning and enter the area to select drivers or resolutions.

---

### Post by w4ett on 2007-09-24
Hmmm...now this IS wierd....

I had a 6200 card that did the same thing...I finally RMA'd the thing and got a replacement.  (Not saying YOURS is bad though...too early for that).....BTW...what motherboard are you using this card in?....Does it have an SiS or Via controller?   Reason I'm asking is to see if there is any correlation between the Mobo and the card..

Can you try the card in another motherboard by any chance?  We want to rule out a bad card.

---

### Post by Ubunme2 on 2007-09-24
Oh my, this is getting interesting, We bought the 6200 to replace the (very expensive) ATI 9800 that failed twice, and the first 6200 had already been returned to the store because we were having problems with jerky video.

We are also having problems trying to get a win TV HVR 1600 card to work, that's why we are buying a new computer and trying to get this one set up with linux.

I will be glad to get you the info on the motherboard (how do we do that)?

---

### Post by Ubunme2 on 2007-09-24
I am duel booting Windows and the card is still working okay with that operating system.

The TV tuner card symptoms are: (sometimes jerky picture) (sometimes crashing program) (and trouble with QAM stations)

---

### Post by Ubunme2 on 2007-09-24
OK, I'm running 6.06 live,
Here is the info:

ubuntu@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 (rev a1)0000:02:09.0 Multimedia video controller: Conexant: Unknown device 5b7a
0000:02:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
0000:02:0a.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 03)
0000:02:0b.0 USB Controller: NEC Corporation USB (rev 43)
0000:02:0b.1 USB Controller: NEC Corporation USB (rev 43)
0000:02:0b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0000:02:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:0d.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)
ubuntu@ubuntu:~$



ubuntu@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1011MB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.66GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.7
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: e0000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e0000000-e3ffffff
        *-pci:0
             description: PCI bridge
             product: 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: GeForce 6200
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:ec000000-ecffffff iomemory:d0000000-dfffffff iomemory:ed000000-edffffff irq:10
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:d800-d81f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:d000-d01f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Human interface device
                   product: WingMan Cordless Gamepad
                   vendor: Logitech
                   physical id: 2
                   bus info: usb@2:2
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:d400-d41f irq:169
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: USB hub
                   product: TUSB2046 Hub
                   vendor: Texas Instruments, Inc.
                   physical id: 2
                   bus info: usb@3:2
                   version: 1.25
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s                 *-usb:0
                      description: Mass storage device
                      product: USB Reader
                      physical id: 3
                      bus info: usb@3:2.3
                      version: 1.00
                      serial: 0E33040047B5
                      capabilities: usb-1.10 scsi
                      configuration: driver=usb-storage maxpower=350mA speed=12.0MB/s
                 *-usb:1
                      description: Human interface device
                      product: EverestFBB
                      vendor: HP
                      physical id: 4
                      bus info: usb@3:2.4
                      version: 1.00
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:ef000000-ef0003ff irq:193
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.15-26-386 ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-multimedia:0 UNCLAIMED
                description: Multimedia video controller
                product: Conexant
                vendor: Conexant
                physical id: 9
                bus info: pci@02:09.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:e4000000-e7ffffff irq:255
           *-multimedia:1
                description: Multimedia audio controller
                product: SB Audigy
                vendor: Creative Labs
                physical id: a
                bus info: pci@02:0a.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=EMU10K1_Audigy
                resources: ioport:c000-c01f irq:209
           *-input
                description: Input device controller
                product: SB Audigy MIDI/Game port
                vendor: Creative Labs
                physical id: a.1
                bus info: pci@02:0a.1
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=Emu10k1_gameport
                resources: ioport:c400-c407
           *-usb:0
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: b
                bus info: pci@02:0b.0
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci_hcd
                resources: iomemory:e9003000-e9003fff irq:185
              *-usbhost
                   product: OHCI Host Controller
                   vendor: Linux 2.6.15-26-386 ohci_hcd
                   physical id: 1
                   bus info: usb@5
                   logical name: usb5
                   version: 2.06
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s           *-usb:1
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: b.1
                bus info: pci@02:0b.1
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci_hcd
                resources: iomemory:e9000000-e9000fff irq:177
              *-usbhost
                   product: OHCI Host Controller
                   vendor: Linux 2.6.15-26-386 ohci_hcd
                   physical id: 1
                   bus info: usb@7
                   logical name: usb7
                   version: 2.06
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=0mA slots=1 speed=12.0MB/s           *-usb:2
                description: USB Controller
                product: USB 2.0
                vendor: NEC Corporation
                physical id: b.2
                bus info: pci@02:0b.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: ehci bus_master cap_list
                configuration: driver=ehci_hcd
                resources: iomemory:e9001000-e90010ff irq:201
              *-usbhost
                   product: EHCI Host Controller
                   vendor: Linux 2.6.15-26-386 ehci_hcd
                   physical id: 1
                   bus info: usb@6
                   logical name: usb6
                   version: 2.06
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=0mA slots=3 speed=480.0MB/s
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: c
                bus info: pci@02:0c.0
                logical name: eth0
                version: 10
                serial: 00:10:dc:f7:7b:ee
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too ip=192.168.1.100 multicast=yes
                resources: ioport:c800-c8ff iomemory:e9002000-e90020ff irq:193
           *-firewire
                description: FireWire (IEEE 1394)
                product: uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr
                vendor: NEC Corporation
                physical id: d
                bus info: pci@02:0d.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:e9004000-e9004fff irq:193
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:f000-f00f iomemory:50100000-501003ff irq:169
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: WDC WD1600AB-22DBA0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 149GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom:0
                   product: Hewlett-Packard DVD Writer 300
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capacity: 698MB
                   capabilities: packet
              *-cdrom:1
                   product: FX48++W
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   capabilities: packet
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             resources: ioport:500-51f irq:255
  *-scsi
       physical id: 1
       bus info: scsi@0
       logical name: scsi0
       capabilities: scsi-host
       configuration: driver=usb-storage
ubuntu@ubuntu:~$

---

### Post by Ubunme2 on 2007-09-25
The ubuntu splash screen looks fine, but instead of the login screen appearing on the monitor it shows random colors and lines.

This seems to be a problem with 7.04 because the live 6.06 CD works fine.

---

### Post by w4ett on 2007-09-25
At this point I think I'll need to direct you to the official Nvidia linux forum and IRC channel.  For the lfe of me, I don't see anything that should keep it from working.

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

irc://freenode/nvidia

---

### Post by PmDematagoda on 2007-09-25
I seem to be having your specs as well:-

Nvidia GeForce 6200
1Gb RAM
P4 with HT
Not an HP though

But I don't have any problems.

---

### Post by PmDematagoda on 2007-09-25
Could you post the errors when you try to startx in Recovery mode, after you "startx" wait for some time, then press Alt+F2, this brings you back to the terminal where you can see the errors.

---

