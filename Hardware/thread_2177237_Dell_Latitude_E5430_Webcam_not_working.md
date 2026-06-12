---
title: "Dell Latitude E5430 Webcam not working"
date: 2013-09-27
forum: Hardware
---

### Post by miguel8 on 2013-09-27
Hello,

          I have a Dell Latitude E5430 Laptop running  Ubuntu and I can't seem to get my integrated Webcam to work. I looked  online and tried the following things with no success:


[LIST]
[*]Check to see if device is recognized with lsusb 
[*]result: 
[/LIST]

                             ```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:6449  Microdia     <------------------------------------------ This is  my webcam
Bus 002 Device 002: ID 80ee:0021 VirtualBox USB Tablet
```

After  I did that I downloaded an application called Cheese. When I ran the  program the LED on my webcam turns on denoting that its being used but  the screen on cheese stays black no matter what I do


After  that I tried the line  gstreamer-properties from the command prompt. I  got a window and switched to the video tab. I tried video for  linux2(v4l2) and chose my webcam from the dropdown list. When I pressed  test a small box appeared that said testing. My webcam's LED turned on  again but no picture is shown. I tried mixing the settings but nothing  worked.

Next I tried using a program called guvcview. Again The  LED turns on but there is no picture. Here is the output from the  command prompt:


```

guvcview 1.5.3
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround71
ALSA  lib setup.c:565:(add_elem) Cannot obtain info for CTL elem  (MIXER,'IEC958 Playback Default',0,0,0): No such file or directory
ALSA  lib setup.c:565:(add_elem) Cannot obtain info for CTL elem  (MIXER,'IEC958 Playback Default',0,0,0): No such file or directory
ALSA  lib setup.c:565:(add_elem) Cannot obtain info for CTL elem  (MIXER,'IEC958 Playback Default',0,0,0): No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
video device: /dev/video0 
Init. Laptop_Integrated_Webcam_E4HD (location: usb-0000:00:0b.0-1)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/10, 1/5, 
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
vid:0c45 
pid:6449 
driver:uvcvideo
checking format: 842094169
fps is set to 1/10
drawing controls

Checking video mode 1280x720@32bpp : OK 
 Could not grab image (select timeout): Resource temporarily unavailable (this repeats over and over)
```


I also tried entering the line webcam in the terminal. 

here is the output


```
reading config file: /home/miguel/.webcamrc
video4linux webcam v1.5 - (c) 1998-2002 Gerd Knorr
grabber config:
  size 320x240 [none]
  input (null), norm (null), jpeg quality 75
  rotate=0, top=0, left=0, bottom=240, right=320
```


The Webcam's LED turns on but there is no picture 

Lastly I tried running the line Dmesg.

I will paste that last since it was long. Does anyone have any idea why this is happening?


Dmesg output:

```

[    0.016714] mce: CPU supports 0 MCE banks
[    0.031269] ACPI: Core revision 20110623
[    0.031931] ftrace: allocating 26592 entries in 105 pages
[    0.036360] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.079425] CPU0: Intel(R) Core(TM) i5-3320M CPU @ 2.60GHz stepping 09
[    0.080004] APIC calibration not consistent with PM-Timer: 98ms instead of 100ms
[    0.080004] APIC delta adjusted to PM-Timer: 6250023 (6173285)
[    0.080004] Performance Events: unsupported p6 CPU model 58 no PMU driver, software events only.
[    0.080004] NMI watchdog disabled (cpu0): hardware events not enabled
[    0.080004] Booting Node   0, Processors  #1 Ok.
[    0.080004] smpboot cpu 1: start_ip = 9a000
[    0.020001] mce: CPU supports 0 MCE banks
[    0.168009] TSC synchronization [CPU#0 -> CPU#1]:
[    0.168009] Measured 8742351 cycles TSC warp between CPUs, turning off TSC clock.
[    0.168009] Marking TSC unstable due to check_tsc_sync_source failed
[    0.168071] NMI watchdog disabled (cpu1): hardware events not enabled
[    0.168138] Brought up 2 CPUs
[    0.168143] Total of 2 processors activated (10263.40 BogoMIPS).
[    0.168597] devtmpfs: initialized
[    0.168597] EVM: security.selinux
[    0.168597] EVM: security.SMACK64
[    0.168597] EVM: security.capability
[    0.168673] print_constraints: dummy: 
[    0.168722] RTC time:  0:13:43, date: 09/28/13
[    0.168752] NET: Registered protocol family 16
[    0.168923] ACPI: bus type pci registered
[    0.168853] Trying to unpack rootfs image as initramfs...
[    0.169027] PCI: Using configuration type 1 for base access
[    0.169792] bio: create slab <bio-0> at 0
[    0.169888] ACPI: Added _OSI(Module Device)
[    0.169893] ACPI: Added _OSI(Processor Device)
[    0.169896] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.169900] ACPI: Added _OSI(Processor Aggregator Device)
[    0.170147] ACPI: EC: Look up EC in DSDT
[    0.172055] ACPI: Executed 1 blocks of module-level executable AML code
[    0.174226] ACPI: Interpreter enabled
[    0.174232] ACPI: (supports S0 S5)
[    0.174246] ACPI: Using IOAPIC for interrupt routing
[    0.175937] ACPI: No dock devices found.
[    0.176020] HEST: Table not found.
[    0.176025] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.176097] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.176202] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.176207] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.176211] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.176215] pci_root PNP0A03:00: host bridge window [mem 0x40000000-0xffdfffff] (ignored)
[    0.176261] pci 0000:00:00.0: [8086:1237] type 0 class 0x000600
[    0.176628] pci 0000:00:01.0: [8086:7000] type 0 class 0x000601
[    0.177189] pci 0000:00:01.1: [8086:7111] type 0 class 0x000101
[    0.177586] pci 0000:00:01.1: reg 20: [io  0xd000-0xd00f]
[    0.177879] pci 0000:00:02.0: [80ee:beef] type 0 class 0x000300
[    0.179369] pci 0000:00:02.0: reg 10: [mem 0xe0000000-0xe1ffffff pref]
[    0.188633] pci 0000:00:03.0: [8086:100e] type 0 class 0x000200
[    0.189752] pci 0000:00:03.0: reg 10: [mem 0xf0000000-0xf001ffff]
[    0.191446] pci 0000:00:03.0: reg 18: [io  0xd010-0xd017]
[    0.195313] pci 0000:00:04.0: [80ee:cafe] type 0 class 0x000880
[    0.196548] pci 0000:00:04.0: reg 10: [io  0xd020-0xd03f]
[    0.197657] pci 0000:00:04.0: reg 14: [mem 0xf0400000-0xf07fffff]
[    0.198570] pci 0000:00:04.0: reg 18: [mem 0xf0800000-0xf0803fff pref]
[    0.201667] pci 0000:00:05.0: [8086:2415] type 0 class 0x000401
[    0.201777] pci 0000:00:05.0: reg 10: [io  0xd100-0xd1ff]
[    0.201854] pci 0000:00:05.0: reg 14: [io  0xd200-0xd23f]
[    0.202487] pci 0000:00:06.0: [106b:003f] type 0 class 0x000c03
[    0.203427] pci 0000:00:06.0: reg 10: [mem 0xf0804000-0xf0804fff]
[    0.208333] pci 0000:00:07.0: [8086:7113] type 0 class 0x000680
[    0.209031] pci 0000:00:0b.0: [8086:265c] type 0 class 0x000c03
[    0.209863] pci 0000:00:0b.0: reg 10: [mem 0xf0805000-0xf0805fff]
[    0.214814] pci 0000:00:0d.0: [8086:2829] type 0 class 0x000106
[    0.215351] pci 0000:00:0d.0: reg 10: [io  0xd240-0xd247]
[    0.217384] pci 0000:00:0d.0: reg 18: [io  0xd250-0xd257]
[    0.219209] pci 0000:00:0d.0: reg 20: [io  0xd260-0xd26f]
[    0.220048] pci 0000:00:0d.0: reg 24: [mem 0xf0806000-0xf0807fff]
[    0.221267] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.221880]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
[    0.226330] ACPI: PCI Interrupt Link [LNKA] (IRQs *5 9 10 11)
[    0.226520] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 9 10 *11)
[    0.226593] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 9 *10 11)
[    0.226734] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *9 10 11)
[    0.226906] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.226913] vgaarb: loaded
[    0.226917] vgaarb: bridge control possible 0000:00:02.0
[    0.227013] i2c-core: driver [aat2870] using legacy suspend method
[    0.227017] i2c-core: driver [aat2870] using legacy resume method
[    0.227102] SCSI subsystem initialized
[    0.228069] libata version 3.00 loaded.
[    0.228126] usbcore: registered new interface driver usbfs
[    0.228140] usbcore: registered new interface driver hub
[    0.228193] usbcore: registered new device driver usb
[    0.236603] PCI: Using ACPI for IRQ routing
[    0.236603] PCI: pci_cache_line_size set to 64 bytes
[    0.236603] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.236603] reserve RAM buffer: 000000003fff0000 - 000000003fffffff 
[    0.236603] NetLabel: Initializing
[    0.236603] NetLabel:  domain hash size = 128
[    0.236603] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.236603] NetLabel:  unlabeled traffic allowed by default
[    0.245251] AppArmor: AppArmor Filesystem Enabled
[    0.245283] pnp: PnP ACPI init
[    0.245304] ACPI: bus type pnp registered
[    0.245411] pnp 00:00: [bus 00-ff]
[    0.245418] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.245424] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.245429] pnp 00:00: [io  0x0d00-0xffff window]
[    0.245435] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.245441] pnp 00:00: [mem 0x40000000-0xffdfffff window]
[    0.245485] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.245508] pnp 00:01: [io  0x0060]
[    0.245514] pnp 00:01: [io  0x0064]
[    0.245551] pnp 00:01: [irq 1]
[    0.245585] pnp 00:01: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.245604] pnp 00:02: [io  0x0000-0x000f]
[    0.245609] pnp 00:02: [io  0x0080-0x008f]
[    0.245615] pnp 00:02: [io  0x00c0-0x00df]
[    0.245620] pnp 00:02: [dma 4]
[    0.245646] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.245720] pnp 00:03: [irq 12]
[    0.245753] pnp 00:03: Plug and Play ACPI device, IDs PNP0f03 (active)
[    0.245772] pnp 00:04: [io  0x0378-0x037f]
[    0.245778] pnp 00:04: [io  0x0778-0x077f]
[    0.245806] pnp 00:04: [irq 7]
[    0.245848] pnp 00:04: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.246467] pnp: PnP ACPI: found 5 devices
[    0.246472] ACPI: ACPI bus type pnp unregistered
[    0.254005] Switching to clocksource acpi_pm
[    0.254067] PCI: max bus depth: 0 pci_try_num: 1
[    0.254077] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.254081] pci_bus 0000:00: resource 1 [mem 0x00000000-0xfffffffff]
[    0.254117] NET: Registered protocol family 2
[    0.254178] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.254668] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.255359] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.255576] TCP: Hash tables configured (established 131072 bind 65536)
[    0.255580] TCP reno registered
[    0.255589] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.255598] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.255603] NET: Registered protocol family 1
[    0.255635] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    0.255668] pci 0000:00:01.0: Activating ISA DMA hang workarounds
[    0.255713] pci 0000:00:02.0: Boot video device
[    0.255792] pci 0000:00:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.312278] pci 0000:00:06.0: PCI INT A disabled
[    0.312411] pci 0000:00:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.312493] pci 0000:00:0b.0: PCI INT A disabled
[    0.312521] PCI: CLS 64 bytes, default 64
[    0.312686] platform rtc_cmos: registered platform RTC device (no PNP device found)
[    0.312980] audit: initializing netlink socket (disabled)
[    0.312995] type=2000 audit(1380327222.312:1): initialized
[    0.332419] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.334206] VFS: Disk quotas dquot_6.5.2
[    0.334251] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.334977] fuse init (API version 7.17)
[    0.335069] msgmni has been set to 1956
[    0.335657] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.335718] io scheduler noop registered
[    0.335722] io scheduler deadline registered
[    0.335750] io scheduler cfq registered (default)
[    0.335839] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.335854] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.335956] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.336079] ACPI: AC Adapter [AC] (on-line)
[    0.336127] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.336134] ACPI: Power Button [PWRF]
[    0.336202] input: Sleep Button as /devices/LNXSYSTM:00/LNXSLPBN:00/input/input1
[    0.336207] ACPI: Sleep Button [SLPF]
[    0.337097] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.337127] ACPI: Battery Slot [BAT0] (battery present)
[    0.337142] ERST: Table is not found!
[    0.337146] GHES: HEST is not enabled!
[    0.337279] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.338325] ACPI: Battery Slot [BAT0] (battery present)
[    0.402600] Freeing initrd memory: 13916k freed
[    0.476685] Linux agpgart interface v0.103
[    0.484894] brd: module loaded
[    0.488508] loop: module loaded
[    0.488662] ahci 0000:00:0d.0: version 3.0
[    0.488741] ahci 0000:00:0d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.488920] ahci: SSS flag set, parallel bus scan disabled
[    0.489191] ahci 0000:00:0d.0: AHCI 0001.0100 32 slots 1 ports 3 Gbps 0x1 impl SATA mode
[    0.489198] ahci 0000:00:0d.0: flags: 64bit ncq stag only ccc 
[    0.489877] scsi0 : ahci
[    0.489986] ata1: SATA max UDMA/133 abar m8192@0xf0806000 port 0xf0806100 irq 21
[    0.490055] ata_piix 0000:00:01.1: version 2.13
[    0.490944] scsi1 : ata_piix
[    0.491248] scsi2 : ata_piix
[    0.491308] ata2: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0xd000 irq 14
[    0.491315] ata3: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0xd008 irq 15
[    0.491780] Fixed MDIO Bus: probed
[    0.491815] tun: Universal TUN/TAP device driver, 1.6
[    0.491821] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.491884] PPP generic driver version 2.4.2
[    0.492159] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.492199] ehci_hcd 0000:00:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.492264] ehci_hcd 0000:00:0b.0: EHCI Host Controller
[    0.492319] ehci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    0.492918] ehci_hcd 0000:00:0b.0: irq 19, io mem 0xf0805000
[    0.504173] ehci_hcd 0000:00:0b.0: USB 2.0 started, EHCI 1.00
[    0.504646] hub 1-0:1.0: USB hub found
[    0.504655] hub 1-0:1.0: 8 ports detected
[    0.504779] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.504821] ohci_hcd 0000:00:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.504886] ohci_hcd 0000:00:06.0: OHCI Host Controller
[    0.505233] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 2
[    0.505326] ohci_hcd 0000:00:06.0: irq 22, io mem 0xf0804000
[    0.561403] hub 2-0:1.0: USB hub found
[    0.561439] hub 2-0:1.0: 8 ports detected
[    0.562273] uhci_hcd: USB Universal Host Controller Interface driver
[    0.562371] usbcore: registered new interface driver libusual
[    0.562425] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.656308] ata3.00: ATAPI: VBOX CD-ROM, 1.0, max UDMA/133
[    0.664260] ata3.00: configured for UDMA/33
[    1.126591] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.126603] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.126980] mousedev: PS/2 mouse device common for all mice
[    1.127552] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.128168] rtc_cmos rtc_cmos: rtc core: registered rtc_cmos as rtc0
[    1.128236] rtc0: alarms up to one day, 114 bytes nvram
[    1.128319] device-mapper: uevent: version 1.0.3
[    1.128498] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.128521] cpuidle: using governor ladder
[    1.128525] cpuidle: using governor menu
[    1.128528] EFI Variables Facility v0.08 2004-May-17
[    1.128672] TCP cubic registered
[    1.128760] NET: Registered protocol family 10
[    1.129110] NET: Registered protocol family 17
[    1.129117] Registering the dns_resolver key type
[    1.129596] PM: Hibernation image not present or could not be loaded.
[    1.129615] registered taskstats version 1
[    1.139148]   Magic number: 13:287:204
[    1.139282] rtc_cmos rtc_cmos: setting system clock to 2013-09-28 00:13:44 UTC (1380327224)
[    1.139329] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.139333] EDD information not available.
[    1.392452] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.392532] ata1.00: ATA-6: VBOX HARDDISK, 1.0, max UDMA/133
[    1.392537] ata1.00: 41943040 sectors, multi 128: LBA48 NCQ (depth 31/32)
[    1.392631] ata1.00: configured for UDMA/133
[    1.392976] scsi 0:0:0:0: Direct-Access     ATA      VBOX HARDDISK    1.0  PQ: 0 ANSI: 5
[    1.393149] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.393174] sd 0:0:0:0: [sda] 41943040 512-byte logical blocks: (21.4 GB/20.0 GiB)
[    1.393250] sd 0:0:0:0: [sda] Write Protect is off
[    1.393255] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.393288] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.393672] scsi 2:0:0:0: CD-ROM            VBOX     CD-ROM           1.0  PQ: 0 ANSI: 5
[    1.394286] sr0: scsi3-mmc drive: 32x/32x xa/form2 tray
[    1.394296] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.394839] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.395340] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.395621]  sda: sda1 sda2 < sda5 >
[    1.396775] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.397976] Freeing unused kernel memory: 924k freed
[    1.398095] Write protecting the kernel read-only data: 12288k
[    1.401461] Freeing unused kernel memory: 1588k freed
[    1.404058] Freeing unused kernel memory: 1188k freed
[    1.431235] udevd[91]: starting version 175
[    1.469340] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
[    1.469345] e1000: Copyright (c) 1999-2006 Intel Corporation.
[    1.469396] e1000 0000:00:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.504117] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    2.154837] e1000 0000:00:03.0: eth0: (PCI:33MHz:32-bit) 08:00:27:63:70:a0
[    2.154849] e1000 0000:00:03.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.200279] usb 2-1: new full-speed USB device number 2 using ohci_hcd
[    2.349235] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.349242] EXT4-fs (sda1): write access will be enabled during recovery
[    2.472472] input: VirtualBox USB Tablet as /devices/pci0000:00/0000:00:06.0/usb2/2-1/2-1:1.0/input/input3
[     2.472743] generic-usb 0003:80EE:0021.0001: input,hidraw0: USB HID v1.10  Mouse [VirtualBox USB Tablet] on usb-0000:00:06.0-1/input0
[    2.472948] usbcore: registered new interface driver usbhid
[    2.472953] usbhid: USB HID core driver
[    2.942833] EXT4-fs (sda1): orphan cleanup on readonly fs
[    2.942846] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 159522
[    2.943296] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 298862
[    2.943327] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 787487
[    2.943377] EXT4-fs (sda1): 3 orphan inodes deleted
[    2.943381] EXT4-fs (sda1): recovery complete
[    3.723281] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    4.711054] Adding 1046524k swap on /dev/sda5.  Priority:-1 extents:1 across:1046524k 
[    4.773376] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    4.883097] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.907429] udevd[357]: starting version 175
[    5.155233] lp: driver loaded but no devices found
[    5.400991] parport_pc 00:04: reported by Plug and Play ACPI
[    5.453059] piix4_smbus 0000:00:07.0: SMBus base address uninitialized - upgrade BIOS or use force_addr=0xaddr
[    5.470426] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input4
[    5.474570] vboxguest 0000:00:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    5.475455] input: Unspecified device as /devices/pci0000:00/0000:00:04.0/input/input5
[    5.476350] vboxguest: major 0, IRQ 20, I/O port d020, MMIO at 00000000f0400000 (size 0x400000)
[    5.476355] vboxguest: Successfully loaded version 4.2.18 (interface 0x00010004)
[    5.489550] [drm] Initialized drm 1.1.0 20060810
[    5.567098] Linux video capture interface: v2.00
[    5.587840] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_E4HD (0c45:6449)
[    5.591669] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.593909] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    5.593914] [drm] No driver support for vblank timestamp query.
[    5.593919] [drm] Initialized vboxvideo 1.0.0 20090303 for 0000:00:02.0 on minor 0
[     5.611984] type=1400 audit(1380327228.967:2): apparmor="STATUS"  operation="profile_load" name="/sbin/dhclient" pid=658  comm="apparmor_parser"
[    5.611998] type=1400  audit(1380327228.967:3): apparmor="STATUS" operation="profile_load"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=658  comm="apparmor_parser"
[    5.617740] type=1400  audit(1380327228.975:4): apparmor="STATUS" operation="profile_replace"  name="/sbin/dhclient" pid=644 comm="apparmor_parser"
[    5.618005]  type=1400 audit(1380327228.975:5): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=644  comm="apparmor_parser"
[    5.618166] type=1400  audit(1380327228.975:6): apparmor="STATUS" operation="profile_load"  name="/usr/lib/connman/scripts/dhclient-script" pid=644  comm="apparmor_parser"
[    5.618984] type=1400  audit(1380327228.975:7): apparmor="STATUS" operation="profile_replace"  name="/usr/lib/connman/scripts/dhclient-script" pid=658  comm="apparmor_parser"
[    5.658468] input: Laptop_Integrated_Webcam_E4HD as /devices/pci0000:00/0000:00:0b.0/usb1/1-1/1-1:1.0/input/input6
[    5.659733] usbcore: registered new interface driver uvcvideo
[    5.659738] USB Video Class driver (1.1.1)
[    5.677498] ppdev: user-space parallel port driver
[     5.759310] type=1400 audit(1380327229.115:8): apparmor="STATUS"  operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=706  comm="apparmor_parser"
[    5.759641] type=1400  audit(1380327229.115:9): apparmor="STATUS" operation="profile_load"  name="/usr/sbin/cupsd" pid=706 comm="apparmor_parser"
[    5.841438] Bluetooth: Core ver 2.16
[    5.841482] NET: Registered protocol family 31
[    5.841486] Bluetooth: HCI device and connection manager initialized
[    5.841491] Bluetooth: HCI socket layer initialized
[    5.841494] Bluetooth: L2CAP socket layer initialized
[    5.841502] Bluetooth: SCO socket layer initialized
[    5.926203] Bluetooth: RFCOMM TTY layer initialized
[    5.926210] Bluetooth: RFCOMM socket layer initialized
[    5.926214] Bluetooth: RFCOMM ver 1.11
[    6.009856] init: failsafe main process (677) killed by TERM signal
[    6.041681] snd_intel8x0 0000:00:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    6.045659] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.045664] Bluetooth: BNEP filters: protocol multicast
[    6.364164] intel8x0_measure_ac97_clock: measured 55996 usecs (6239 samples)
[    6.364169] intel8x0: measured clock 111418 rejected
[    6.408537] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
[    6.409499] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.409565] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[     6.422110] type=1400 audit(1380327229.779:10): apparmor="STATUS"  operation="profile_replace" name="/sbin/dhclient" pid=826  comm="apparmor_parser"
[    6.423529] type=1400  audit(1380327229.779:11): apparmor="STATUS" operation="profile_replace"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=826  comm="apparmor_parser"
[    6.706201] init: alsa-restore main process (872) terminated with status 19
[    6.724220] intel8x0_measure_ac97_clock: measured 56004 usecs (7200 samples)
[    6.724226] intel8x0: measured clock 128562 rejected
[    6.904349] vboxsf: Successfully loaded version 4.2.18 (interface 0x00010004)
[    7.084177] intel8x0_measure_ac97_clock: measured 55944 usecs (7200 samples)
[    7.084182] intel8x0: measured clock 128700 rejected
[    7.084186] intel8x0: clocking to 48000
[    7.211013] vesafb: mode is 640x480x32, linelength=2560, pages=0
[    7.211018] vesafb: scrolling: redraw
[    7.211022] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    7.211034] mtrr: your processor doesn't support write-combining
[    7.211176] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90001b00000, using 1216k, total 1216k
[    7.211882] Console: switching to colour frame buffer device 80x30
[    7.211894] fb0: VESA VGA frame buffer device
[    8.426171] init: plymouth-upstart-bridge main process (590) killed by TERM signal
[   10.128739] VBoxGuest: VBoxGuestCommonGuestCapsAcquire: pSession(0xffff88003a491e10), OR(0x0), NOT(0xffffffff), flags(0x0)
[   10.440880] VBoxGuest: VBoxGuestCommonGuestCapsAcquire: pSession(0xffff88003bb32410), OR(0x0), NOT(0xffffffff), flags(0x0)
[   16.709247] VBoxGuest: VBoxGuestCommonGuestCapsAcquire: pSession(0xffff88003bb33610), OR(0x0), NOT(0xffffffff), flags(0x0)
[   16.743457] VBoxGuest: VBoxGuestCommonGuestCapsAcquire: pSession(0xffff88003b38f010), OR(0x0), NOT(0xffffffff), flags(0x0)
[   16.790749] VBoxGuest: VBoxGuestCommonGuestCapsAcquire: pSession(0xffff88003c4da610), OR(0x0), NOT(0xffffffff), flags(0x0)
[   16.791853] VBoxGuest: VBoxGuestCommonGuestCapsAcquire: pSession(0xffff88003c4dae10), OR(0x0), NOT(0xffffffff), flags(0x0)
[   16.819531] VBoxGuest: VBoxGuestCommonGuestCapsAcquire: pSession(0xffff88003c4dae10), OR(0x0), NOT(0xffffffff), flags(0x0)
[   16.944067] eth0: no IPv6 routers present
[   17.322107] ISO 9660 Extensions: Microsoft Joliet Level 3
[   17.341334] ISO 9660 Extensions: RRIP_1991A
[   45.832621] VBoxGuest: VBoxGuestCommonGuestCapsAcquire: pSession(0xffff88003a491e10), OR(0x0), NOT(0xffffffff), flags(0x0)
[  129.519712] uvcvideo: Failed to resubmit video URB (-27).
[  129.519731] uvcvideo: Failed to resubmit video URB (-27).
[  129.519742] uvcvideo: Failed to resubmit video URB (-27).
[  129.519753] uvcvideo: Failed to resubmit video URB (-27).
[  129.519765] uvcvideo: Failed to resubmit video URB (-27).
[  202.290383] VBoxGuest: VBoxGuestCommonGuestCapsAcquire: pSession(0xffff8800230f6810), OR(0x0), NOT(0xffffffff), flags(0x0)
[  202.327261] VBoxGuest: VBoxGuestCommonGuestCapsAcquire: pSession(0xffff8800194da610), OR(0x0), NOT(0xffffffff), flags(0x0)
[  230.578361] uvcvideo: Failed to resubmit video URB (-27).
[  230.578386] uvcvideo: Failed to resubmit video URB (-27).
[  230.578408] uvcvideo: Failed to resubmit video URB (-27).
[  230.578429] uvcvideo: Failed to resubmit video URB (-27).
[  230.578450] uvcvideo: Failed to resubmit video URB (-27).
[  241.531366] VBoxGuest: VBoxGuestCommonGuestCapsAcquire: pSession(0xffff8800230f7410), OR(0x0), NOT(0xffffffff), flags(0x0)
[  241.575580] VBoxGuest: VBoxGuestCommonGuestCapsAcquire: pSession(0xffff8800230f7410), OR(0x0), NOT(0xffffffff), flags(0x0)
[  451.660236] uvcvideo: Failed to resubmit video URB (-27).
[  451.660236] uvcvideo: Failed to resubmit video URB (-27).
[  451.660236] uvcvideo: Failed to resubmit video URB (-27).
[  451.660236] uvcvideo: Failed to resubmit video URB (-27).
[  451.660236] uvcvideo: Failed to resubmit video URB (-27).
[  484.494190] uvcvideo: Failed to resubmit video URB (-27).
[  484.494216] uvcvideo: Failed to resubmit video URB (-27).
[  484.494238] uvcvideo: Failed to resubmit video URB (-27).
[  484.494260] uvcvideo: Failed to resubmit video URB (-27).
[  484.494282] uvcvideo: Failed to resubmit video URB (-27).
[  657.042589] uvcvideo: Failed to resubmit video URB (-27).
[  657.042614] uvcvideo: Failed to resubmit video URB (-27).
[  657.042636] uvcvideo: Failed to resubmit video URB (-27).
[  657.042657] uvcvideo: Failed to resubmit video URB (-27).
[  657.042678] uvcvideo: Failed to resubmit video URB (-27).
[  686.472628] uvcvideo: Failed to resubmit video URB (-27).
[  686.472654] uvcvideo: Failed to resubmit video URB (-27).
[  686.472675] uvcvideo: Failed to resubmit video URB (-27).
[  686.472696] uvcvideo: Failed to resubmit video URB (-27).
[  686.472717] uvcvideo: Failed to resubmit video URB (-27).
[  697.830125] uvcvideo: Failed to resubmit video URB (-27).
[  697.830151] uvcvideo: Failed to resubmit video URB (-27).
[  697.830172] uvcvideo: Failed to resubmit video URB (-27).
[  697.830193] uvcvideo: Failed to resubmit video URB (-27).
[  697.830214] uvcvideo: Failed to resubmit video URB (-27).
[  725.592971] uvcvideo: Failed to resubmit video URB (-27).
[  725.592997] uvcvideo: Failed to resubmit video URB (-27).
[  725.593019] uvcvideo: Failed to resubmit video URB (-27).
[  725.593040] uvcvideo: Failed to resubmit video URB (-27).
[  725.593061] uvcvideo: Failed to resubmit video URB (-27).
[  764.623892] uvcvideo: Failed to resubmit video URB (-27).
[  764.623918] uvcvideo: Failed to resubmit video URB (-27).
[  764.623940] uvcvideo: Failed to resubmit video URB (-27).
[  764.623961] uvcvideo: Failed to resubmit video URB (-27).
[  764.623982] uvcvideo: Failed to resubmit video URB (-27).
[ 1028.419333] uvcvideo: Failed to resubmit video URB (-27).
[ 1028.419343] uvcvideo: Failed to resubmit video URB (-27).
[ 1028.419351] uvcvideo: Failed to resubmit video URB (-27).
[ 1028.419360] uvcvideo: Failed to resubmit video URB (-27).
[ 1028.419368] uvcvideo: Failed to resubmit video URB (-27).
[ 1038.821464] uvcvideo: Failed to resubmit video URB (-27).
[ 1038.821554] uvcvideo: Failed to resubmit video URB (-27).
[ 1038.821612] uvcvideo: Failed to resubmit video URB (-27).
[ 1038.821660] uvcvideo: Failed to resubmit video URB (-27).
[ 1038.821729] uvcvideo: Failed to resubmit video URB (-27).
[ 2323.178941] VBoxGuest: VBoxGuestCommonGuestCapsAcquire: pSession(0xffff880036e06c10), OR(0x0), NOT(0xffffffff), flags(0x0)
[ 2326.571848] uvcvideo: Failed to resubmit video URB (-27).
[ 2326.571858] uvcvideo: Failed to resubmit video URB (-27).
[ 2326.571867] uvcvideo: Failed to resubmit video URB (-27).
[ 2326.571875] uvcvideo: Failed to resubmit video URB (-27).
[ 2326.571883] uvcvideo: Failed to resubmit video URB (-27).
[ 2338.466362] VBoxGuest: VBoxGuestCommonGuestCapsAcquire: pSession(0xffff880036e06c10), OR(0x0), NOT(0xffffffff), flags(0x0)
[ 2619.262723] uvcvideo: Failed to resubmit video URB (-27).
[ 2619.262745] uvcvideo: Failed to resubmit video URB (-27).
[ 2619.262763] uvcvideo: Failed to resubmit video URB (-27).
[ 2619.262783] uvcvideo: Failed to resubmit video URB (-27).
[ 2619.262810] uvcvideo: Failed to resubmit video URB (-27).
[ 2731.300355] uvcvideo: Failed to resubmit video URB (-27).
[ 2731.300372] uvcvideo: Failed to resubmit video URB (-27).
[ 2731.300386] uvcvideo: Failed to resubmit video URB (-27).
[ 2731.300398] uvcvideo: Failed to resubmit video URB (-27).
[ 2731.300411] uvcvideo: Failed to resubmit video URB (-27).
[ 3052.383190] uvcvideo: Failed to resubmit video URB (-27).
[ 3052.383201] uvcvideo: Failed to resubmit video URB (-27).
[ 3052.383209] uvcvideo: Failed to resubmit video URB (-27).
[ 3052.383217] uvcvideo: Failed to resubmit video URB (-27).
[ 3052.383225] uvcvideo: Failed to resubmit video URB (-27).
```

---

### Post by mörgæs on 2013-09-28
Hi, welcome to the fora.

Guvcview 1.5.3 seems to indicate that you are on Buntu 12.04, which is a fairly old release considered how new the computer is.

You might find better hardware support in later releases. How does the webcam work in a live boot of 13.10 beta?

---

### Post by miguel8 on 2013-09-28
> **mörgæs said:**
> Hi, welcome to the fora.

Guvcview 1.5.3 seems to indicate that you are on Buntu 12.04, which is a fairly old release considered how new the computer is.

You might find better hardware support in later releases. How does the webcam work in a live boot of 13.10 beta?


Thanks for your suggestion. I tried installing 13.10.  I actually got some results with guvcviewer this time, unfortunately they aren't much better.

Here is what I tried:



retried cheese. The result was the same, My webcam's  light turns on but nothing is shown on screen

```
miguel@miguel-VirtualBox:~$ cheese

(cheese:6434): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1605:38: '' is not a valid color name

(cheese:6434): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1605:38: '' is not a valid color name

```

I tried gstreamer-properties. The result was the same.

output ```
miguel@miguel-VirtualBox:~$ gstreamer-properties

(gstreamer-properties:6531): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1605:38: '' is not a valid color name

(gstreamer-properties:6531): Gtk-WARNING **: Unknown property: GtkDialog.has-separator

(gstreamer-properties:6531): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'


```


Lastly I tried guvcviewer. The only setting that seemed to work was mjpg, but the picture only output every few frames with garbage in between. In addition to that, I tried using all of the codecs listed under the video settings. The result seems to be the same no matter which codec I choose, although some codecs seem to run faster than others. Here is the terminal output.

```
miguel@miguel-VirtualBox:~$ guvcview
guvcview 1.7.1
file guvcview_video.mkv has extension type 1
file guvcview_image.jpg has extension type 0

(guvcview:6769): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1605:38: '' is not a valid color name
file guvcview_image.jpg has extension type 0
Video file suffix detected: 1
Image file suffix detected: 0
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround71
ALSA lib setup.c:548:(add_elem) Cannot obtain info for CTL elem (MIXER,'IEC958 Playback Default',0,0,0): No such file or directory
ALSA lib setup.c:548:(add_elem) Cannot obtain info for CTL elem (MIXER,'IEC958 Playback Default',0,0,0): No such file or directory
ALSA lib setup.c:548:(add_elem) Cannot obtain info for CTL elem (MIXER,'IEC958 Playback Default',0,0,0): No such file or directory
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_dmix.c:961:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
video device: /dev/video0 
Init. Laptop_Integrated_Webcam_E4HD (location: usb-0000:00:0b.0-1)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/10, 1/5, 
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
vid:0c45 
pid:6449 
driver:uvcvideo
checking format: 1196444237
VIDIOC_G_COMP:: Inappropriate ioctl for device
fps is set to 1/30
drawing controls

fps is set to 1/30
Checking video mode 1280x720@32bpp : OK 
^Cwrite /home/miguel/.config/guvcview/video0 OK
free controls
cleaned allocations - 100%
Closing portaudio ...OK
Closing GTK... OK


```


I did notice the Inappropriate ioctl for device message in the terminal output. Could that have something to do with it?

---

### Post by mörgæs on 2013-09-28
I can't answer that, sorry.

Do you feel like discussing the bug in the [development forum]("http://ubuntuforums.org/forumdisplay.php?f=427") and after that perhaps report it in Launchpad? A bug report based upon 13.10 is likely to get more attention than 12.04.

---

