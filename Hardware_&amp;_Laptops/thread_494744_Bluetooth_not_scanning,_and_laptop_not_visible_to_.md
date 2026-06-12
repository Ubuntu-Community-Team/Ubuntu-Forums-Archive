---
title: "Bluetooth not scanning, and laptop not visible to my phone etc."
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by Nanoboy on 2007-07-07
Hi, 

I've tried to sort this out for a couple day but no joy :(

I think my internal bluetooth card is loaded on boot on my Dell Inspiron 9100.  I have installed Bluez-gnome and bluez-utils packages, and even went to the bluez website downloaded and manually installed bluez-firmware-1.2 and bluez-libs-3.12 which were not listed on Synaptic Package Manager.

Do *hciconfig enable* command, output:
```
hci0:   Type: USB
        BD Address: 00:10:C6:4E:07:51 ACL MTU: 192:8 SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN 
        RX bytes:912 acl:0 sco:0 events:47 errors:0
        TX bytes:641 acl:0 sco:0 commands:36 errors:0

```
Then *hcitool scan*
```
jack@hedgehog:~$ hcitool scan
Scanning ...
jack@hedgehog:~$ 

```
Appeared time out.

Tried *sudo hcitool inq*
```
jack@hedgehog:~$ sudo hcitool inq
Password:
Inquiring ...
jack@hedgehog:~$ 

```
Returned nothing.

Done *sudo /etc/init.d/bluetooth restart* and *sudo hciconfig hci0 reset*, same outcome.

Put the followings in /etc/rc.local
```
# These lines are for resetting bluetooth every bootup.
hciconfig hci0 reset;

hciconfig hci0 inqmode 0;
#

exit 0
```
No effects was seen.

Changed security setting in my /etc/bluetooth/hcid.conf
```
# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security [COLOR="Red"]auto[/COLOR];

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# Default PIN code for incoming connections
	passkey "0410";
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x3e0100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;
	discovto 0;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}
```
Didn't help.

In /etc/init.d/bluetooth, I changed HIDD_ENABLED value from 0 to 1.  Don't know if I need DUND and PAND, but I enabled them as well anyway.  DUND is for ppp login.  I don't know what ppp stands for...
```
PATH=/sbin:/bin:/usr/sbin:/usr/bin
DESC="Bluetooth services"

HCID=/usr/sbin/hcid
HCIATTACH=/usr/sbin/hciattach
HCID_NAME=hcid
HCID_OPTIONS="-x -s"

HID2HCI=/usr/sbin/hid2hci

UART_CONF=/etc/bluetooth/uart

RFCOMM=/usr/bin/rfcomm
RFCOMM_NAME=rfcomm
RFCOMM_CONF=/etc/bluetooth/rfcomm.conf

SDPTOOL=/usr/bin/sdptool

DUND_DAEMON=/usr/bin/dund
DUND_NAME=dund
PAND_DAEMON=/usr/bin/pand
PAND_NAME=pand
HIDD_DAEMON=/usr/bin/hidd
HIDD_NAME=hidd

DUND_ENABLED=[COLOR="Red"]1[/COLOR]
PAND_ENABLED=[COLOR="Red"]1[/COLOR]
HIDD_ENABLED=[COLOR="Red"]1[/COLOR]
DUND_OPTIONS=""
PAND_OPTIONS=""
HIDD_OPTIONS="--master --server"

test -f /etc/default/bluetooth && . /etc/default/bluetooth
test -f /etc/default/rcS && . /etc/default/rcS

. /lib/lsb/init-functions
```

There're some instruction commented within /etc/default/bluetooth:
HIDD already enabled, but I removed --master in HIDD_OPTIONS as recommended below
```
############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=1
[COLOR="Red"]HIDD_OPTIONS="--server"[/COLOR]
# to make hidd always use a particular interface, use something
# like this, substituting the bdaddr of the interface:
# HIDD_OPTIONS="-i AA:BB:CC:DD:EE:FF --server"
#
# remove '--master' if you're having trouble working with Ericsson
# T630 phones with hidd operational at the same time.
```

I enabled DUND here, and in the terminal I run *dund --listen --channel 3* as it was recommended below for Ericsson phones (although I have a Sony Ericsson K800).
```
############ DUND
#
# Run dund -- this allows ppp logins. 1 for enabled, 0 for disabled.
DUND_ENABLED=[COLOR="Red"]1[/COLOR]

# Arguments to dund: defaults to acting as a server
DUND_OPTIONS="--listen --persist"

# Run dund --help to see the full array of options.
# Here are some examples:
#
# Connect to any nearby host offering access
# DUND_OPTIONS="--search"
#
# Connect to host 00:11:22:33:44:55
# DUND_OPTIONS="--connect 00:11:22:33:44:55"
#
# Listen on channel 3
# DUND_OPTIONS="--listen --channel 3"

# Special consideration is needed for certain devices. Microsoft
# users see the --msdun option.  Ericsson P800 users will need to
# listen on channel 3 and also run 'sdptool add --channel=3 SP'
```

Finally, run *hidd --search*
```
jack@hedgehog:~$ hidd --search
Searching ...
        No devices in range or visible
jack@hedgehog:~$ 

```

My phone cannot discover my laptop either.  The bluelight on the laptop for bluetooth never came on, even though the gnome bluetooth manager said it is discoverable.

And my *dmesg* output:
```
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 262058) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262058
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262058
[    0.000000] On node 0 totalpages: 262058
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32427 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fde90
[    0.000000] ACPI: RSDT (v001 DELL    CPi R   0x27d40518 ASL  0x00000061) @ 0x3ffefbcd
[    0.000000] ACPI: FADT (v001 DELL    CPi R   0x27d40518 ASL  0x00000061) @ 0x3fff0400
[    0.000000] ACPI: MADT (v001 DELL    CPi R   0x27d40518 ASL  0x00000047) @ 0x3fff0c00
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030522) @ 0x3ffefbfd
[    0.000000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:3 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] Detected 3192.253 MHz processor.
[   21.943671] Built 1 zonelists.  Total pages: 260011
[   21.943674] Kernel command line: root=UUID=8c9f2871-4d83-4f5d-a026-a4e3834d0e96 ro quiet splash
[   21.943819] mapped APIC to ffffd000 (fee00000)
[   21.943822] mapped IOAPIC to ffffc000 (fec00000)
[   21.943824] Enabling fast FPU save and restore... done.
[   21.943827] Enabling unmasked SIMD FPU exception support... done.
[   21.943835] Initializing CPU#0
[   21.943885] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   21.944807] Console: colour VGA+ 80x25
[   21.945135] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   21.945473] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   21.964827] Memory: 1028028k/1048232k available (1992k kernel code, 19508k reserved, 900k data, 328k init, 130728k highmem)
[   21.964836] virtual kernel memory layout:
[   21.964838]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   21.964839]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   21.964840]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   21.964841]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   21.964842]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   21.964843]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   21.964844]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   21.964847] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.043646] Calibrating delay using timer specific routine.. 6388.89 BogoMIPS (lpj=12777796)
[   22.043688] Security Framework v1.0.0 initialized
[   22.043694] SELinux:  Disabled at boot.
[   22.043708] Mount-cache hash table entries: 512
[   22.043839] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[   22.043847] monitor/mwait feature present.
[   22.043849] using mwait in idle threads.
[   22.043855] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   22.043858] CPU: L2 cache: 1024K
[   22.043860] CPU: Physical Processor ID: 0
[   22.043862] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003180 0000441d 00000000 00000000
[   22.043873] Compat vDSO mapped to ffffe000.
[   22.043877] Remapping vsyscall page to ffffe000
[   22.043891] Checking 'hlt' instruction... OK.
[   22.059691] SMP alternatives: switching to UP code
[   22.060021] Early unpacking initramfs... done
[   22.317023] ACPI: Core revision 20060707
[   22.323048] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   22.325858] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
[   22.325877] SMP alternatives: switching to SMP code
[   22.325966] Booting processor 1/1 eip 3000
[   22.393987] Initializing CPU#1
[   22.472479] Calibrating delay using timer specific routine.. 6384.47 BogoMIPS (lpj=12768952)
[   22.472488] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[   22.472494] monitor/mwait feature present.
[   22.472501] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   22.472504] CPU: L2 cache: 1024K
[   22.472506] CPU: Physical Processor ID: 0
[   22.472508] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003180 0000441d 00000000 00000000
[   22.415027] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
[   22.415066] Total of 2 processors activated (12773.37 BogoMIPS).
[   22.415194] ENABLING IO-APIC IRQs
[   22.415364] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   22.562378] checking TSC synchronization across 2 CPUs: 
[    0.000002] CPU#0 had -28944 usecs TSC skew, fixed it up.
[    0.000006] CPU#1 had 28944 usecs TSC skew, fixed it up.
[    0.003990] Brought up 2 CPUs
[    0.088569] migration_cost=132
[    0.088838] Booting paravirtualized kernel on bare hardware
[    0.088905] Time: 12:52:32  Date: 06/07/107
[    0.088933] NET: Registered protocol family 16
[    0.089019] EISA bus registered
[    0.089024] ACPI: bus type pci registered
[    0.121557] PCI: PCI BIOS revision 2.10 entry at 0xfcc7e, last bus=2
[    0.121559] PCI: Using configuration type 1
[    0.121561] Setting up standard PCI resources
[    0.132479] ACPI: Interpreter enabled
[    0.132482] ACPI: Using IOAPIC for interrupt routing
[    0.133152] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.133161] PCI: Probing PCI hardware (bus 00)
[    0.133240] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    0.138891] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.138895] PCI quirk: region 1080-10bf claimed by ICH4 GPIO
[    0.139120] Boot video device is 0000:01:00.0
[    0.139389] PCI: Transparent bridge - 0000:00:1e.0
[    0.139453] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[    0.139456] Please report the result to linux-kernel to fix this permanently
[    0.139476] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.148166] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.148415] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    0.148657] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    0.148903] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[    0.149133] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.149379] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.150806] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.151624] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.151975] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.151989] pnp: PnP ACPI init
[    0.165968] pnp: PnP ACPI: found 11 devices
[    0.165972] PnPBIOS: Disabled by ACPI PNP
[    0.166021] PCI: Using ACPI for IRQ routing
[    0.166024] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.173451] NET: Registered protocol family 8
[    0.173454] NET: Registered protocol family 20
[    0.179407] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.179410] pnp: 00:02: ioport range 0x1000-0x1005 could not be reserved
[    0.179413] pnp: 00:02: ioport range 0x1008-0x100f could not be reserved
[    0.179416] pnp: 00:02: ioport range 0x800-0x80f has been reserved
[    0.179421] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.179424] pnp: 00:03: ioport range 0x1006-0x1007 has been reserved
[    0.179426] pnp: 00:03: ioport range 0x1010-0x105f could not be reserved
[    0.179429] pnp: 00:03: ioport range 0x1060-0x107f has been reserved
[    0.179431] pnp: 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.179434] pnp: 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.179441] pnp: 00:08: ioport range 0x900-0x97f has been reserved
[    0.179768] PCI: Bridge: 0000:00:01.0
[    0.179771]   IO window: c000-cfff
[    0.179776]   MEM window: fc000000-fdffffff
[    0.179780]   PREFETCH window: f0000000-f7ffffff
[    0.179791] PCI: Bus 3, cardbus bridge: 0000:02:01.0
[    0.179794]   IO window: 0000e000-0000e0ff
[    0.179798]   IO window: 0000e400-0000e4ff
[    0.179803]   PREFETCH window: 50000000-53ffffff
[    0.179808]   MEM window: 58000000-5bffffff
[    0.179812] PCI: Bridge: 0000:00:1e.0
[    0.179816]   IO window: e000-efff
[    0.179822]   MEM window: fa000000-fbffffff
[    0.179826]   PREFETCH window: 50000000-53ffffff
[    0.179843] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.179858] PCI: Enabling device 0000:02:01.0 (0000 -> 0003)
[    0.179864] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 19 (level, low) -> IRQ 16
[    0.179900] NET: Registered protocol family 2
[    0.219507] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.219630] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.220169] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.220501] TCP: Hash tables configured (established 131072 bind 65536)
[    0.220504] TCP reno registered
[    0.231575] checking if image is initramfs... it is
[    0.735624] Freeing initrd memory: 6787k freed
[    0.736185] audit: initializing netlink socket (disabled)
[    0.736197] audit(1183812752.440:1): initialized
[    0.736288] highmem bounce pool size: 64 pages
[    0.736372] VFS: Disk quotas dquot_6.5.1
[    0.736391] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.736440] io scheduler noop registered
[    0.736443] io scheduler anticipatory registered
[    0.736445] io scheduler deadline registered
[    0.736459] io scheduler cfq registered (default)
[    0.736733] isapnp: Scanning for PnP cards...
[    1.087540] isapnp: No Plug & Play device found
[    1.112722] Real Time Clock Driver v1.12ac
[    1.112777] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.113380] ACPI: PCI Interrupt 0000:00:1f.6[b] -> GSI 17 (level, low) -> IRQ 17
[    1.113389] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[    1.113458] mice: PS/2 mouse device common for all mice
[    1.114041] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.114186] input: Macintosh mouse button emulation as /class/input/input0
[    1.114226] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.114230] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.114410] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.119118] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.119123] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.119476] EISA: Probing bus 0 at eisa.0
[    1.119483] Cannot allocate resource for EISA slot 1
[    1.119503] EISA: Detected 0 cards.
[    1.122726] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.149506] TCP cubic registered
[    1.149516] NET: Registered protocol family 1
[    1.149539] Starting balanced_irq
[    1.149546] Using IPI No-Shortcut mode
[    1.149621] ACPI: (supports S0 S1 S3 S4 S5)
[    1.149661]   Magic number: 15:142:885
[    1.149736]   hash matches device ptyx9
[    1.149746]   hash matches device ptyuc
[    1.149938] Freeing unused kernel memory: 328k freed
[    1.153171] Time: tsc clocksource has been installed.
[    2.615402] Capability LSM initialized
[    2.655072] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    2.655205] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.655482] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    2.655557] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.658988] ACPI: Thermal Zone [THM] (45 C)
[    3.162517] usbcore: registered new interface driver usbfs
[    3.162547] usbcore: registered new interface driver hub
[    3.204333] usbcore: registered new device driver usb
[    3.205702] USB Universal Host Controller Interface driver v3.0
[    3.205758] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 18
[    3.205772] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.205778] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.205887] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.205918] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000bf80
[    3.206056] usb usb1: configuration #1 chosen from 1 choice
[    3.206096] hub 1-0:1.0: USB hub found
[    3.206104] hub 1-0:1.0: 2 ports detected
[    3.225014] SCSI subsystem initialized
[    3.233197] libata version 2.20 loaded.
[    3.272192] ieee1394: Initialized config rom entry `ip1394'
[    3.311991] ACPI: PCI Interrupt 0000:00:1d.1[b] -> GSI 19 (level, low) -> IRQ 16
[    3.312008] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.312015] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.312047] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.312083] uhci_hcd 0000:00:1d.1: irq 16, io base 0x0000bf60
[    3.312216] usb usb2: configuration #1 chosen from 1 choice
[    3.312254] hub 2-0:1.0: USB hub found
[    3.312262] hub 2-0:1.0: 2 ports detected
[    3.419617] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[    3.419632] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.419638] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.419669] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.419696] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000bf40
[    3.419848] usb usb3: configuration #1 chosen from 1 choice
[    3.419891] hub 3-0:1.0: USB hub found
[    3.419904] hub 3-0:1.0: 2 ports detected
[    3.527337] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 18
[    3.527351] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.527357] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.527390] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.527415] uhci_hcd 0000:00:1d.3: irq 18, io base 0x0000bf20
[    3.527550] usb usb4: configuration #1 chosen from 1 choice
[    3.527597] hub 4-0:1.0: USB hub found
[    3.527608] hub 4-0:1.0: 2 ports detected
[    3.555166] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    3.635219] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 20
[    3.635238] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.635245] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.635289] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.635342] ehci_hcd 0000:00:1d.7: debug port 1
[    3.635353] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[    3.635367] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xf8fffc00
[    3.639249] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.639351] usb usb5: configuration #1 chosen from 1 choice
[    3.639388] hub 5-0:1.0: USB hub found
[    3.639396] hub 5-0:1.0: 8 ports detected
[    3.746848] ACPI: PCI Interrupt 0000:02:01.1[A] -> GSI 19 (level, low) -> IRQ 16
[    3.796569] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[faffd800-faffdfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.796648] ata_piix 0000:00:1f.1: version 2.10ac1
[    3.796665] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    3.796671] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 18
[    3.796692] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.796751] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
[    3.796789] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
[    3.796812] scsi0 : ata_piix
[    3.966613] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[    3.966618] ata1.00: ATA-6: FUJITSU MHU2100AT, 00000008, max UDMA/100
[    3.966621] ata1.00: 195371568 sectors, multi 8: LBA 
[    3.982562] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[    3.982565] ata1.00: configured for UDMA/100
[    3.982575] scsi1 : ata_piix
[    4.101800] usb 1-2: device not accepting address 2, error -71
[    4.321464] ata2.00: ATAPI, max UDMA/33
[    4.505010] ata2.00: configured for UDMA/33
[    4.505130] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHU2100A 0000 PQ: 0 ANSI: 5
[    4.524831] scsi 1:0:0:0: CD-ROM            _NEC     DVD+-RW ND-6500A 203D PQ: 0 ANSI: 5
[    4.525148] b44.c:v1.01 (Jun 16, 2006)
[    4.525171] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 19
[    4.528758] eth0: Broadcom 4400 10/100BaseT Ethernet 00:0f:1f:23:38:18
[    4.540771] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[    4.540792] sda: Write Protect is off
[    4.540797] sda: Mode Sense: 00 3a 00 00
[    4.540823] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.540899] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[    4.540915] sda: Write Protect is off
[    4.540919] sda: Mode Sense: 00 3a 00 00
[    4.540950] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.540959]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    4.618778] sd 0:0:0:0: Attached scsi disk sda
[    4.623312] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.623343] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.716282] usb 5-3: new high speed USB device using ehci_hcd and address 3
[    4.810183] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.810189] Uniform CD-ROM driver Revision: 3.20
[    4.810247] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.852405] usb 5-3: configuration #1 chosen from 1 choice
[    4.969434] Attempting manual resume
[    4.969437] swsusp: Resume From Partition 8:6
[    4.969439] PM: Checking swsusp image.
[    4.969675] PM: Resume from disk failed.
[    5.013506] kjournald starting.  Commit interval 5 seconds
[    5.013514] EXT3-fs: mounted filesystem with ordered data mode.
[    5.067554] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[464fc00009a9a030]
[    5.095336] usb 1-2: new full speed USB device using uhci_hcd and address 4
[    5.317391] usb 1-2: configuration #1 chosen from 1 choice
[   19.123480] input: PC Speaker as /class/input/input2
[   19.349731] NET: Registered protocol family 17
[   19.403502] iTCO_vendor_support: vendor-support=0
[   19.405610] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   19.438348] Linux agpgart interface v0.102 (c) Dave Jones
[   19.498905] Bluetooth: Core ver 2.11
[   19.499390] NET: Registered protocol family 31
[   19.499394] Bluetooth: HCI device and connection manager initialized
[   19.499401] Bluetooth: HCI socket layer initialized
[   19.511965] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.521154] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.706804] agpgart: Detected an Intel 865 Chipset.
[   19.712444] agpgart: AGP aperture is 128M @ 0xe8000000
[   19.879459] Bluetooth: HCI USB driver ver 2.9
[   19.898590] input: PS/2 Mouse as /class/input/input3
[   19.913785] ieee80211_crypt: registered algorithm 'NULL'
[   19.924027] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[   19.928397] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x1060)
[   19.928437] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   19.953488] Yenta: CardBus bridge found at 0000:02:01.0 [1028:0159]
[   19.953508] Yenta: Using CSCINT to route CSC interrupts to PCI
[   19.953511] Yenta: Routing CardBus interrupts to PCI
[   19.953517] Yenta TI: socket 0000:02:01.0, mfunc 0x012c1202, devctl 0x64
[   19.995534] usbcore: registered new interface driver hci_usb
[   20.146605] intel_rng: FWH not detected
[   20.154117] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Freecom)' in cold state, will try to load a firmware
[   20.170475] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   20.170483] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   20.190549] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   20.190553] Socket status: 30000086
[   20.190556] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   20.190561] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xefff
[   20.190565] cs: IO port probe 0xe000-0xefff: clean.
[   20.190829] pcmcia: parent PCI bridge Memory window: 0xfa000000 - 0xfbffffff
[   20.190831] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   20.292130] dvb-usb: downloading firmware from file 'dvb-usb-wt220u-02.fw'
[   20.341194] bcm43xx driver
[   20.341289] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 17 (level, low) -> IRQ 17
[   20.348007] usbcore: registered new interface driver dvb_usb_dtt200u
[   20.697769] cs: IO port probe 0x100-0x3af: clean.
[   20.698867] cs: IO port probe 0x3e0-0x4ff: clean.
[   20.699335] cs: IO port probe 0x820-0x8ff: clean.
[   20.699724] cs: IO port probe 0xc00-0xcf7: clean.
[   20.700245] cs: IO port probe 0xa00-0xaff: clean.
[   20.799250] ACPI: PCI Interrupt 0000:00:1f.5[b] -> GSI 17 (level, low) -> IRQ 17
[   20.799283] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   21.362912] usb 5-3: USB disconnect, address 3
[   21.362947] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
[   21.622243] intel8x0_measure_ac97_clock: measured 55487 usecs
[   21.622246] intel8x0: clocking to 48000
[   21.800702] fuse init (API version 7.8)
[   21.879752] lp: driver loaded but no devices found
[   21.938904] Adding 899600k swap on /dev/disk/by-uuid/5928264c-237a-4a61-9318-cc92079c4517.  Priority:-1 extents:1 across:899600k
[   22.190423] EXT3 FS on sda5, internal journal
[   22.607799] usb 5-3: new high speed USB device using ehci_hcd and address 4
[   22.740288] usb 5-3: configuration #1 chosen from 1 choice
[   22.740493] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Freecom)' in warm state.
[   22.740574] dvb-usb: will use the device's hardware PID filter (table count: 15).
[   22.741600] DVB: registering new adapter (WideView WT-220U PenType Receiver (Typhoon/Freecom)).
[   22.741731] DVB: registering frontend 0 (WideView USB DVB-T)...
[   22.741998] input: IR-receiver inside an USB DVB receiver as /class/input/input5
[   22.742040] dvb-usb: schedule remote query interval to 300 msecs.
[   22.742045] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) successfully initialized and connected.
[   22.915654] kjournald starting.  Commit interval 5 seconds
[   22.915993] EXT3 FS on sda3, internal journal
[   22.915999] EXT3-fs: mounted filesystem with ordered data mode.
[   25.037803] dvb-usb: recv bulk message failed: -110
[   27.067982] Using specific hotkey driver
[   27.124302] input: Lid Switch as /class/input/input6
[   27.124331] ACPI: Lid Switch [LID]
[   27.124382] input: Power Button (CM) as /class/input/input7
[   27.124419] ACPI: Power Button (CM) [PBTN]
[   27.124465] input: Sleep Button (CM) as /class/input/input8
[   27.124499] ACPI: Sleep Button (CM) [SBTN]
[   27.495661] ACPI: Battery Slot [BAT0] (battery present)
[   27.566886] ibm_acpi: ec object not found
[   27.590660] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   27.601000] ACPI: AC Adapter [AC] (off-line)
[   27.626868] No dock devices found.
[   27.726060] pcc_acpi: loading...
[   30.805464] SoftMAC: Open Authentication completed with 00:0c:f6:21:2b:4b
[   31.145858] NET: Registered protocol family 10
[   31.145989] lo: Disabled Privacy Extensions
[   31.146066] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.834009] [drm] Initialized drm 1.1.0 20060810
[   31.849449] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 18
[   31.850339] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   32.901437] ppdev: user-space parallel port driver
[   33.755116] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   33.755139] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[   33.755180] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[   33.794052] apm: BIOS not found.
[   34.064386] [drm] Setting GART location based on new memory map
[   34.064397] [drm] Loading R300 Microcode
[   34.064443] [drm] writeback test succeeded in 1 usecs
[   34.336811] Bluetooth: L2CAP ver 2.8
[   34.336817] Bluetooth: L2CAP socket layer initialized
[   34.563436] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   34.746368] Bluetooth: RFCOMM socket layer initialized
[   34.746381] Bluetooth: RFCOMM TTY layer initialized
[   34.746384] Bluetooth: RFCOMM ver 1.8
[   41.975636] eth1: no IPv6 routers present
[   75.719860] eth1: no IPv6 routers present
[  177.869788] usb 4-1: new low speed USB device using uhci_hcd and address 2
[  178.046379] usb 4-1: configuration #1 chosen from 1 choice
[  178.125407] usbcore: registered new interface driver hiddev
[  178.137240] input: KYE USB MOUSE as /class/input/input9
[  178.137326] input: USB HID v1.10 Mouse [KYE USB MOUSE] on usb-0000:00:1d.3-1
[  178.137345] usbcore: registered new interface driver usbhid
[  178.137351] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[  437.115785] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  437.641636] SoftMAC: Open Authentication completed with 00:1b:63:22:7d:a7
[  437.893504] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  452.143890] eth1: no IPv6 routers present
```

Would be really grateful for any advice.  Thanks.

---

### Post by Nanoboy on 2007-07-07
No-one?

---

### Post by Nanoboy on 2007-07-07
*bump thread* as am getting a bit frustrated and desperate...

---

### Post by Nanoboy on 2007-07-07
Still struggling....

---

### Post by Nanoboy on 2007-07-08
Still noone comes to rescue...

---

### Post by kennythegeek on 2007-07-08
well, it says remove --master if you got an ericsson t630, not k800... try to add it again...
Ericsson and Sony Ericsson is basicly the same thing, just a note :P
Seems to be the bluetooth being down... the bluetooth light should light up when the module is on, are you sure that theres no wireless button to turn wifi on with? normally that button also controls bluetooth.
also, are you completly sure that you turned bluetooth on and sat "Discoverable" to yes on your phone? it can be disabled, and it saves a little power, so maybe it is sat to no.

---

### Post by Nanoboy on 2007-07-08
Thanks for your reply.

My phone is definitely switched to visible.

On my laptop, Fn+F2 keys used to turn the wireless on and off.  Ever since I installed bluetooth manager, the keys now supposed to be switching on the bluetooth (a pop up box from the bluetooth manager icon on the panel says "bluetooth is now switched to discoverable mode"), but the blue LED light never came on.

I've done a lot of searches and I think I've done everything I could, still nothing gets the bluetooth to work.

---

### Post by karadoc on 2007-08-09
Hi,

I have the same problem... Exactly the same...
Have you find a way to fix it ?
Please, let me know what you have done since your last message... and finally if you have some ideas to solve this.

Thanks,

Karadoc

---

### Post by takdavid on 2008-01-29
The same problem with my devices, and still not working.
Phone is Sony-Ericsson K320i, notebook is Asus F3M, Ubuntu is 7.04.
Strange is that sometimes it works, sometimes (most of the time) not.

---

