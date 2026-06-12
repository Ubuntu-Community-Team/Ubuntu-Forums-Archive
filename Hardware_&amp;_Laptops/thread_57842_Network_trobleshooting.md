---
title: "Network trobleshooting"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by cosmarium on 2005-08-18
I installed ubuntu today (and entered the linux world), in my Compaq Presario V2000 laptop today. I cannot navigate from ubuntu. I dont know how should I configure the internet. At home I use wireless at work I use wire connection.

During the installation there was a message about a problem with the network, I decided to continue the installation. I click on repair later.
There is a message in the network window saying connection is idle...

I am very new in this...

Thanks for any help, folks!

---

### Post by strandlooper on 2005-08-18
Hi
I'm not an expert but I went through some troubles because I have one of this "bad boys" an Acer TM 8100 so at least I can try to help.

To help please provide some details about your wireless card to find the right kernel module. When the module is loaded you can configure it. There are a lot of forum network issues which can help as well.

Open a shell for expample "Applications-SystemTools-RootTerminal" 
Type in the shell "iwconfig" and post the output.
post the outpot of "lscpi" and "lsmod | grep ip"

Cheers

---

### Post by cosmarium on 2005-08-18
Thanks in advance for your help. It navigate now, but in my work, where I use wire connection. At home, it does not. Here is the output of the commands in the shell.
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

carolina@:~$ lscpi
bash: lscpi: command not found
carolina@:~$ lsmod
Module                  Size  Used by
speedstep_centrino      7892  1
proc_intf               4100  0
freq_table              4100  1 speedstep_centrino
cpufreq_userspace       4572  1
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
pcmcia                 21380  2
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
i915                   18304  1
drm                    59412  2 i915
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  9
af_packet              20744  2
ohci1394               31876  0
yenta_socket           19584  0
pcmcia_core            53568  2 pcmcia,yenta_socket
8139cp                 19200  0
8139too                24320  0
mii                     4736  2 8139cp,8139too
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
i2c_i801                8076  0
i2c_core               21264  1 i2c_i801
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
ehci_hcd               29444  0
uhci_hcd               30224  0
usbcore               107384  3 ehci_hcd,uhci_hcd
intel_agp              20636  1
agpgart                31784  3 drm,intel_agp
rtc                    12216  0
evdev                   9088  1
joydev                  9408  0
md                     43856  0
tsdev                   7488  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
sr_mod                 16036  0
sbp2                   22408  0
scsi_mod              119936  2 sr_mod,sbp2
ieee1394              100408  2 ohci1394,sbp2
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  0
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  2 sr_mod,ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  3
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk
unix                   26164  874
thermal                13576  0
processor              22708  2 speedstep_centrino,thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

carolina@:~$ lscpi
bash: lscpi: command not found
carolina@:~$ lsmod
Module                  Size  Used by
speedstep_centrino      7892  1
proc_intf               4100  0
freq_table              4100  1 speedstep_centrino
cpufreq_userspace       4572  1
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
pcmcia                 21380  2
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
i915                   18304  1
drm                    59412  2 i915
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  9
af_packet              20744  2
ohci1394               31876  0
yenta_socket           19584  0
pcmcia_core            53568  2 pcmcia,yenta_socket
8139cp                 19200  0
8139too                24320  0
mii                     4736  2 8139cp,8139too
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
i2c_i801                8076  0
i2c_core               21264  1 i2c_i801
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
ehci_hcd               29444  0
uhci_hcd               30224  0
usbcore               107384  3 ehci_hcd,uhci_hcd
intel_agp              20636  1
agpgart                31784  3 drm,intel_agp
rtc                    12216  0
evdev                   9088  1
joydev                  9408  0
md                     43856  0
tsdev                   7488  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
sr_mod                 16036  0
sbp2                   22408  0
scsi_mod              119936  2 sr_mod,sbp2
ieee1394              100408  2 ohci1394,sbp2
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  0
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  2 sr_mod,ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  3
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk
unix                   26164  874
thermal                13576  0
processor              22708  2 speedstep_centrino,thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

---

### Post by strandlooper on 2005-08-18
Hi
Your wireless card wasn't detected by your system. Please find out what type of card do you use. Go to the Device Manger and have a look. At least somthing like Net 80211 should be somewhere noticed. Another possibility is to boot 
MS and see which type is detected. In my previous email there is a typing error. Please post the output of lspci and dmesg.
lspci lists the devices on the pci bus
dmesg shows kernel massages

Good luck :)

---

### Post by cosmarium on 2005-08-24
Hi, thanks for your help again. This is what I got:
carolina@:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0000:02:09.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:02:09.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:02:09.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:02:09.4 0805: Texas Instruments: Unknown device 8034
carolina@:~$ dmesg
Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
 BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
 BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000003dee0000 (usable)
 BIOS-e820: 000000003dee0000 - 000000003deec000 (ACPI data)
 BIOS-e820: 000000003deec000 - 000000003df00000 (ACPI NVS)
 BIOS-e820: 000000003df00000 - 0000000040000000 (reserved)
 BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
 BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
Warning only 896MB will be used.
Use a HIGHMEM enabled kernel.
896MB LOWMEM available.
found SMP MP-table at 000f7e30
On node 0 totalpages: 229376
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 225280 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
DMI present.
ACPI: RSDP (v000 HP                                    ) @ 0x000f7e00
ACPI: RSDT (v001 HP     09B8     0x06040000  LTP 0x00000000) @ 0x3dee75e4
ACPI: FADT (v001 HP     09B8     0x06040000 PTL  0x00000050) @ 0x3deebe8c
ACPI: HPET (v001 HP     09B8     0x06040000 PTL  0x00000000) @ 0x3deebf00
ACPI: MADT (v001 HP     09B8     0x06040000 PTL  0x00000050) @ 0x3deebf38
ACPI: MADT (v001 HP     09B8     0x06040000 PTL  0x00000000) @ 0x3deebf92
ACPI: BOOT (v001 HP     09B8     0x06040000  LTP 0x00000001) @ 0x3deebfd8
ACPI: SSDT (v001 HP     09B8     0x00000001 INTL 0x20030224) @ 0x3dee7a27
ACPI: SSDT (v001 HP     09B8     0x00002000 INTL 0x20030224) @ 0x3dee7624
ACPI: DSDT (v001 HP     09B8     0x06040000 MSFT 0x0100000e) @ 0x00000000
ACPI: PM-Timer IO Port: 0x1008
ACPI: Local APIC address 0xfee00000
ACPI: 2 duplicate APIC table ignored.
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Processor #0 6:13 APIC version 20
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
ACPI: HPET id: 0x8086a201 base: 0x0
Using ACPI (MADT) for SMP configuration information
Built 1 zonelists
Kernel command line: root=/dev/hda3 ro quiet splash
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
Initializing CPU#0
PID hash table entries: 4096 (order: 12, 65536 bytes)
Detected 1795.513 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 902044k/917504k available (1436k kernel code, 14928k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 3563.52 BogoMIPS (lpj=1781760)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: afe9fbbf 00000000 00000000 00000000 00000180 00000000
CPU: After vendor identify, caps: afe9fbbf 00000000 00000000 00000000 00000180 00000000
CPU: L1 I cache: 32K, L1 D cache: 32K
CPU: L2 cache: 2048K
CPU: After all inits, caps: afe9fbbf 00000000 00000000 00000040 00000180 00000000
CPU: Intel(R) Pentium(R) M processor 1.80GHz stepping 06
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=2 pin2=-1
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4248k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfd9c2, last bus=2
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
ACPI: PCI Interrupt Link [LNKC] (IRQs *4)
ACPI: PCI Interrupt Link [LNKD] (IRQs *3)
ACPI: PCI Interrupt Link [LNKE] (IRQs *11)
ACPI: PCI Interrupt Link [LNKF] (IRQs 3) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs *4)
ACPI: PCI Interrupt Link [LNKH] (IRQs *3)
ACPI: Embedded Controller [H_EC] (gpe 29)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 6 devices
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
audit(1124907640.144:0): initialized
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
ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 17 (level, low) -> IRQ 17
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 1
Cannot allocate resource for EISA slot 2
Cannot allocate resource for EISA slot 3
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 8192 buckets, 64Kbytes
TCP: Hash tables configured (established 262144 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
PCIB  LAN PS2K PSM2 USB0 USB1 USB2 USB7
ACPI: (supports S0 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4248KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
ACPI: Thermal Zone [THRM] (67 C)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH4: IDE controller at PCI slot 0000:00:1f.1
PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
ICH4: chipset revision 3
ICH4: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0x1818-0x181f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: TOSHIBA MK6025GAS, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 117210240 sectors (60011 MB), CHS=65535/16/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 > p3
Probing IDE interface ide1...
hdc: DV-W24EW, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (455 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 755012k swap on /dev/hda6.  Priority:-1 extents:1
EXT3 FS on hda3, internal journal
hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2193kB Cache
Uniform CD-ROM driver Revision: 3.20
lp: driver loaded but no devices found
mice: PS/2 mouse device common for all mice
Synaptics Touchpad, model: 1
 Firmware: 5.10
 Sensor: 37
 new absolute packet format
 Touchpad has extended capability bits
 -> multifinger detection
 -> palm detection
input: SynPS/2 Synaptics TouchPad on isa0060/serio1
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
Capability LSM initialized
ts: Compaq touchscreen protocol output
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
Real Time Clock Driver v1.12
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 855 Chipset.
agpgart: Maximum main memory to use for agp memory: 816M
agpgart: Detected 32636K stolen memory.
agpgart: AGP aperture is 128M @ 0xe8000000
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.0: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 16, io base 0x1820
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
uhci_hcd 0000:00:1d.1: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 19, io base 0x1840
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
uhci_hcd 0000:00:1d.2: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 18, io base 0x1860
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 23, pci mem 0xe0100000
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
PCI: cache line size of 32 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
hw_random: cannot enable RNG, aborting
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:00:1f.5 to 64
intel8x0_measure_ac97_clock: measured 49899 usecs
intel8x0: clocking to 48000
8139too Fast Ethernet driver 0.9.27
ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
eth0: RealTek RTL8139 at 0x3000, 00:c0:9f:6b:5f:4e, IRQ 16
eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
ACPI: PCI interrupt 0000:02:09.0[A] -> GSI 20 (level, low) -> IRQ 20
Yenta: CardBus bridge found at 0000:02:09.0 [103c:3080]
Yenta: ISA IRQ mask 0x0cf8, PCI irq 20
Socket status: 30000006
eth0: link up, 100Mbps, full-duplex, lpa 0x43E1
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:02:09.2[C] -> GSI 22 (level, low) -> IRQ 22
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[e0208000-e02087ff]  Max Packet=[2048]
NET: Registered protocol family 17
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f0000328f80]
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: AC Adapter [ACAD] (off-line)
[drm] Initialized drm 1.0.0 20040925
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[drm] Initialized i915 1.2.0 20040405 on minor 0: Intel Corp. 82852/855GM Integrated Graphics Device
[drm] Initialized i915 1.2.0 20040405 on minor 1: Intel Corp. 82852/855GM Integrated Graphics Device (#2)
mtrr: base(0xe8020000) is not aligned on a size(0x3c0000) boundary
ACPI: Battery Slot [BAT0] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Lid Switch [LID0]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
cs: IO port probe 0x0100-0x04ff: excluding 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: excluding 0x800-0x807
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
eth0: no IPv6 routers present
carolina@:~$

Besides, there is a message when I just start the session, that says: Could not look up internet address for. This could prevent GNOME from operating correctly. It may be possible to correct the problem by adding to the file/etc/hosts. Login anyway, OR try again. I click login anyway and it navigates by using the wire connection.
well hope it helps, and hope to find a solution. Thanks in advance,
bless you,
Cosmarium

---

### Post by strandlooper on 2005-09-01
Hi Cosmarium
Sorry for the late response. I spent some days with my family without laptop.

The posted information says your machine uses a Broadcom BCM4306 card. According to the threads in this forum it can be tricky to get it work. The good news is there is a HOWTO which might help.
 
                ** HOW TO: Configure wireless cards with Broadcom chipsets**


[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom)



Good Speed

Strandlooper

---

### Post by vijaya2e on 2008-07-09
> **strandlooper said:**
> hi
I'm Not An Expert But I Went Through Some Troubles Because I Have One Of This "bad Boys" An Acer Tm 8100 So At Least I Can Try To Help.

To Help Please Provide Some Details About Your Wireless Card To Find The Right Kernel Module. When The Module Is Loaded You Can Configure It. There Are A Lot Of Forum Network Issues Which Can Help As Well.

Open A Shell For Expample "applications-systemtools-rootterminal" 
Type In The Shell "iwconfig" And Post The Output.
Post The Outpot Of "lscpi" And "lsmod | Grep Ip"

Cheers

Hi
I Want To Know Clearly About Network Troubleshooting

---

