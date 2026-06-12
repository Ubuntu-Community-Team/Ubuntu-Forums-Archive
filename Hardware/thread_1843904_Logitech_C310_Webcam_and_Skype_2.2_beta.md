---
title: "Logitech C310 Webcam and Skype 2.2 beta"
date: 2011-09-14
forum: Hardware
---

### Post by Robinfox88 on 2011-09-14
I've searched the forums, and I've also scoured the internet at large to find out what the problem is, but no luck.

And the problem is that every few seconds or sometimes every few minutes, my webcam will freeze, both in the preview that I see, and for the person receiving the video stream, the freeze also happens in cheese, and happens in both 10.10 and 11.04, although it has to be noted, not as bad in 10.10 as it was in 11.04, but it still makes video calling a un-enjoyable experience.

My laptop is a Dell Inspiron 1300 with a 1.6GHz dothan Pentium-m, 1GB of RAM, and 320GB HDD and DVD RW drive. The processor is never maxed out when video calling and sits at around 65%, and RAM usage is as low as 190MB with 15MB or less of swap in use at any one time.

I've tried everything that I can think of, and looked all over for a solution, but nothing fits my problem 100%, and it's really frustrating.

I need this to work properly, as the person I'm video calling is my girlfriend, and seeing as we're in a long distance relationship, being able to Skype each other is massively important.

I was beginning to suspect Skype until earlier today when I tested with cheese, but because it happens there as well, I'm beginning to suspect that it's either the laptop, which I wouldn't have thought so seeing as it's not being overly stressed when video calling, or it's Ubuntu, as on the same laptop, this problem never occurred in Windows XP, although aside from being Windows, it had other problems, noticeably the wireless connection kept dropping every few seconds, which oddly enough doesn't happen in Ubuntu.

I'm not entirely sure if this is in the right place, and I sincerely apologise for if it isn't, but this seemed to be the correct place when I decided to post about this. Thanks in advance to anyone who tries to help me on this, it's very much appreciated. :)

---

### Post by diasf on 2011-09-14
No weird USB messages on dmesg?

---

### Post by Robinfox88 on 2011-09-14
> **diasf said:**
> No weird USB messages on dmesg?

I've run the command, but I'm not entirely sure what I'm looking for, there are no obvious error messages relating to USB atm, but again, my knowledge of this stuff is fairly limited, so here below is what I think is the relevant section of dmesg, and I'll let someone analyse it for me ^__^ 

[    1.305890] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.305951] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.305994] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.306005] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.306107] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.306202] ehci_hcd 0000:00:1d.7: debug port 1
[    1.309865] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.313910] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xb0000000
[    1.320004] ata2: port disabled. ignoring.
[    1.336004] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.336004] hub 1-0:1.0: USB hub found
[    1.336004] hub 1-0:1.0: 8 ports detected
[    1.336004] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.336004] uhci_hcd: USB Universal Host Controller Interface driver
[    1.336004] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.336004] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.336004] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.336004] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.336004] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
[    1.336004] hub 2-0:1.0: USB hub found
[    1.336004] hub 2-0:1.0: 2 ports detected
[    1.336004]   alloc irq_desc for 17 on node -1
[    1.336004]   alloc kstat_irqs on node -1
[    1.336004] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.336004] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.336004] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.336004] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.336004] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000bf60
[    1.336004] hub 3-0:1.0: USB hub found
[    1.336004] hub 3-0:1.0: 2 ports detected
[    1.336004]   alloc irq_desc for 18 on node -1
[    1.336004]   alloc kstat_irqs on node -1
[    1.336004] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.336004] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.336004] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.336004] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.336004] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bf40
[    1.336004] hub 4-0:1.0: USB hub found
[    1.336004] hub 4-0:1.0: 2 ports detected
[    1.336004] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.336004] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.336004] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.336004] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.336004] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000bf20
[    1.336004] hub 5-0:1.0: USB hub found
[    1.336004] hub 5-0:1.0: 2 ports detected
[    1.336004] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12

There are 3 USB 2.0 480mb/s ports on the laptop, and all three produce the same problem with the webcam, all other USB devices work without a problem, and I've not noticed this happen with any more frequency with other USB devices being used at the same time as without, as in, it's the same frequency of freezing no matter what else the computer is doing, or what is plugged into the laptop, it never happened in Windows XP, however, because of the terrible connection strength with the wireless, and just because it's Windows, I moved to Ubuntu, and so far, this has been the only problem. Everything else has been perfect.

I will compare the outputs at different times especially when it freezes, and if I notice anything different, I'll update, but I'm not entirely sure if what I'll find will be relevant to the problem.

And thank you for your time, it's much appreciated :)

---

### Post by Robinfox88 on 2011-09-14
The camera froze again while viewing the stream from the camera in skype, same old same old, but when I ran dmesg again when it froze this showed up at the end of the output;

[ 1312.537396] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 1320.192290] usb 1-5: new high speed USB device using ehci_hcd and address 2
[ 1320.635778] Linux video capture interface: v2.00
[ 1320.684008] uvcvideo: Found UVC 1.00 device <unnamed> (046d:081b)
[ 1320.780199] input: UVC Camera (046d:081b) as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input8
[ 1320.780360] usbcore: registered new interface driver uvcvideo
[ 1320.780366] USB Video Class driver (v0.1.0)
[ 1321.784283] 2:3:1: cannot get freq at ep 0x86
[ 1321.948216] usbcore: registered new interface driver snd-usb-audio
[ 1509.852341] Skipping EDID probe due to cached edid
[ 1634.976411] Skipping EDID probe due to cached edid
[ 1762.800351] Skipping EDID probe due to cached edid
[ 1890.816365] Skipping EDID probe due to cached edid
[ 2326.551204] uvcvideo: Failed to resubmit video URB (-27).
[ 2326.551204] uvcvideo: Failed to resubmit video URB (-27).
[ 2326.551204] uvcvideo: Failed to resubmit video URB (-27).
[ 2326.551204] uvcvideo: Failed to resubmit video URB (-27).
[ 2326.551204] uvcvideo: Failed to resubmit video URB (-27).

This has got me intrigued, I'm wondering if when the camera refreshes itself, it can't shut down the feed and restart it properly? There isn't any problem with the camera itself, but in Windows occasionally, the camera will freeze there, but that happens very very rarely, maybe what causes it to freeze in Windows is amplified when in Linux due to a bug in the UVC driver?
This is an uneducated guess by someone who is still learning Linux, but that's my theory so far, maybe someone who knows more than me can give a better answer :D

---

### Post by diasf on 2011-09-14
dmesg is a big system log. (the command prints it). 
The first number, between [] is the time that happened (0 being when the pc booted). So all those messages happened on boot process. I was expecting something like:

[32232.020093] usb 7-1: reset full speed USB device using ohci_hcd and address 2

this is from my own log.. I noticed that sometimes my external drives just reset the connection, giving messages like: 

Sep  9 11:07:01 dalaran kernel: [66666.128083] usb 1-7: reset high speed USB device using ehci_hcd and address 5

So what I was thinking is that an usb reset might crash the camera.

---

### Post by Robinfox88 on 2011-09-14
> **diasf said:**
> dmesg is a big system log. (the command prints it). 
The first number, between [] is the time that happened (0 being when the pc booted). So all those messages happened on boot process. I was expecting something like:

[32232.020093] usb 7-1: reset full speed USB device using ohci_hcd and address 2

this is from my own log.. I noticed that sometimes my external drives just reset the connection, giving messages like: 

Sep  9 11:07:01 dalaran kernel: [66666.128083] usb 1-7: reset high speed USB device using ehci_hcd and address 5

So what I was thinking is that an usb reset might crash the camera.

Well, here's as much of dmesg as I can get from terminal, as I think that rather than me trying to second guess how much of it you need, I'll post as much as I can get from it. ^___^

[    0.167027] pci 0000:02:00.0: reg 10: [mem 0xdfbfe000-0xdfbfffff]
[    0.167177] pci 0000:02:00.0: supports D1 D2
[    0.167183] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.167196] pci 0000:02:00.0: PME# disabled
[    0.167310] pci 0000:02:03.0: reg 10: [mem 0xdfbfd000-0xdfbfdfff]
[    0.167493] pci 0000:02:03.0: PME# supported from D0 D3hot D3cold
[    0.167507] pci 0000:02:03.0: PME# disabled
[    0.167661] pci 0000:00:1e.0: PCI bridge to [bus 02-02] (subtractive decode)
[    0.167675] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.167689] pci 0000:00:1e.0:   bridge window [mem 0xdfb00000-0xdfbfffff]
[    0.167710] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.167718] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.167726] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.167781] pci_bus 0000:00: on NUMA node 0
[    0.167792] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.168000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.168000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.168000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.176000] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.176000] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.176000] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[    0.176000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)
[    0.176000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.176000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.176000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.176000] HEST: Table is not found!
[    0.176000] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.176000] vgaarb: loaded
[    0.176000] SCSI subsystem initialized
[    0.176000] libata version 3.00 loaded.
[    0.176000] usbcore: registered new interface driver usbfs
[    0.176000] usbcore: registered new interface driver hub
[    0.176000] usbcore: registered new device driver usb
[    0.176000] ACPI: WMI: Mapper loaded
[    0.176000] PCI: Using ACPI for IRQ routing
[    0.176000] PCI: pci_cache_line_size set to 64 bytes
[    0.176000] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.176000] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
[    0.176000] reserve RAM buffer: 000000003f7d3800 - 000000003fffffff 
[    0.176000] NetLabel: Initializing
[    0.176000] NetLabel:  domain hash size = 128
[    0.176000] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.176000] NetLabel:  unlabeled traffic allowed by default
[    0.176000] hpet clockevent registered
[    0.176000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.176000] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.176000] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.180041] Switching to clocksource tsc
[    0.205285] AppArmor: AppArmor Filesystem Enabled
[    0.205285] pnp: PnP ACPI init
[    0.205285] ACPI: bus type pnp registered
[    0.279924] pnp 00:02: disabling [io  0x1000-0x1005] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.279924] pnp 00:02: disabling [io  0x1008-0x100f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.279924] pnp 00:03: disabling [io  0x1006-0x1007] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.279924] pnp 00:03: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.279924] pnp 00:03: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.279924] pnp: PnP ACPI: found 11 devices
[    0.279924] ACPI: ACPI bus type pnp unregistered
[    0.279924] PnPBIOS: Disabled by ACPI PNP
[    0.279924] system 00:00: [mem 0x00000000-0x0009fbff] could not be reserved
[    0.279924] system 00:00: [mem 0x0009fc00-0x0009ffff] could not be reserved
[    0.279924] system 00:00: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.279924] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.279924] system 00:00: [mem 0x00100000-0x3f7d37ff] could not be reserved
[    0.279924] system 00:00: [mem 0x3f7d3800-0x3f7fffff] has been reserved
[    0.279924] system 00:00: [mem 0x3f800000-0x3fffffff] has been reserved
[    0.279924] system 00:00: [mem 0xfeda0000-0xfedfffff] has been reserved
[    0.279924] system 00:00: [mem 0xffb00000-0xffffffff] has been reserved
[    0.279924] system 00:00: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.279924] system 00:00: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.279924] system 00:00: [mem 0xfed20000-0xfed9ffff] has been reserved
[    0.279924] system 00:00: [mem 0xf0000000-0xf0003fff] has been reserved
[    0.279924] system 00:00: [mem 0xf0004000-0xf0004fff] has been reserved
[    0.279924] system 00:00: [mem 0xf0005000-0xf0005fff] has been reserved
[    0.279924] system 00:00: [mem 0xf0006000-0xf0006fff] has been reserved
[    0.279924] system 00:00: [mem 0xf0008000-0xf000bfff] has been reserved
[    0.279924] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.279924] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.279924] system 00:03: [io  0xf400-0xf4fe] has been reserved
[    0.279924] system 00:03: [io  0x1080-0x10bf] has been reserved
[    0.279924] system 00:03: [io  0x10c0-0x10df] has been reserved
[    0.279924] system 00:03: [io  0x10e0-0x10ff] has been reserved
[    0.279924] system 00:08: [io  0x0900-0x090f] has been reserved
[    0.279924] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.279924] system 00:08: [io  0x0920-0x092f] has been reserved
[    0.279924] system 00:08: [io  0x0930-0x093f] has been reserved
[    0.279924] system 00:08: [io  0x0940-0x097f] has been reserved
[    0.373761] pci 0000:00:1c.0: BAR 14: assigned [mem 0x40000000-0x401fffff]
[    0.373774] pci 0000:00:1c.0: BAR 15: assigned [mem 0x40200000-0x403fffff 64bit pref]
[    0.373783] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.373791] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
[    0.373802] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.373819] pci 0000:00:1c.0:   bridge window [mem 0x40000000-0x401fffff]
[    0.373834] pci 0000:00:1c.0:   bridge window [mem 0x40200000-0x403fffff 64bit pref]
[    0.373855] pci 0000:00:1c.3: PCI bridge to [bus 0c-0d]
[    0.373865] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.373882] pci 0000:00:1c.3:   bridge window [mem 0xdfc00000-0xdfdfffff]
[    0.373897] pci 0000:00:1c.3:   bridge window [mem 0xd0000000-0xd01fffff 64bit pref]
[    0.373919] pci 0000:00:1e.0: PCI bridge to [bus 02-02]
[    0.373924] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.373942] pci 0000:00:1e.0:   bridge window [mem 0xdfb00000-0xdfbfffff]
[    0.373955] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.374015]   alloc irq_desc for 16 on node -1
[    0.374021]   alloc kstat_irqs on node -1
[    0.374041] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.374058] pci 0000:00:1c.0: setting latency timer to 64
[    0.374086]   alloc irq_desc for 19 on node -1
[    0.374091]   alloc kstat_irqs on node -1
[    0.374101] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.374114] pci 0000:00:1c.3: setting latency timer to 64
[    0.374135] pci 0000:00:1e.0: setting latency timer to 64
[    0.374148] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.374155] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.374162] pci_bus 0000:0b: resource 0 [io  0x2000-0x2fff]
[    0.374169] pci_bus 0000:0b: resource 1 [mem 0x40000000-0x401fffff]
[    0.374176] pci_bus 0000:0b: resource 2 [mem 0x40200000-0x403fffff 64bit pref]
[    0.374184] pci_bus 0000:0c: resource 0 [io  0xd000-0xdfff]
[    0.374190] pci_bus 0000:0c: resource 1 [mem 0xdfc00000-0xdfdfffff]
[    0.374198] pci_bus 0000:0c: resource 2 [mem 0xd0000000-0xd01fffff 64bit pref]
[    0.374205] pci_bus 0000:02: resource 1 [mem 0xdfb00000-0xdfbfffff]
[    0.374212] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.374219] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
[    0.374338] NET: Registered protocol family 2
[    0.374544] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.375239] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.375916] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.375916] TCP: Hash tables configured (established 131072 bind 65536)
[    0.375916] TCP reno registered
[    0.375916] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.375916] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.375916] NET: Registered protocol family 1
[    0.375916] pci 0000:00:02.0: Boot video device
[    0.375916] PCI: CLS 64 bytes, default 64
[    0.375916] cpufreq-nforce2: No nForce2 chipset.
[    0.375916] Scanning for low memory corruption every 60 seconds
[    0.375916] audit: initializing netlink socket (disabled)
[    0.375916] type=2000 audit(1316013936.368:1): initialized
[    0.407911] Trying to unpack rootfs image as initramfs...
[    0.447753] highmem bounce pool size: 64 pages
[    0.447773] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.450585] VFS: Disk quotas dquot_6.5.2
[    0.450585] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.450585] fuse init (API version 7.14)
[    0.450585] msgmni has been set to 1709
[    1.217899] Freeing initrd memory: 10552k freed
[    1.248536] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.248549] io scheduler noop registered
[    1.248555] io scheduler deadline registered
[    1.248606] io scheduler cfq registered (default)
[    1.248952] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.249079]   alloc irq_desc for 40 on node -1
[    1.249086]   alloc kstat_irqs on node -1
[    1.249127] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    1.249417] pcieport 0000:00:1c.3: setting latency timer to 64
[    1.249532]   alloc irq_desc for 41 on node -1
[    1.249537]   alloc kstat_irqs on node -1
[    1.249559] pcieport 0000:00:1c.3: irq 41 for MSI/MSI-X
[    1.249866] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.250066] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.250524] ACPI: AC Adapter [AC] (off-line)
[    1.250524] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.250524] ACPI: Lid Switch [LID]
[    1.250524] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    1.250524] ACPI: Power Button [PBTN]
[    1.250524] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    1.250524] ACPI: Sleep Button [SBTN]
[    1.250524] ACPI: acpi_idle registered with cpuidle
[    1.250524] Marking TSC unstable due to TSC halts in idle
[    1.264951] Switching to clocksource hpet
[    1.267474] thermal LNXTHERM:01: registered as thermal_zone0
[    1.267496] ACPI: Thermal Zone [THM] (37 C)
[    1.272841] ERST: Table is not found!
[    1.272841] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.276061] brd: module loaded
[    1.276061] loop: module loaded
[    1.276061] ata_piix 0000:00:1f.1: version 2.13
[    1.276061] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.276061] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.276061] isapnp: Scanning for PnP cards...
[    1.300032] scsi0 : ata_piix
[    1.300249] scsi1 : ata_piix
[    1.304551] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    1.304560] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    1.305472] Fixed MDIO Bus: probed
[    1.305563] PPP generic driver version 2.4.2
[    1.305690] tun: Universal TUN/TAP device driver, 1.6
[    1.305696] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.305890] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.305951] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.305994] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.306005] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.306107] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.306202] ehci_hcd 0000:00:1d.7: debug port 1
[    1.309865] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.313910] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xb0000000
[    1.320004] ata2: port disabled. ignoring.
[    1.336004] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.336004] hub 1-0:1.0: USB hub found
[    1.336004] hub 1-0:1.0: 8 ports detected
[    1.336004] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.336004] uhci_hcd: USB Universal Host Controller Interface driver
[    1.336004] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.336004] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.336004] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.336004] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.336004] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
[    1.336004] hub 2-0:1.0: USB hub found
[    1.336004] hub 2-0:1.0: 2 ports detected
[    1.336004]   alloc irq_desc for 17 on node -1
[    1.336004]   alloc kstat_irqs on node -1
[    1.336004] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.336004] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.336004] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.336004] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.336004] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000bf60
[    1.336004] hub 3-0:1.0: USB hub found
[    1.336004] hub 3-0:1.0: 2 ports detected
[    1.336004]   alloc irq_desc for 18 on node -1
[    1.336004]   alloc kstat_irqs on node -1
[    1.336004] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.336004] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.336004] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.336004] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.336004] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bf40
[    1.336004] hub 4-0:1.0: USB hub found
[    1.336004] hub 4-0:1.0: 2 ports detected
[    1.336004] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.336004] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.336004] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.336004] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.336004] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000bf20
[    1.336004] hub 5-0:1.0: USB hub found
[    1.336004] hub 5-0:1.0: 2 ports detected
[    1.336004] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.336004] i8042.c: Warning: Keylock active.
[    1.354996] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.355012] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.355278] mice: PS/2 mouse device common for all mice
[    1.355669] rtc_cmos 00:06: RTC can wake from S4
[    1.355773] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.355903] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.356004] device-mapper: uevent: version 1.0.3
[    1.356004] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.356004] device-mapper: multipath: version 1.1.1 loaded
[    1.356004] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.356004] EISA: Probing bus 0 at eisa.0
[    1.356004] Cannot allocate resource for EISA slot 1
[    1.356004] Cannot allocate resource for EISA slot 2
[    1.356004] EISA: Detected 0 cards.
[    1.356004] cpuidle: using governor ladder
[    1.356004] cpuidle: using governor menu
[    1.356004] TCP cubic registered
[    1.356004] NET: Registered protocol family 10
[    1.356004] lo: Disabled Privacy Extensions
[    1.356004] NET: Registered protocol family 17
[    1.356004] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.440004] isapnp: No Plug & Play device found
[    1.560928] Using IPI No-Shortcut mode
[    1.560928] PM: Resume from disk failed.
[    1.560928] registered taskstats version 1
[    1.561245]   Magic number: 11:36:437
[    1.561513] rtc_cmos 00:06: setting system clock to 2011-09-14 15:25:37 UTC (1316013937)
[    1.561522] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.561526] EDD information not available.
[    1.566696] ACPI: Battery Slot [BAT0] (battery present)
[    1.651733] ata1.00: ATA-8: WDC WD3200BEVE-00A0HT0, 11.01A11, max UDMA/100
[    1.651742] ata1.00: 625142448 sectors, multi 8: LBA48 
[    1.651843] ata1.01: ATAPI: SONY DVD+/-RW DW-Q58A, UDS1, max UDMA/33
[    1.665777] ata1.00: configured for UDMA/100
[    1.680993] ata1.01: configured for UDMA/33
[    1.681884] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVE-0 11.0 PQ: 0 ANSI: 5
[    1.682229] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.682552] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.682552] sd 0:0:0:0: [sda] Write Protect is off
[    1.682552] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.682552] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.682954]  sda: sda1 sda2 <
[    1.691776] scsi 0:0:1:0: CD-ROM            SONY     DVD+-RW DW-Q58A  UDS1 PQ: 0 ANSI: 5
[    1.722523]  sda5 >
[    1.723586] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.725865] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.725874] Uniform CD-ROM driver Revision: 3.20
[    1.726082] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.726193] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.726320] Freeing unused kernel memory: 688k freed
[    1.727332] Write protecting the kernel text: 4944k
[    1.727425] Write protecting the kernel read-only data: 1976k
[    1.744011] udev[69]: starting version 163
[    2.000008] b44 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.016109] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    2.016129] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    2.016149] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    2.056317] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[    2.056684] b44: b44.c:v2.0
[    2.077911] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:14:22:ac:8f:95
[    2.192004] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   12.424158] Adding 3069948k swap on /dev/sda5.  Priority:-1 extents:1 across:3069948k 
[   12.452731] udev[376]: starting version 163
[   12.567018] lp: driver loaded but no devices found
[   12.568576] intel_rng: FWH not detected
[   12.681450] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input4
[   12.681622] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   12.681668] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   12.744009] lib80211: common routines for IEEE802.11 drivers
[   12.744009] lib80211_crypt: registered algorithm 'NULL'
[   12.836010] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   12.938482] Linux agpgart interface v0.103
[   12.976010] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[   12.976010] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   13.049864] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   13.100005] cfg80211: Calling CRDA to update world regulatory domain
[   13.140012] libipw: 802.11 data/management/control stack, git-1.1.13
[   13.140012] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   13.183671] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.200008] cfg80211: World regulatory domain updated:
[   13.200008]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.200008]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.200008]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.200008]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.200008]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.200008]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.213060] type=1400 audit(1316013949.150:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=635 comm="apparmor_parser"
[   13.214711] type=1400 audit(1316013949.150:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=635 comm="apparmor_parser"
[   13.215596] type=1400 audit(1316013949.150:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=635 comm="apparmor_parser"
[   13.219787] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   13.219799] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   13.220011] ipw2200 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.224013] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   13.256011] [drm] Initialized drm 1.1.0 20060810
[   13.440005] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.440005] i915 0000:00:02.0: setting latency timer to 64
[   13.453777] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
[   13.460008] [drm] set up 7M of stolen space
[   13.508005] composite sync not supported
[   13.508005] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   13.508005] [drm] initialized overlay support
[   14.200011] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x200000/0x0
[   14.204011] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.228980] type=1400 audit(1316013950.166:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=846 comm="apparmor_parser"
[   14.234756] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[   14.244008] type=1400 audit(1316013950.178:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=847 comm="apparmor_parser"
[   14.244008] type=1400 audit(1316013950.178:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=847 comm="apparmor_parser"
[   14.244008] type=1400 audit(1316013950.178:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=847 comm="apparmor_parser"
[   14.292007] type=1400 audit(1316013950.226:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=849 comm="apparmor_parser"
[   14.312008] type=1400 audit(1316013950.246:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=849 comm="apparmor_parser"
[   14.316011] type=1400 audit(1316013950.250:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=849 comm="apparmor_parser"
[   14.460330] Skipping EDID probe due to cached edid
[   14.854374] Console: switching to colour frame buffer device 160x50
[   14.859302] fb0: inteldrmfb frame buffer device
[   14.859307] drm: registered panic notifier
[   14.864009] Slow work thread pool: Starting up
[   14.864657] Slow work thread pool: Ready
[   14.864694] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   14.864842] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.864984]   alloc irq_desc for 42 on node -1
[   14.864991]   alloc kstat_irqs on node -1
[   14.865028] HDA Intel 0000:00:1b.0: irq 42 for MSI/MSI-X
[   14.865116] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.899996] lib80211_crypt: registered algorithm 'TKIP'
[   14.991407] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   14.992005] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   15.080272] Skipping EDID probe due to cached edid
[   15.109565] ppdev: user-space parallel port driver
[   15.829790] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[   16.016594] Skipping EDID probe due to cached edid
[   16.496660] Skipping EDID probe due to cached edid
[   17.724014] Skipping EDID probe due to cached edid
[   18.208442] Skipping EDID probe due to cached edid
[   18.332503] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[   18.688258] Skipping EDID probe due to cached edid
[   19.168365] Skipping EDID probe due to cached edid
[   20.420311] Skipping EDID probe due to cached edid
[   21.032260] Skipping EDID probe due to cached edid
[   24.856041] eth1: no IPv6 routers present
[   25.188392] Skipping EDID probe due to cached edid
[ 1283.044010] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 1312.537396] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 1320.192290] usb 1-5: new high speed USB device using ehci_hcd and address 2
[ 1320.635778] Linux video capture interface: v2.00
[ 1320.684008] uvcvideo: Found UVC 1.00 device <unnamed> (046d:081b)
[ 1320.780199] input: UVC Camera (046d:081b) as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input8
[ 1320.780360] usbcore: registered new interface driver uvcvideo
[ 1320.780366] USB Video Class driver (v0.1.0)
[ 1321.784283] 2:3:1: cannot get freq at ep 0x86
[ 1321.948216] usbcore: registered new interface driver snd-usb-audio
[ 1509.852341] Skipping EDID probe due to cached edid
[ 1634.976411] Skipping EDID probe due to cached edid
[ 1762.800351] Skipping EDID probe due to cached edid
[ 1890.816365] Skipping EDID probe due to cached edid
[ 2326.551204] uvcvideo: Failed to resubmit video URB (-27).
[ 2326.551204] uvcvideo: Failed to resubmit video URB (-27).
[ 2326.551204] uvcvideo: Failed to resubmit video URB (-27).
[ 2326.551204] uvcvideo: Failed to resubmit video URB (-27).
[ 2326.551204] uvcvideo: Failed to resubmit video URB (-27).
[ 3488.588374] Skipping EDID probe due to cached edid
[ 3964.412571] uvcvideo: Failed to resubmit video URB (-27).
[ 3964.412643] uvcvideo: Failed to resubmit video URB (-27).
[ 3964.412658] uvcvideo: Failed to resubmit video URB (-27).
[ 3964.412674] uvcvideo: Failed to resubmit video URB (-27).
[ 3964.412689] uvcvideo: Failed to resubmit video URB (-27).
[ 3984.508393] uvcvideo: Failed to resubmit video URB (-27).
[ 3984.508416] uvcvideo: Failed to resubmit video URB (-27).
[ 3984.508432] uvcvideo: Failed to resubmit video URB (-27).
[ 3984.508447] uvcvideo: Failed to resubmit video URB (-27).
[ 3984.508461] uvcvideo: Failed to resubmit video URB (-27).
[ 4202.708384] Skipping EDID probe due to cached edid
[ 4326.138093] uvcvideo: Failed to resubmit video URB (-27).
[ 4326.138243] uvcvideo: Failed to resubmit video URB (-27).
[ 4326.138282] uvcvideo: Failed to resubmit video URB (-27).
[ 4326.138317] uvcvideo: Failed to resubmit video URB (-27).
[ 4326.138351] uvcvideo: Failed to resubmit video URB (-27).
[ 4476.857079] uvcvideo: Failed to resubmit video URB (-27).
[ 4476.857237] uvcvideo: Failed to resubmit video URB (-27).
[ 4476.857273] uvcvideo: Failed to resubmit video URB (-27).
[ 4476.857310] uvcvideo: Failed to resubmit video URB (-27).
[ 4476.857344] uvcvideo: Failed to resubmit video URB (-27).
[ 4627.575864] uvcvideo: Failed to resubmit video URB (-27).
[ 4627.575890] uvcvideo: Failed to resubmit video URB (-27).
[ 4627.575904] uvcvideo: Failed to resubmit video URB (-27).
[ 4627.575919] uvcvideo: Failed to resubmit video URB (-27).
[ 4627.575935] uvcvideo: Failed to resubmit video URB (-27).
[ 4918.965757] uvcvideo: Failed to resubmit video URB (-27).
[ 4918.965906] uvcvideo: Failed to resubmit video URB (-27).
[ 4918.965942] uvcvideo: Failed to resubmit video URB (-27).
[ 4918.965981] uvcvideo: Failed to resubmit video URB (-27).
[ 4918.966015] uvcvideo: Failed to resubmit video URB (-27).
[ 5260.594988] uvcvideo: Failed to resubmit video URB (-27).
[ 5260.595013] uvcvideo: Failed to resubmit video URB (-27).
[ 5260.595028] uvcvideo: Failed to resubmit video URB (-27).
[ 5260.595043] uvcvideo: Failed to resubmit video URB (-27).
[ 5260.595057] uvcvideo: Failed to resubmit video URB (-27).
[ 5541.936906] uvcvideo: Failed to resubmit video URB (-27).
[ 5541.936941] uvcvideo: Failed to resubmit video URB (-27).
[ 5541.936956] uvcvideo: Failed to resubmit video URB (-27).
[ 5541.936971] uvcvideo: Failed to resubmit video URB (-27).
[ 5541.936986] uvcvideo: Failed to resubmit video URB (-27).
[ 5600.060379] Skipping EDID probe due to cached edid
[ 6195.052605] uvcvideo: Failed to resubmit video URB (-27).
[ 6195.052683] uvcvideo: Failed to resubmit video URB (-27).
[ 6195.052712] uvcvideo: Failed to resubmit video URB (-27).
[ 6195.052738] uvcvideo: Failed to resubmit video URB (-27).
[ 6195.052764] uvcvideo: Failed to resubmit video URB (-27).

I'm beginning to think that the problem is one of a couple of things, feel free to shoot me down in flames if any of this is wrong, but I personally think that it's either, there's a problem with the UVC driver, which only shows up in rare circumstances, and mine just happens to be that set of circumstances, or there is a problem with the part of the kernel that deals with USB as a whole (The kernel version I'm using is 2.6.35-30-generic btw) or less likely given that this problem almost never happens with XP, the computer itself, and right now, I'm thinking that it's one of the first two.
This problem is not a clockwork occurrence, I can go several minutes before it occurs or sometimes less than 10 seconds, but I can guarantee that it'll happen, no matter what the computer is doing.

Again, thank you so much for your help, it's much appreciated :)

---

### Post by diasf on 2011-09-14
I didn't see your previous post while I was posting my answer...
But yeah, seems like it is something like that.
AFAIK, this "refresh" is quite common, at least I see it fairly often, but never got any problems with it. 
IMO now is to google around something like that. I don't think so, but maybe there's a patch for something (either the camera or the controller or the driver) that fix it. Or, more probable, it exists some option somewhere that can help. But I'm just guessing.

On a quick googled around, I saw some ppl with the same error message on dmesg, but after a system suspend...

---

### Post by Robinfox88 on 2011-09-14
> **diasf said:**
> I didn't see your previous post while I was posting my answer...
But yeah, seems like it is something like that.
AFAIK, this "refresh" is quite common, at least I see it fairly often, but never got any problems with it. 
IMO now is to google around something like that. I don't think so, but maybe there's a patch for something (either the camera or the controller or the driver) that fix it. Or, more probable, it exists some option somewhere that can help. But I'm just guessing.

On a quick googled around, I saw some ppl with the same error message on dmesg, but after a system suspend...


Yeah I kinda thought that you'd missed that lol :D But no worries, I have been posting quite a lot with regards to this, so it's no wonder that you missed it :)

Yeah, I had been googling a lot about this, even before I started posting this, but it wasn't until I got the output from dmesg that I sort of knew what to look for, and what you mentioned about the suspend issue that others are having is the same thing that I found in my searches, and I had found a patch of sorts, but that was for kernel 2.6.27 in Fedora 13, and obviously that's no good for me :(

I'm wondering the same as you, that if there is maybe some option of some sorts to stop the webcam from refreshing its video, either through a config file or whatever, but the more I look at the dmesg output the more and more convinced that it's a bug with the UVC driver.
I think that I'll google for a way to force the webcam to not refresh its state, and/or maybe for older version of the Linux kernel and try and install it into my current install of Ubuntu and see where that gets me (Probably with a wrecked install :D)

---

### Post by Robinfox88 on 2011-09-15
I've been looking around now for some time on this, and I've come to the conclusion that this is definitely a driver bug, however, as this is not with any particular program, it happens on multiple programs and is a problem with the UVC driver, I'm not entirely sure how to file a bug report on it, as it isn't with a particular package or program.

If someone can give a couple of pointers on how to file a bug report on a driver using ubuntu-bug, that would be great.

Thank you so much for your time and help diasf, you've been great, and it's thanks to you that I've narrowed down the possibilities of the cause of my problem, so thanks again, it really is much appreciated[B].

[/B]This wouldn't have been a problem if Logitech weren't such idle bastards and actually made the effort to write a decent driver for their webcams instead of ignoring Linux. I paid for the god damn thing, the least I expect is some fudging support for it. x\

And Skype need to buck their ideas up, a year and a half is it? To update from 2.1 to 2.2? Idle gits, I could grow an entire operating system from the festering snot of a diseased pig faster than they can update. :D

---

