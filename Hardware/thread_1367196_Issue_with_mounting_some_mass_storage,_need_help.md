---
title: "Issue with mounting some mass storage, need help"
date: 2009-12-29
forum: Hardware
---

### Post by radoi_catalin87 on 2009-12-29
Hardware
Hp 6830S KU406EA laptop
1-WD320ML USB HDD (fat32)
1-kingmax 8GB(fat32)

Software: 
-Ubuntu 9.10 64bit
-kernel 2.6.31-16-generic
-gnome

On my laptop HDD I have 2 patition (etx4) 200GB filesystem and (ext4) 50GB for storage
Default 50GB partition was b2d69bef-5b5e-4053-af7a-06942fa1a2e7 and I have tried to chane it to something else using the command:

          sudo tune2fs -L Stocare /dev/sda5
        
since then i can't mount 50GB partition because I can't find it in menu Places.
I have edited /etc/fstab with this line:

          UUID=b2d69bef-5b5e-4053-af7a-06942fa1a2e7 /media/sda5               ext4    errors=remount-ro 0       1

Now I can use that 50GB partition but i can't unmount it like before, i must use a root nautilus to do this.

But the big problem is before I use the first command the system auto mount my USD HDD and kingmax, now if I connect them, doesn't appear anything. I want to use them like before. What can I do?

I'm a mid-level Ubuntu user. 

Here is the mount command result with my WD connected:
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda5 on /media/sda5 type ext4 (rw,errors=remount-ro)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rooot/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rooot)



Excuse if my english is bad!

---

### Post by Morbius1 on 2009-12-29
Please post the output of the following commands:

[B]sudo blkid -c /dev/null
cat /etc/fstab
[/B]

---

### Post by radoi_catalin87 on 2009-12-29
**sudo blkid -c /dev/null:**
/dev/sda1: UUID="43d2d49f-1ed2-427c-8218-f7099207c84c" TYPE="ext4" 
/dev/sda5: LABEL="b2d69bef-5b5e-40" UUID="b2d69bef-5b5e-4053-af7a-06942fa1a2e7" TYPE="ext4" 
/dev/sdb1: LABEL="My Passport" UUID="91A7-8CC8" TYPE="vfat" 

**cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=43d2d49f-1ed2-427c-8218-f7099207c84c /               ext4    errors=remount-ro 0       1
UUID=b2d69bef-5b5e-4053-af7a-06942fa1a2e7 /media/sda5               ext4    errors=remount-ro 0

---

### Post by Morbius1 on 2009-12-29
I'm getting a little confused by the title of your post and your description of the problem.

From fstab:
> UUID=b2d69bef-5b5e-4053-af7a-06942fa1a2e7 /media/sda5               ext4    errors=remount-ro 0     from blkid:
> /dev/sda5: LABEL="b2d69bef-5b5e-40" UUID="b2d69bef-5b5e-4053-af7a-06942fa1a2e7" TYPE="ext4" from your description:
> Now I can use that 50GB partition but i can't unmount it like before, i must use a root nautilus to do this.Why do you want to unmount an internal partition. There's no need to unmount an internal partition.

Second question about the external USB devices: They are not automounting and launching nautilus as before? If you plug the "My Passport" in and go to /media/My Passport do you not see the files?

---

### Post by radoi_catalin87 on 2009-12-29
I want to unmount: security reason. 

There are not automounting and lunch nautilus as before. If I plug My Passport and go to /media there is no My Passport dir. I've attached a screenshot  with /media folder and My Passport Connected to USB

---

### Post by radoi_catalin87 on 2009-12-29
Before I use command to rename sda5 partition, when I plug My Passport or any else usb storage my system automount it and lunch nautilus in /media/MyPassport or /media/Kingmax, etc. Now When I plug any usb storage device doesn't appear nautilus. If i open one nautilus and go to /media there is no folder for my storage device.

---

### Post by Morbius1 on 2009-12-29
The easiest way to have sda5 mount so that you can have security and be able to unmount it is to remove it from fstab.

It will show up under Places and request a password to mount and will allow you to unmount it without becoming root. 

As for your inability to automount usb devices. I don't know. I'm trying to figure out the relationship between tune2fs and USB automounting. I don't have an answer for that one at the moment.

I suppose you could force a mount in fstab with the noauto parameter for those but that's a workaround not an answer.

---

### Post by radoi_catalin87 on 2009-12-29
I've tried to mount My Passport manual using : 
sudo mount /dev/sdb1

and output is:
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab

---

### Post by radoi_catalin87 on 2009-12-29
[B]dmsg output:
[/B]
[    0.726574] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.726576] ACPI: Sleep Button [SLPB]
[    0.726611] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.726693] ACPI: Lid Switch [LID]
[    0.726929] fan PNP0C0B:00: registered as cooling_device0
[    0.726934] ACPI: Fan [FAN5] (off)
[    0.727130] fan PNP0C0B:01: registered as cooling_device1
[    0.727134] ACPI: Fan [FAN6] (off)
[    0.727329] fan PNP0C0B:02: registered as cooling_device2
[    0.727333] ACPI: Fan [FAN7] (off)
[    0.727529] fan PNP0C0B:03: registered as cooling_device3
[    0.727538] ACPI: Fan [FAN8] (off)
[    0.727735] fan PNP0C0B:04: registered as cooling_device4
[    0.727740] ACPI: Fan [FAN9] (off)
[    0.727834] fan PNP0C0B:05: registered as cooling_device5
[    0.727838] ACPI: Fan [FANG] (off)
[    0.728033] fan PNP0C0B:06: registered as cooling_device6
[    0.728038] ACPI: Fan [FAN0] (off)
[    0.728232] fan PNP0C0B:07: registered as cooling_device7
[    0.728237] ACPI: Fan [FAN1] (off)
[    0.728434] fan PNP0C0B:08: registered as cooling_device8
[    0.728439] ACPI: Fan [FAN2] (off)
[    0.728633] fan PNP0C0B:09: registered as cooling_device9
[    0.728638] ACPI: Fan [FAN3] (off)
[    0.728832] fan PNP0C0B:0a: registered as cooling_device10
[    0.728838] ACPI: Fan [FAN4] (off)
[    0.729764] ACPI: SSDT 00000000bfcc7c18 00275 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
[    0.730304] ACPI: SSDT 00000000bfcc5618 0057B (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
[    0.732657] Monitor-Mwait will be used to enter C-1 state
[    0.732675] Monitor-Mwait will be used to enter C-2 state
[    0.732682] Marking TSC unstable due to TSC halts in idle
[    0.732695] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    0.732711] processor LNXCPU:00: registered as cooling_device11
[    0.732714] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.733181] ACPI: SSDT 00000000bfcc6e18 001D7 (v01  PmRef    ApIst 00003000 INTL 20060912)
[    0.733619] ACPI: SSDT 00000000bfcc7f18 0008D (v01  PmRef    ApCst 00003000 INTL 20060912)
[    0.734722] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    0.734739] processor LNXCPU:01: registered as cooling_device12
[    0.734742] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.749891] thermal LNXTHERM:01: registered as thermal_zone0
[    0.749898] ACPI: Thermal Zone [GFXZ] (44 C)
[    0.772726] thermal LNXTHERM:02: registered as thermal_zone1
[    0.772733] ACPI: Thermal Zone [DTSZ] (46 C)
[    1.069565] thermal LNXTHERM:03: registered as thermal_zone2
[    1.069572] ACPI: Thermal Zone [CPUZ] (50 C)
[    1.073709] thermal LNXTHERM:04: registered as thermal_zone3
[    1.073716] ACPI: Thermal Zone [SKNZ] (45 C)
[    1.084323] thermal LNXTHERM:05: registered as thermal_zone4
[    1.084329] ACPI: Thermal Zone [BATZ] (24 C)
[    1.091687] thermal LNXTHERM:06: registered as thermal_zone5
[    1.091694] ACPI: Thermal Zone [FDTZ] (74 C)
[    1.092763] Linux agpgart interface v0.103
[    1.092771] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.093850] brd: module loaded
[    1.094224] loop: module loaded
[    1.094284] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.094384] ahci 0000:00:1f.2: version 3.0
[    1.094396]   alloc irq_desc for 21 on node 0
[    1.094398]   alloc kstat_irqs on node 0
[    1.094403] ahci 0000:00:1f.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.094431]   alloc irq_desc for 30 on node 0
[    1.094433]   alloc kstat_irqs on node 0
[    1.094441] ahci 0000:00:1f.2: irq 30 for MSI/MSI-X
[    1.094492] ahci: SSS flag set, parallel bus scan disabled
[    1.094524] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x23 impl SATA mode
[    1.094527] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems 
[    1.094532] ahci 0000:00:1f.2: setting latency timer to 64
[    1.140051] scsi0 : ahci
[    1.140124] scsi1 : ahci
[    1.140167] scsi2 : ahci
[    1.140212] scsi3 : ahci
[    1.140258] scsi4 : ahci
[    1.140304] scsi5 : ahci
[    1.140461] ata1: SATA max UDMA/133 abar m2048@0xd8504000 port 0xd8504100 irq 30
[    1.140465] ata2: SATA max UDMA/133 abar m2048@0xd8504000 port 0xd8504180 irq 30
[    1.140466] ata3: DUMMY
[    1.140467] ata4: DUMMY
[    1.140468] ata5: DUMMY
[    1.140471] ata6: SATA max UDMA/133 abar m2048@0xd8504000 port 0xd8504380 irq 30
[    1.141182] Fixed MDIO Bus: probed
[    1.141211] PPP generic driver version 2.4.2
[    1.141291] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.141341]   alloc irq_desc for 19 on node 0
[    1.141343]   alloc kstat_irqs on node 0
[    1.141347] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.141358] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.141361] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.141410] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.145307] ehci_hcd 0000:00:1a.7: debug port 1
[    1.145313] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.145325] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xd8504c00
[    1.160015] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.160072] usb usb1: configuration #1 chosen from 1 choice
[    1.160100] hub 1-0:1.0: USB hub found
[    1.160106] hub 1-0:1.0: 6 ports detected
[    1.160191]   alloc irq_desc for 20 on node 0
[    1.160193]   alloc kstat_irqs on node 0
[    1.160197] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 20 (level, low) -> IRQ 20
[    1.160245] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.160248] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.160275] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.164166] ehci_hcd 0000:00:1d.7: debug port 1
[    1.164172] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.164185] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd8504800
[    1.168591] ACPI: Battery Slot [BAT0] (battery present)
[    1.180012] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.180058] usb usb2: configuration #1 chosen from 1 choice
[    1.180081] hub 2-0:1.0: USB hub found
[    1.180087] hub 2-0:1.0: 6 ports detected
[    1.180146] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.180159] uhci_hcd: USB Universal Host Controller Interface driver
[    1.180225] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.180231] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.180234] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.180261] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.180292] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000080c0
[    1.180361] usb usb3: configuration #1 chosen from 1 choice
[    1.180386] hub 3-0:1.0: USB hub found
[    1.180394] hub 3-0:1.0: 2 ports detected
[    1.180465] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.180471] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.180474] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.180507] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.180538] uhci_hcd 0000:00:1a.1: irq 17, io base 0x000080a0
[    1.180607] usb usb4: configuration #1 chosen from 1 choice
[    1.180628] hub 4-0:1.0: USB hub found
[    1.180634] hub 4-0:1.0: 2 ports detected
[    1.180701] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.180707] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.180710] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.180740] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    1.180770] uhci_hcd 0000:00:1a.2: irq 18, io base 0x00008080
[    1.180839] usb usb5: configuration #1 chosen from 1 choice
[    1.180862] hub 5-0:1.0: USB hub found
[    1.180871] hub 5-0:1.0: 2 ports detected
[    1.180937] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.180943] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.180946] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.180971] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    1.180994] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00008060
[    1.181060] usb usb6: configuration #1 chosen from 1 choice
[    1.181084] hub 6-0:1.0: USB hub found
[    1.181089] hub 6-0:1.0: 2 ports detected
[    1.181156]   alloc irq_desc for 22 on node 0
[    1.181158]   alloc kstat_irqs on node 0
[    1.181162] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    1.181167] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.181170] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.181196] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.181226] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00008040
[    1.181295] usb usb7: configuration #1 chosen from 1 choice
[    1.181316] hub 7-0:1.0: USB hub found
[    1.181322] hub 7-0:1.0: 2 ports detected
[    1.181391] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.181397] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.181400] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.181425] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.181448] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00008020
[    1.181516] usb usb8: configuration #1 chosen from 1 choice
[    1.181537] hub 8-0:1.0: USB hub found
[    1.181543] hub 8-0:1.0: 2 ports detected
[    1.181629] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.183394] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.184150] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.184155] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.184157] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.184159] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.184162] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.184214] mice: PS/2 mouse device common for all mice
[    1.184313] rtc_cmos 00:08: RTC can wake from S4
[    1.184344] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.184372] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.184450] device-mapper: uevent: version 1.0.3
[    1.184522] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.184584] device-mapper: multipath: version 1.1.0 loaded
[    1.184587] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.184774] cpuidle: using governor ladder
[    1.184848] cpuidle: using governor menu
[    1.185180] TCP cubic registered
[    1.185292] NET: Registered protocol family 10
[    1.185678] lo: Disabled Privacy Extensions
[    1.185925] NET: Registered protocol family 17
[    1.185940] Bluetooth: L2CAP ver 2.13
[    1.185942] Bluetooth: L2CAP socket layer initialized
[    1.185945] Bluetooth: SCO (Voice Link) ver 0.6
[    1.185947] Bluetooth: SCO socket layer initialized
[    1.185976] Bluetooth: RFCOMM TTY layer initialized
[    1.185979] Bluetooth: RFCOMM socket layer initialized
[    1.185980] Bluetooth: RFCOMM ver 1.11
[    1.186718] PM: Resume from disk failed.
[    1.186729] registered taskstats version 1
[    1.186827]   Magic number: 5:724:785
[    1.186943] rtc_cmos 00:08: setting system clock to 2009-12-29 12:46:30 UTC (1262090790)
[    1.186945] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.186947] EDD information not available.
[    1.206394] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.490117] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.491137] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    1.491142] ata1.00: ATA-8: Hitachi HTS543225L9A300, FBEOC40J, max UDMA/100
[    1.491144] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.492346] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    1.492360] ata1.00: configured for UDMA/100
[    1.500098] Clocksource tsc unstable (delta = -291022617 ns)
[    1.511478] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54322 FBEO PQ: 0 ANSI: 5
[    1.511589] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.511623] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.511661] sd 0:0:0:0: [sda] Write Protect is off
[    1.511663] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.511683] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.511791]  sda: sda1 sda2 < sda5 >
[    1.552028] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.600115] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    1.790215] usb 1-5: configuration #1 chosen from 1 choice
[    2.070122] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    2.246436] usb 3-1: configuration #1 chosen from 1 choice
[    2.260151] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.274953] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.274956] ata2.00: ATAPI: Optiarc DVD RW AD-7581S, 4H03, max UDMA/100
[    2.291814] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.291827] ata2.00: configured for UDMA/100
[    2.312555] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7581S  4H03 PQ: 0 ANSI: 5
[    2.318866] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.318870] Uniform CD-ROM driver Revision: 3.20
[    2.318954] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.319003] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.660182] ata6: SATA link down (SStatus 0 SControl 300)
[    2.680238] Freeing unused kernel memory: 660k freed
[    2.680441] Write protecting the kernel read-only data: 7584k
[    2.784827] acpi device:04: registered as cooling_device13
[    2.785456] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input5
[    2.785491] ACPI: Video Device [DGFX] (multi-head: yes  rom: no  post: no)
[    2.800670] sky2 driver version 1.23
[    2.800818] sky2 0000:86:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.800870] sky2 0000:86:00.0: setting latency timer to 64
[    2.800963] sky2 0000:86:00.0: Yukon-2 Extreme chip revision 2
[    2.801583]   alloc irq_desc for 31 on node 0
[    2.801585]   alloc kstat_irqs on node 0
[    2.801652] sky2 0000:86:00.0: irq 31 for MSI/MSI-X
[    2.802470] sky2 eth0: addr 00:24:81:66:89:24
[    3.494947] EXT4-fs (sda1): barriers enabled
[    3.512989] kjournald2 starting: pid 404, dev sda1:8, commit interval 5 seconds
[    3.513010] EXT4-fs (sda1): delayed allocation enabled
[    3.513015] EXT4-fs: file extents enabled
[    3.523630] EXT4-fs: mballoc enabled
[    3.523642] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.110722] type=1505 audit(1262090793.414:2): operation="profile_load" pid=427 name=/usr/share/gdm/guest-session/Xsession
[    4.112778] type=1505 audit(1262090793.424:3): operation="profile_load" pid=428 name=/sbin/dhclient3
[    4.113419] type=1505 audit(1262090793.424:4): operation="profile_load" pid=428 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.113741] type=1505 audit(1262090793.424:5): operation="profile_load" pid=428 name=/usr/lib/connman/scripts/dhclient-script
[    4.150924] type=1505 audit(1262090793.454:6): operation="profile_load" pid=429 name=/usr/bin/evince
[    4.160600] type=1505 audit(1262090793.464:7): operation="profile_load" pid=429 name=/usr/bin/evince-previewer
[    4.166206] type=1505 audit(1262090793.474:8): operation="profile_load" pid=429 name=/usr/bin/evince-thumbnailer
[    4.195589] type=1505 audit(1262090793.504:9): operation="profile_load" pid=431 name=/usr/lib/cups/backend/cups-pdf
[   16.756745] udev: starting version 147
[   16.859786] udev: renamed network interface eth0 to eth1
[   16.875137] lis3lv02d: laptop model unknown, using default axes configuration
[   16.875941] lis3lv02d: 1-byte sensor found
[   16.880892] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.889236] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   16.889240] Disabling lock debugging due to kernel taint
[   16.921011] lp: driver loaded but no devices found
[   16.925701] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input6
[   16.925782] Registered led device: hp::hddprotect
[   16.925808] lis3lv02d driver loaded.
[   16.945696] [fglrx] Maximum main memory to use for locked dma buffers: 2869 MBytes.
[   16.945924] [fglrx]   vendor: 1002 device: 95c2 count: 1
[   16.946253] [fglrx] ioport: bar 1, base 0x7000, size: 0x100
[   16.946269] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.946275] pci 0000:01:00.0: setting latency timer to 64
[   16.946415] [fglrx] Kernel PAT support is enabled
[   16.946437] [fglrx] module loaded - fglrx 8.66.10 [Sep  3 2009] with 1 minors
[   16.946962] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   16.947064] usbcore: registered new interface driver btusb
[   16.962885] Linux video capture interface: v2.00
[   16.965120] uvcvideo: Found UVC 1.00 device CKF7063 (04f2:b083)
[   16.987142] input: CKF7063 as /devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5:1.0/input/input7
[   16.987196] usbcore: registered new interface driver uvcvideo
[   16.987197] USB Video Class driver (v0.1.0)
[   17.000184] cfg80211: Calling CRDA to update world regulatory domain
[   17.012649] EXT4-fs (sda1): internal journal on sda1:8
[   17.036756] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   17.036759] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   17.054111] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.054143] iwlagn 0000:03:00.0: setting latency timer to 64
[   17.054197] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   17.093609] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   17.093672]   alloc irq_desc for 32 on node 0
[   17.093674]   alloc kstat_irqs on node 0
[   17.093692] iwlagn 0000:03:00.0: irq 32 for MSI/MSI-X
[   17.101053] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   17.107532] udev: renamed network interface wlan0 to wlan1
[   17.117393] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   17.117404] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.117439] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.162316] cfg80211: World regulatory domain updated:
[   17.162318]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.162321]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.162323]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.162326]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.162328]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.162330]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.534146] EXT4-fs (sda5): barriers enabled
[   17.534447] kjournald2 starting: pid 836, dev sda5:8, commit interval 5 seconds
[   17.546229] EXT4-fs (sda5): internal journal on sda5:8
[   17.546234] EXT4-fs (sda5): delayed allocation enabled
[   17.546237] EXT4-fs: file extents enabled
[   17.549465] EXT4-fs: mballoc enabled
[   17.549478] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   17.595355] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   17.707133] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0x200000
[   17.747805] __ratelimit: 9 callbacks suppressed
[   17.747809] type=1505 audit(1262090807.053:13): operation="profile_replace" pid=999 name=/usr/share/gdm/guest-session/Xsession
[   17.749175] type=1505 audit(1262090807.053:14): operation="profile_replace" pid=1000 name=/sbin/dhclient3
[   17.749836] type=1505 audit(1262090807.053:15): operation="profile_replace" pid=1000 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   17.750179] type=1505 audit(1262090807.063:16): operation="profile_replace" pid=1000 name=/usr/lib/connman/scripts/dhclient-script
[   17.754598] type=1505 audit(1262090807.063:17): operation="profile_replace" pid=1001 name=/usr/bin/evince
[   17.764552] type=1505 audit(1262090807.073:18): operation="profile_replace" pid=1001 name=/usr/bin/evince-previewer
[   17.770206] type=1505 audit(1262090807.083:19): operation="profile_replace" pid=1001 name=/usr/bin/evince-thumbnailer
[   17.778665] type=1505 audit(1262090807.083:20): operation="profile_replace" pid=1004 name=/usr/lib/cups/backend/cups-pdf
[   17.779366] type=1505 audit(1262090807.083:21): operation="profile_replace" pid=1004 name=/usr/sbin/cupsd
[   17.781388] type=1505 audit(1262090807.093:22): operation="profile_replace" pid=1005 name=/usr/sbin/mysqld
[   17.783571] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   17.943587] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   17.975176] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[   18.125247] Registered led device: iwl-phy0::radio
[   18.125269] Registered led device: iwl-phy0::assoc
[   18.125286] Registered led device: iwl-phy0::RX
[   18.125302] Registered led device: iwl-phy0::TX
[   18.180934] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   18.185283] sky2 eth1: enabling interface
[   18.185701] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   18.273383] usplash:370 freeing invalid memtype ffffffffc0000000-ffffffffc1000000
[   18.772822]   alloc irq_desc for 33 on node 0
[   18.772825]   alloc kstat_irqs on node 0
[   18.772837] fglrx_pci 0000:01:00.0: irq 33 for MSI/MSI-X
[   18.773310] [fglrx] Firegl kernel thread PID: 1358
[   19.993787] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.993790] Bluetooth: BNEP filters: protocol multicast
[   19.999903] Bridge firewalling registered
[   20.031802] ppdev: user-space parallel port driver
[   20.240804] [fglrx] Gart USWC size:940 M.
[   20.240807] [fglrx] Gart cacheable size:372 M.
[   20.240812] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   20.240814] [fglrx] Reserved FB block: Unshared offset:fd08000, size:2f3000 
[   20.240816] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
[   20.770953] CPU0 attaching NULL sched-domain.
[   20.770958] CPU1 attaching NULL sched-domain.
[   20.800175] CPU0 attaching sched-domain:
[   20.800178]  domain 0: span 0-1 level MC
[   20.800180]   groups: 0 1
[   20.800185] CPU1 attaching sched-domain:
[   20.800186]  domain 0: span 0-1 level MC
[   20.800188]   groups: 1 0
[   20.854014] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* interrupt source ff000066 is not supported on this hardware (return code = 1)
[   23.481416] CPU0 attaching NULL sched-domain.
[   23.481422] CPU1 attaching NULL sched-domain.
[   23.521426] CPU0 attaching sched-domain:
[   23.521437]  domain 0: span 0-1 level MC
[   23.521439]   groups: 0 1
[   23.521444] CPU1 attaching sched-domain:
[   23.521446]  domain 0: span 0-1 level MC
[   23.521448]   groups: 1 0
[   24.632809] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   24.633757] input: Microsoft Bluetooth Notebook Mouse 5000 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/bluetooth/hci0/hci0:11/input10
[   24.633869] generic-bluetooth 0005:045E:0700.0001: input,hidraw0: BLUETOOTH HID v1.00 Mouse [Microsoft Bluetooth Notebook Mouse 5000] on 00:24:7E:4E:E3:D4
[   39.831022] wlan1: authenticate with AP 00:1c:f0:b9:5c:21
[   39.832822] wlan1: authenticated
[   39.832825] wlan1: associate with AP 00:1c:f0:b9:5c:21
[   39.836030] wlan1: RX AssocResp from 00:1c:f0:b9:5c:21 (capab=0x431 status=0 aid=2)
[   39.836033] wlan1: associated
[   39.837568] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   39.869055] Intel AES-NI instructions are not detected.
[   39.898926] padlock: VIA PadLock not detected.
[   50.670036] wlan1: no IPv6 routers present
[   65.610166] usb 2-1: new high speed USB device using ehci_hcd and address 2
[   65.762704] usb 2-1: configuration #1 chosen from 1 choice
[   65.852247] usbcore: registered new interface driver hiddev
[   65.853248] input: Western Digital  External HDD     as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.1/input/input11
[   65.853314] generic-usb 0003:1058:0705.0002: input,hidraw1: USB HID v1.10 Device [Western Digital  External HDD    ] on usb-0000:00:1d.7-1/input1
[   65.853327] usbcore: registered new interface driver usbhid
[   65.853329] usbhid: v2.6:USB HID core driver
[   65.860570] Initializing USB Mass Storage driver...
[   65.860740] scsi6 : SCSI emulation for USB Mass Storage devices
[   65.860854] usbcore: registered new interface driver usb-storage
[   65.860857] USB Mass Storage support registered.
[   65.861061] usb-storage: device found at 2
[   65.861063] usb-storage: waiting for device to settle before scanning
[   70.850413] usb-storage: device scan complete
[   70.851011] scsi 6:0:0:0: Direct-Access     WD       3200BEV External 1.75 PQ: 0 ANSI: 4
[   70.851480] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   70.852134] sd 6:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[   70.852726] sd 6:0:0:0: [sdb] Write Protect is off
[   70.852729] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   70.852731] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   70.854236] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   70.854241]  sdb: sdb1
[   70.903713] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   70.903717] sd 6:0:0:0: [sdb] Attached SCSI disk
[  142.590253] usb 2-2: new high speed USB device using ehci_hcd and address 3
[  142.744477] usb 2-2: configuration #1 chosen from 1 choice
[  142.751556] scsi7 : SCSI emulation for USB Mass Storage devices
[  142.753023] usb-storage: device found at 3
[  142.753029] usb-storage: waiting for device to settle before scanning
[  147.751596] usb-storage: device scan complete
[  147.752342] scsi 7:0:0:0: Direct-Access     Kingmax  USB2.0 FlashDisk 1.00 PQ: 0 ANSI: 2
[  147.753462] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  147.767321] sd 7:0:0:0: [sdc] 15933440 512-byte logical blocks: (8.15 GB/7.59 GiB)
[  147.768055] sd 7:0:0:0: [sdc] Write Protect is off
[  147.768063] sd 7:0:0:0: [sdc] Mode Sense: 23 00 00 00
[  147.768068] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  147.771947] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  147.771960]  sdc: sdc1
[  147.925465] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  147.925476] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[  237.946559] iwlagn 0000:03:00.0: iwl_tx_agg_start on ra = 00:1c:f0:b9:5c:21 tid = 0
[  340.994471] usb 2-2: USB disconnect, address 3
[ 3267.410431] iwlagn 0000:03:00.0: iwl_tx_agg_start on ra = 00:1c:f0:b9:5c:21 tid = 6
[ 7726.340265] usb 2-2: new high speed USB device using ehci_hcd and address 4
[ 7726.493781] usb 2-2: configuration #1 chosen from 1 choice
[ 7726.508560] scsi8 : SCSI emulation for USB Mass Storage devices
[ 7726.514241] usb-storage: device found at 4
[ 7726.514243] usb-storage: waiting for device to settle before scanning
[ 7731.510575] usb-storage: device scan complete
[ 7731.511337] scsi 8:0:0:0: Direct-Access     Kingmax  USB2.0 FlashDisk 1.00 PQ: 0 ANSI: 2
[ 7731.512394] sd 8:0:0:0: Attached scsi generic sg3 type 0
[ 7731.516705] sd 8:0:0:0: [sdc] 15933440 512-byte logical blocks: (8.15 GB/7.59 GiB)
[ 7731.517588] sd 8:0:0:0: [sdc] Write Protect is off
[ 7731.517597] sd 8:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 7731.517603] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 7731.522450] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 7731.522462]  sdc: sdc1
[ 7731.671564] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 7731.671575] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[ 9232.370478] FAT: Unrecognized mount option "force" or missing value
[ 9249.155044] FAT: Unrecognized mount option "force" or missing value

---

### Post by radoi_catalin87 on 2009-12-29
Please some help from someone

---

