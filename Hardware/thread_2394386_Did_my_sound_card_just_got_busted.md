---
title: "Did my sound card just got busted?"
date: 2018-06-15
forum: Hardware
---

### Post by marsel-kozubik on 2018-06-15
Hi,

im using Mortar Arctic h270m.

yesterday i heard a kind of a short trash sound comming from my pc, but then all was ok, no changes, today i could not set volume with shortcut (was able with audio panel), but after restart it all died.

First i suspected kernel i installed 2 days ago, but changing it for the older one did nothing, then i tried to reinstall pulse and alsa, but there was no results. It also seems bios sees no issues with mobo (tho all i can do is turn HD audio controller on and off, but it seems bios sees it).
 
some commands:

pacmd
```
 elcome to PulseAudio 8.0! Use "help" for usage information.>>> list-sinks
1 sink(s) available.
  * index: 0
    name: <auto_null>
    driver: <module-null-sink.c>
    flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: RUNNING
    suspend cause: 
    priority: 1000
    volume: front-left: 34080 /  52% / -17,04 dB,   front-right: 34080 /  52% / -17,04 dB
            balance 0,00
    base volume: 65536 / 100% / 0,00 dB
    volume steps: 65537
    muted: no
    current latency: 76,16 ms
    max request: 15 KiB
    max rewind: 15 KiB
    monitor source: 0
    sample spec: s16le 2 k 44100 Hz
    channel map: front-left,front-right
                 Stereo
    used by: 1
    linked by: 1
    configured latency: 90,00 ms; range is 0,50 .. 2000,00 ms
    module: 10
    properties:
        device.description = "G&#322;uche wyj&#347;cie"
        device.class = "abstract"
        device.icon_name = "audio-card"



```
G&#322;uche wyj&#347;cie = Dummy output.

cat /proc/asound/cards
```
 --- no soundcards ---  
```

lspci
```
00:00.0 Host bridge: Intel Corporation Device 590f (rev 06)00:02.0 VGA compatible controller: Intel Corporation Device 5912 (rev 04)
00:08.0 System peripheral: Intel Corporation Sky Lake Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation Device a2af
00:14.2 Signal processing controller: Intel Corporation Device a2b1
00:16.0 Communication controller: Intel Corporation Device a2ba
00:17.0 SATA controller: Intel Corporation Device a282
00:1f.0 ISA bridge: Intel Corporation Device a2c4
00:1f.2 Memory controller: Intel Corporation Device a2a1
00:1f.3 Audio device: Intel Corporation Device a2f0
00:1f.4 SMBus: Intel Corporation Device a2a3
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (2) I219-V



```

As you see lspci shows something.

alxamixergiu shows nothing. Audio-panel only states "Dummy output". I ran my backup pendrive copy of 16.04, but there was also no sound on it (i dont remember i had that issue on livecd, so it may be useless info). I had tried 2 different sets of speakers and also tried to connect them from my monitor output jack (it was always bad but i think it played with a lot of trashing, but now its only trashing left).

Adding to that, i never was a geeky linux user, for past 10 years (starting with 8.10) it just worked for me for the most part (no brightness setting on my laptops, curses!) so i could be go-happy leech of the community, so im sorry if i should have put here any other imputs and i didnt, im in woods here.

EDIT:
Just remembered 1 command.
```
zeke                          description: Desktop Computer
    product: MS-7A69 (Default string)
    vendor: MSI
    version: 2.0
    serial: Default string
    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 vsyscall32
    configuration: boot=normal chassis=desktop family=Default string sku=Default string uuid=00000000-0000-0000-0000-4CCC6AD6D8E8
  *-core
       description: Motherboard
       product: H270M MORTAR ARCTIC (MS-7A69)
       vendor: MSI
       physical id: 0
       version: 2.0
       serial: H216251599
       slot: Default string
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: B.00
          date: 12/13/2016
          size: 64KiB
          capacity: 15MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 3c
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: [empty]
             physical id: 0
             slot: ChannelA-DIMM0
        *-bank:1
             description: DIMM Synchronous 2400 MHz (0,4 ns)
             product: IR2400D464L15S/8G
             vendor: Hitachi
             physical id: 1
             serial: 00000000
             slot: ChannelA-DIMM1
             size: 8GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
        *-bank:2
             description: [empty]
             physical id: 2
             slot: ChannelB-DIMM0
        *-bank:3
             description: [empty]
             physical id: 3
             slot: ChannelB-DIMM1
     *-cache:0
          description: L1 cache
          physical id: 42
          slot: L1 Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 43
          slot: L2 Cache
          size: 512KiB
          capacity: 512KiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: 44
          slot: L3 Cache
          size: 3MiB
          capacity: 3MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) CPU G4600 @ 3.60GHz
          vendor: Intel Corp.
          physical id: 45
          bus info: cpu@0
          version: Intel(R) Pentium(R) CPU G4600 @ 3.60GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 1882MHz
          capacity: 4005MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave rdrand lahf_lm abm 3dnowprefetch invpcid_single intel_pt ibrs ibpb stibp kaiser tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust smep erms invpcid mpx rdseed smap clflushopt xsaveopt xsavec xgetbv1 dtherm arat pln pts hwp hwp_notify hwp_act_window hwp_epp cpufreq
          configuration: cores=2 enabledcores=2 threads=4
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 06
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915_bpo latency=0
             resources: irq:123 memory:de000000-deffffff memory:c0000000-cfffffff ioport:f000(size=64)
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: Sky Lake Gaussian Mixture Model
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
             resources: memory:df04f000-df04ffff
        *-usb
             description: USB controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:120 memory:df030000-df03ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.4.0-128-generic xhci-hcd
                physical id: 0
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-3.00
                configuration: driver=hub slots=8 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.4.0-128-generic xhci-hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=16 speed=480Mbit/s
              *-usb:0
                   description: Human interface device
                   product: obins anne keyboard
                   vendor: STMicroelectronics
                   physical id: 5
                   bus info: usb@1:5
                   version: 2.00
                   serial: STM32
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=400mA speed=12Mbit/s
              *-usb:1
                   description: Mouse
                   product: USB Receiver
                   vendor: Logitech
                   physical id: 7
                   bus info: usb@1:7
                   version: 30.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
              *-usb:2
                   description: Bluetooth wireless interface
                   product: CSR8510 A10
                   vendor: Cambridge Silicon Radio, Ltd
                   physical id: b
                   bus info: usb@1:b
                   version: 88.91
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
        *-generic:1 UNCLAIMED
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:df04e000-df04efff
        *-communication
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:124 memory:df04d000-df04dfff
        *-storage
             description: SATA controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:121 memory:df048000-df049fff memory:df04c000-df04c0ff ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:df04b000-df04b7ff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory UNCLAIMED
             description: Memory controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 00
             width: 32 bits
             clock: 33MHz (30.3ns)
             capabilities: bus_master
             configuration: latency=0
             resources: memory:df044000-df047fff
        *-multimedia
             description: Audio device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:125 memory:df040000-df043fff memory:df020000-df02ffff
        *-serial UNCLAIMED
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:df04a000-df04a0ff ioport:f040(size=32)
        *-network
             description: Ethernet interface
             product: Ethernet Connection (2) I219-V
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             logical name: enp0s31f6
             version: 00
             serial: 4c:cc:6a:d6:d8:e8
             size: 100Mbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.8-4 ip=192.168.1.101 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:122 memory:df000000-df01ffff
     *-scsi
          physical id: 1
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD10JPVX-22J
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: 1A01
             serial: WD-WXM1E14JDCU7
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=7a076451
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 66a7309c-0db6-4e52-a6e7-08f37e846bda
                size: 18GiB
                capacity: 18GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2017-12-18 23:44:01 filesystem=ext4 lastmountpoint=/ modified=2018-06-15 22:40:53 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2018-06-15 22:41:00 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                size: 8081MiB
                capacity: 8081MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 8081MiB
                   capabilities: nofs
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@1:0.0.0,3
                logical name: /dev/sda3
                logical name: /home
                version: 1.0
                serial: dc144065-620c-4748-b86e-5eab2974acf4
                size: 904GiB
                capacity: 904GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2017-11-19 12:32:25 filesystem=ext4 lastmountpoint=/home modified=2018-06-15 22:41:05 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2018-06-15 22:41:05 state=mounted
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh



```

---

### Post by marsel-kozubik on 2018-06-18
Hmmmm...


For some reason after pc was turned off for a bit, the sound card is showing now in [COLOR=#000000]cat /proc/asound/cards.[/COLOR]

[COLOR=#000000]Tho, there still was no sound, even if everything behaved like it is (including pavucountrol). Also running Windows showed that sound card is working, so i think this topic should be moved to different section?[/COLOR]

[COLOR=#000000]Now, what happened next, well i tried couple of solutions found on the internet (adding stuff to mobprobe, new settings to config, purging and forcing restarts etc), after many pc restarts nothing changed, not even on guest account. Just a while ago i did killall pulseaudio (aplay was playing something, tho it was demons matting call if you ask me adn supposed to be soundtrack from Hobbit, so i guessed its not alsa, also pulseaudio --kill seems not working?) and started pulseaudio again... and it worked. Tho i doubt simple killing and restarting pulseaudio is the solution, if it would be, restarting pc would work too.[/COLOR]


[COLOR=#000000]So... i have no idea how i "fixed" it... and now im afraid to turn off my pc... What is happening?

EDIT: It happened live, so i need to restart each program (browser/players), else it wont have sound, so i guess it may indeed be pulseaudio, but still no idea what fixed it.[/COLOR]

---

