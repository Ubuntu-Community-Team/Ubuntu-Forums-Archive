---
title: "SCSI Raid (basically have no idea what im doing!)"
date: 2005-05-15
forum: Hardware &amp; Laptops
---

### Post by lozzd on 2005-05-15
Hey,

I set up a new server yesterday for use with apache as a webserver. Everything working fine, apart from the SCSI RAID.
I have two identical 36gb 10,000rpm drives that I set up in the BIOS to be RAID1 (and it spent ages creating the array, etc) and that was all fine, they show as a pair of drives in the SCSISelect utility thing.

I installed ubuntu last night, and it detected both drives.. strange, i thought, but never mind it must still mirror. So i selected the first of the two drives, and everything is running fine but the drives are clearly not RAID'd.. The second hard drive isn't doing anything at all!
What have I done wrong? Is it easily fixable? (without loosing my data also!) 

Thanks
Laurie  ](*,)

---

### Post by nad on 2005-05-15
"it spent ages creating the array"

This should not have taken "ages".

"they show as a pair of drives in the SCSISelect utility thing"

Did you activate the raid? Please be more specific here with make and model of controller and your exact configuration.

---

### Post by alastair on 2005-05-15
What SCSI card?

There is a chance that a BIOS level RAID will not be recognised by Linux, unless a Linux driver exists to use it. You would be better off in the this case using Linux s/w RAID. You can set this up at install time.

---

### Post by lozzd on 2005-05-15
Sorry for the complete lack of information. 
When I say it took ages, it was obviously copying the data from one drive to the other. But yeah it does take a long time. Is that bad? It moves along at a constant pce, then gets to 99% and says "Read failed on ID 1. Continue?" in which case I press yes and it carrys on file, and says rebuild complete. Then both drives are "optimal", which is how its supposed to be.. and yes the RAID is activated and bootable etc.
The card is shown up in Linux device manager as "AIC-7901A U320 w/HostRAID" (its an adaptec one built onto the motherboard) and it uses the SCSISelect raid utility to set up this "HostRAID" stuff. 
I will have to try and look for a linux driver, because although I can manually update the second drive by rebuilding it, the whole point was it doing it automatically! 
Thanks for your help.

Laurie

---

### Post by lozzd on 2005-05-15
I've found some interesting stuff:
[http://www.linuxquestions.org/hcl/showproduct.php?product=2126&sort=8&cat=all&page=1](http://www.linuxquestions.org/hcl/showproduct.php?product=2126&sort=8&cat=all&page=1)

Apparently its supported by "aacraid" - whatever that is and however I install that. More investigation needed!

[http://linux.dell.com/files/aacraid/](http://linux.dell.com/files/aacraid/)

Looks like I can get a patch here. Is this wise? will it even work for a version of ubuntu that's already installed? I'm quite a newbie, i'm really hoping I can just patch up and it'll work. 

Thanks
Laurie

---

### Post by lozzd on 2005-05-15
[QUOTE=lozzd]I've found some interesting stuff:
[http://www.linuxquestions.org/hcl/showproduct.php?product=2126&sort=8&cat=all&page=1](http://www.linuxquestions.org/hcl/showproduct.php?product=2126&sort=8&cat=all&page=1)

Apparently its supported by "aacraid" - whatever that is and however I install that. More investigation needed!

[http://linux.dell.com/files/aacraid/](http://linux.dell.com/files/aacraid/)

Looks like I can get a patch here. Is this wise? will it even work for a version of ubuntu that's already installed? I'm quite a newbie, i'm really hoping I can just patch up and it'll work. 

Thanks
Laurie[/QUOTE]
 Alot of talking to myself here...

Did a search for aacraid on the Filesystem and theres already some modules called aacraid... how do i enable them!?

Laurie

---

### Post by nad on 2005-05-15
man aacraid and find out.

---

### Post by lozzd on 2005-05-16
[QUOTE=nad]man aacraid and find out.[/QUOTE]
 No man pages found for aacraid im afraid.

Damnit.. It seems like it should be so easy but I just don't know how. 

Thanks
Laurie

---

### Post by lozzd on 2005-05-16
> 
Check to see if the kernel has the SCSI adapter driver built in, or if it is using some type of generic support.

cd /usr/src/linux
make menuconfig

It is always a good idea (in my mind) to compile a kernel for your hardware rather than a distrobutions CD trying to do it for you. Verify that each device is supported and remove unwanted or un-used support that you don't need.

You can gather the necessary infomation about your system by typing
lsmod
lspci


I found this on another page. I did the thing at the top and enabled loads of modules and stuff, and then did the lsmod and it does have mentions of aacraid, but i think thats because i added them using.. a command I dont remember. Now I have restarted and no difference. It picks up all the details of the SCSI card correctly and finds both devices fine its obviously just using the wrong low level driver to access them (i.e. bypassing the RAID) but I really have no idea how to change which drive it needs.
Would really really appreciate help if anyone can! 

Thanks for your help so far.

Laurie

---

### Post by lozzd on 2005-05-16
dmesg output...

```

lozzd@zebedee:~$ sudo dmesg
Password:
Linux version 2.6.10-5-686-smp (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 SMP Tue Apr 5 12:41:40 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
 BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
 BIOS-e820: 000000007fff0000 - 000000007ffff000 (ACPI data)
 BIOS-e820: 000000007ffff000 - 0000000080000000 (ACPI NVS)
 BIOS-e820: 00000000fec00000 - 00000000fed00000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
1151MB HIGHMEM available.
896MB LOWMEM available.
found SMP MP-table at 000ff780
On node 0 totalpages: 524272
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 225280 pages, LIFO batch:16
  HighMem zone: 294896 pages, LIFO batch:16
DMI 2.3 present.
ACPI: RSDP (v000 INTEL                                 ) @ 0x000ff9b0
ACPI: RSDT (v001 INTEL  SBR20    0x00000001 MSFT 0x01000000) @ 0x7fff0000
ACPI: FADT (v001 INTEL  SBR20    0x00000001 MSFT 0x01000000) @ 0x7fff0030
ACPI: MADT (v001 INTEL  SBR20    0x00000001 MSFT 0x01000000) @ 0x7fff00b0
ACPI: OEMR (v001 INTEL  SBR20    0x00000001 MSFT 0x01000000) @ 0x7fff0140
ACPI: DSDT (v001  INTEL    SBR20 0x00000100 INTL 0x20020918) @ 0x00000000
ACPI: PM-Timer IO Port: 0x408
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Processor #0 15:2 APIC version 20
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x06] enabled)
Processor #6 15:2 APIC version 20
ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Processor #1 15:2 APIC version 20
ACPI: LAPIC (acpi_id[0x03] lapic_id[0x07] enabled)
Processor #7 15:2 APIC version 20
ACPI: LAPIC_NMI (acpi_id[0x00] high level lint[0x1])
ACPI: LAPIC_NMI (acpi_id[0x01] high level lint[0x1])
ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
ACPI: IOAPIC (id[0x09] address[0xfec81000] gsi_base[24])
IOAPIC[1]: apic_id 9, version 32, address 0xfec81000, GSI 24-47
ACPI: IOAPIC (id[0x0a] address[0xfec81400] gsi_base[48])
IOAPIC[2]: apic_id 10, version 32, address 0xfec81400, GSI 48-71
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Enabling APIC mode:  Flat.  Using 3 I/O APICs
Using ACPI (MADT) for SMP configuration information
Built 1 zonelists
Kernel command line: root=/dev/sda1 ro quiet splash
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
mapped IOAPIC to ffffb000 (fec81000)
mapped IOAPIC to ffffa000 (fec81400)
Initializing CPU#0
PID hash table entries: 4096 (order: 12, 65536 bytes)
Detected 1994.897 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 2071240k/2097088k available (1604k kernel code, 24900k reserved, 719k data, 192k init, 1179584k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 3948.54 BogoMIPS (lpj=1974272)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000
CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000
CPU: Trace cache: 12K uops, L1 D cache: 8K
CPU: L2 cache: 512K
CPU: Physical Processor ID: 0
CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
CPU0: Intel P4/Xeon Extended MCE MSRs (12) available
CPU0: Thermal monitoring enabled
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
ACPI: Looking for DSDT in initrd... not found!
    ACPI-0586: *** Warning: Type override - [DEB_] had invalid type (Integer) for Scope operator, changed to (Scope)
    ACPI-0586: *** Warning: Type override - [MLIB] had invalid type (Integer) for Scope operator, changed to (Scope)
    ACPI-0586: *** Warning: Type override - [DATA] had invalid type (String) for Scope operator, changed to (Scope)
    ACPI-0586: *** Warning: Type override - [SIO_] had invalid type (String) for Scope operator, changed to (Scope)
    ACPI-0586: *** Warning: Type override - [LEDP] had invalid type (String) for Scope operator, changed to (Scope)
    ACPI-0586: *** Warning: Type override - [GPEN] had invalid type (String) for Scope operator, changed to (Scope)
    ACPI-0586: *** Warning: Type override - [GPST] had invalid type (String) for Scope operator, changed to (Scope)
    ACPI-0586: *** Warning: Type override - [GP1N] had invalid type (String) for Scope operator, changed to (Scope)
    ACPI-0586: *** Warning: Type override - [WUES] had invalid type (String) for Scope operator, changed to (Scope)
    ACPI-0586: *** Warning: Type override - [WUSE] had invalid type (String) for Scope operator, changed to (Scope)
    ACPI-0586: *** Warning: Type override - [SBID] had invalid type (String) for Scope operator, changed to (Scope)
    ACPI-0586: *** Warning: Type override - [SWCE] had invalid type (String) for Scope operator, changed to (Scope)
    ACPI-0586: *** Warning: Type override - [SMIR] had invalid type (String) for Scope operator, changed to (Scope)
CPU0: Intel(R) Xeon(TM) CPU 2.00GHz stepping 07
per-CPU timeslice cutoff: 1463.40 usecs.
task migration cache decay timeout: 2 msecs.
Booting processor 1/1 eip 3000
Initializing CPU#1
Calibrating delay loop... 3981.31 BogoMIPS (lpj=1990656)
CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000
CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000
CPU: Trace cache: 12K uops, L1 D cache: 8K
CPU: L2 cache: 512K
CPU: Physical Processor ID: 0
CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#1.
CPU1: Intel P4/Xeon Extended MCE MSRs (12) available
CPU1: Thermal monitoring enabled
CPU1: Intel(R) Xeon(TM) CPU 2.00GHz stepping 07
Booting processor 2/6 eip 3000
Initializing CPU#2
Calibrating delay loop... 3981.31 BogoMIPS (lpj=1990656)
CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000
CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000
CPU: Trace cache: 12K uops, L1 D cache: 8K
CPU: L2 cache: 512K
CPU: Physical Processor ID: 3
CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#2.
CPU2: Intel P4/Xeon Extended MCE MSRs (12) available
CPU2: Thermal monitoring enabled
CPU2: Intel(R) Xeon(TM) CPU 2.00GHz stepping 07
Booting processor 3/7 eip 3000
Initializing CPU#3
Calibrating delay loop... 3981.31 BogoMIPS (lpj=1990656)
CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000
CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000
CPU: Trace cache: 12K uops, L1 D cache: 8K
CPU: L2 cache: 512K
CPU: Physical Processor ID: 3
CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#3.
CPU3: Intel P4/Xeon Extended MCE MSRs (12) available
CPU3: Thermal monitoring enabled
CPU3: Intel(R) Xeon(TM) CPU 2.00GHz stepping 07
Total of 4 processors activated (15892.48 BogoMIPS).
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=2 pin2=-1
checking TSC synchronization across 4 CPUs: passed.
Brought up 4 CPUs
CPU0:
 domain 0: span 03
  groups: 01 02
  domain 1: span 0f
   groups: 03 0c
CPU1:
 domain 0: span 03
  groups: 02 01
  domain 1: span 0f
   groups: 03 0c
CPU2:
 domain 0: span 0c
  groups: 04 08
  domain 1: span 0f
   groups: 0c 03
CPU3:
 domain 0: span 0c
  groups: 08 04
  domain 1: span 0f
   groups: 0c 03
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4536k freed
NET: Registered protocol family 16
PCI: PCI BIOS revision 2.10 entry at 0xfdb55, last bus=4
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
ACPI: Embedded Controller [EC0] (gpe 8)
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs *11 12 14 15)
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5.P5P6._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5.P5P7._PRT]
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 12 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
pnp: 00:00: ioport range 0x3f0-0x3f1 has been reserved
pnp: 00:00: ioport range 0x400-0x4bf could not be reserved
pnp: 00:00: ioport range 0x4d0-0x4d1 has been reserved
pnp: 00:00: ioport range 0x40b-0x40b could not be reserved
pnp: 00:00: ioport range 0x4d6-0x4d6 has been reserved
audit: initializing netlink socket (disabled)
audit(1116276268.826:0): initialized
highmem bounce pool size: 64 pages
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
NET: Registered protocol family 2
IP: routing cache hash table of 16384 buckets, 128Kbytes
TCP: Hash tables configured (established 524288 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
SLPB PS2M PS2K UAR1 UAR2 USB1 USB2 USB3 SMB0 P0P1 P5P6 P5P7
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4536KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 192k freed
NET: Registered protocol family 1
SCSI subsystem initialized
ACPI: PCI interrupt 0000:03:03.0[A] -> GSI 26 (level, low) -> IRQ 26
scsi0 : Adaptec AIC79XX PCI-X SCSI HBA DRIVER, Rev 1.3.11
        <Adaptec AIC7901A Ultra320 SCSI adapter>
        aic7901A: Ultra320 Wide Channel A, SCSI Id=7, PCI-X 67-100Mhz, 512 SCBs

elevator: using anticipatory as default io scheduler
(scsi0:A:1): 40.000MB/s transfers (20.000MHz, 16bit)
(scsi0:A:2): 40.000MB/s transfers (20.000MHz, 16bit)
  Vendor: MAXTOR    Model: ATLAS10K4_36WLS   Rev: DFV0
  Type:   Direct-Access                      ANSI SCSI revision: 03
scsi0:A:1:0: Tagged Queuing enabled.  Depth 32
  Vendor: MAXTOR    Model: ATLAS10K4_36WLS   Rev: DFV0
  Type:   Direct-Access                      ANSI SCSI revision: 03
scsi0:A:2:0: Tagged Queuing enabled.  Depth 32
SCSI device sda: 71833096 512-byte hdwr sectors (36779 MB)
SCSI device sda: drive cache: write through
SCSI device sda: 71833096 512-byte hdwr sectors (36779 MB)
SCSI device sda: drive cache: write through
 /dev/scsi/host0/bus0/target1/lun0: p1 p2 < p5 >
Attached scsi disk sda at scsi0, channel 0, id 1, lun 0
SCSI device sdb: 71833096 512-byte hdwr sectors (36779 MB)
SCSI device sdb: drive cache: write through
SCSI device sdb: 71833096 512-byte hdwr sectors (36779 MB)
SCSI device sdb: drive cache: write through
 /dev/scsi/host0/bus0/target2/lun0: p1 p2 < p5 >
Attached scsi disk sdb at scsi0, channel 0, id 2, lun 0
Stopping tasks: ==|
Freeing memory... done (466 pages freed)
Restarting tasks... done
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 1485972k swap on /dev/sda5.  Priority:-1 extents:1
EXT3 FS on sda1, internal journal
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Probing IDE interface ide0...
hda: CDU5211, ATAPI CD/DVD-ROM drive
Probing IDE interface ide1...
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: ATAPI 52X CD-ROM drive, 120kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
Red Hat/Adaptec aacraid driver (1.1.2-lk2 Apr  5 2005)
ts: Compaq touchscreen protocol output
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-686-smp
Floppy drive(s): fd0 is 1.44M
FDC 0 is a National Semiconductor PC87306
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.0: Intel Corp. 82801CA/CAM USB (Hub #1)
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 16, io base 0x3040
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
uhci_hcd 0000:00:1d.1: Intel Corp. 82801CA/CAM USB (Hub #2)
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 19, io base 0x3020
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
uhci_hcd 0000:00:1d.2: Intel Corp. 82801CA/CAM USB (Hub #3)
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 18, io base 0x3000
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
hw_random hardware driver 1.0.0 loaded
ICH3: IDE controller at PCI slot 0000:00:1f.1
PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
ICH3: chipset revision 2
ICH3: not 100% native mode: will probe irqs later
ICH3: port 0x01f0 already claimed by ide0
    ide1: BM-DMA at 0x03a8-0x03af, BIOS settings: hdc:pio, hdd:pio
Probing IDE interface ide1...
e100: Intel(R) PRO/100 Network Driver, 3.2.3-k2-NAPI
e100: Copyright(c) 1999-2004 Intel Corporation
ACPI: PCI interrupt 0000:01:03.0[A] -> GSI 20 (level, low) -> IRQ 20
e100: eth0: e100_probe: addr 0xfe7e0000, irq 20, MAC addr 00:03:47:2F:B3:F3
Intel(R) PRO/1000 Network Driver - version 5.5.4-k2
Copyright (c) 1999-2004 Intel Corporation.
ACPI: PCI interrupt 0000:01:04.0[A] -> GSI 21 (level, low) -> IRQ 21
e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
NET: Registered protocol family 10
Disabled Privacy Extensions on device c0317e40(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
apm: BIOS not found.
eth0: no IPv6 routers present
UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A

```

---

### Post by lozzd on 2005-05-18
bump.

---

### Post by alastair on 2005-05-18
To install on a RAID device, you have to see the device as a single (RAID) device at install time i.e. 1 disk (/dev/sda) say, not two disks.

I have a Dell with a CERC 6ch. RAID at work - this uses the "aacraid" driver as well. But Ubuntu (or latest testing Debian) will not install onto it (no media is found, driver falls over etc.). My H/W is SATA RAID.

My advice is - forget about "H/W" raid and use Linux MD s/w RAID (1) at install i.e.

 - turn off RAID in BIOS
 - partition each drive as required
 - config. MD RAID over the paired partitions (/ = /dev/sda1 + /dev/sdb1 say, etc.)
 - install

This should work fine. From what I can see (do your own research), current "aacraid" seems to be either flaky, or not working.

---

### Post by lozzd on 2005-05-18
[QUOTE=alastair]To install on a RAID device, you have to see the device as a single (RAID) device at install time i.e. 1 disk (/dev/sda) say, not two disks.

I have a Dell with a CERC 6ch. RAID at work - this uses the "aacraid" driver as well. But Ubuntu (or latest testing Debian) will not install onto it (no media is found, driver falls over etc.). My H/W is SATA RAID.

My advice is - forget about "H/W" raid and use Linux MD s/w RAID (1) at install i.e.

 - turn off RAID in BIOS
 - partition each drive as required
 - config. MD RAID over the paired partitions (/ = /dev/sda1 + /dev/sdb1 say, etc.)
 - install

This should work fine. From what I can see (do your own research), current "aacraid" seems to be either flaky, or not working.[/QUOTE]
 Ok, thanks for your reply. I guess this will work as well as the hardware RAID anyway? 

Since the server is already set up and can see both drives, can I set it up now with the server already running? I don't really want to install again. Its already being used in a production environment. Aside from that I guess I can just search for Raid howto on these forums and there'll be a guide (i need step by step, still a newbie, heh)?

Thanks so much for your reply, its fustrating when I know its possible but I dont know how to do it!

Laurie

---

### Post by alastair on 2005-05-19
There are ways to arrange a RAID/MD config post-install. It involves creating a "degraded" array i.e. an MD array where one device is missing. You then partition and format the 2nd device identically to the first, and "hot add" it to the array. The RAID should then rebuild.

This probably requires partitions of type "fd" (linux raid auto) and should be considered dangerous for the inexperienced (I would be very cautious - BACKUP data etc.).

Do your own research - but some potentially interesting links :

[http://xtronics.com/reference/SATA-RAID-debian-for-2.6.html](http://xtronics.com/reference/SATA-RAID-debian-for-2.6.html)
[http://lists.ubuntu.com/archives/ubuntu-users/2004-December/014480.html](http://lists.ubuntu.com/archives/ubuntu-users/2004-December/014480.html)
[http://www.linux-sxs.org/hardware/raid_for_idiots.html](http://www.linux-sxs.org/hardware/raid_for_idiots.html)

Remember - BACKUP!

Doing this at install time is much easier.

---

### Post by lozzd on 2005-05-19
[QUOTE=alastair]There are ways to arrange a RAID/MD config post-install. It involves creating a "degraded" array i.e. an MD array where one device is missing. You then partition and format the 2nd device identically to the first, and "hot add" it to the array. The RAID should then rebuild.

This probably requires partitions of type "fd" (linux raid auto) and should be considered dangerous for the inexperienced (I would be very cautious - BACKUP data etc.).

Do your own research - but some potentially interesting links :

[http://xtronics.com/reference/SATA-RAID-debian-for-2.6.html](http://xtronics.com/reference/SATA-RAID-debian-for-2.6.html)
[http://lists.ubuntu.com/archives/ubuntu-users/2004-December/014480.html](http://lists.ubuntu.com/archives/ubuntu-users/2004-December/014480.html)
[http://www.linux-sxs.org/hardware/raid_for_idiots.html](http://www.linux-sxs.org/hardware/raid_for_idiots.html)

Remember - BACKUP!

Doing this at install time is much easier.[/QUOTE]
 Thanks very much for your help.. i'll look into it..
Yes install time is probably easier but it took me a good 15 solid hours setting up the server exactly how I wanted anyway.. Hopefully the RAID will be easier, hehe. 

Thanks again,
Laurie

---

### Post by lozzd on 2005-05-20
Well, I had a go tonight using the guide here: [http://xtronics.com/reference/SATA-RAID-debian-for-2.6.html](http://xtronics.com/reference/SATA-RAID-debian-for-2.6.html)
everything was fine all through the steps apart from I was making things "jfs" when they were originally ext3... Not sure if that makes a difference, plus they're using 3 paritions instaed of my 2 (one logical and one extended) 
On rebooting, it said Starting Ubuntu then complained of a file missing, and although I seem so close i'm sure i'm probably not.

Which makes me wonder if I should just start over, back up all the data and try and rebuild the server again from scratch, only this time using a RAID from the beginning. How is this done? Can you specifiy to setup a software RAID in the setup routine? If not whats the easiest way to do it? Follow the instructions in the link above word for word? 

Thanks again
Laurie

---

### Post by lozzd on 2005-05-21
Btw, I meant to say that the file it couldn't find was "/dev/console"...
I'm thinking its because in the guide they have 3 different partitions, one just for boot, wheras everything is on / for me (apart from the swap)..
I just need to try and find the part of the guide where i went wrong... If anyone could help it would be greatly appreciated!
Thanks
Laurie

---

