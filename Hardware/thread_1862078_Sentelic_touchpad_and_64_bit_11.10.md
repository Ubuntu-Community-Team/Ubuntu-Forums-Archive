---
title: "Sentelic touchpad and 64 bit 11.10"
date: 2011-10-16
forum: Hardware
---

### Post by campbelt on 2011-10-16
I recently bought an Asus Zenbook which is equipped with a Sentelic touchpad.  I installed Ubuntu 64 bit Ocelot (11.10) dual boot.  The problem is that I can't find a way to adjust the touchpad to turn off the annoying default "tap to click" feature, and the touchpad is so sensitive that it causes the pointer to move if I only hover my finger near it.  When I go to the app "Mouse and Touchpad" there is only a tab for adjusting the mouse, not the touchpad.  I understand there are 32 bit drivers from Sentelic available on Sourceforge, but when I download these I get the message "incorrect architecture".  I can completely disable the the touchpad with "xinput set-prop 12 "Device Enabled" 0", but I'd like to be able to use the touchpad and not attach a mouse.

Any suggestions?

---

### Post by campbelt on 2011-10-16
bump

---

### Post by shakabra on 2011-10-16
I'm in the same boat. Campbelt let me know what you've figured out. Also let me know if you fix the horrible battery life.

---

### Post by campbelt on 2011-10-16
I found a post somewhere during a Google search in which the poster claimed to have emailed Sentelic about a lack of Linux drivers (32 bit) and got a reply and drivers.  I can't use those with a 64 bit install.  I did email them about 64 bit drivers.  We'll see what happens.

For now I have disabled the "internal pointing device" in BIOS and am using a USB mouse instead.  I found that I couldn't efficiently use the keyboard with the touchpad activated, as it is so sensitive that getting a finger anywhere near it made the cursor move on the screen.

I haven't used the laptop for any period of time not attached to AC power, so I can't comment on the battery life.  Other than the touchpad issue I do like it.  I do a lot of photos when traveling and use Bibble to edit them.  I have another ASUS that is big and heavy that stays at home that I do most of the editing on, but I wanted a lightweight thin notebook to carry on trips, and the "Zenbook" fills the bill.  I can do a lot of my initial stage editing on it.

---

### Post by shakabra on 2011-10-16
Yep I read the same thing. As far as I know we should be able to use those drivers as long as we have ia32-libs installed. I don't know. I'm definitely not an expert.

I'm about to boot up the 32bit version. I'll let you know about the touchpad support.

---

### Post by atliang on 2011-10-18
> **campbelt said:**
> [...]  I can completely disable the the touchpad with "xinput set-prop 12 "Device Enabled" 0", but I'd like to be able to use the touchpad and not attach a mouse.

Any suggestions?

By any chance would you please provide the output of "cat /proc/bus/input/devices" in Ubuntu 64?

---

### Post by campbelt on 2011-10-18
Here you are:

tom@Zen:~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Asus WMI hotkeys"
P: Phys=asus-nb-wmi/input0
S: Sysfs=/devices/platform/asus-nb-wmi/input/input4
U: Uniq=
H: Handlers=rfkill kbd event4 
B: PROP=0
B: EV=100013
B: KEY=40000 0 800000000000 0 0 a1606c00900000 200027800501000 e000000000000 0
B: MSC=10

I: Bus=0003 Vendor=064e Product=f300 Version=0217
N: Name="USB 2.0 UVC 0.3M Webcam"
P: Phys=usb-0000:00:1d.0-1.5/button
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input7
U: Uniq=
H: Handlers=event7 
B: PROP=0
B: EV=21
B: SW=100

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input8
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0003 Vendor=046d Product=c06a Version=0111
N: Name="Logitech USB Optical Mouse"
P: Phys=usb-0000:00:1d.0-1.2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input9
U: Uniq=
H: Handlers=mouse0 event9 
B: PROP=0
B: EV=17
B: KEY=70000 0 0 0 0
B: REL=103
B: MSC=10

tom@Zen:~$

---

### Post by campbelt on 2011-10-18
Sorry, in the previous post the output listed was with the touchpad turned off in the BIOS and a USB mouse attached.  Here is the output with the internal device (touchpad) turned on:

tom@Zen:~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=064e Product=f300 Version=0217
N: Name="USB 2.0 UVC 0.3M Webcam"
P: Phys=usb-0000:00:1d.0-1.5/button
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0011 Vendor=0002 Product=0006 Version=0000
N: Name="ImExPS/2 Elantech Explorer Mouse"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=0
B: EV=7
B: KEY=1f0000 0 0 0 0
B: REL=143

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Asus WMI hotkeys"
P: Phys=asus-nb-wmi/input0
S: Sysfs=/devices/platform/asus-nb-wmi/input/input6
U: Uniq=
H: Handlers=rfkill kbd event6 
B: PROP=0
B: EV=100013
B: KEY=40000 0 800000000000 0 0 a1606c00900000 200027800501000 e000000000000 0
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input8
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=100

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input9
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=4

tom@Zen:~$ 



Thanks for your help

---

### Post by atliang on 2011-10-18
> **campbelt said:**
> Sorry, in the previous post the output listed was with the touchpad turned off in the BIOS and a USB mouse attached.  Here is the output with the internal device (touchpad) turned on:

tom@Zen:~$ cat /proc/bus/input/devices
[...]
I: Bus=0011 Vendor=0002 Product=0006 Version=0000
N: Name="ImExPS/2 Elantech Explorer Mouse"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=0
B: EV=7
B: KEY=1f0000 0 0 0 0
B: REL=143

[...]

Interesting.  "ImExPS/2 Elantech Explorer Mouse" doesn't look like a Sentelic Finger-sensing Pad to me.

Would you please also provide full dmesg as well as 'ls -la /devices/platform/i8042/serio4' output?

---

### Post by campbelt on 2011-10-19
here is dsmeg:

[    0.695802] TCP: Hash tables configured (established 524288 bind 65536)
[    0.695804] TCP reno registered
[    0.695812] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.695831] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.695932] NET: Registered protocol family 1
[    0.695944] pci 0000:00:02.0: Boot video device
[    0.817851] PCI: CLS 64 bytes, default 64
[    0.817856] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.817858] Placing 64MB software IO TLB between ffff8800b6c0d000 - ffff8800bac0d000
[    0.817860] software IO TLB at phys 0xb6c0d000 - 0xbac0d000
[    0.818232] audit: initializing netlink socket (disabled)
[    0.818240] type=2000 audit(1318976790.660:1): initialized
[    0.824537] Freeing initrd memory: 13416k freed
[    0.840971] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.849981] VFS: Disk quotas dquot_6.5.2
[    0.850029] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.850475] fuse init (API version 7.16)
[    0.850540] msgmni has been set to 7729
[    0.850864] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.850890] io scheduler noop registered
[    0.850892] io scheduler deadline registered
[    0.850920] io scheduler cfq registered (default)
[    0.851000] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.851052] pcieport 0000:00:1c.0: irq 42 for MSI/MSI-X
[    0.851117] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.851159] pcieport 0000:00:1c.1: irq 43 for MSI/MSI-X
[    0.851223] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.851265] pcieport 0000:00:1c.3: irq 44 for MSI/MSI-X
[    0.851339] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.851344] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.851356] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
[    0.851358] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    0.851363] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded
[    0.851375] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    0.851377] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.851381] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    0.851391] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.851408] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.851441] intel_idle: MWAIT substates: 0x21120
[    0.851442] intel_idle: v0.4 model 0x2A
[    0.851443] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.851518] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.851551] ACPI: AC Adapter [AC0] (on-line)
[    0.851651] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.865892] ACPI: Lid Switch [LID]
[    0.865921] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.865925] ACPI: Power Button [PWRB]
[    0.865951] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.865954] ACPI: Sleep Button [SLPB]
[    0.865971] ACPI: acpi_idle yielding to intel_idle
[    0.867775] thermal LNXTHERM:00: registered as thermal_zone0
[    0.867778] ACPI: Thermal Zone [THRM] (74 C)
[    0.867796] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.867811] ERST: Table is not found!
[    0.867875] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.882169] ACPI: Battery Slot [BAT0] (battery present)
[    1.025812] Linux agpgart interface v0.103
[    1.025867] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    1.026000] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.027156] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    1.027249] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.028004] brd: module loaded
[    1.028361] loop: module loaded
[    1.028643] Fixed MDIO Bus: probed
[    1.028658] PPP generic driver version 2.4.2
[    1.028680] tun: Universal TUN/TAP device driver, 1.6
[    1.028681] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.028731] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.028756] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.028773] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.028777] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.028801] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    1.028825] ehci_hcd 0000:00:1d.0: debug port 2
[    1.032715] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.032731] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xdfe07000
[    1.045490] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.045641] hub 1-0:1.0: USB hub found
[    1.045644] hub 1-0:1.0: 2 ports detected
[    1.045687] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.045695] uhci_hcd: USB Universal Host Controller Interface driver
[    1.045741] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.047225] i8042: Detected active multiplexing controller, rev 1.1
[    1.051060] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.051065] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.051073] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.051075] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.051077] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.051182] mousedev: PS/2 mouse device common for all mice
[    1.051278] rtc_cmos 00:06: RTC can wake from S4
[    1.051364] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.051390] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.051469] device-mapper: uevent: version 1.0.3
[    1.051519] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    1.051603] cpuidle: using governor ladder
[    1.051734] cpuidle: using governor menu
[    1.051735] EFI Variables Facility v0.08 2004-May-17
[    1.051894] TCP cubic registered
[    1.051981] NET: Registered protocol family 10
[    1.052313] NET: Registered protocol family 17
[    1.052323] Registering the dns_resolver key type
[    1.052386] PM: Hibernation image not present or could not be loaded.
[    1.052394] registered taskstats version 1
[    1.061676]   Magic number: 15:87:452
[    1.061768] rtc_cmos 00:06: setting system clock to 2011-10-18 22:26:31 UTC (1318976791)
[    1.062484] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.062486] EDD information not available.
[    1.063978] Freeing unused kernel memory: 984k freed
[    1.064098] Write protecting the kernel read-only data: 10240k
[    1.064335] Freeing unused kernel memory: 20k freed
[    1.067903] Freeing unused kernel memory: 1400k freed
[    1.080724] udevd[88]: starting version 173
[    1.086895] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.120393] xhci_hcd 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.120440] xhci_hcd 0000:03:00.0: setting latency timer to 64
[    1.120446] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    1.120506] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 2
[    1.120660] xhci_hcd 0000:03:00.0: irq 19, io mem 0xde000000
[    1.120762] xhci_hcd 0000:03:00.0: irq 45 for MSI/MSI-X
[    1.120771] xhci_hcd 0000:03:00.0: irq 46 for MSI/MSI-X
[    1.120779] xhci_hcd 0000:03:00.0: irq 47 for MSI/MSI-X
[    1.120787] xhci_hcd 0000:03:00.0: irq 48 for MSI/MSI-X
[    1.120795] xhci_hcd 0000:03:00.0: irq 49 for MSI/MSI-X
[    1.120983] xHCI xhci_add_endpoint called for root hub
[    1.120986] xHCI xhci_check_bandwidth called for root hub
[    1.121019] hub 2-0:1.0: USB hub found
[    1.121028] hub 2-0:1.0: 2 ports detected
[    1.121092] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    1.121141] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 3
[    1.121231] xHCI xhci_add_endpoint called for root hub
[    1.121233] xHCI xhci_check_bandwidth called for root hub
[    1.121267] hub 3-0:1.0: USB hub found
[    1.121275] hub 3-0:1.0: 2 ports detected
[    1.123332] ahci 0000:00:1f.2: version 3.0
[    1.123349] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.123415] ahci 0000:00:1f.2: irq 50 for MSI/MSI-X
[    1.123472] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x1 impl SATA mode
[    1.123477] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
[    1.123484] ahci 0000:00:1f.2: setting latency timer to 64
[    1.124172] scsi0 : ahci
[    1.124295] scsi1 : ahci
[    1.124364] scsi2 : ahci
[    1.124437] scsi3 : ahci
[    1.124500] scsi4 : ahci
[    1.124566] scsi5 : ahci
[    1.124709] ata1: SATA max UDMA/133 abar m2048@0xdfe06000 port 0xdfe06100 irq 50
[    1.124711] ata2: DUMMY
[    1.124712] ata3: DUMMY
[    1.124713] ata4: DUMMY
[    1.124714] ata5: DUMMY
[    1.124715] ata6: DUMMY
[    1.357215] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    1.445106] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.456544] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.456582] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    1.456584] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.467070] ata1.00: ATA-8: ADATA XM11 128GB, 322ABBF0, max UDMA/133
[    1.467080] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.476511] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.476539] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    1.476542] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.487063] ata1.00: configured for UDMA/133
[    1.487308] scsi 0:0:0:0: Direct-Access     ATA      ADATA XM11 128GB 322A PQ: 0 ANSI: 5
[    1.487445] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.487492] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.487613] sd 0:0:0:0: [sda] Write Protect is off
[    1.487616] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.487644] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.488418]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.488854] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.489617] hub 1-1:1.0: USB hub found
[    1.489744] hub 1-1:1.0: 8 ports detected
[    1.536930] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    1.760817] usb 1-1.5: new high speed USB device number 3 using ehci_hcd
[    1.816641] Refined TSC clocksource calibration: 1696.146 MHz.
[    1.816653] Switching to clocksource tsc
[    1.934401] udevd[324]: starting version 173
[    1.940575] usb 1-1.7: new high speed USB device number 4 using ehci_hcd
[    2.108402] usb 1-1.8: new full speed USB device number 5 using ehci_hcd
[    3.415856] Adding 4094972k swap on /dev/sda6.  Priority:-1 extents:1 across:4094972k SS
[    3.433851] lp: driver loaded but no devices found
[    3.448951] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[    3.473113] Bluetooth: Core ver 2.16
[    3.473169] NET: Registered protocol family 31
[    3.473171] Bluetooth: HCI device and connection manager initialized
[    3.473174] Bluetooth: HCI socket layer initialized
[    3.473177] Bluetooth: L2CAP socket layer initialized
[    3.474507] Bluetooth: SCO socket layer initialized
[    3.474909] mei: module is from the staging directory, the quality is unknown, you have been warned.
[    3.475386] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.475394] mei 0000:00:16.0: setting latency timer to 64
[    3.475820] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    3.476685] usbcore: registered new interface driver btusb
[    3.484677] cfg80211: Calling CRDA to update world regulatory domain
[    3.517687] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.517701] ath9k 0000:02:00.0: setting latency timer to 64
[    3.530015] ath: EEPROM regdomain: 0x60
[    3.530018] ath: EEPROM indicates we should expect a direct regpair map
[    3.530021] ath: Country alpha2 being used: 00
[    3.530023] ath: Regpair used: 0x60
[    3.530566] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    3.530570] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.530572] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    3.530576] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.530578] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    3.530581] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.530584] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    3.530587] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.530590] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    3.530593] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.530595] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    3.530598] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.530601] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    3.530604] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.530606] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    3.530609] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.530612] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    3.530615] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.530617] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    3.530620] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.530623] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    3.530644] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.530647] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    3.530650] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.530652] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    3.530655] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.530658] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[    3.530661] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    3.535394] wmi: Mapper loaded
[    3.540424] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[    3.541607] [drm] Initialized drm 1.1.0 20060810
[    3.562236] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    3.564849] Registered led device: ath9k-phy0
[    3.564860] ieee80211 phy0: Atheros AR9485 Rev:1 mem=0xffffc90005500000, irq=17
[    3.586526] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.586533] i915 0000:00:02.0: setting latency timer to 64
[    3.587575] type=1400 audit(1318994794.023:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=595 comm="apparmor_parser"
[    3.587977] type=1400 audit(1318994794.023:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=595 comm="apparmor_parser"
[    3.588223] type=1400 audit(1318994794.023:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=595 comm="apparmor_parser"
[    3.593925] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[    3.596091] Initializing rts5139 USB card reader driver...
[    3.616104] scsi6 : SCSI emulation for RTS5139 USB card reader
[    3.618862] scsi 6:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[    3.621391] usbcore: registered new interface driver rts5139
[    3.621394] Realtek rts5139 USB card reader support registered.
[    3.709797] i915 0000:00:02.0: irq 51 for MSI/MSI-X
[    3.709803] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    3.709805] [drm] Driver supports precise vblank timestamp query.
[    3.709842] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    3.741024] Linux video capture interface: v2.00
[    3.744303] uvcvideo: Found UVC 1.00 device USB 2.0 UVC 0.3M Webcam (064e:f300)
[    3.783977] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    3.788351] input: USB 2.0 UVC 0.3M Webcam as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input4
[    3.788417] usbcore: registered new interface driver uvcvideo
[    3.788419] USB Video Class driver (v1.1.0)
[    3.809071] asus_wmi: ASUS WMI generic driver loaded
[    3.811832] asus_wmi: Initialization: 0x1
[    3.811980] asus_wmi: BIOS WMI version: 1792.6
[    3.812039] asus_wmi: SFUN value: 0xa0877
[    3.815539] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[    3.815544] cfg80211: World regulatory domain updated:
[    3.815546] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    3.815549] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.815553] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    3.815556] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    3.815559] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.815562] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.817670] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input5
[    3.835651] type=1400 audit(1318994794.271:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=860 comm="apparmor_parser"
[    3.836360] type=1400 audit(1318994794.271:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=860 comm="apparmor_parser"
[    3.836609] type=1400 audit(1318994794.271:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=860 comm="apparmor_parser"
[    3.836989] type=1400 audit(1318994794.271:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=858 comm="apparmor_parser"
[    3.839082] type=1400 audit(1318994794.275:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=863 comm="apparmor_parser"
[    3.839513] type=1400 audit(1318994794.275:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=863 comm="apparmor_parser"
[    3.839518] 2.6.2X-Elan-touchpad-2011-04-12
[    3.856183] asus_wmi: Backlight controlled by ACPI video driver
[    3.870354] sd 6:0:0:0: Attached scsi generic sg1 type 0
[    3.872024] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    3.908925] init: failsafe main process (746) killed by TERM signal
[    3.911091] init: apport pre-start process (924) terminated with status 1
[    3.911672] init: alsa-restore main process (928) terminated with status 19
[    3.923716] init: apport post-stop process (953) terminated with status 1
[    4.013668] Bluetooth: RFCOMM TTY layer initialized
[    4.013673] Bluetooth: RFCOMM socket layer initialized
[    4.013675] Bluetooth: RFCOMM ver 1.11
[    4.015796] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.015799] Bluetooth: BNEP filters: protocol multicast
[    4.107623] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[    4.201948] elantech.c: PSMOUSE_CMD_RESET_BAT  param[0]=aa param[1]=0 param[2]=0
[    4.247160] elantech.c: Elantech version query result 0x00, 0x01, 0x64.
[    4.675181] input: ImExPS/2 Elantech Explorer Mouse as /devices/platform/i8042/serio4/input/input6
[    5.257794] fbcon: inteldrmfb (fb0) is primary device
[    5.257891] Console: switching to colour frame buffer device 200x56
[    5.257919] fb0: inteldrmfb frame buffer device
[    5.257920] drm: registered panic notifier
[    5.301467] ACPI Warning: _BQC returned an invalid level (20110413/video-473)
[    5.301801] acpi device:3e: registered as cooling_device4
[    5.302299] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
[    5.302350] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    5.302430] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    5.302517] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    5.302578] HDA Intel 0000:00:1b.0: irq 52 for MSI/MSI-X
[    5.302599] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    5.318290] init: plymouth-splash main process (1117) terminated with status 1
[    5.849659] hda_codec: ALC269VB: BIOS auto-probing.
[    5.855462] HDMI status: Pin=6 Presence_Detect=0 ELD_Valid=0
[    5.855629] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    5.855857] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    6.023560] ppdev: user-space parallel port driver
[    6.030395] audit_printk_skb: 24 callbacks suppressed
[    6.030398] type=1400 audit(1318994796.467:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1167 comm="apparmor_parser"
[    6.030796] type=1400 audit(1318994796.467:20): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1167 comm="apparmor_parser"
[    6.671095] wlan0: authenticate with 00:22:6b:67:a1:dc (try 1)
[    6.673233] wlan0: authenticated
[    6.689223] wlan0: associate with 00:22:6b:67:a1:dc (try 1)
[    6.693264] wlan0: RX AssocResp from 00:22:6b:67:a1:dc (capab=0x401 status=0 aid=6)
[    6.693273] wlan0: associated
[    6.697903] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    7.772372] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   15.284963] CPU1: Package power limit notification (total events = 1)
[   15.284967] CPU3: Package power limit notification (total events = 1)
[   15.284972] CPU2: Package power limit notification (total events = 1)
[   15.284976] CPU0: Package power limit notification (total events = 1)
[   15.297985] CPU3: Package power limit normal
[   15.297989] CPU2: Package power limit normal
[   15.297993] CPU0: Package power limit normal
[   15.297996] CPU1: Package power limit normal
[   17.581199] wlan0: no IPv6 routers present
[   83.554637] wlan0: deauthenticating from 00:22:6b:67:a1:dc by local choice (reason=3)
[   83.615645] cfg80211: All devices are disconnected, going to restore regulatory settings
[   83.615658] cfg80211: Restoring regulatory settings
[   83.615677] cfg80211: Calling CRDA to update world regulatory domain
[   83.625526] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   83.625531] cfg80211: World regulatory domain updated:
[   83.625533] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   83.625537] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   83.625540] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   83.625543] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   83.625545] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   83.625548] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   84.683872] wlan0: authenticate with 00:22:6b:67:a1:dc (try 1)
[   84.685952] wlan0: authenticated
[   84.701951] wlan0: associate with 00:22:6b:67:a1:dc (try 1)
[   84.706118] wlan0: RX ReassocResp from 00:22:6b:67:a1:dc (capab=0x401 status=0 aid=6)
[   84.706129] wlan0: associated
[   95.441055] wlan0: no IPv6 routers present
[  299.479336] [Hardware Error]: Machine check events logged
[  308.496955] cfg80211: All devices are disconnected, going to restore regulatory settings
[  308.496970] cfg80211: Restoring regulatory settings
[  308.496980] cfg80211: Calling CRDA to update world regulatory domain
[  308.503727] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  308.503736] cfg80211: World regulatory domain updated:
[  308.503741] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  308.503748] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  308.503754] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  308.503760] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  308.503765] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  308.503771] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  309.639711] wlan0: authenticate with 00:22:6b:67:a1:dc (try 1)
[  309.642031] wlan0: authenticated
[  309.658035] wlan0: associate with 00:22:6b:67:a1:dc (try 1)
[  309.661963] wlan0: RX ReassocResp from 00:22:6b:67:a1:dc (capab=0x401 status=0 aid=6)
[  309.661973] wlan0: associated
[  317.293060] CPU0: Package power limit notification (total events = 138)
[  317.293063] CPU2: Package power limit notification (total events = 138)
[  317.293089] CPU1: Package power limit notification (total events = 138)
[  317.293092] CPU3: Package power limit notification (total events = 138)
[  317.304069] CPU0: Package power limit normal
[  317.304073] CPU2: Package power limit normal
[  317.304077] CPU1: Package power limit normal
[  317.304080] CPU3: Package power limit normal
[  449.300047] [Hardware Error]: Machine check events logged
[  664.724885] CPU0: Package power limit notification (total events = 221)
[  664.724889] CPU2: Package power limit notification (total events = 221)
[  664.724901] CPU1: Package power limit notification (total events = 221)
[  664.724904] CPU3: Package power limit notification (total events = 221)
[  664.735867] CPU0: Package power limit normal
[  664.735881] CPU1: Package power limit normal
[  664.735890] CPU2: Package power limit normal
[  664.735898] CPU3: Package power limit normal
[  674.031080] [Hardware Error]: Machine check events logged
[  990.986979] CPU1: Package power limit notification (total events = 267)
[  990.986984] CPU3: Package power limit notification (total events = 267)
[  990.986988] CPU0: Package power limit notification (total events = 267)
[  990.986992] CPU2: Package power limit notification (total events = 267)
[  990.997981] CPU1: Package power limit normal
[  990.997991] CPU3: Package power limit normal
[  990.998002] CPU0: Package power limit normal
[  990.998011] CPU2: Package power limit normal
[ 1198.403580] [Hardware Error]: Machine check events logged
[ 1373.384321] CPU2: Package power limit notification (total events = 356)
[ 1373.384325] CPU0: Package power limit notification (total events = 356)
[ 1373.384337] CPU3: Package power limit notification (total events = 356)
[ 1373.384340] CPU1: Package power limit notification (total events = 356)
[ 1373.395303] CPU1: Package power limit normal
[ 1373.395312] CPU3: Package power limit normal
[ 1373.395344] CPU2: Package power limit normal
[ 1373.395353] CPU0: Package power limit normal
[ 1589.690074] compiz[1562] general protection ip:7f90d83a3ac0 sp:7fff8cc6a860 error:0 in libunityshell.so[7f90d825b000+222000]
[ 1674.704656] CPU2: Package power limit notification (total events = 582)
[ 1674.704660] CPU0: Package power limit notification (total events = 582)
[ 1674.704671] CPU1: Package power limit notification (total events = 582)
[ 1674.704674] CPU3: Package power limit notification (total events = 582)
[ 1674.715624] CPU2: Package power limit normal
[ 1674.715628] CPU3: Package power limit normal
[ 1674.715630] CPU1: Package power limit normal
[ 1674.715633] CPU0: Package power limit normal
tom@Zen:~$

---

### Post by campbelt on 2011-10-19
The other command returned this:

tom@Zen:~$ ls -la /devices/platform/i8042/serio4
ls: cannot access /devices/platform/i8042/serio4: No such file or directory
tom@Zen:~$

---

### Post by atliang on 2011-10-19
> **campbelt said:**
> The other command returned this:

tom@Zen:~$ ls -la /devices/platform/i8042/serio4
ls: cannot access /devices/platform/i8042/serio4: No such file or directory
tom@Zen:~$
Oops, should be 'ls -la /sys/devices/platform/i8042/serio4' instead.

Additionally, is the original Windoze 7 bundled in this Zenbook still bootable? It would be helpful if you can
also provide the Windoze driver information which can be obtained from Device Manager.

---

### Post by campbelt on 2011-10-19
Here it is:

tom@Zen:~$ ls -la /sys/devices/platform/i8042/serio4
total 0
drwxr-xr-x 5 root root    0 2011-10-19 01:00 .
drwxr-xr-x 8 root root    0 2011-10-19 01:00 ..
-rw-r--r-- 1 root root 4096 2011-10-19 06:09 bind_mode
-r--r--r-- 1 root root 4096 2011-10-19 06:00 description
lrwxrwxrwx 1 root root    0 2011-10-19 06:00 driver -> ../../../../bus/serio/drivers/psmouse
--w------- 1 root root 4096 2011-10-19 06:09 drvctl
drwxr-xr-x 2 root root    0 2011-10-19 06:09 id
drwxr-xr-x 3 root root    0 2011-10-19 06:00 input
-r--r--r-- 1 root root 4096 2011-10-19 06:09 modalias
drwxr-xr-x 2 root root    0 2011-10-19 06:09 power
-rw-r--r-- 1 root root 4096 2011-10-19 06:09 protocol
-rw-r--r-- 1 root root 4096 2011-10-19 06:09 rate
-rw-r--r-- 1 root root 4096 2011-10-19 06:09 resetafter
-rw-r--r-- 1 root root 4096 2011-10-19 06:09 resolution
-rw-r--r-- 1 root root 4096 2011-10-19 06:09 resync_time
lrwxrwxrwx 1 root root    0 2011-10-19 01:00 subsystem -> ../../../../bus/serio
-rw-r--r-- 1 root root 4096 2011-10-19 01:00 uevent
tom@Zen:~$ 


In Windows Device Manager the device is identified as a Sentelic device with driver V9.1.7.0

---

### Post by atliang on 2011-10-19
> **campbelt said:**
> Here it is:

tom@Zen:~$ ls -la /sys/devices/platform/i8042/serio4
total 0
drwxr-xr-x 5 root root    0 2011-10-19 01:00 .
drwxr-xr-x 8 root root    0 2011-10-19 01:00 ..
-rw-r--r-- 1 root root 4096 2011-10-19 06:09 bind_mode
-r--r--r-- 1 root root 4096 2011-10-19 06:00 description
lrwxrwxrwx 1 root root    0 2011-10-19 06:00 driver -> ../../../../bus/serio/drivers/psmouse
--w------- 1 root root 4096 2011-10-19 06:09 drvctl
drwxr-xr-x 2 root root    0 2011-10-19 06:09 id
drwxr-xr-x 3 root root    0 2011-10-19 06:00 input
-r--r--r-- 1 root root 4096 2011-10-19 06:09 modalias
drwxr-xr-x 2 root root    0 2011-10-19 06:09 power
-rw-r--r-- 1 root root 4096 2011-10-19 06:09 protocol
-rw-r--r-- 1 root root 4096 2011-10-19 06:09 rate
-rw-r--r-- 1 root root 4096 2011-10-19 06:09 resetafter
-rw-r--r-- 1 root root 4096 2011-10-19 06:09 resolution
-rw-r--r-- 1 root root 4096 2011-10-19 06:09 resync_time
lrwxrwxrwx 1 root root    0 2011-10-19 01:00 subsystem -> ../../../../bus/serio
-rw-r--r-- 1 root root 4096 2011-10-19 01:00 uevent
tom@Zen:~$ 


In Windows Device Manager the device is identified as a Sentelic device with driver V9.1.7.0

Weird.  I've tried to USB boot a copy of Ubuntu 11.10 downloaded from [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download), the dmesg indicates that it's a Sentelic pointing device rather than an Elantech one:

> dmesg
...
Finger Sensing Pad, hw: 14.3.1, sw: 1.0.0-K, buttons: 4
input: FSPPS/2 Sentelic FingerSensingPad as /devices/platform/i8042/serio4/...
...

Did you happen to make any manual reconfiguration of kernel after installation?  What does 'uname -a' say?

---

### Post by campbelt on 2011-10-19
tom@Zen:~$ uname -a
Linux Zen 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
tom@Zen:~$ 

I did not to my knowledge manually alter the kernel after install.

---

### Post by croddy on 2011-10-19
That output about the Elantech pad is weird. Which model do you have? I have the UX21 that Amazon's been selling, and my touchpad reports as:

```
I: Bus=0011 Vendor=0002 Product=000f Version=0000
N: Name="FSPPS/2 Sentelic FingerSensingPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input10
U: Uniq=
H: Handlers=mouse1 event10 
B: PROP=0
B: EV=7
B: KEY=670000 0 0 0 0
B: REL=143
```

FWIW I am thinking I can probably live without scrolling, if it comes to it, but what's really killing me is that there is no way to middle-click, at least that I can find... brutal.

---

### Post by campbelt on 2011-10-19
I have a UX31.

Now this is strange.  I booted off a USB stick and got this description with the dmsg command:

I: Bus=0011 Vendor=0002 Product=000f Version=0000
N: Name="FSPPS/2 Sentelic FingerSensingPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input7
U: Uniq=
H: Handlers=mouse0 event7 
B: PROP=0
B: EV=7
B: KEY=670000 0 0 0 0
B: REL=143

That's not what I got when I booted from the SDD installed version:

I: Bus=0011 Vendor=0002 Product=0006 Version=0000
N: Name="ImExPS/2 Elantech Explorer Mouse"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input5
U: Uniq=
H: Handlers=mouse0 event5
B: PROP=0
B: EV=7
B: KEY=1f0000 0 0 0 0
B: REL=143

Maybe I should do a clean install?

I still don't have a tab for touchpad in the "mouse and touchpad" adjustments app.

---

### Post by atliang on 2011-10-19
> **campbelt said:**
> I have a UX31.

Now this is strange.  I booted off a USB stick and got this description with the dmsg command:

I: Bus=0011 Vendor=0002 Product=000f Version=0000
N: Name="FSPPS/2 Sentelic FingerSensingPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input7
U: Uniq=
H: Handlers=mouse0 event7 
B: PROP=0
B: EV=7
B: KEY=670000 0 0 0 0
B: REL=143


  Great! This is identical to what I've seen on UX31. Now we can use some command line knobs to enable/disable on-pad clicking.

> **campbelt said:**
> 
That's not what I got when I booted from the SDD installed version:

I: Bus=0011 Vendor=0002 Product=0006 Version=0000
N: Name="ImExPS/2 Elantech Explorer Mouse"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input5
U: Uniq=
H: Handlers=mouse0 event5
B: PROP=0
B: EV=7
B: KEY=1f0000 0 0 0 0
B: REL=143

Maybe I should do a clean install?


  By any chance would you please provide the output of 'grep CONFIG_MOUSE /boot/config*' on the suspicious SDD version before doing a full re-installation?

> **campbelt said:**
> 
I still don't have a tab for touchpad in the "mouse and touchpad" adjustments app.

  Before the re-linked configuration GUI is ready, you can try following command to tweak FSP:

  # enable on-pad clicking
  # echo -n C > /sys/devices/platform/i8042/serio4/flags

  # disable on-pad clicking
  # echo -n c > /sys/devices/platform/i8042/serio4/flags

---

### Post by campbelt on 2011-10-19
Here you are:

tom@Zen:/boot$ grep CONFIG_MOUSE /boot/config*
CONFIG_MOUSE_PS2=m
CONFIG_MOUSE_PS2_ALPS=y
CONFIG_MOUSE_PS2_LOGIPS2PP=y
CONFIG_MOUSE_PS2_SYNAPTICS=y
CONFIG_MOUSE_PS2_LIFEBOOK=y
CONFIG_MOUSE_PS2_TRACKPOINT=y
CONFIG_MOUSE_PS2_ELANTECH=y
CONFIG_MOUSE_PS2_SENTELIC=y
# CONFIG_MOUSE_PS2_TOUCHKIT is not set
CONFIG_MOUSE_SERIAL=m
CONFIG_MOUSE_APPLETOUCH=m
CONFIG_MOUSE_BCM5974=m
CONFIG_MOUSE_VSXXXAA=m
CONFIG_MOUSE_GPIO=m
CONFIG_MOUSE_SYNAPTICS_I2C=m
tom@Zen:/boot$ 

I have also come across a file /etc/share/asus-touchpad.sh:


#!/bin/sh
[ -f /usr/share/acpi-support/state-funcs ] || exit 0 

. /usr/share/acpi-support/power-funcs

# if this is the right behavior, then this should be moved out of acpi-support
# to hal (or whatever is replacing hal for such events)
getXconsole

XINPUTNUM=`xinput list | grep 'SynPS/2 Synaptics TouchPad' | sed -n -e's/.*id=\([0-9]\+\).*/\1/p'`

# get the current state of the touchpad
TPSTATUS=`xinput list-props $XINPUTNUM | awk '/Synaptics Off/ { print $NF }'`

# if getting the status failed, exit
test -z $TPSTATUS && exit 1

if [ $TPSTATUS = 0 ]; then
   xinput set-int-prop $XINPUTNUM "Synaptics Off" 8 1
else
   xinput set-int-prop $XINPUTNUM "Synaptics Off" 8 0
fi


I'm not sure if the contents of this file are relevant to my problem or not.

---

### Post by atliang on 2011-10-20
> **campbelt said:**
> Here you are:

tom@Zen:/boot$ grep CONFIG_MOUSE /boot/config*
CONFIG_MOUSE_PS2=m
CONFIG_MOUSE_PS2_ALPS=y
CONFIG_MOUSE_PS2_LOGIPS2PP=y
CONFIG_MOUSE_PS2_SYNAPTICS=y
CONFIG_MOUSE_PS2_LIFEBOOK=y
CONFIG_MOUSE_PS2_TRACKPOINT=y
CONFIG_MOUSE_PS2_ELANTECH=y
CONFIG_MOUSE_PS2_SENTELIC=y
# CONFIG_MOUSE_PS2_TOUCHKIT is not set
CONFIG_MOUSE_SERIAL=m
CONFIG_MOUSE_APPLETOUCH=m
CONFIG_MOUSE_BCM5974=m
CONFIG_MOUSE_VSXXXAA=m
CONFIG_MOUSE_GPIO=m
CONFIG_MOUSE_SYNAPTICS_I2C=m
tom@Zen:/boot$ 

  Thank you.  However, why this version of Ubuntu misidentifies FSP as an Elantech alternative is still a mystery to me.  I'm wondering how did you install the current SSD version?  Is that the same source from your USB bootable one?

> **campbelt said:**
> I have also come across a file /etc/share/asus-touchpad.sh:


#!/bin/sh
[ -f /usr/share/acpi-support/state-funcs ] || exit 0 

. /usr/share/acpi-support/power-funcs
[...]

I'm not sure if the contents of this file are relevant to my problem or not.

  Unlikely.  On the other hand, once you have a freshly re-installed Ubuntu 11.10, replace /etc/share/asus-touchpad.sh with the following probably help on Fn-F9(assuming that the asus-laptop module and the ACPI support framework do work) switch:
```
#!/bin/sh
#
# Quick hack to switch on/off Sentelic Finger-sensing Pad
#
[ -f /usr/share/acpi-support/state-funcs ] || exit 0

. /usr/share/acpi-support/power-funcs

FLAGS=""

# looking for FSP control node
for d in /sys/devices/platform/i8042/serio*; do
        if [ -e ${d}/ver -a ! -z "`grep '^Sentelic FSP' ${d}/ver 2>/dev/null`" ]; then
                FLAGS=${d}/flags
                break
        fi
done

# exit if no active device was found
test -z ${FLAGS} && exit 1

if [ -z `grep C ${FLAGS}` ]; then
        echo -n C > ${FLAGS}
else
        echo -n c > ${FLAGS}
fi
```

---

### Post by campbelt on 2011-10-20
I have done a fresh install of 64 bit 11.10, and this is the output of "cat /proc/bus/input/devices:

I: Bus=0011 Vendor=0002 Product=000f Version=0000
N: Name="FSPPS/2 Sentelic FingerSensingPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input7
U: Uniq=
H: Handlers=mouse0 event7 
B: PROP=0
B: EV=7
B: KEY=670000 0 0 0 0
B: REL=143p


and this is grep CONFIG_MOUSE /boot/config*:

tom@Zen:~$ grep CONFIG_MOUSE /boot/config*
CONFIG_MOUSE_PS2=m
CONFIG_MOUSE_PS2_ALPS=y
CONFIG_MOUSE_PS2_LOGIPS2PP=y
CONFIG_MOUSE_PS2_SYNAPTICS=y
CONFIG_MOUSE_PS2_LIFEBOOK=y
CONFIG_MOUSE_PS2_TRACKPOINT=y
CONFIG_MOUSE_PS2_ELANTECH=y
CONFIG_MOUSE_PS2_SENTELIC=y
# CONFIG_MOUSE_PS2_TOUCHKIT is not set
CONFIG_MOUSE_SERIAL=m
CONFIG_MOUSE_APPLETOUCH=m
CONFIG_MOUSE_BCM5974=m
CONFIG_MOUSE_VSXXXAA=m
CONFIG_MOUSE_GPIO=m
CONFIG_MOUSE_SYNAPTICS_I2C=m


I still don't have a tab in the "Mouse and Touchpad" to adjust the touchpad settings.  At a minimum I'd like to turn of the tap to click feature.

Can anyone help me with this?

---

### Post by campbelt on 2011-10-21
Bump.

---

### Post by shakabra on 2011-10-22
Still no joy? There must be somebody out there knowledgeable enough to fix this. I wonder if this deserves a new bug report. 

"Do you pine for the nice days of minix-1.1, when men were men and wrote their own device drivers?"

~Linus Torvalds

Answer: Yes

~Shakabra

---

### Post by RR123RR on 2011-10-22
> **shakabra said:**
> Still no joy? There must be somebody out there knowledgeable enough to fix this. I wonder if this deserves a new bug report. 

We should probably start one for the touchpad, sleep crash, brightness changes on battery, switch to external screen, etc.

---

### Post by croddy on 2011-10-22
You folks get that deafening buzz from the headphone port? Plug some speakers in... mine is packed for return.

---

### Post by RR123RR on 2011-10-22
> **croddy said:**
> You folks get that deafening buzz from the headphone port? Plug some speakers in... mine is packed for return.

I get a perfect sound with my HD555 headphones... Try some other speakers / headphones maybe?

---

### Post by campbelt on 2011-10-22
I think there is a bug thread out there.  Do a search with keyword "Sentelic" on the bugs site and you will find it.  It was started 2 or 3 years ago with the last addition in 9/11.

The problem (as I understand it) is that Sentelic for *legal* reasons has limited the driver it makes available for linux, removing enough of its function to make the driver useless.  It would be great if open source developers could write a generic driver that would work, but that's me expecting some kind soul out there to do it for free.

---

### Post by atliang on 2011-10-24
> **campbelt said:**
> I have done a fresh install of 64 bit 11.10, and this is the output of "cat /proc/bus/input/devices:

I: Bus=0011 Vendor=0002 Product=000f Version=0000
N: Name="FSPPS/2 Sentelic FingerSensingPad"
[...]
I still don't have a tab in the "Mouse and Touchpad" to adjust the touchpad settings.  At a minimum I'd like to turn of the tap to click feature.

Can anyone help me with this?
Does the script included in my previous reply work?

---

### Post by RR123RR on 2011-10-24
> **atliang said:**
> Does the script included in my previous reply work?

I just tried and it doesn't disable the touch pad with Fn-F9 ...
(Didn't reboot but I'm guessing it's being called live and not cached somewhere by the ACPI subsystem)

---

### Post by campbelt on 2011-10-24
> **atliang said:**
> Does the script included in my previous reply work?

No, it did not turn off the tap to click feature.  I tried it several times.

---

### Post by atliang on 2011-10-25
> **campbelt said:**
> No, it did not turn off the tap to click feature.  I tried it several times.
Does running following command as root turn off the tap-to-click feature?
```
echo -n c > /sys/devices/platform/i8042/serio4/flags
```

---

### Post by campbelt on 2011-10-25
> **atliang said:**
> Does running following command as root turn off the tap-to-click feature?
```
echo -n c > /sys/devices/platform/i8042/serio4/flags
```

No, after running it tap to click is still active.  I ran it several times:


root@Zen:/# echo -n c > /sys/devices/platform/i8042/serio4/flags
root@Zen:/# echo -n c > /sys/devices/platform/i8042/serio4/flags
root@Zen:/#

---

### Post by naystin on 2011-10-26
> **campbelt said:**
> No, after running it tap to click is still active.  I ran it several times:


root@Zen:/# echo -n c > /sys/devices/platform/i8042/serio4/flags
root@Zen:/# echo -n c > /sys/devices/platform/i8042/serio4/flags
root@Zen:/#

I tried that too but it did not disable tap to click.

---

### Post by atliang on 2011-10-27
> **naystin said:**
> I tried that too but it did not disable tap to click.

Try to apply the following command first and see if the 'echo -n c ...' trick works or not:
```
echo -n 0x90 0x80 > /sys/devices/platform/i8042/serio4/setreg
```If it works, put the above code in /etc/rc.local.

---

### Post by naystin on 2011-10-27
> **atliang said:**
> Try to apply the following command first and see if the 'echo -n c ...' trick works or not:
```
echo -n 0x90 0x80 > /sys/devices/platform/i8042/serio4/setreg
```If it works, put the above code in /etc/rc.local.

Awesome, that helped!

---

### Post by shakabra on 2011-10-28
Naytsin, what did it help to do? It doesn't seem to do anything on my machine.

I've tried to get somebodies attention at ASUS using twitter, but nobody has responded. :-{

---

### Post by hasofanten on 2011-10-29
I don't know if this will help, I don't know what kernel version ubuntu 11.10 is using...

[http://en.gentoo-wiki.com/wiki/Sentelic_touchpad](http://en.gentoo-wiki.com/wiki/Sentelic_touchpad)

---

### Post by erandom on 2011-10-30
> **atliang said:**
> Try to apply the following command first and see if the 'echo -n c ...' trick works or not:
```
echo -n 0x90 0x80 > /sys/devices/platform/i8042/serio4/setreg
```If it works, put the above code in /etc/rc.local.

That worked for me as well (UX31, the touchpad is identified as Sentelic, not elantec).
FWIW, Sentelic's documentation ([http://www.mjmwired.net/kernel/Documentation/input/sentelic.txt#506](http://www.mjmwired.net/kernel/Documentation/input/sentelic.txt#506)) points to register 0x31. not 0x90.

---

### Post by shakabra on 2011-10-31
> **atliang said:**
> Try to apply the following command first and see if the 'echo -n c ...' trick works or not:
```
echo -n 0x90 0x80 > /sys/devices/platform/i8042/serio4/setreg
```If it works, put the above code in /etc/rc.local.

I don't really understand this code. From what I understand it just adds 0x90 0x80 to /sys/devices/platform.i8042/serio4. Does this disable 'tap-to-click"?

If so which registers would you use to enable vertical and horizontal scrolling?

---

### Post by LxndrPhnx on 2011-11-01
I'm on a ASUS G74xs running Ubuntu 11.04 64bit and 

```
echo -n 0x90 0x80 > /sys/devices/platform/i8042/serio4/setreg
echo -n c > /sys/devices/platform/i8042/serio4/flags
```

worked for me to disable tap-to-click.  I tried doing 

```
echo -n C > /sys/devices/platform/i8042/serio4/flags
```

to turn tap-to-click back on, but it isn't working.  How do I turn tap-to-touch back on?

---

### Post by shakabra on 2011-11-04
I have been in contact with the developer at Sentelic who is in charge of developing the Linux drivers. Here's what he has to say:

> Unless driver does some non-trivial works based on coordinates output,
I'm afraid that it won't have scrolling support at this moment. 

and:

> 
  Windows driver does scrolling in driver where current Linux driver
doesn't have such feature, yet.  Additionaly, given that the resource
is quite limited at this moment, I'm afraid that there is no firm
schedule for scrolling support in Linux driver. 

Doesn't seem too promising for us.

---

### Post by hasofanten on 2011-11-05
Thanks for the info Shakabra! Too bad though :(

---

### Post by GodzillaMonster on 2011-11-06
I can confirm that both of these lines

```

echo -n 0x90 0x80 > /sys/devices/platform/i8042/serio4/setreg
echo -n c > /sys/devices/platform/i8042/serio4/flags

```

should be placed in /etc/rc.local to disable tap-to-click on a ux31.

---

### Post by Galdrapiu on 2011-11-16
The upper script in  /etc/rc.local  dosn't works .... 

Ubuntu 11.10 32Bit "found" a Elantech Touchpad instead of Sentelic on my UX21 (Core i7).

$ uname -a
Linux PiuZenBook 3.0.0-12-generic-pae #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 i686 i686 i386 GNU/Linux

$ dmesg | grep PS/2
[    1.341935] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.344408] mousedev: PS/2 mouse device common for all mice
[    6.090217] input: PS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input9

$ cat /proc/bus/input/devices
[...]
I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Elantech Touchpad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input9
U: Uniq=
H: Handlers=mouse0 event9 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3
[...]

$grep CONFIG_MOUSE /boot/config*
[...]
/boot/config-3.0.0-12-generic-pae:CONFIG_MOUSE_PS2=m
/boot/config-3.0.0-12-generic-pae:CONFIG_MOUSE_PS2_ALPS=y
/boot/config-3.0.0-12-generic-pae:CONFIG_MOUSE_PS2_LOGIPS2PP=y
/boot/config-3.0.0-12-generic-pae:CONFIG_MOUSE_PS2_SYNAPTICS=y
/boot/config-3.0.0-12-generic-pae:CONFIG_MOUSE_PS2_LIFEBOOK=y
/boot/config-3.0.0-12-generic-pae:CONFIG_MOUSE_PS2_TRACKPOINT=y
/boot/config-3.0.0-12-generic-pae:CONFIG_MOUSE_PS2_ELANTECH=y
/boot/config-3.0.0-12-generic-pae:CONFIG_MOUSE_PS2_SENTELIC=y
/boot/config-3.0.0-12-generic-pae:# CONFIG_MOUSE_PS2_TOUCHKIT is not set
/boot/config-3.0.0-12-generic-pae:CONFIG_MOUSE_SERIAL=m
/boot/config-3.0.0-12-generic-pae:CONFIG_MOUSE_APPLETOUCH=m
/boot/config-3.0.0-12-generic-pae:CONFIG_MOUSE_BCM5974=m
/boot/config-3.0.0-12-generic-pae:CONFIG_MOUSE_INPORT=m
/boot/config-3.0.0-12-generic-pae:# CONFIG_MOUSE_ATIXL is not set
/boot/config-3.0.0-12-generic-pae:CONFIG_MOUSE_LOGIBM=m
/boot/config-3.0.0-12-generic-pae:CONFIG_MOUSE_PC110PAD=m
/boot/config-3.0.0-12-generic-pae:CONFIG_MOUSE_VSXXXAA=m
/boot/config-3.0.0-12-generic-pae:CONFIG_MOUSE_GPIO=m
/boot/config-3.0.0-12-generic-pae:CONFIG_MOUSE_SYNAPTICS_I2C=m



Anybody any idea?

Galdrapiu

---

### Post by GodzillaMonster on 2011-11-18
Not sure, Galdrapiu.

Most of the above is for the Sentilic touch pad.

Can this article, which details setting up an Elantec TP on a different ASUS machine, help you with your Zenbook? [http://wiki.daviddarts.com/Ubuntu_Maverick_on_the_Asus_UL30VT]("http://wiki.daviddarts.com/Ubuntu_Maverick_on_the_Asus_UL30VT")

---

### Post by Galdrapiu on 2011-11-19
Thanx GozillaMonster for the Link, it gave me some insights and learning ...

It seems, that some of the Asus UX Laptops have built in Elantec Tocuhpads.
Found some further information here: [http://ubuntuforums.org/showthread.php?t=1615564](http://ubuntuforums.org/showthread.php?t=1615564)
But didn't succed yet with 
- disable/enable "touch-on-tab"
- disable/enable Touchpad via Fn+F9
- enable multitouch

Have somebody else a Elantech Tochpad, and solved any of this problems?

Galdrapiu

---

