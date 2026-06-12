---
title: "sound card not detected"
date: 2005-12-05
forum: General Help
---

### Post by serenity on 2005-12-05
i've been having a problem with ALSA detecting my sound card during boot up ever since i installed Ubuntu 5.10, usually it was about every other time i booted the sound card wouldn't be detected which wasn't too bad since rebooting usually fixed it

however, a couple reboots ago, every time i start up it doesn't detect my sound card at all any more


on the boot up screen when the sound card is detected it'll look something like:
> 
.......
.......
setting up alsa card 0 OK
..........
setting up alsa OK
..........

and when it isn't detected:
> 
.........
.........
.........
.........
setting up alsa OK
.........

it completely skips the line about 'card 0' when it doesn't work


my sound card is an integrated soundmax III, but linux detects it as nForce audio, and according to alsa that's intel8x0

my lspci:
> 
0000:00:00.0 Host bridge: nVidia Corporation nForce CPU bridge (rev b2)
0000:00:00.1 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
0000:00:00.2 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
0000:00:00.3 RAM memory: nVidia Corporation: Unknown device 01aa (rev b2)
0000:00:01.0 ISA bridge: nVidia Corporation nForce ISA Bridge (rev c3)
0000:00:01.1 SMBus: nVidia Corporation nForce PCI System Management (rev c1)
0000:00:02.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
0000:00:03.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce Ethernet Controller (rev c2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce Audio (rev c2)
0000:00:08.0 PCI bridge: nVidia Corporation nForce PCI-to-PCI bridge (rev c2)
0000:00:09.0 IDE interface: nVidia Corporation nForce IDE (rev c3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce AGP to PCI Bridge (rev b2)
0000:01:00.0 VGA compatible controller: nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] (rev b1)
0000:02:07.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)


i've seen alot of other threads about non-working sound, but i'm really lost as to what i should do or where to begin

---

### Post by schdefan on 2005-12-05
can print the output of
```
$ cat /proc/asound/cards
```
and
```
$ lsmod|grep snd
```
when you run alsamixer in a terminal do you see the mixer?

schdefan

---

### Post by serenity on 2005-12-05
```
$ cat /proc/asound/cards
```
--- no soundcards ---


```
lsmod|grep snd
```
snd_intel8x0           33344  0
snd_ac97_codec         84028  1 snd_intel8x0
snd_pcm_oss            53152  0
snd_mixer_oss          19392  1 snd_pcm_oss
snd_pcm                89032  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24260  1 snd_pcm
snd                    55172  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9696  1 snd
snd_page_alloc         10696  2 snd_intel8x0,snd_pcm


```
alsamixer
```
alsamixer: function snd_ctl_open failed for default: No such file or directory

---

### Post by serenity on 2005-12-05
ok, just rebooted, and now the sound card is detected (after about 10 reboots where it wasn't)

with the soundcard detected:

```
$ cat /proc/asound/cards
```
0 [nForce         ]: NFORCE - NVidia nForce
                     NVidia nForce with AD1885 at 0xf8502000, irq 20

```
lsmod|grep snd
```
snd_intel8x0           33344  3
snd_ac97_codec         84028  1 snd_intel8x0
snd_pcm_oss            53152  0
snd_mixer_oss          19392  1 snd_pcm_oss
snd_pcm                89032  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24260  2 snd_pcm
snd                    55172  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9696  1 snd
snd_page_alloc         10696  2 snd_intel8x0,snd_pcm

```
alsamixer
```
yes, it displays now


any idea what's going on, so it'll detect the sound card every time ??

---

### Post by schdefan on 2005-12-06
Have you checked your BIOS settings?
When the soundcard is not detected search in ```
dmesg | grep alsa
```
and post the errrors.
This is a very strange behaviour. 
schdefan

---

### Post by serenity on 2005-12-06
the only thing i'm seeing in my bios for sound is under pci devices, it lists
```

Compaq Audio Device -- IRQ 10

```


i am dual booting with Windows XP, and the sound always works fine with that

i had been noticing that alot of the times when i had been in Windows and then restarted and went into Ubuntu was when the sound wouldn't work, but that 10 times rebooting in a row where the sound card wasn't detected was just into ubuntu each time

what's dmesg | grep alsa ?? is that a terminal command, a folder .... ??

---

### Post by schdefan on 2005-12-07
from the manpage of dmesg:

> dmesg is used to examine or control the kernel ring buffer.
The program helps users to print out their bootup messages

and grep alsa is afilter to look for alsa related errors.

**EDIT:**
grep alsa does not help in dmesg as i noticed.

schdefan

---

### Post by serenity on 2005-12-08
okay here's dmesg when the soundcard isn't detected:

```

: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294672.284000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.286000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.286000] io scheduler noop registered
[4294672.286000] io scheduler anticipatory registered
[4294672.286000] io scheduler deadline registered
[4294672.286000] io scheduler cfq registered
[4294672.287000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294672.287000] NET: Registered protocol family 2
[4294672.296000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294672.296000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[4294672.296000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294672.296000] TCP: Hash tables configured (established 16384 bind 16384)
[4294672.296000] NET: Registered protocol family 8
[4294672.296000] NET: Registered protocol family 20
[4294672.296000] ACPI wakeup devices:
[4294672.296000] PCI0 COM1  HUB USB0 USB1 MAC0 PBTN
[4294672.296000] ACPI: (supports S0 S1 S3 S4 S5)
[4294672.297000] Freeing unused kernel memory: 168k freed
[4294672.314000] vga16fb: initializing
[4294672.314000] vga16fb: mapped to 0xc00a0000
[4294672.461000] Console: switching to colour frame buffer device 80x30
[4294672.461000] fb0: VGA16 VGA frame buffer device
[4294672.474000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294673.611000] Capability LSM initialized
[4294673.624000] NET: Registered protocol family 1
[4294673.643000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294673.643000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294673.643000] ACPI: bus type ide registered
[4294673.647000] SCSI subsystem initialized
[4294673.648000] libata version 1.11 loaded.
[4294673.653000] NFORCE: IDE controller at PCI slot 0000:00:09.0
[4294673.653000] NFORCE: chipset revision 195
[4294673.653000] NFORCE: not 100% native mode: will probe irqs later
[4294673.653000] NFORCE: BIOS didn't set cable bits correctly. Enabling workaround.
[4294673.653000] NFORCE: 0000:00:09.0 (rev c3) UDMA100 controller
[4294673.653000]     ide0: BM-DMA at 0x24c0-0x24c7, BIOS settings: hda:DMA, hdb:DMA
[4294673.653000]     ide1: BM-DMA at 0x24c8-0x24cf, BIOS settings: hdc:DMA, hdd:DMA
[4294673.653000] Probing IDE interface ide0...
[4294673.917000] hda: ST380020A, ATA DISK drive
[4294674.172000] hdb: ST3160023A, ATA DISK drive
[4294674.229000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.229000] Probing IDE interface ide1...
[4294674.901000] hdc: OPTORITEDVD RW DD1205, ATAPI CD/DVD-ROM drive
[4294675.615000] hdd: LITE-ON LTR-52327S, ATAPI CD/DVD-ROM drive
[4294675.666000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.666000] Probing IDE interface ide2...
[4294676.179000] Probing IDE interface ide3...
[4294676.691000] Probing IDE interface ide4...
[4294677.203000] Probing IDE interface ide5...
[4294677.719000] hda: max request size: 128KiB
[4294677.720000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[4294677.720000] hda: cache flushes not supported
[4294677.720000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 < p5 p6 >
[4294677.770000] hdb: max request size: 1024KiB
[4294677.771000] hdb: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(100)
[4294677.771000] hdb: cache flushes supported
[4294677.771000]  /dev/ide/host0/bus0/target1/lun0: p1 p2 < p5 >
[4294677.804000] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294677.804000] Uniform CD-ROM driver Revision: 3.20
[4294677.806000] hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
[4294678.223000] Attempting manual resume
[4294678.224000] swsusp: Suspend partition has wrong signature?
[4294678.289000] usbcore: registered new driver usbfs
[4294678.289000] usbcore: registered new driver hub
[4294678.290000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294678.291000] ACPI: PCI Interrupt Link [LNKU] enabled at IRQ 22
[4294678.291000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKU] -> GSI 22 (level, high) -> IRQ 22
[4294678.291000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[4294678.291000] ohci_hcd 0000:00:02.0: nVidia Corporation nForce USB Controller
[4294678.291000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[4294678.291000] ohci_hcd 0000:00:02.0: irq 22, io mem 0xf8500000
[4294678.294000] hub 1-0:1.0: USB hub found
[4294678.294000] hub 1-0:1.0: 4 ports detected
[4294678.297000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKU] -> GSI 22 (level, high) -> IRQ 22
[4294678.297000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[4294678.297000] ohci_hcd 0000:00:03.0: nVidia Corporation nForce USB Controller (#2)
[4294678.297000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[4294678.297000] ohci_hcd 0000:00:03.0: irq 22, io mem 0xf8501000
[4294678.350000] hub 2-0:1.0: USB hub found
[4294678.350000] hub 2-0:1.0: 2 ports detected
[4294678.372000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.41.
[4294678.373000] ACPI: PCI Interrupt Link [LNKJ] enabled at IRQ 21
[4294678.373000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKJ] -> GSI 21 (level, high) -> IRQ 21
[4294678.373000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[4294678.383000] usb 1-1: new full speed USB device using ohci_hcd and address 2
[4294678.491000] hub 1-1:1.0: USB hub found
[4294678.494000] hub 1-1:1.0: 2 ports detected
[4294678.749000] usb 1-1.1: new full speed USB device using ohci_hcd and address 3
[4294678.885000] eth0: forcedeth.c: subsystem: 00e11:00a8 bound to 0000:00:04.0
[4294678.958000] usb 1-1.2: new full speed USB device using ohci_hcd and address 4
[4294681.536000] ACPI: CPU0 (power states: C1[C1])
[4294681.536000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294681.762000] Attempting manual resume
[4294681.763000] swsusp: Suspend partition has wrong signature?
[4294681.779000] kjournald starting.  Commit interval 5 seconds
[4294681.779000] EXT3-fs: mounted filesystem with ordered data mode.
[4294683.355000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294688.458000] Adding 1204832k swap on /dev/hda6.  Priority:-1 extents:1
[4294810.431000] EXT3 FS on hda2, internal journal
[4294816.753000] parport: PnPBIOS parport detected.
[4294816.753000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294816.842000] lp0: using parport0 (interrupt-driven).
[4294816.877000] mice: PS/2 mouse device common for all mice
[4294816.928000] Linux agpgart interface v0.101 (c) Dave Jones
[4294816.961000] nvidia: module license 'NVIDIA' taints kernel.
[4294817.004000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 19
[4294817.004000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKE] -> GSI 19 (level, high) -> IRQ 19
[4294817.005000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7667  Fri Jun 17 07:01:04 PDT 2005
[4294817.235000] input: PS2++ Logitech MX Mouse on isa0060/serio1
[4294817.498000] ts: Compaq touchscreen protocol output
[4294820.349000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294821.284000] cdrom: open failed.
[4294821.323000] cdrom: open failed.
[4294822.165000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4294822.249000] NTFS volume version 3.1.
[4294822.285000] NTFS volume version 3.1.
[4294822.320000] NTFS volume version 3.1.
[4294823.899000] agpgart: Detected NVIDIA nForce chipset
[4294823.921000] agpgart: AGP aperture is 64M @ 0xec000000
[4294824.638000] PCI: Enabling device 0000:00:06.0 (0000 -> 0003)
[4294824.638000] ACPI: PCI Interrupt Link [LNKL] enabled at IRQ 20
[4294824.638000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKL] -> GSI 20 (level, high) -> IRQ 20
[4294824.638000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[4294824.890000] AC'97 warm reset still in progress? [0xffffffff]
[4294824.890000] ACPI: PCI interrupt for device 0000:00:06.0 disabled
[4294824.890000] Intel ICH: probe of 0000:00:06.0 failed with error -5
[4294825.610000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294825.617000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294825.617000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294825.796000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294825.796000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294827.844000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x043D pid 0x0069[4294827.874000] usbcore: registered new driver usblp
[4294827.874000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[4294828.037000] Real Time Clock Driver v1.12
[4294828.134000] input: PC Speaker
[4294828.404000] Floppy drive(s): fd0 is 1.44M
[4294828.417000] FDC 0 is a post-1991 82077
[4294830.262000] NET: Registered protocol family 17
[4294835.628000] NET: Registered protocol family 10
[4294835.628000] Disabled Privacy Extensions on device c0321b80(lo)
[4294835.628000] IPv6 over IPv4 tunneling driver
[4294837.174000] ACPI: Power Button (FF) [PWRF]
[4294837.174000] ACPI: Power Button (CM) [PBTN]
[4294837.300000] ibm_acpi: ec object not found
[4294843.354000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294843.354000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294843.354000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294845.377000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294845.377000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294845.377000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294845.968000] eth0: no IPv6 routers present
[4294851.160000] apm: BIOS not found.
[4294852.887000] ip_tables: (C) 2000-2002 Netfilter core team
[4294852.922000] ip_conntrack version 2.1 (3839 buckets, 30712 max) - 248 bytes per conntrack
[4294853.993000] Bluetooth: Core ver 2.7
[4294853.993000] NET: Registered protocol family 31
[4294853.993000] Bluetooth: HCI device and connection manager initialized
[4294853.993000] Bluetooth: HCI socket layer initialized
[4294854.013000] Bluetooth: L2CAP ver 2.7
[4294854.013000] Bluetooth: L2CAP socket layer initialized
[4294854.035000] Bluetooth: RFCOMM ver 1.5
[4294854.035000] Bluetooth: RFCOMM socket layer initialized
[4294854.035000] Bluetooth: RFCOMM TTY layer initialized
[4295045.248000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295045.248000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295045.381000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295045.381000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295045.451000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295045.451000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295045.545000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295045.545000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295045.615000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295045.615000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295045.670000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295045.670000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295045.779000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295045.779000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295045.834000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295045.834000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295045.932000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295045.932000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295045.988000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295045.988000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295046.058000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295046.058000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295046.152000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295046.152000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295046.223000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295046.223000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295046.317000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295046.317000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295046.503000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295046.503000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295046.597000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295046.597000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295046.744000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295046.744000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295046.838000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295046.838000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295047.724000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295047.724000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295047.856000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295047.856000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295049.246000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295049.246000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295049.378000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295049.378000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295059.232000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295059.232000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295059.958000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295059.958000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295060.144000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295060.144000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295060.238000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295060.238000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295060.424000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295060.424000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295060.557000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295060.557000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295181.609000] Inbound IN=eth0 OUT= MAC=00:40:ca:2b:41:6b:00:10:db:70:b0:88:08:00 SRC=134.121.253.174 DST=134.121.241.83 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=30312 DF PROTO=TCP SPT=1793 DPT=135 WINDOW=16384 RES=0x00 SYN URGP=0
[4295184.517000] Inbound IN=eth0 OUT= MAC=00:40:ca:2b:41:6b:00:10:db:70:b0:88:08:00 SRC=134.121.253.174 DST=134.121.241.83 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=30482 DF PROTO=TCP SPT=1793 DPT=135 WINDOW=16384 RES=0x00 SYN URGP=0

```

---

### Post by schdefan on 2005-12-08
Can you run an 
```
#update-pciids
```
Because you said it is a soundmax III, but ubuntu detects it as nForce audio.
This will download a new version of the PCI ID list.
Maybe there is something wrong.
Have you looked in the alsa database on [http://www.alsa-project.org/alsa-doc/]("http://www.alsa-project.org/alsa-doc/") for your soundcard

If you boot from a LiveCD can you hear some sound. Find out the module of your soundcard with > $lsmod | grep snd
And if your soundcard is not detected load this module with > #modprobe <modulename>

schdefan

---

