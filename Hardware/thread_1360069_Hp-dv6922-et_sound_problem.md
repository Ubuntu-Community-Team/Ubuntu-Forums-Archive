---
title: "Hp-dv6922-et sound problem"
date: 2009-12-20
forum: Hardware
---

### Post by MaXSpeeD on 2009-12-20
I have no sound with 9.10.
aplay -l

aplay: device_list:223: no soundcards found...

lspci -v

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30cc
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel

I'm trying to install driver but in a step im taking an error.
this step is successful.
sudo ./configure --with-cards=snd-hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)but when im using "make" or "sudo make" command im taking this error:

/usr/src/alsa/alsa-driver-1.0.19/acore/info.c: In function ‘snd_info_entry_prepare’:
/usr/src/alsa/alsa-driver-1.0.19/acore/info.c:161: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/usr/src/alsa/alsa-driver-1.0.19/acore/info.c: In function ‘snd_info_register’:
/usr/src/alsa/alsa-driver-1.0.19/acore/info.c:1020: error: ‘struct proc_dir_entry’ has no member named ‘owner’
make[3]: *** [/usr/src/alsa/alsa-driver-1.0.19/acore/info.o] Error 1
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.19/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.19] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [compile] Error 2

And im stucking in this step. So i couldnt install my sound driver. 
How can i fix this?

---

### Post by mikewhatever on 2009-12-20
Not quite sure why you are compiling the older driver, when Karmic has 1.0.20 by default.

---

### Post by MaXSpeeD on 2009-12-21
I have upgraded my alsa to 1.0.21 now. 

Advanced Linux Sound Architecture Driver Version 1.0.21.
Compiled on Dec  2 2009 for kernel 2.6.31-16-generic (SMP).


I have used [http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/) this website as a guide.

But still i get "No soundcards found..." error. 

I have realtek alc268 sound card. How can i solve this problem?

---

### Post by stblack on 2009-12-21
Try
sudo gedit /etc/modprobe.d/alsa-base.conf

When there is:
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N

Replace with
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel model=hp-dv5 power_save=10 power_save_controller=N

To my dv6-1323 it goes.

Bye
Stblack

---

### Post by MaXSpeeD on 2009-12-21
> **stblack said:**
> Try
sudo gedit /etc/modprobe.d/alsa-base.conf

When there is:
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N

Replace with
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel model=hp-dv5 power_save=10 power_save_controller=N

To my dv6-1323 it goes.

Bye
Stblack

I did but it didnt solve my problem. When i open my sound preferences, and choose hardware, there is not any device in there...

---

### Post by kapetus on 2009-12-21
i also get the same problem,
no sound devices found on 'sound preferences'
but i use skype and i got sound when i use it...
it's very strange...

---

### Post by stblack on 2009-12-21
Ok.
The /var/log/dmesg (and it's friend messages and syslog) what are logging about sound ?

Maybe this post can help you.
[https://answers.launchpad.net/ubuntu/+question/93465](https://answers.launchpad.net/ubuntu/+question/93465)

or better this :
[URL="http://www.aldeby.org/blog/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio"]http://www.aldeby.org/blog/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio
[/URL]
Bye
Stblack

---

### Post by MaXSpeeD on 2009-12-21
the second link is try to install 1.0.19

/var/log/dmesg gives this result;

[    0.848076] scsi3 : ata_piix
[    0.848131] scsi4 : ata_piix
[    0.848665] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[    0.848668] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[    0.849494] Fixed MDIO Bus: probed
[    0.849525] PPP generic driver version 2.4.2
[    0.849601] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.849617]   alloc irq_desc for 18 on node -1
[    0.849619]   alloc kstat_irqs on node -1
[    0.849623] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.849633] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.849637] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.849681] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.853591] ehci_hcd 0000:00:1a.7: debug port 1
[    0.853598] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.853610] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf8404800
[    0.868014] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.868080] usb usb1: configuration #1 chosen from 1 choice
[    0.868106] hub 1-0:1.0: USB hub found
[    0.868113] hub 1-0:1.0: 4 ports detected
[    0.868165]   alloc irq_desc for 23 on node -1
[    0.868167]   alloc kstat_irqs on node -1
[    0.868171] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.868180] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.868184] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.868212] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.872119] ehci_hcd 0000:00:1d.7: debug port 1
[    0.872125] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.872138] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf8404c00
[    0.888018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.888085] usb usb2: configuration #1 chosen from 1 choice
[    0.888110] hub 2-0:1.0: USB hub found
[    0.888116] hub 2-0:1.0: 6 ports detected
[    0.888174] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.888189] uhci_hcd: USB Universal Host Controller Interface driver
[    0.888208] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.888215] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.888218] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.888244] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.888279] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    0.888352] usb usb3: configuration #1 chosen from 1 choice
[    0.888376] hub 3-0:1.0: USB hub found
[    0.888382] hub 3-0:1.0: 2 ports detected
[    0.888428]   alloc irq_desc for 21 on node -1
[    0.888429]   alloc kstat_irqs on node -1
[    0.888434] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.888440] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.888443] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.888470] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.888504] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    0.888577] usb usb4: configuration #1 chosen from 1 choice
[    0.888600] hub 4-0:1.0: USB hub found
[    0.888606] hub 4-0:1.0: 2 ports detected
[    0.888652] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.888659] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.888662] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.888692] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.888719] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[    0.888788] usb usb5: configuration #1 chosen from 1 choice
[    0.888814] hub 5-0:1.0: USB hub found
[    0.888819] hub 5-0:1.0: 2 ports detected
[    0.888863] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.888871] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.888875] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.888900] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.888934] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[    0.889005] usb usb6: configuration #1 chosen from 1 choice
[    0.889030] hub 6-0:1.0: USB hub found
[    0.889036] hub 6-0:1.0: 2 ports detected
[    0.889078] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.889084] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.889088] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.889116] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.889143] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[    0.889219] usb usb7: configuration #1 chosen from 1 choice
[    0.889242] hub 7-0:1.0: USB hub found
[    0.889249] hub 7-0:1.0: 2 ports detected
[    0.889339] PNP: PS/2 Controller [PNP0303S2K,PNP0f13S2M] at 0x60,0x64 irq 1,12
[    0.932114] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.932120] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.932173] mice: PS/2 mouse device common for all mice
[    0.932293] rtc_cmos 00:08: RTC can wake from S4
[    0.932322] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    0.932355] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.932440] device-mapper: uevent: version 1.0.3
[    0.932512] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.932571] device-mapper: multipath: version 1.1.0 loaded
[    0.932573] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.932669] EISA: Probing bus 0 at eisa.0
[    0.932675] Cannot allocate resource for EISA slot 1
[    0.932677] Cannot allocate resource for EISA slot 2
[    0.932683] Cannot allocate resource for EISA slot 4
[    0.932685] Cannot allocate resource for EISA slot 5
[    0.932687] Cannot allocate resource for EISA slot 6
[    0.932689] Cannot allocate resource for EISA slot 7
[    0.932690] Cannot allocate resource for EISA slot 8
[    0.932692] EISA: Detected 0 cards.
[    0.932816] cpuidle: using governor ladder
[    0.934572] cpuidle: using governor menu
[    0.935012] TCP cubic registered
[    0.935152] NET: Registered protocol family 10
[    0.935567] lo: Disabled Privacy Extensions
[    0.935873] NET: Registered protocol family 17
[    0.935888] Bluetooth: L2CAP ver 2.13
[    0.935889] Bluetooth: L2CAP socket layer initialized
[    0.935892] Bluetooth: SCO (Voice Link) ver 0.6
[    0.935894] Bluetooth: SCO socket layer initialized
[    0.935915] Bluetooth: RFCOMM TTY layer initialized
[    0.935918] Bluetooth: RFCOMM socket layer initialized
[    0.935919] Bluetooth: RFCOMM ver 1.11
[    0.936444] Using IPI No-Shortcut mode
[    0.936498] PM: Resume from disk failed.
[    0.936509] registered taskstats version 1
[    0.936619]   Magic number: 5:130:587
[    0.936641] pci_bus 0000:08: hash matches
[    0.936697] rtc_cmos 00:08: setting system clock to 2009-12-21 14:34:56 UTC (1261406096)
[    0.936700] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.936701] EDD information not available.
[    0.965314] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.036416] ata4.00: ATAPI: TSSTcorp CDDVDW TS-L632N, 0503, max MWDMA2
[    1.068327] ata4.00: configured for MWDMA2
[    1.164154] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.165636] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    1.165640] ata1.00: ATA-8: WDC WD1600BEVT-60ZCT0, 12.01A12, max UDMA/100
[    1.165643] ata1.00: 312581808 sectors, multi 16: LBA48 
[    1.167179] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    1.167202] ata1.00: configured for UDMA/100
[    1.169100] ata2: SATA link down (SStatus 0 SControl 300)
[    1.169125] ata3: SATA link down (SStatus 0 SControl 300)
[    1.180233] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-6 12.0 PQ: 0 ANSI: 5
[    1.180330] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.180371] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.180412] sd 0:0:0:0: [sda] Write Protect is off
[    1.180415] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.180436] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.180554]  sda:
[    1.187319] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632N  0503 PQ: 0 ANSI: 5
[    1.203067] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.203072] Uniform CD-ROM driver Revision: 3.20
[    1.203192] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.203238] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.209828]  sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >
[    1.268307] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.268341] Freeing unused kernel memory: 540k freed
[    1.268666] Write protecting the kernel text: 4568k
[    1.268720] Write protecting the kernel read-only data: 1836k
[    1.365600] Linux agpgart interface v0.103
[    1.410899] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.410926] r8169 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.410984] r8169 0000:08:00.0: setting latency timer to 64
[    1.411064]   alloc irq_desc for 29 on node -1
[    1.411066]   alloc kstat_irqs on node -1
[    1.411087] r8169 0000:08:00.0: irq 29 for MSI/MSI-X
[    1.411703] eth0: RTL8101e at 0xf80e8000, 00:1e:68:ca:54:35, XID 34200000 IRQ 29
[    1.417312] acpi device:06: registered as cooling_device2
[    1.417432] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input6
[    1.417470] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    1.427117] usb 2-4: new high speed USB device using ehci_hcd and address 4
[    1.429922]   alloc irq_desc for 20 on node -1
[    1.429925]   alloc kstat_irqs on node -1
[    1.429932] ohci1394 0000:09:09.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.490157] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[f8100000-f81007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.504036] Clocksource tsc unstable (delta = -148732347 ns)
[    1.569066] usb 2-4: configuration #1 chosen from 1 choice
[    1.808057] usb 5-2: new full speed USB device using uhci_hcd and address 2
[    1.977876] usb 5-2: configuration #1 chosen from 1 choice
[    1.985333] usbcore: registered new interface driver hiddev
[    1.989173] input: USB Multi-Smart Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input7
[    1.989245] generic-usb 0003:04FC:0801.0001: input,hidraw0: USB HID v1.11 Mouse [USB Multi-Smart Mouse] on usb-0000:00:1d.0-2/input0
[    1.989256] usbcore: registered new interface driver usbhid
[    1.989261] usbhid: v2.6:USB HID core driver
[    2.224028] usb 6-1: new full speed USB device using uhci_hcd and address 2
[    2.497029] usb 6-1: configuration #1 chosen from 1 choice
[    2.824602] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00cd202d01]
[    2.944713] PM: Starting manual resume from disk
[    2.944717] PM: Resume from partition 8:8
[    2.944719] PM: Checking hibernation image.
[    2.944852] PM: Resume from disk failed.
[    3.005947] kjournald starting.  Commit interval 5 seconds
[    3.005955] EXT3-fs: mounted filesystem with writeback data mode.
[    3.750149] type=1505 audit(1261406099.312:2): operation="profile_load" pid=455 name=/usr/share/gdm/guest-session/Xsession
[    3.778668] type=1505 audit(1261406099.339:3): operation="profile_load" pid=456 name=/sbin/dhclient3
[    3.779315] type=1505 audit(1261406099.339:4): operation="profile_load" pid=456 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.779658] type=1505 audit(1261406099.339:5): operation="profile_load" pid=456 name=/usr/lib/connman/scripts/dhclient-script
[    3.826340] type=1505 audit(1261406099.387:6): operation="profile_load" pid=457 name=/usr/bin/evince
[    3.836478] type=1505 audit(1261406099.399:7): operation="profile_load" pid=457 name=/usr/bin/evince-previewer
[    3.842505] type=1505 audit(1261406099.403:: operation="profile_load" pid=457 name=/usr/bin/evince-thumbnailer
[    3.884954] type=1505 audit(1261406099.447:9): operation="profile_load" pid=459 name=/usr/lib/cups/backend/cups-pdf
[   17.329086] Adding 4947980k swap on /dev/sda6.  Priority:-1 extents:1 across:4947980k 
[   17.329254] udev: starting version 147
[   17.377322] Adding 9944192k swap on /dev/sda8.  Priority:-2 extents:1 across:9944192k 
[   17.516186] cfg80211: Calling CRDA to update world regulatory domain
[   17.534397] nvidia: module license 'NVIDIA' taints kernel.
[   17.534401] Disabling lock debugging due to kernel taint
[   17.538598] lp: driver loaded but no devices found
[   17.750840] EXT3 FS on sda7, internal journal
[   17.804060] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   17.804072] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.804081] nvidia 0000:01:00.0: setting latency timer to 64
[   17.804230] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
[   17.814370] sdhci: Secure Digital Host Controller Interface driver
[   17.814373] sdhci: Copyright(c) Pierre Ossman
[   17.815568] sdhci-pci 0000:09:09.1: SDHCI controller found [1180:0822] (rev 22)
[   17.815586] sdhci-pci 0000:09:09.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   17.816383] cfg80211: World regulatory domain updated:
[   17.816385]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.816388]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.816391]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.816393]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.816395]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.816398]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.817629] Registered led device: mmc0::
[   17.818654] mmc0: SDHCI controller on PCI [0000:09:09.1] using PIO
[   17.819234] ricoh-mmc: Ricoh MMC Controller disabling driver
[   17.819237] ricoh-mmc: Copyright(c) Philip Langdale
[   17.819257] ricoh-mmc: Ricoh MMC controller found at 0000:09:09.2 [1180:0843] (rev 12)
[   17.819273] ricoh-mmc: Controller is now disabled.
[   17.871512] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   17.871515] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   17.871627] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.871641] iwl3945 0000:02:00.0: setting latency timer to 64
[   17.886944] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.902615] snd_hda_intel: Unknown symbol snd_hidden_kzalloc
[   17.902806] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   17.902808] snd_hda_intel: Unknown symbol snd_pcm_new
[   17.902891] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   17.902894] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   17.903150] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   17.903152] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   17.903256] snd_hda_intel: disagrees about version of symbol snd_hda_bus_new
[   17.903258] snd_hda_intel: Unknown symbol snd_hda_bus_new
[   17.903405] snd_hda_intel: Unknown symbol snd_hidden_kcalloc
[   17.903520] snd_hda_intel: Unknown symbol snd_hidden_kfree
[   17.903630] snd_hda_intel: disagrees about version of symbol snd_hda_build_pcms
[   17.903632] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[   17.903772] snd_hda_intel: disagrees about version of symbol snd_pcm_set_sync
[   17.903774] snd_hda_intel: Unknown symbol snd_pcm_set_sync
[   17.903962] snd_hda_intel: disagrees about version of symbol snd_hda_codec_new
[   17.903964] snd_hda_intel: Unknown symbol snd_hda_codec_new
[   17.904196] snd_hda_intel: disagrees about version of symbol snd_hda_queue_unsol_event
[   17.904198] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[   17.904298] snd_hda_intel: disagrees about version of symbol snd_hda_power_up
[   17.904300] snd_hda_intel: Unknown symbol snd_hda_power_up
[   17.904385] snd_hda_intel: disagrees about version of symbol snd_pcm_sgbuf_get_chunk_size
[   17.904388] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_get_chunk_size
[   17.904484] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   17.904486] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   17.904568] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   17.904570] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   17.904666] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   17.904668] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   17.904774] snd_hda_intel: disagrees about version of symbol snd_hda_power_down
[   17.904776] snd_hda_intel: Unknown symbol snd_hda_power_down
[   17.904939] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   17.904942] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   17.905119] snd_hda_intel: disagrees about version of symbol snd_hda_suspend
[   17.905121] snd_hda_intel: Unknown symbol snd_hda_suspend
[   17.905311] snd_hda_intel: disagrees about version of symbol snd_pcm_sgbuf_ops_page
[   17.905313] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_ops_page
[   17.905427] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   17.905429] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   17.905588] snd_hda_intel: disagrees about version of symbol snd_hda_resume
[   17.905590] snd_hda_intel: Unknown symbol snd_hda_resume
[   17.905672] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   17.905674] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   17.905776] snd_hda_intel: disagrees about version of symbol snd_hda_build_controls
[   17.905778] snd_hda_intel: Unknown symbol snd_hda_build_controls
[   17.905999] snd_hda_intel: disagrees about version of symbol snd_pci_quirk_lookup
[   17.906001] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[   17.906284] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   17.906287] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   17.906367] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   17.906369] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[   17.910030] Linux video capture interface: v2.00
[   17.912704] uvcvideo: Found UVC 1.00 device HP Webcam (04f2:b015)
[   17.916026] snd_hda_intel: Unknown symbol snd_hidden_kzalloc
[   17.916217] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   17.916219] snd_hda_intel: Unknown symbol snd_pcm_new
[   17.916303] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   17.916305] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   17.916563] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   17.916565] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   17.916670] snd_hda_intel: disagrees about version of symbol snd_hda_bus_new
[   17.916672] snd_hda_intel: Unknown symbol snd_hda_bus_new
[   17.916820] snd_hda_intel: Unknown symbol snd_hidden_kcalloc
[   17.916935] snd_hda_intel: Unknown symbol snd_hidden_kfree
[   17.917080] snd_hda_intel: disagrees about version of symbol snd_hda_build_pcms
[   17.917082] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[   17.917222] snd_hda_intel: disagrees about version of symbol snd_pcm_set_sync
[   17.917224] snd_hda_intel: Unknown symbol snd_pcm_set_sync
[   17.917413] snd_hda_intel: disagrees about version of symbol snd_hda_codec_new
[   17.917415] snd_hda_intel: Unknown symbol snd_hda_codec_new
[   17.917647] snd_hda_intel: disagrees about version of symbol snd_hda_queue_unsol_event
[   17.917649] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[   17.917750] snd_hda_intel: disagrees about version of symbol snd_hda_power_up
[   17.917752] snd_hda_intel: Unknown symbol snd_hda_power_up
[   17.917837] snd_hda_intel: disagrees about version of symbol snd_pcm_sgbuf_get_chunk_size
[   17.917840] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_get_chunk_size
[   17.917937] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   17.917939] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   17.918021] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   17.918023] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   17.918120] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   17.918122] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   17.918228] snd_hda_intel: disagrees about version of symbol snd_hda_power_down
[   17.918230] snd_hda_intel: Unknown symbol snd_hda_power_down
[   17.918394] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   17.918396] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   17.918512] snd_hda_intel: disagrees about version of symbol snd_hda_suspend
[   17.918514] snd_hda_intel: Unknown symbol snd_hda_suspend
[   17.918706] snd_hda_intel: disagrees about version of symbol snd_pcm_sgbuf_ops_page
[   17.918708] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_ops_page
[   17.918823] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   17.918825] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   17.918985] snd_hda_intel: disagrees about version of symbol snd_hda_resume
[   17.918987] snd_hda_intel: Unknown symbol snd_hda_resume
[   17.919069] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   17.919072] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   17.919174] snd_hda_intel: disagrees about version of symbol snd_hda_build_controls
[   17.919176] snd_hda_intel: Unknown symbol snd_hda_build_controls
[   17.919397] snd_hda_intel: disagrees about version of symbol snd_pci_quirk_lookup
[   17.919399] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[   17.919684] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   17.919687] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   17.919768] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   17.919770] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[   17.920835] snd_hda_intel: Unknown symbol snd_hidden_kzalloc
[   17.921059] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   17.921062] snd_hda_intel: Unknown symbol snd_pcm_new
[   17.921145] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   17.921147] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   17.921406] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   17.921408] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   17.921513] snd_hda_intel: disagrees about version of symbol snd_hda_bus_new
[   17.921515] snd_hda_intel: Unknown symbol snd_hda_bus_new
[   17.921663] snd_hda_intel: Unknown symbol snd_hidden_kcalloc
[   17.921778] snd_hda_intel: Unknown symbol snd_hidden_kfree
[   17.921888] snd_hda_intel: disagrees about version of symbol snd_hda_build_pcms
[   17.921890] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[   17.922031] snd_hda_intel: disagrees about version of symbol snd_pcm_set_sync
[   17.922033] snd_hda_intel: Unknown symbol snd_pcm_set_sync
[   17.922222] snd_hda_intel: disagrees about version of symbol snd_hda_codec_new
[   17.922224] snd_hda_intel: Unknown symbol snd_hda_codec_new
[   17.922456] snd_hda_intel: disagrees about version of symbol snd_hda_queue_unsol_event
[   17.922458] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[   17.922559] snd_hda_intel: disagrees about version of symbol snd_hda_power_up
[   17.922561] snd_hda_intel: Unknown symbol snd_hda_power_up
[   17.922647] snd_hda_intel: disagrees about version of symbol snd_pcm_sgbuf_get_chunk_size
[   17.922649] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_get_chunk_size
[   17.922746] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   17.922748] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   17.922830] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   17.922832] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   17.922928] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   17.922931] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   17.923037] snd_hda_intel: disagrees about version of symbol snd_hda_power_down
[   17.923039] snd_hda_intel: Unknown symbol snd_hda_power_down
[   17.923203] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   17.923205] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   17.923322] snd_hda_intel: disagrees about version of symbol snd_hda_suspend
[   17.923324] snd_hda_intel: Unknown symbol snd_hda_suspend
[   17.923515] snd_hda_intel: disagrees about version of symbol snd_pcm_sgbuf_ops_page
[   17.923517] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_ops_page
[   17.923632] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   17.923634] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   17.923795] snd_hda_intel: disagrees about version of symbol snd_hda_resume
[   17.923797] snd_hda_intel: Unknown symbol snd_hda_resume
[   17.923879] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   17.923881] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   17.923983] snd_hda_intel: disagrees about version of symbol snd_hda_build_controls
[   17.923985] snd_hda_intel: Unknown symbol snd_hda_build_controls
[   17.924206] snd_hda_intel: disagrees about version of symbol snd_pci_quirk_lookup
[   17.924208] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[   17.924493] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   17.924496] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   17.924576] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   17.924579] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[   17.929190] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input8
[   17.929236] usbcore: registered new interface driver uvcvideo
[   17.929239] USB Video Class driver (v0.1.0)
[   17.956820] iwl3945 0000:02:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   17.956823] iwl3945 0000:02:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   17.956950]   alloc irq_desc for 30 on node -1
[   17.956952]   alloc kstat_irqs on node -1
[   17.956985] iwl3945 0000:02:00.0: irq 30 for MSI/MSI-X
[   17.984406] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   18.651449] __ratelimit: 6 callbacks suppressed
[   18.651452] type=1505 audit(1261398914.212:12): operation="profile_replace" pid=1027 name=/usr/share/gdm/guest-session/Xsession
[   18.652926] type=1505 audit(1261398914.215:13): operation="profile_replace" pid=1028 name=/sbin/dhclient3
[   18.653595] type=1505 audit(1261398914.215:14): operation="profile_replace" pid=1028 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   18.653938] type=1505 audit(1261398914.215:15): operation="profile_replace" pid=1028 name=/usr/lib/connman/scripts/dhclient-script
[   18.657363] type=1505 audit(1261398914.219:16): operation="profile_replace" pid=1029 name=/usr/bin/evince
[   18.667732] type=1505 audit(1261398914.227:17): operation="profile_replace" pid=1029 name=/usr/bin/evince-previewer
[   18.673954] type=1505 audit(1261398914.235:1: operation="profile_replace" pid=1029 name=/usr/bin/evince-thumbnailer
[   18.682513] type=1505 audit(1261398914.243:19): operation="profile_replace" pid=1031 name=/usr/lib/cups/backend/cups-pdf
[   18.683249] type=1505 audit(1261398914.243:20): operation="profile_replace" pid=1031 name=/usr/sbin/cupsd
[   18.685450] type=1505 audit(1261398914.247:21): operation="profile_replace" pid=1032 name=/usr/sbin/tcpdump
[   18.878966] iwl3945 0000:02:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   19.039667] iwl3945 0000:02:00.0: loaded firmware version 15.32.2.9
[   19.039779] iwl3945 0000:02:00.0: Radio disabled by HW RF Kill switch
[   19.061416] r8169: eth0: link up
[   19.061420] r8169: eth0: link up
[   19.110514] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0xa00000
[   19.219049] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   22.285389] ppdev: user-space parallel port driver
[  203.601072] CE: hpet increasing min_delta_ns to 15000 nsec


LSPCI gives this;

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
09:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


lsmod gives this;

Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
arc4                    1660  2 
ecb                     2524  2 
iptable_filter          3100  0 
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
snd_hda_codec          78300  0 
snd_hwdep               7392  1 snd_hda_codec
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_pcm_oss            37312  0 
snd_mixer_oss          16188  1 snd_pcm_oss
iwl3945                77212  0 
iwlcore               112540  1 iwl3945
mac80211              181076  2 iwl3945,iwlcore
snd_pcm                74976  2 snd_hda_codec,snd_pcm_oss
ricoh_mmc               3676  0 
sdhci_pci               7100  0 
sdhci                  17472  1 sdhci_pci
snd_seq_dummy           2752  0 
led_class               4096  3 iwl3945,iwlcore,sdhci
joydev                 10272  0 
snd_seq_oss            29280  0 
psmouse                56500  0 
serio_raw               5280  0 
snd_seq_midi            6624  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                51088  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21540  2 snd_pcm,snd_seq
snd_seq_device          7208  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               9586440  39 
cfg80211               93052  3 iwl3945,iwlcore,mac80211
snd                    60900  12 snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9060  1 snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
usbhid                 38208  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
r8169                  32064  0 
mii                     5212  1 r8169
video                  19380  0 
output                  2780  1 video
intel_agp              27484  0 
agpgart                34988  2 nvidia,intel_agp


aplay gives this;

ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:608: audio open error: No such file or directory


amixer gives this;

```
 amixer: Mixer attach default error: No such file or directory
```

---

### Post by MaXSpeeD on 2009-12-21
> **stblack said:**
> Ok.
The /var/log/dmesg (and it's friend messages and syslog) what are logging about sound ?

Maybe this post can help you.
[https://answers.launchpad.net/ubuntu/+question/93465](https://answers.launchpad.net/ubuntu/+question/93465)

or better this :
[URL="http://www.aldeby.org/blog/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio"]http://www.aldeby.org/blog/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio
[/URL]
Bye
Stblack


[http://www.alsa-project.org/db/?f=3447bcebd9f5a00334f9cfbb0f4d7117d996c779](http://www.alsa-project.org/db/?f=3447bcebd9f5a00334f9cfbb0f4d7117d996c779)

is this what you want?

---

### Post by MaXSpeeD on 2009-12-21
The Silence of ubuntuers...

---

