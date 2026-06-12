---
title: "About to ditch Ubuntu, Please Help Me"
date: 2005-08-11
forum: Hardware &amp; Laptops
---

### Post by ux5b2 on 2005-08-11
Hi, I have posted a few threads on this matter and have read around everywhere but have found no solution.  The problem is that I cannot get ACPI working correctly (or whatever I need for fan and cpu management).  I am new to linux so if you can please explain in detail.

I have a Dell 700m and and it is clearly running hotter than it did when I use WinXP.  The fan is on pretty much all the time (though not at the highest speed) and the battery doesnt seem to last as long as it did in windows.

I do not know how to check the temperature of the cpu with this machine since all the programs I downloaded for this dont work.  When I go into /proc/acpi/thermal_zone  I have two folders: THRS and THRC.  THRS seems to linger around 58C while THRC remains in the 40's.  I do not know what these represent.   Please help me since I love Ubuntu and if my laptop continues to run this hot I will have to switch back to windows.

Thanks

---

### Post by blind0wl on 2005-08-11
Whats your dmesg output look like?  Please post.

---

### Post by ux5b2 on 2005-08-12
dmesg produces the following:

Linux version 2.6.10-5-386 (buildd@vernadsky) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Fri Jun 24 16:53:01 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
 BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000001eee0000 (usable)
 BIOS-e820: 000000001eee0000 - 000000001eeeb000 (ACPI data)
 BIOS-e820: 000000001eeeb000 - 000000001ef00000 (ACPI NVS)
 BIOS-e820: 000000001ef00000 - 0000000020000000 (reserved)
 BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
 BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
494MB LOWMEM available.
On node 0 totalpages: 126688
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 122592 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.3 present.
ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6cd0
ACPI: RSDT (v001 PTLTD  Montara  0x06040000  LTP 0x00000000) @ 0x1eee5c9b
ACPI: FADT (v001 INTEL  MONTARAG 0x06040000 PTL  0x00000050) @ 0x1eeeaa2d
ACPI: SSDT (v001 INTEL    GV3Ref 0x06040000 MSFT 0x0100000e) @ 0x1eeeaaa1
ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1eeeafd8
ACPI: DSDT (v001 INTEL  MONTARAG 0x06040000 MSFT 0x0100000e) @ 0x00000000
ACPI: PM-Timer IO Port: 0x1008
Built 1 zonelists
Kernel command line: root=/dev/hda1 ro quiet splash
Local APIC disabled by BIOS -- you can enable it with "lapic"
mapped APIC to ffffd000 (013e4000)
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 32768 bytes)
Detected 598.315 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 494748k/506752k available (1436k kernel code, 11344k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 1183.74 BogoMIPS (lpj=591872)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000
CPU: After vendor identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000
CPU: L1 I cache: 32K, L1 D cache: 32K
CPU: L2 cache: 2048K
CPU: After all inits, caps: afe9f9bf 00000000 00000000 00000040 00000180 00000000
CPU: Intel(R) Pentium(R) M processor 1.60GHz stepping 06
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ACPI: setting ELCR to 0200 (from 0c00)
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4300k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfd812, last bus=2
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
ACPI: PCI Interrupt Link [LNKB] (IRQs *10 11)
ACPI: PCI Interrupt Link [LNKC] (IRQs *10 11)
ACPI: PCI Interrupt Link [LNKD] (IRQs *10 11)
ACPI: PCI Interrupt Link [LNKE] (IRQs *10 11)
ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs 10 *11)
ACPI: Embedded Controller [EC0] (gpe 28)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 8 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
Simple Boot Flag at 0x36 set to 0x1
audit: initializing netlink socket (disabled)
audit(1123828015.436:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
PCI: setting IRQ 10 as level-triggered
ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 10 (level, low) -> IRQ 10
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 1
Cannot allocate resource for EISA slot 2
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
LID0 SLPB LANC MODM
ACPI: (supports S0 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4300KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
ACPI: Processor [CPU0] (supports 8 throttling states)
ACPI: Thermal Zone [THRC] (37 C)
ACPI: Thermal Zone [THRS] (27 C)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH4: IDE controller at PCI slot 0000:00:1f.1
PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 10 (level, low) -> IRQ 10
ICH4: chipset revision 3
ICH4: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0x1818-0x181f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: FUJITSU MHT2060AT PL, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 117210240 sectors (60011 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1
Probing IDE interface ide1...
hdc: PHILIPS CD-RW/DVD-ROM CDD5263, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda1, internal journal
hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
pnp: Device 00:05 activated.
parport: PnPBIOS parport detected.
pnp: Device 00:05 disabled.
lp: driver loaded but no devices found
mice: PS/2 mouse device common for all mice
Synaptics Touchpad, model: 1
 Firmware: 6.2
 180 degree mounted touchpad
 Sensor: 37
 new absolute packet format
 Touchpad has extended capability bits
 -> multifinger detection
 -> palm detection
input: SynPS/2 Synaptics TouchPad on isa0060/serio1
ts: Compaq touchscreen protocol output
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
Real Time Clock Driver v1.12
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 855 Chipset.
agpgart: Maximum main memory to use for agp memory: 423M
agpgart: Detected 16252K stolen memory.
agpgart: AGP aperture is 128M @ 0xe8000000
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 11 (level, low) -> IRQ 11
uhci_hcd 0000:00:1d.0: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 11, io base 0x1820
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 10 (level, low) -> IRQ 10
uhci_hcd 0000:00:1d.1: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 10, io base 0x1840
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 10 (level, low) -> IRQ 10
uhci_hcd 0000:00:1d.2: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 10, io base 0x1860
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 11 (level, low) -> IRQ 11
ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 11, pci mem 0xe0100000
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
PCI: cache line size of 32 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 5 ports detected
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
hw_random hardware driver 1.0.0 loaded
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 10 (level, low) -> IRQ 10
PCI: Setting latency timer of device 0000:00:1f.5 to 64
intel8x0_measure_ac97_clock: measured 49344 usecs
intel8x0: clocking to 48000
ieee80211_crypt: registered algorithm 'NULL'
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
ACPI: PCI interrupt 0000:02:01.0[A] -> GSI 10 (level, low) -> IRQ 10
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
ACPI: PCI interrupt 0000:02:04.0[A] -> GSI 10 (level, low) -> IRQ 10
Yenta: CardBus bridge found at 0000:02:04.0 [1028:018d]
Yenta: ISA IRQ mask 0x00f8, PCI irq 10
Socket status: 30000006
ACPI: PCI interrupt 0000:02:04.1[B] -> GSI 10 (level, low) -> IRQ 10
Yenta: CardBus bridge found at 0000:02:04.1 [1028:018d]
Yenta: ISA IRQ mask 0x00f8, PCI irq 10
Socket status: 30000006
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
PCI: Enabling device 0000:02:04.2 (0000 -> 0002)
ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 10
ACPI: PCI interrupt 0000:02:04.2[C] -> GSI 10 (level, low) -> IRQ 10
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[e0208000-e02087ff]  Max Packet=[2048]
b44.c:v0.95 (Aug 3, 2004)
ACPI: PCI interrupt 0000:02:05.0[A] -> GSI 10 (level, low) -> IRQ 10
eth1: Broadcom 4400 10/100BaseT Ethernet 00:0f:1f:b1:dd:7c
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[811f0f007cddb100]
b44: eth1: Link is down.
NET: Registered protocol family 17
ACPI: AC Adapter [ADP1] (off-line)
ACPI: Battery Slot [BAT0] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Lid Switch [LID0]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
[drm] Initialized drm 1.0.0 20040925
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 11 (level, low) -> IRQ 11
[drm] Initialized i915 1.2.0 20040405 on minor 0: Intel Corp. 82852/855GM Integrated Graphics Device
[drm] Initialized i915 1.2.0 20040405 on minor 1: Intel Corp. 82852/855GM Integrated Graphics Device (#2)
mtrr: base(0xe8020000) is not aligned on a size(0x640000) boundary
ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
NET: Registered protocol family 10
IPv6 over IPv4 tunneling driver
Disabled Privacy Extensions on device c02f0500(lo)
eth0: duplicate address detected!
cs: IO port probe 0x0100-0x04ff: excluding 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: excluding 0x800-0x80f
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
eth0: duplicate address detected!

---

### Post by blind0wl on 2005-08-12
In console what does 'top' say your using CPU percentage wise?

Could be a rogue process pumping up the CPU.  ACPI looks like its working ok.

---

### Post by mlord on 2005-08-12
"echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"

Or find the GNOME GUI dialog that will do this for you.

For Kubuntu, it's in the "Power Control" menu of the KDE "Control Center".

Cheers

---

### Post by ux5b2 on 2005-08-14
I did a 'top' in the terminal and everything seems to be running correctly except for python which seems to be taking about 4% of the CPU at all times.  I do not need python to be running.  Could this be the problem and if so how can I fix it. (Also what is Xorg which also seems to be taking about 4%?)

As for the last reply, could you please explain in more detail since Im new to this.

Thank you very much.

---

### Post by kokiri on 2005-08-14
Xorg is the GUI server...ie it's the server displaying what you're looking at right now and lets you use the mouse and all that good stuff.

---

### Post by JLB on 2005-08-14
[QUOTE=kokiri]Xorg is the GUI server...ie it's the server displaying what you're looking at right now and lets you use the mouse and all that good stuff.[/QUOTE]

what he is trying to say is to ECHO that command to a file using the terminal (the dos box). He uses Kubuntu which is KDE. You use gnome, so he said to find the Gnome equivelant.

What you want to do is this:

Applications - System - Terminal

and at the prompt type out the following, hit enter, then enter your password.

```
sudo echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

For what it is worth, my "scaling_governor" file only contains ```
userspace
```

---

### Post by ux5b2 on 2005-08-15
I tried entering:

sudo echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

However, I get an error: bash: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: No such file or directory


I tried to go into the directory and the directory cpu0 is empty.

What should I do?

Thank you.

---

### Post by dezgot on 2005-08-16
There is a tray applet that shows the speed that your cpu is running at,  If you right click on the tray and add the cpu frequency monitor (im in windows now so I can't recall the exact names) it should verify that it is running at 1.6ghz all the time.

There are other power management dameons that you can install via Syaptic, try powernowd.  You can customize how it works or enable a verbose mode that will tell you exactly what it is doing.  I think there is another one called cpufreqd or something like that if powernowd is what you have now.  Powernowd despite the name is not only for amd chips.

Sorry about the vague suggestions, but try installing powernowd or cpufreqd and using the man pages to see if you can get either one setup nicely, and then add them to startup like that.  But first check that cpu scaling is not working correctly by looking at that tray applet.

---

### Post by Bored1ed on 2005-08-18
I have a Dell Inspiron 600m and I'm having the same problems. I am completely new to Linux so I'm not looking for answers because I'd probably just get confused and give up...but thought I thought I'd let you know your not alone.  :)

---

