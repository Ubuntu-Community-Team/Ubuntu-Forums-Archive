---
title: "touchpad not recognized"
date: 2010-07-20
forum: Hardware
---

### Post by kuckunniwi on 2010-07-20
Am running Lucid NBR, and touchpad is completely nonfunctional. It's worked, in a couple occasions, for a minute or so, and then stopped working.

The device doesn't show up in "xinput list" or "cat /proc/bus/input/devices". I heard a variation of my xorg.conf file could help with the issue, but to my surprise, xorg.conf shows up blank (gksudo gedit xorg.conf). I'm not running from LiveCD.

Could this be a hardware problem? Touchpad wasn't detected in EasyPeasy 1.6, Ubuntu 9.04 NBR or Moblin either...If anyone has any ideas of what it could be or what I could try, I'd be very grateful! Thanks

---

### Post by gordintoronto on 2010-07-20
What brand and model of computer is this? Has the touchpad ever worked?

---

### Post by kuckunniwi on 2010-07-20
> **gordintoronto said:**
> What brand and model of computer is this? Has the touchpad ever worked?

It's a Clevo M815P, distributed by Spanish vendor Ahtec under the name LUGCM810P.

lshw:

>       description: Computer
    product: M815P
    vendor: CLEVO CO.
    version: Not Applicable
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=oem-specific cpus=1 uuid=0090F5A0-23EA-0000-0000-000000000000
  *-core
       description: Motherboard
       product: M815P
       vendor: CLEVO CO.
       physical id: 0
       version: Not Applicable
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 6.00 (02/11/2010)
          size: 97KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect int9keyboard int10video acpi usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N450   @ 1.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.10
          serial: [REMOVED]
          slot: CPU 1
          size: 1333MHz
          capacity: 3300MHz
          width: 64 bits
          capabilities: boot fpu fpu_exception wp vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm pse cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: burst internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 012345678901234567890123456789012345
             vendor: 48spaces
             physical id: 0
             serial: [REMOVED]
             slot: J6G1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns) [empty]
             product: 012345678901234567890123456789012345
             vendor: 48spaces
             physical id: 1
             serial: [REMOVED]
             slot: J6G2
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: N10 Family DMI Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: N10 Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:28 memory:f0300000-f037ffff ioport:18e8(size=8) memory:d0000000-dfffffff(prefetchable) memory:f0000000-f00fffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: N10 Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f0380000-f03fffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:f0400000-f0403fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:2000(size=4096) memory:f0100000-f01fffff memory:80000000-801fffff(prefetchable)
           *-network
                description: Wireless interface
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wlan0
                version: 10
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl819xSE driverversion=0015.0127.2010 firmware=62 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=802.11bg
                resources: irq:16 ioport:2000(size=256) memory:f0100000-f0103fff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:4000(size=4096) memory:80200000-803fffff memory:80400000-805fffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:3000(size=4096) memory:f0200000-f02fffff memory:80600000-807fffff(prefetchable)
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:09:00.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:19 memory:f0204000-f02040ff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:09:00.2
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:f0204400-f02044ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:09:00.3
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:19 memory:f0204800-f02048ff
           *-network
                description: Ethernet interface
                product: JMC260 PCI Express Fast Ethernet Controller
                vendor: JMicron Technology Corp.
                physical id: 0.5
                bus info: pci@0000:09:00.5
                logical name: eth0
                version: 02
                serial: [REMOVED]
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.5 duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:29 memory:f0200000-f0203fff ioport:3400(size=128) ioport:3000(size=256)
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f0604000-f06043ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: NM10 Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: N10/ICH7 Family SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:27 ioport:18e0(size=8) ioport:18d4(size=4) ioport:18d8(size=8) ioport:18d0(size=4) ioport:18c0(size=16) memory:f0604400-f06047ff
           *-disk
                description: ATA Disk
                product: TOSHIBA MK3255GS
                vendor: Toshiba
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: FG01
                serial: [REMOVED]
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000be880
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: [REMOVED]
                   size: 38GiB
                   capacity: 38GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-07-16 18:12:25 filesystem=ext4 lastmountpoint=/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;g &#65533;&#65533;&#65533;}&#65533;_/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;w&#65533;&#65533;&#65533;w&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;j modified=2010-07-19 14:52:17 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-07-20 21:15:57 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 259GiB
                   capacity: 259GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3905MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /home
                      capacity: 256GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18a0(size=32)


The touchpad has work for a few brief moments in a couple of occasions. Didn't work on any of the other systems mentioned above either. Haven't tried on Windows, as the device has no optical unit, and for now I don't have a flash drive with enough space to create a USB loader for a copy of Windows 7 that someone lent me, so I have no reference for functioning on non-Linux OS. 

I've written to distributor asking for exact model of the touchpad, but am thinking that since the netbook is only a week old, maybe I can have their tech support solve it for me. Which brings me to a turning point in my Ubuntu experience (off-topic): I've never taken a computer running anything but Windows to tech support. What kind of response can I expect from them if I choose to take it in? I don't think there's an OS-specific clause in the sale contract, but then again...they profit off of selling Microsoft OS's, so...

Back on topic:

Does anyone have any suggestions for a newbie? If I try installing WinXP from USB and to see if the touchpad works & ind out if it's a hardware problem, Windows installation will screw up my Grub, won't it?

---

### Post by irv on 2010-07-20
I open my 05-evdev.conf file in gedit and mind looked like this:
the file is located in /usr/lib/x11/xorg.conf.d/
```
# Catchall classes for input devices
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
	Identifier "evdev pointer catchall"
	MatchIsPointer "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
EndSection

Section "InputClass"
	Identifier "evdev keyboard catchall"
	MatchIsKeyboard "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
EndSection

[COLOR="Red"]Section "InputClass"
	Identifier "evdev touchpad catchall"
	MatchIsTouchpad "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
EndSection[/COLOR]

Section "InputClass"
	Identifier "evdev tablet catchall"
	MatchIsTablet "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
EndSection

Section "InputClass"
	Identifier "evdev touchscreen catchall"
	MatchIsTouchscreen "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
EndSection
```
You might want to see if you have what I have marked in [COLOR="Red"]RED[/COLOR] in your file.
Here is a screen shot of my System> Preference> mouse, and the touchpad tab. [ATTACH]164062[/ATTACH]

---

### Post by kuckunniwi on 2010-07-20
> **irv said:**
> I open my 05-evdev.conf file in gedit and mind looked like this:
the file is located in /usr/lib/x11/xorg.conf.d/
```
# Catchall classes for input devices
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
	Identifier "evdev pointer catchall"
	MatchIsPointer "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
EndSection

Section "InputClass"
	Identifier "evdev keyboard catchall"
	MatchIsKeyboard "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
EndSection

[COLOR="Red"]Section "InputClass"
	Identifier "evdev touchpad catchall"
	MatchIsTouchpad "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
EndSection[/COLOR]

Section "InputClass"
	Identifier "evdev tablet catchall"
	MatchIsTablet "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
EndSection

Section "InputClass"
	Identifier "evdev touchscreen catchall"
	MatchIsTouchscreen "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
EndSection
```
You might want to see if you have what I have marked in [COLOR="Red"]RED[/COLOR] in your file.
Here is a screen shot of my System> Preference> mouse, and the touchpad tab. [ATTACH]164062[/ATTACH]

So that would be "gksudo gedit /usr/lib/x11/xorg.conf.d/05-evdev.conf" ? (SOrry, very new to command line here...)

File is blank. Xorg.conf is also blank. And under mouse configuration, I get no tab for the touchpad...

xinput list output is:
> 
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=11	[slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                       	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]

and cat /proc/bus/input/devices is:

> I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
U: Uniq=
H: Handlers=event1 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=mouse0 event4 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0001 Vendor=10ec Product=0272 Version=0001
N: Name="HDA Digital PCBeep"
P: Phys=card0/codec#0/beep0
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=192f Product=0616 Version=0111
N: Name="USB Optical Mouse"
P: Phys=usb-0000:00:1d.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input8
U: Uniq=
H: Handlers=mouse1 event8 
B: EV=17
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10

travis@wonderland:~$ sudo cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
U: Uniq=
H: Handlers=event1 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=mouse0 event4 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0001 Vendor=10ec Product=0272 Version=0001
N: Name="HDA Digital PCBeep"
P: Phys=card0/codec#0/beep0
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=192f Product=0616 Version=0111
N: Name="USB Optical Mouse"
P: Phys=usb-0000:00:1d.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input8
U: Uniq=
H: Handlers=mouse1 event8 
B: EV=17
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10

This means the system isn't even detecting the hardware, right?

---

### Post by kuckunniwi on 2010-07-20
OK..sorry, complete newbie/idiot here. Managed to open 05-evdev.conf. In theory, touchpad is "on"...

# Catchall classes for input devices
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
	Identifier "evdev pointer catchall"
	MatchIsPointer "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
EndSection

Section "InputClass"
	Identifier "evdev keyboard catchall"
	MatchIsKeyboard "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
EndSection

Section "InputClass"
	Identifier "evdev touchpad catchall"
	MatchIsTouchpad "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
EndSection

Section "InputClass"
	Identifier "evdev tablet catchall"
	MatchIsTablet "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
EndSection

Section "InputClass"
	Identifier "evdev touchscreen catchall"
	MatchIsTouchscreen "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
EndSection

---

### Post by gordintoronto on 2010-07-20
If the computer is brand new, I would go right back to the vendor.

Did it have an OS installed when you got it?

---

### Post by kuckunniwi on 2010-07-20
> **gordintoronto said:**
> If the computer is brand new, I would go right back to the vendor.

Did it have an OS installed when you got it?

No, I bought it with no OS. But they can't deny service just because I'm not running Windows, can they??? ;)

---

### Post by irv on 2010-07-21
> **kuckunniwi said:**
> No, I bought it with no OS. But they can't deny service just because I'm not running Windows, can they??? ;)

Best Buy did it to me. I bought the extended warranty and they did not want to honor that either, so I made them give me my money back on the warranty, but I had to keep the computer. I fixed it myself, and I will never do business with them again.

---

### Post by kuckunniwi on 2010-07-21
> **irv said:**
> Best Buy did it to me. I bought the extended warranty and they did not want to honor that either, so I made them give me my money back on the warranty, but I had to keep the computer. I fixed it myself, and I will never do business with them again.

Took it to the distributor. The problem had nothing to do with Ubuntu. As it turns out, the touchpad connection was loose. I must say, I was extremely pleased with the tech support: they fixed it on the spot. I didn't mention which OS I was using, just to see what happened, and the netbook was returned to me 10 minutes later, with no mention of OS (no mention=no discrimination?). When I asked the guy if he had tested it to see if it worked, he told me the netbook had been booted with a live CD of Lucid & the touchpad worked perfectly, which led him to make an ironic remark concerning how touchpads and such devices generally work out of the box under Ubuntu, as opposed to how complicated it can be to get certain wifi cards up & running, thanks to the [little] effort certain manufacturers put into developing drivers for Linux-based OS's. 

It short, I'm extremely pleased with the support I received. There's something to be said about non-mainstream distributors & OEMs....

---

### Post by irv on 2010-07-21
Makes me wish I would have order my laptop from a place like this.
Glad you got it fix.

---

