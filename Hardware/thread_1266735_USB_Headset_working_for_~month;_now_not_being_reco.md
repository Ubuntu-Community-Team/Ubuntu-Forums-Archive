---
title: "USB Headset working for ~month; now not being recognized"
date: 2009-09-15
forum: Hardware
---

### Post by teemtight on 2009-09-15
Hi all,

I am running on the latest version of ubuntu. For the past month I've been using the logitech clearchat pro usb headset (mic + headphones) and they've worked great.  

However, randomly today when I plugged them in, they are no longer being recognized.  What I mean is that when I got to System --- Preferences --- Sound, they have them listed there as an option (b/c I was using them perfectly) but next to it it says (not connected), when in fact, they are connected to the USB port.  Also, the light on the headset isn't coming on, indicating that it isn't connected.

I've tried my USB flash drive to check if they usb port was messed up, but it popped up, which leads me to beleive its either the headset or the failure of recognition of the headset on the computer...i'm more inclined to the second option.  However, I'm not too great with the techinical aspects of ubuntu, so if anyone has any ideas about what my problem is, I'd greatly appreciate it.  I need my headset for phone calls back home, thats all I really use them for, so I really need them to work

Thanks a lot

---

### Post by Whiffle on 2009-09-15
Unplug the headphones, then plug them back in.  Now, open up a terminal (Applications > Accessories > Terminal).  Type "dmesg" in the terminal.  Post up the last 30 lines or so, there should be something in there about your headphones.

---

### Post by teemtight on 2009-09-15
The dmesg results (sorry if there too long, wasnt sure where to cut/paste)

: 0 ANSI: 5
[    2.156892] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
[    2.156896] Uniform CD-ROM driver Revision: 3.20
[    2.156985] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    2.157024] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    2.157695] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.157718] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.157741] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.157746] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.157816] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.161746] ehci_hcd 0000:00:1d.7: debug port 1
[    2.161753] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.161770] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb0004000
[    2.176009] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.176083] usb usb1: configuration #1 chosen from 1 choice
[    2.176114] hub 1-0:1.0: USB hub found
[    2.176126] hub 1-0:1.0: 8 ports detected
[    2.176259] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.176277] uhci_hcd: USB Universal Host Controller Interface driver
[    2.176303] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.176310] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.176314] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.176363] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.176388] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    2.176477] usb usb2: configuration #1 chosen from 1 choice
[    2.176505] hub 2-0:1.0: USB hub found
[    2.176513] hub 2-0:1.0: 2 ports detected
[    2.176599] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.176605] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.176609] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.176651] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.176685] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    2.176767] usb usb3: configuration #1 chosen from 1 choice
[    2.176795] hub 3-0:1.0: USB hub found
[    2.176804] hub 3-0:1.0: 2 ports detected
[    2.176891] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.176898] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.176902] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.176954] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.176987] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    2.177075] usb usb4: configuration #1 chosen from 1 choice
[    2.177102] hub 4-0:1.0: USB hub found
[    2.177109] hub 4-0:1.0: 2 ports detected
[    2.177197] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.177204] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.177208] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.177250] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.177283] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    2.177367] usb usb5: configuration #1 chosen from 1 choice
[    2.177395] hub 5-0:1.0: USB hub found
[    2.177403] hub 5-0:1.0: 2 ports detected
[    2.177549] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.181947] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.185229] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.185234] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.185237] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.185240] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.185243] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.185408] mice: PS/2 mouse device common for all mice
[    2.185578] rtc_cmos 00:05: RTC can wake from S4
[    2.185620] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.185655] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.185719] device-mapper: uevent: version 1.0.3
[    2.185835] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.185885] device-mapper: multipath: version 1.0.5 loaded
[    2.185888] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.185972] EISA: Probing bus 0 at eisa.0
[    2.185981] Cannot allocate resource for EISA slot 1
[    2.185984] Cannot allocate resource for EISA slot 2
[    2.186016] EISA: Detected 0 cards.
[    2.186083] cpuidle: using governor ladder
[    2.186150] cpuidle: using governor menu
[    2.186696] TCP cubic registered
[    2.186809] NET: Registered protocol family 10
[    2.187267] lo: Disabled Privacy Extensions
[    2.187609] NET: Registered protocol family 17
[    2.187628] Bluetooth: L2CAP ver 2.11
[    2.187630] Bluetooth: L2CAP socket layer initialized
[    2.187633] Bluetooth: SCO (Voice Link) ver 0.6
[    2.187635] Bluetooth: SCO socket layer initialized
[    2.187660] Bluetooth: RFCOMM socket layer initialized
[    2.187668] Bluetooth: RFCOMM TTY layer initialized
[    2.187670] Bluetooth: RFCOMM ver 1.10
[    2.187966] Using IPI No-Shortcut mode
[    2.188059] registered taskstats version 1
[    2.188178]   Magic number: 9:178:1
[    2.188252] rtc_cmos 00:05: setting system clock to 2009-09-16 00:00:25 UTC (1253059225)
[    2.188256] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.188258] EDD information not available.
[    2.188570] Freeing unused kernel memory: 532k freed
[    2.188697] Write protecting the kernel text: 4116k
[    2.188742] Write protecting the kernel read-only data: 1528k
[    2.386943] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.917391] ohci1394 0000:06:03.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.967171] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[b0104000-b01047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.974802] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI
[    2.974805] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.976867] e100 0000:06:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.009382] e100 0000:06:08.0: PME# disabled
[    3.012113] e100: eth0: e100_probe: addr 0xb0107000, irq 20, MAC addr 00:01:4a:5e:a4:c3
[    3.265720] Marking TSC unstable due to TSC halts in idle
[    3.294238] PM: Starting manual resume from disk
[    3.294243] PM: Resume from partition 8:5
[    3.294245] PM: Checking hibernation image.
[    3.294427] PM: Resume from disk failed.
[    3.350129] kjournald starting.  Commit interval 5 seconds
[    3.350139] EXT3-fs: mounted filesystem with ordered data mode.
[    3.688032] Clocksource tsc unstable (delta = -369100323 ns)
[    4.248152] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460301e2fe28]
[   11.504783] udev: starting version 141
[   11.983412] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:07/input/input5
[   11.988482] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   12.072525] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   12.136986] sony-laptop: Sony Notebook Control Driver v0.6.
[   12.138513] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:18/SNY5001:00/input/input7
[   12.139329] input: Sony Vaio Jogdial as /devices/virtual/input/input8
[   12.293265] yenta_cardbus 0000:06:03.0: CardBus bridge found [104d:818f]
[   12.293293] yenta_cardbus 0000:06:03.0: Enabling burst memory read transactions
[   12.293301] yenta_cardbus 0000:06:03.0: Using CSCINT to route CSC interrupts to PCI
[   12.293304] yenta_cardbus 0000:06:03.0: Routing CardBus interrupts to PCI
[   12.293311] yenta_cardbus 0000:06:03.0: TI: mfunc 0x01001b22, devctl 0x64
[   12.525243] yenta_cardbus 0000:06:03.0: ISA IRQ mask 0x0cf8, PCI irq 16
[   12.525250] yenta_cardbus 0000:06:03.0: Socket status: 30000006
[   12.525255] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   12.525264] yenta_cardbus 0000:06:03.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   12.525268] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: clean.
[   12.525508] yenta_cardbus 0000:06:03.0: pcmcia: parent PCI bridge Memory window: 0xb0100000 - 0xb01fffff
[   12.525512] yenta_cardbus 0000:06:03.0: pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   12.583447] ieee80211_crypt: registered algorithm 'NULL'
[   12.588626] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   12.588630] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   12.725214] intel_rng: FWH not detected
[   12.874720] tifm_7xx1 0000:06:03.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   12.895623] Linux agpgart interface v0.103
[   12.896448] tifm_core: MMC/SD card detected in socket 0:0
[   12.962761] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   13.060170] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[   13.060750] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   13.063669] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   13.120459] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   13.120463] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   13.120630] ipw2200 0000:06:04.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.121209] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   13.121263] ipw2200 0000:06:04.0: firmware: requesting ipw2200-bss.fw
[   13.130135] iTCO_vendor_support: vendor-support=0
[   13.132728] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   13.132864] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   13.132875] iTCO_wdt: No card detected
[   13.375013] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.380891] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   13.440469] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   13.442800] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   13.443803] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   13.444640] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   13.445659] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   13.571912] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input9
[   13.592185] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input10
[   13.653668] lp: driver loaded but no devices found
[   13.748457] Adding 1461872k swap on /dev/sda5.  Priority:-1 extents:1 across:1461872k
[   13.764084] EXT3 FS on sda1, internal journal
[   14.401016] type=1505 audit(1253059237.711:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1883
[   14.470401] type=1505 audit(1253059237.779:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1887
[   14.470538] type=1505 audit(1253059237.779:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1887
[   14.470593] type=1505 audit(1253059237.779:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1887
[   14.470645] type=1505 audit(1253059237.779:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1887
[   14.650025] type=1505 audit(1253059237.959:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1892
[   14.650296] type=1505 audit(1253059237.959:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1892
[   14.683793] type=1505 audit(1253059237.991:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1897
[   17.984880] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.984885] Bluetooth: BNEP filters: protocol multicast
[   18.012158] Bridge firewalling registered
[   20.279014] ppdev: user-space parallel port driver
[   21.231647] [drm] Initialized drm 1.1.0 20060810
[   21.240521] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.240530] pci 0000:00:02.0: setting latency timer to 64
[   21.240714] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   21.345370] [drm:i915_setparam] *ERROR* unknown parameter 4
[   21.345396] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   22.721424] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   23.705946] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.372063] eth1: no IPv6 routers present
[   52.359930] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   61.042143] CPU0 attaching NULL sched-domain.
[   61.052063] CPU0 attaching NULL sched-domain.
[  247.148044] usb 3-1: new full speed USB device using uhci_hcd and address 2
[  247.272042] usb 3-1: device descriptor read/64, error -71
[  247.500050] usb 3-1: device descriptor read/64, error -71
[  247.716041] usb 3-1: new full speed USB device using uhci_hcd and address 3
[  247.840033] usb 3-1: device descriptor read/64, error -71
[  248.064050] usb 3-1: device descriptor read/64, error -71
[  248.280057] usb 3-1: new full speed USB device using uhci_hcd and address 4
[  248.692031] usb 3-1: device not accepting address 4, error -71
[  248.804058] usb 3-1: new full speed USB device using uhci_hcd and address 5
[  249.216046] usb 3-1: device not accepting address 5, error -71
[  249.216078] hub 3-0:1.0: unable to enumerate USB device on port 1


and lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Whiffle on 2009-09-15
Try doing:
```

sudo echo Y > /sys/module/usbcore/parameters/old_scheme_first

```

in a terminal, and then try it again.  Its not permanent, but if it works then we can change a couple of things to make it work.  If not, its back to google...

---

### Post by teemtight on 2009-09-15
I tried the line with the headset plugged in, should I try it and then plug in the headset and then reboot or do the line in terminal, reboot, then put the headphones in?

I tried it the first way and upon reboot still no recognition

If it helps, I have a seperate USB soundcard, and that works fine when plugged in (recognized), its just these headphones w/mic don't.

Also, when i turn on my computer, before going to the login screen the screen shows a few error messages (like 4 in a row), but it is only on the screen for a second so i couldn't get the name/number of it.

Thanks for the input so far, i appreciate it

---

### Post by Whiffle on 2009-09-15
Well, that change will go away after a reboot, so I would unplug the headphones, run the command, and then plug them in, and see what happens.

---

### Post by teemtight on 2009-09-15
Tried that right now, no luck, any other suggestions?

---

### Post by teemtight on 2009-09-16
bump

---

### Post by teemtight on 2009-09-17
bump....does anyone else have any ideas?  I think its just something simple since they were working perfectly before....I really need the headphones so I can call home thru skype...without them working I might have to do a complete clean and start over with windows..(which i REALLY dont want to do, as i am starting to get accustomed to ubuntu)

---

### Post by nyth0 on 2009-09-17
Well we can cut down the possibilities if you have access to a computer that runs windows. My suggestion is to find a windows install on a computer somewhere and try the headphones there if you can. That will let us know if its an issue with the actual headphones (as in maybe they're faulty, shorted, or something like that) or if its something to do with linux specifically.

---

