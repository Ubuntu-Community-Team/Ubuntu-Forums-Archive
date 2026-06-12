---
title: "sound card issues: no more sound"
date: 2005-05-18
forum: Hardware &amp; Laptops
---

### Post by rekurzion on 2005-05-18
I dual boot between XP and Hoary.  XP I use for my music production and Ubuntu for everything else.  I recently add two new USB audio devices in XP:
1) a usb midi keyboard
2) a usb audio/midi interface (basically a better sounds card through usb)

I recently noticed that I no longer can play CD's MP3's DVD's (the sound that is) in linux.  I am thinking that this is a problem but unaware of how to fix the problem.  Uninstalling the drivers in XP does not seem to help.  This is the output from cat /dev/sndstat:

Sound Driver:3.8.1a-980706 (ALSA v1.0.6 emulation code)
Kernel: Linux laibon 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
SiS SI7012 with STAC9721/23 at 0xdc00, irq 11

Audio devices:
0: SiS SI7012 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: SigmaTel STAC9721/23

So it can see what sound card I have.  Had to run ast-register (never had that happen before) when trying to run the default CD player in Ubuntu.  After that, CD player just gave a drive error message when run.

However, I can get system sounds like beeps and the nice soudns when you log on and off.  But nothing else.  No longer have the option for a sound icon.  

I did start Linux once with the usb audio/midi interface still plugged in by accident.  Is it possible that even though the drivers for the device were made for XP that during bootup linux tried to recognize the audio device and overwrote something?

thanks

---

### Post by arunsub on 2005-05-18
Did you try the options in this thread?
[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)

---

### Post by rekurzion on 2005-08-23
ok, 

I have tried the thread to no solution.  Now sometimes I am getting bootup errors as such:
Buffer I/O error on device hdc, logical block 1 hdc

However when I pop in a CD CDPlayer automatically opens it but does not play anything.  When I close CDPlayer and open it again I get "Drive Error".  When I posted the original message I was getting system sounds.  Like beeps and stuff, now I can't get any sounds anywhere.  When I play a DVD in xine, i get picture with no sound.  This all happened after upgrading to Hoary.  I have a winbook J4 laptop, dual boot with windows xp pro.  In XP Pro I make music using Reason and Cubase with an external USB Tascam US-122 audio/midi device.  Now in windows when i can't get sound except through Reason and Cubase when using the external sound card.  Using the Winbook sound card everything is ok.  

This is frustrating, it seems everytim I turn on the system something with the sound is getting worse.  I don't want to wipe and reinstall back to Horty, but I might have to.  But everything was working in Hoary just fine for a few days.

This is output to dmesg:

*************************************************************************
Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000001bff0000 (usable)
 BIOS-e820: 000000001bff0000 - 000000001bff8000 (ACPI data)
 BIOS-e820: 000000001bff8000 - 000000001c000000 (ACPI NVS)
 BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000ffee0000 - 00000000fff0ffff (reserved)
 BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
447MB LOWMEM available.
On node 0 totalpages: 114672
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 110576 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.3 present.
ACPI: RSDP (v000 AMI                                   ) @ 0x000fa7a0
ACPI: RSDT (v001 AMIINT SiS650XX 0x00000010 MSFT 0x0100000b) @ 0x1bff0000
ACPI: FADT (v002 AMIINT SiS650XX 0x00000011 MSFT 0x0100000b) @ 0x1bff0030
ACPI: DSDT (v001    SiS      650 0x00001000 MSFT 0x0100000d) @ 0x00000000
ACPI: PM-Timer IO Port: 0x808
Built 1 zonelists
Kernel command line: root=/dev/hda3 ro quiet splash
Local APIC disabled by BIOS -- you can enable it with "lapic"
mapped APIC to ffffd000 (01386000)
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 32768 bytes)
Detected 1992.440 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 447132k/458688k available (1436k kernel code, 10968k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 3948.54 BogoMIPS (lpj=1974272)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: bfebf9ff 00000000 00000000 00000000 00000000 00000000
CPU: Trace cache: 12K uops, L1 D cache: 8K
CPU: L2 cache: 512K
CPU: After all inits, caps: bfebf9ff 00000000 00000000 00000080 00000000 00000000
CPU: Intel(R) Pentium(R) 4 CPU 2.00GHz stepping 07
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ACPI: setting ELCR to 0200 (from 0800)
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4300k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
Uncovering SIS961 that hid as a SIS503 (compatible=1)
Enabling SiS 96x SMBus.
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: Power Resource [URP1] (off)
ACPI: Power Resource [URP2] (off)
ACPI: Power Resource [FDDP] (off)
ACPI: Power Resource [LPTP] (off)
ACPI: Embedded Controller [EC] (gpe 26)
ACPI: PCI Interrupt Link [LNKA] (IRQs *11)
ACPI: PCI Interrupt Link [LNKB] (IRQs 11) *0, disabled.
ACPI: PCI Interrupt Link [LNKC] (IRQs 11) *0, disabled.
ACPI: PCI Interrupt Link [LNKD] (IRQs 11) *0, disabled.
ACPI: PCI Interrupt Link [LNKE] (IRQs *11)
ACPI: PCI Interrupt Link [LNKF] (IRQs *11)
ACPI: PCI Interrupt Link [LNKG] (IRQs *11)
ACPI: PCI Interrupt Link [LNKH] (IRQs *11)
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
audit: initializing netlink socket (disabled)
audit(1124812083.017:0): initialized
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
ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI interrupt 0000:00:02.6[C] -> GSI 11 (level, low) -> IRQ 11
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
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
USB1 USB2  LAN MODM CBUS MPC1 MPC2 
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4300KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
SIS5513: IDE controller at PCI slot 0000:00:02.5
SIS5513: chipset revision 208
SIS5513: not 100% native mode: will probe irqs later
SIS5513: SiS 961 MuTIOL IDE UDMA100 controller
    ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hda: IC25N030ATCS04-0, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 58605120 sectors (30005 MB) w/1768KiB Cache, CHS=58140/16/63, UDMA(33)
hda: cache flushes not supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 p7 > p3
Probing IDE interface ide1...
hdc: Slimtype COMBO LSC-24081, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Unable to find swap-space signature
EXT3 FS on hda3, internal journal
Synaptics Touchpad, model: 1
 Firmware: 5.9
 180 degree mounted touchpad
 Sensor: 15
 new absolute packet format
 Touchpad has extended capability bits
 -> four buttons
 -> multifinger detection
 -> palm detection
input: SynPS/2 Synaptics TouchPad on isa0060/serio1
mice: PS/2 mouse device common for all mice
ts: Compaq touchscreen protocol output
hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
lp0: using parport0 (interrupt-driven).
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda6, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
Unable to find swap-space signature
Real Time Clock Driver v1.12
input: PC Speaker
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected SiS 650 chipset
agpgart: Maximum main memory to use for agp memory: 380M
agpgart: AGP aperture is 64M @ 0xe0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
i2c-sis96x version 1.0.0
sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:02.2[D] -> GSI 11 (level, low) -> IRQ 11
ohci_hcd 0000:00:02.2: Silicon Integrated Systems [SiS] USB 1.0 Controller
ohci_hcd 0000:00:02.2: irq 11, pci mem 0xdfffa000
ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:02.3[A] -> GSI 11 (level, low) -> IRQ 11
ohci_hcd 0000:00:02.3: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
ohci_hcd 0000:00:02.3: irq 11, pci mem 0xdfffb000
ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 3 ports detected
usb 2-1: new low speed USB device using ohci_hcd and address 2
usbcore: registered new driver hiddev
input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:02.3-1
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
ACPI: PCI interrupt 0000:00:02.7[C] -> GSI 11 (level, low) -> IRQ 11
intel8x0_measure_ac97_clock: measured 49198 usecs
intel8x0: clocking to 48000
sis900.c: v1.08.07 11/02/2003
ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:03.0[A] -> GSI 11 (level, low) -> IRQ 11
0000:00:03.0: Realtek RTL8201 PHY transceiver found at address 1.
0000:00:03.0: Using transceiver found at address 1 as default
eth0: SiS 900 PCI Fast Ethernet at 0xcc00, IRQ 11, 00:50:eb:0b:ca:65.
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 11 (level, low) -> IRQ 11
Yenta: CardBus bridge found at 0000:00:0a.0 [1039:b731]
Yenta: adjusting diagnostic: 40 -> 60
Yenta: Using CSCINT to route CSC interrupts to PCI
Yenta: Routing CardBus interrupts to PCI
Yenta TI: socket 0000:00:0a.0, mfunc 0x000c1002, devctl 0x44
Yenta: ISA IRQ mask 0x0400, PCI irq 11
Socket status: 30000006
NET: Registered protocol family 17
eth0: Media Link On 100mbps full-duplex 
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: AC Adapter [ADP0] (off-line)
ACPI: Battery Slot [BAT0] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Lid Switch [LID0]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
eth0: no IPv6 routers present
cs: IO port probe 0x0100-0x04ff: excluding 0x200-0x20f 0x480-0x48f 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: excluding 0x818-0x86f
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
program eject is using a deprecated SCSI ioctl, please convert it to SG_IO
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 64
attempt to access beyond end of device
hdc: rw=0, want=1199340, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=1198316, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=1198092, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=1199332, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=1198308, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=1198084, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=1198740, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=1197716, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=1197492, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=1198732, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=1197708, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=1197484, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=984076, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=983052, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=982828, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=984068, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=983044, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=982820, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=983476, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=982452, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=982228, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=983468, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=982444, limit=535736
attempt to access beyond end of device
hdc: rw=0, want=982220, limit=535736
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 1248
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 1024
UDF-fs: No partition found (1)
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 64
isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

***************************************************************************

both <lsof /dev/dsp> and <lsof /dev/snd/*> return nothing.

rekurzion@laibon:~ $ lsmod | grep snd
snd_intel8x0           29984  1 
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0 
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  2 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

rekurzion@laibon:~ $ mount /dev/hdc
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

rekurzion@laibon:~ $ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:00:0a.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

I have tweeked alsamixer all kinds of ways and still no result.  Help is much appreciated.

---

### Post by chaumurky on 2005-09-06
EDIT: thought I had the same problem. Fixed now - somewhere along the line I accidentally selected "Exchange Front/Surround" in kmix...  :roll:

---

