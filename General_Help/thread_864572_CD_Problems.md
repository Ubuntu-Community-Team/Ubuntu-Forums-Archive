---
title: "CD Problems"
date: 2008-07-19
forum: General Help
---

### Post by ron3090 on 2008-07-19
Hello! I'm new to both the forums and Linux, so I really don't know anything about it. I have successfully installed Xubuntu Feisty Ferret, and have had it updated completely. However, when I insert a CD, it is immediately ejected without my doing anything, no matter if it is a CD-R or not. Any help?

---

### Post by unutbu on 2008-07-19
Stick in a CD, let it pop out. Then open a terminal
and type
```

tail -n10 /var/log/messages
```

Please post the output.

---

### Post by ron3090 on 2008-07-19
Jul 19 16:36:41 ubuntu-Sanyatu kernel: [  565.388278] UDF-fs: No VRS found
Jul 19 16:36:43 ubuntu-Sanyatu kernel: [  567.606630] UDF-fs: No VRS found
Jul 19 16:45:06 ubuntu-Sanyatu kernel: [ 1070.341274] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
Jul 19 16:45:06 ubuntu-Sanyatu kernel: [ 1070.342061] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
Jul 19 16:45:06 ubuntu-Sanyatu kernel: [ 1070.342572] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
Jul 19 16:51:54 ubuntu-Sanyatu kernel: [ 1477.935050] UDF-fs: No VRS found
Jul 19 16:54:49 ubuntu-Sanyatu kernel: [ 1653.162887] UDF-fs: No VRS found
Jul 19 16:59:07 ubuntu-Sanyatu kernel: [ 1911.048588] UDF-fs: No VRS found
Jul 19 17:03:28 ubuntu-Sanyatu kernel: [ 2172.242245] UDF-fs: No VRS found
Jul 19 17:28:02 ubuntu-Sanyatu kernel: [ 3645.362291] UDF-fs: No VRS found

That's it. I can't make any sense of it.

---

### Post by unutbu on 2008-07-19
Please post 
```

cat /etc/fstab
```

---

### Post by ron3090 on 2008-07-19
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=12613613-f773-4c00-ad19-01d539d5872d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ee1b85b8-2e95-48ed-83b4-1b2f5091db98 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

There that is. What next?

---

### Post by unutbu on 2008-07-19
Please post 

```
ls -l /media/
```

Then type

```
sudo mkdir -p /media/cdrom
gksu gedit /etc/fstab
```

Change
```

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```
to
```

/dev/scd0 /media/**cdrom** **iso9660,udf** user,noauto,exec,utf8 0 0
```

Then try popping a CD in. 
If it is spat out, please post dmesg.out as an attachment:

```
dmesg > dmesg.out
```

---

### Post by ron3090 on 2008-07-19
total 8
lrwxrwxrwx 1 root 999    6 2008-07-19 09:31 cdrom -> cdrom0
drwxr-xr-x 2 root 999 4096 2008-07-19 09:31 cdrom0
lrwxrwxrwx 1 root 999    7 2008-07-19 09:31 floppy -> floppy0
drwxr-xr-x 2 root 999 4096 2008-07-19 09:31 floppy0

Okay. Next?

---

### Post by unutbu on 2008-07-19
Oops, sorry. Please re-read my edited post above.

Edit: Will be back in an hour...

---

### Post by ron3090 on 2008-07-19
Tried that. After the sudo command line, I got this: sudo: unable to resolve host ubuntu-Sanyatu

I continued on, but how do I change the file?

---

### Post by unutbu on 2008-07-19
If sudo is giving you an error, we had better fix that first (it may even be related? I'm not sure...)

Did you say gksu gedit works (i.e. does it bring up a text editing window?)

If so, try
```

gksu gedit /etc/hosts
```

and either add or make sure there is a line that says
```

127.0.0.1 localhost ubuntu-Sanyatu
```

Save the file. Then open /etc/hostname (Click on the Open button and type /etc/hostname in the Location field). Make sure this file has

```
ubuntu-Sanyatu
```
as its only contents. Again save and quit gedit.

Go back to the terminal and type```

sudo mkdir -p /media/cdrom
```

This command is innocuous. Since /media/cdrom already exists, it should do nothing, but let's try it anyway to see if the error message goes away.

After you make these changes, try inserting a CD again. Any better?

---

### Post by ron3090 on 2008-07-19
No. gedit does not work. When I enter it, nothing happens. It just goes to the next blank line. No error message, nothing.

Oh, and sudo does work, I think. I opened something else using it, and it worked fine.

---

### Post by unutbu on 2008-07-19
Something is very wrong with your system.
If this is what the system is like right after a fresh install + updates, something has gone very very wrong.

Unfortunately, I can't imagine what would produce all the symptoms you describe. 

Barring some other reader coming up with a better idea, the best suggestion I can think of (most unfortunately, I'm sorry) is to reinstall the OS.

---

### Post by ron3090 on 2008-07-21
Okay, so I found a way to edit the files you told me to. I used
```
sudo mousepad /etc/hostname
```
and that worked. I edited the files you told me to, and did all that. Now, the CD is still popping out, but not immediately like it used to. I also typed```
dmesg > dmesg.out
```
but where is it saved?

EDIT: I also googled this problem, and it seems a PS3 user had the same trouble as me. [Here.]("http://backports.ubuntuforums.com/showthread.php?p=4560976") See the last post.

---

### Post by ron3090 on 2008-07-21
Oh, and sudo no longer gives me an error message.

---

### Post by unutbu on 2008-07-21
The 
```
dmesg > dmesg.out
```
command saves the output of dmesg in a file called dmesg.out. Look for it in your user directory.

I don't know the reason why the CDs are ejecting, so I'm still just looking for clues.

---

### Post by ron3090 on 2008-07-21
Nevermind, I figured it out. It was a hardware configuration brought on by a Mitsumi drive. Apparantly, Ubuntu systems do not work with Mitsumi drives, so I just replaced it with another CD drive and put the Mitsumi back in the USB casing. Sorry for the trouble!

---

### Post by ron3090 on 2009-06-06
Well, a year later and here I am again. The CD drive I replaced the Mitsumi has broken, so I have been forced to revert back to the Mitsumi. The problem still persists, but only in Linux. I booted into Windows, and the drive works fine. The dmesg output gives me:
> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-24-generic (buildd@rothera) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4)) #1 SMP Wed Apr 15 15:54:25 UTC 2009 (Ubuntu 2.6.24-24.53-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e7000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000040fd800 (usable)
[    0.000000]  BIOS-e820: 00000000040fd800 - 00000000040ff800 (ACPI data)
[    0.000000]  BIOS-e820: 00000000040ff800 - 00000000040ffc00 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000040ffc00 - 0000000018000000 (usable)
[    0.000000]  BIOS-e820: 00000000fffe7000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 384MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 98304) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    98304
[    0.000000]   HighMem     98304 ->    98304
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    98304
[    0.000000] On node 0 totalpages: 98304
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 736 pages used for memmap
[    0.000000]   Normal zone: 93472 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.1 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6AC0 checksum 0
[    0.000000] ACPI: RSDP 000F6AC0, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 040FDA87, 0028 (r1 PTLTD    RSDT          0 PTL   1000000)
[    0.000000] ACPI: FACP 040FF78C, 0074 (r1 GATEWA TABOR II 19991217 PTL     F4240)
[    0.000000] ACPI: DSDT 040FDAAF, 1CDD (r1 GATEWA TABOR II        0 MSFT  1000004)
[    0.000000] ACPI: FACS 040FFBC0, 0040
[    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 18000000:e7fe7000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e7000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e7000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 00000000040fd000 - 00000000040fe000
[    0.000000] swsusp: Registered nosave memory region: 00000000040fe000 - 00000000040ff000
[    0.000000] swsusp: Registered nosave memory region: 00000000040ff000 - 0000000004100000
[    0.000000] swsusp: Registered nosave memory region: 00000000040ff000 - 0000000004100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 97536
[    0.000000] Kernel command line: root=UUID=12613613-f773-4c00-ad19-01d539d5872d ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (0130d000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 596.945 MHz processor.
[   36.313711] Console: colour VGA+ 80x25
[   36.313724] console [tty0] enabled
[   36.314855] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   36.316255] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   36.366161] Memory: 377340k/393216k available (2179k kernel code, 15360k reserved, 1008k data, 368k init, 0k highmem)
[   36.366190] virtual kernel memory layout:
[   36.366194]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   36.366199]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   36.366204]     vmalloc : 0xd8800000 - 0xff7fe000   ( 623 MB)
[   36.366209]     lowmem  : 0xc0000000 - 0xd8000000   ( 384 MB)
[   36.366213]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   36.366218]       .data : 0xc0320d78 - 0xc041cdc4   (1008 kB)
[   36.366222]       .text : 0xc0100000 - 0xc0320d78   (2179 kB)
[   36.366234] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   36.366336] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   36.446355] Calibrating delay using timer specific routine.. 1195.11 BogoMIPS (lpj=2390222)
[   36.446432] Security Framework initialized
[   36.446453] SELinux:  Disabled at boot.
[   36.446494] AppArmor: AppArmor initialized
[   36.446506] Failure registering capabilities with primary security module.
[   36.446533] Mount-cache hash table entries: 512
[   36.446872] Initializing cgroup subsys ns
[   36.446885] Initializing cgroup subsys cpuacct
[   36.446910] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   36.446945] CPU: L1 I cache: 16K, L1 D cache: 16K
[   36.446954] CPU: L2 cache: 256K
[   36.446965] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000 00000000
[   36.446997] Compat vDSO mapped to ffffe000.
[   36.447038] Checking 'hlt' instruction... OK.
[   36.463122] SMP alternatives: switching to UP code
[   36.467449] Freeing SMP alternatives: 11k freed
[   36.467834] Early unpacking initramfs... done
[   37.657989] CPU0: Intel Pentium III (Coppermine) stepping 01
[   37.658012] SMP motherboard not detected.
[   37.658021] Local APIC not detected. Using dummy APIC emulation.
[   37.658232] Brought up 1 CPUs
[   37.658292] CPU0 attaching sched-domain:
[   37.658301]  domain 0: span 01
[   37.658308]   groups: 01
[   37.658923] net_namespace: 64 bytes
[   37.658947] Booting paravirtualized kernel on bare hardware
[   37.660806] Time: 12:00:27  Date: 06/07/09
[   37.660904] NET: Registered protocol family 16
[   37.661646] EISA bus registered
[   37.662504] PCI: PCI BIOS revision 2.10 entry at 0xfd983, last bus=1
[   37.662516] PCI: Using configuration type 1
[   37.662544] Setting up standard PCI resources
[   37.668487] ACPI: Interpreter disabled.
[   37.668500] Linux Plug and Play Support v0.97 (c) Adam Belay
[   37.668614] pnp: PnP ACPI: disabled
[   37.668626] PnPBIOS: Scanning system for PnP BIOS support...
[   37.668681] PnPBIOS: Found PnP BIOS installation structure at 0xc00f6ae0
[   37.668692] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x9e33, dseg 0x400
[   37.675201] PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
[   37.676032] PCI: Probing PCI hardware
[   37.676043] PCI: Probing PCI hardware (bus 00)
[   37.676445] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[   37.676452] * this clock source is slow. Consider trying other clock sources
[   37.676510] PCI quirk: region 8000-803f claimed by PIIX4 ACPI
[   37.676519] PCI quirk: region 7000-700f claimed by PIIX4 SMB
[   37.679035] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
[   37.690124] NET: Registered protocol family 8
[   37.690132] NET: Registered protocol family 20
[   37.690362] AppArmor: AppArmor Filesystem Enabled
[   37.690491] system 00:00: ioport range 0x370-0x371 has been reserved
[   37.690506] system 00:00: iomem range 0xfffc0000-0xffffffff could not be reserved
[   37.690533] system 00:01: iomem range 0x0-0x9ffff could not be reserved
[   37.690544] system 00:01: iomem range 0xe4000-0xfffff could not be reserved
[   37.690554] system 00:01: iomem range 0x100000-0x17ffffff could not be reserved
[   37.690565] system 00:01: iomem range 0xfff80000-0xfffbffff has been reserved
[   37.690600] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[   37.690610] system 00:0a: ioport range 0x8000-0x803f has been reserved
[   37.690620] system 00:0a: ioport range 0x7000-0x700f has been reserved
[   37.690646] system 00:0c: iomem range 0xcb800-0xcbfff has been reserved
[   37.692102] PCI: Failed to allocate mem resource #6:10000@f8000000 for 0000:01:00.0
[   37.692115] PCI: Bridge: 0000:00:01.0
[   37.692120]   IO window: disabled.
[   37.692131]   MEM window: e9000000-e9ffffff
[   37.692140]   PREFETCH window: f0000000-f7ffffff
[   37.692192] NET: Registered protocol family 2
[   37.694085] Time: tsc clocksource has been installed.
[   37.726361] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   37.727181] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   37.727602] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   37.728145] TCP: Hash tables configured (established 16384 bind 16384)
[   37.728156] TCP reno registered
[   37.738578] checking if image is initramfs... it is
[   40.014973] Freeing initrd memory: 7732k freed
[   40.016651] audit: initializing netlink socket (disabled)
[   40.016692] audit(1244376028.652:1): initialized
[   40.024232] VFS: Disk quotas dquot_6.5.1
[   40.024553] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   40.025290] io scheduler noop registered
[   40.025300] io scheduler anticipatory registered
[   40.025307] io scheduler deadline registered
[   40.025359] io scheduler cfq registered (default)
[   40.025390] Limiting direct PCI/PCI transfers.
[   40.025456] Boot video device is 0000:01:00.0
[   40.026275] isapnp: Scanning for PnP cards...
[   40.380465] isapnp: No Plug & Play device found
[   40.496650] Real Time Clock Driver v1.12ac
[   40.496900] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   40.497182] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   40.499332] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   40.502341] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   40.502574] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   40.502939] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   40.506036] serio: i8042 KBD port at 0x60,0x64 irq 1
[   40.506054] serio: i8042 AUX port at 0x60,0x64 irq 12
[   40.517736] mice: PS/2 mouse device common for all mice
[   40.518136] EISA: Probing bus 0 at eisa.0
[   40.518156] Cannot allocate resource for EISA slot 1
[   40.518194] Cannot allocate resource for EISA slot 7
[   40.518202] Cannot allocate resource for EISA slot 8
[   40.518208] EISA: Detected 0 cards.
[   40.518217] cpuidle: using governor ladder
[   40.518223] cpuidle: using governor menu
[   40.518709] NET: Registered protocol family 1
[   40.518805] Using IPI No-Shortcut mode
[   40.518892] registered taskstats version 1
[   40.519131]   Magic number: 13:756:25
[   40.519346] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   40.519354] EDD information not available.
[   40.520678] Freeing unused kernel memory: 368k freed
[   40.520812] Write protecting the kernel read-only data: 806k
[   40.561591] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   42.261686] fuse init (API version 7.9)
[   42.376711] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   43.619479] usbcore: registered new interface driver usbfs
[   43.619559] usbcore: registered new interface driver hub
[   43.647664] usbcore: registered new device driver usb
[   43.683358] SCSI subsystem initialized
[   43.704889] natsemi dp8381x driver, version 2.1, Sept 11, 2006
[   43.704898]   originally by Donald Becker <becker@scyld.com>
[   43.704903]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[   43.705034] PCI: Enabling device 0000:00:0f.0 (0104 -> 0107)
[   43.705052] PCI: setting IRQ 10 as level-triggered
[   43.705060] PCI: Found IRQ 10 for device 0000:00:0f.0
[   43.707520] natsemi eth0: NatSemi DP8381[56] at 0xe8000000 (0000:00:0f.0), 00:09:5b:07:b9:11, IRQ 10, port TP.
[   43.737969] USB Universal Host Controller Interface driver v3.0
[   43.738173] PCI: setting IRQ 9 as level-triggered
[   43.738182] PCI: Found IRQ 9 for device 0000:00:07.2
[   43.738227] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   43.738766] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   43.738823] uhci_hcd 0000:00:07.2: irq 9, io base 0x00001020
[   43.739329] usb usb1: configuration #1 chosen from 1 choice
[   43.739410] hub 1-0:1.0: USB hub found
[   43.739431] hub 1-0:1.0: 2 ports detected
[   44.048738] libata version 3.00 loaded.
[   44.080777] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   44.199137] ata_piix 0000:00:07.1: version 2.12
[   44.229539] scsi0 : ata_piix
[   44.245643] Floppy drive(s): fd0 is 1.44M
[   44.264500] FDC 0 is a post-1991 82077
[   44.264575] scsi1 : ata_piix
[   44.264802] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0x1000 irq 14
[   44.264812] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0x1008 irq 15
[   44.326000] usb 1-1: configuration #1 chosen from 1 choice
[   44.446305] ata1.00: ATA-8: WDC WD3200AAJB-00WGA0, 00.02C01, max UDMA/100
[   44.446321] ata1.00: 625142448 sectors, multi 16: LBA48 
[   44.447410] ata1.01: ATA-5: WDC WD100BB-75CLB0, 05.04E05, max UDMA/100
[   44.447423] ata1.01: 19541088 sectors, multi 16: LBA 
[   44.453618] ata1.00: configured for UDMA/33
[   44.469971] ata1.01: configured for UDMA/33
[   44.568658] usb 1-2: new full speed USB device using uhci_hcd and address 3
[   44.731831] usb 1-2: configuration #1 chosen from 1 choice
[   44.735685] hub 1-2:1.0: USB hub found
[   44.737778] hub 1-2:1.0: 4 ports detected
[   44.953516] ata2.00: ATAPI: CR-4804TE, 3.0D, max MWDMA1
[   44.953595] ata2.01: ATAPI: IOMEGA  ZIP 100       ATAPI, 03.H, max MWDMA1, CDB intr
[   45.050429] usb 1-2.2: new low speed USB device using uhci_hcd and address 4
[   45.124869] ata2.00: configured for MWDMA1
[   45.192693] usb 1-2.2: configuration #1 chosen from 1 choice
[   45.297860] ata2.01: configured for MWDMA1
[   45.298241] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200AAJB-0 00.0 PQ: 0 ANSI: 5
[   45.298626] scsi 0:0:1:0: Direct-Access     ATA      WDC WD100BB-75CL 05.0 PQ: 0 ANSI: 5
[   45.301114] scsi 1:0:0:0: CD-ROM            MITSUMI  CR-4804TE        3.0D PQ: 0 ANSI: 5
[   45.305994] scsi 1:0:1:0: Direct-Access     IOMEGA   ZIP 100          03.H PQ: 0 ANSI: 5
[   46.153258] Driver 'sd' needs updating - please use bus_type methods
[   46.158510] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   46.158566] sd 0:0:0:0: [sda] Write Protect is off
[   46.158576] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   46.158651] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   46.158826] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   46.158870] sd 0:0:0:0: [sda] Write Protect is off
[   46.158879] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   46.158952] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   46.158968]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[   46.197911]  sda5 >
[   46.198236] sd 0:0:0:0: [sda] Attached SCSI disk
[   46.198457] sd 0:0:1:0: [sdb] 19541088 512-byte hardware sectors (10005 MB)
[   46.198507] sd 0:0:1:0: [sdb] Write Protect is off
[   46.198518] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   46.198594] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   46.198745] sd 0:0:1:0: [sdb] 19541088 512-byte hardware sectors (10005 MB)
[   46.198789] sd 0:0:1:0: [sdb] Write Protect is off
[   46.198799] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   46.198873] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   46.198887]  sdb: sdb1
[   46.228547] sd 0:0:1:0: [sdb] Attached SCSI disk
[   46.233763] sd 1:0:1:0: [sdc] Attached SCSI removable disk
[   46.270957] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   46.270973] Uniform CD-ROM driver Revision: 3.20
[   46.271114] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   46.273746] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   46.273815] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   46.273879] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   46.273944] sd 1:0:1:0: Attached scsi generic sg3 type 0
[   50.409010] usb 1-2.3: new full speed USB device using uhci_hcd and address 5
[   50.535221] usb 1-2.3: configuration #1 chosen from 1 choice
[   50.740863] usb 1-2.4: new full speed USB device using uhci_hcd and address 6
[   50.867098] usb 1-2.4: configuration #1 chosen from 1 choice
[   50.870940] usbcore: registered new interface driver hiddev
[   50.879463] usbcore: registered new interface driver libusual
[   50.888561] input: Logitech Inc. iFeel Mouse    as /devices/pci0000:00/0000:00:07.2/usb1/1-1/1-1:1.0/input/input2
[   50.905068] Initializing USB Mass Storage driver...
[   50.907401] input,hidraw0: USB HID v1.00 Mouse [Logitech Inc. iFeel Mouse   ] on usb-0000:00:07.2-1
[   50.924003] input: Gravis GamePad Pro USB  as /devices/pci0000:00/0000:00:07.2/usb1/1-2/1-2.2/1-2.2:1.0/input/input3
[   50.924076] input,hidraw1: USB HID v1.00 Gamepad [Gravis GamePad Pro USB ] on usb-0000:00:07.2-2.2
[   50.924142] usbcore: registered new interface driver usbhid
[   50.924156] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   50.943226] scsi2 : SCSI emulation for USB Mass Storage devices
[   50.945282] usb-storage: device found at 5
[   50.945295] usb-storage: waiting for device to settle before scanning
[   50.957346] scsi3 : SCSI emulation for USB Mass Storage devices
[   50.968108] usbcore: registered new interface driver usb-storage
[   50.968125] USB Mass Storage support registered.
[   50.968430] usb-storage: device found at 6
[   50.968438] usb-storage: waiting for device to settle before scanning
[   51.166290] Attempting manual resume
[   51.166303] swsusp: Resume From Partition 8:5
[   51.166309] PM: Checking swsusp image.
[   51.166749] PM: Resume from disk failed.
[   51.257333] kjournald starting.  Commit interval 5 seconds
[   51.257376] EXT3-fs: mounted filesystem with ordered data mode.
[   55.943672] usb-storage: device scan complete
[   55.946660] scsi 2:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
[   55.952687] sd 2:0:0:0: [sdd] Attached SCSI removable disk
[   55.952815] sd 2:0:0:0: Attached scsi generic sg4 type 0
[   55.967610] usb-storage: device scan complete
[   55.970631] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW SE-S204S  TS01 PQ: 0 ANSI: 0
[   56.002559] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   56.002722] sr 3:0:0:0: Attached scsi CD-ROM sr1
[   56.002839] sr 3:0:0:0: Attached scsi generic sg5 type 5
[   65.468490] Linux agpgart interface v0.102
[   65.524209] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   65.632210] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   65.868249] agpgart: Detected an Intel 440BX Chipset.
[   65.873094] agpgart: AGP aperture is 64M @ 0xec000000
[   66.074933] PCI: Enabling device 0000:00:0e.1 (0104 -> 0105)
[   66.091635] gameport: EMU10K1 is pci0000:00:0e.1/gameport0, io 0x1010, speed 1217kHz
[   66.156379] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   66.468124] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   70.517436] nvidia: module license 'NVIDIA' taints kernel.
[   72.085804] parport_pc 00:14: reported by Plug and Play BIOS
[   72.085882] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   73.043556] PCI: setting IRQ 11 as level-triggered
[   73.043570] PCI: Found IRQ 11 for device 0000:01:00.0
[   73.043593] PCI: Sharing IRQ 11 with 0000:00:0e.0
[   73.044500] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
[   73.826443] PCI: Enabling device 0000:00:0e.0 (0104 -> 0105)
[   73.826465] PCI: Found IRQ 11 for device 0000:00:0e.0
[   73.826495] PCI: Sharing IRQ 11 with 0000:01:00.0
[   78.708923] lp0: using parport0 (interrupt-driven).
[   78.840947] Adding 746980k swap on /dev/sda5.  Priority:-1 extents:1 across:746980k
[   79.574328] EXT3 FS on sda1, internal journal
[   79.863281] device-mapper: uevent: version 1.0.3
[   79.863367] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   87.652018] ip_tables: (C) 2000-2006 Netfilter Core Team
[   90.750153] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   90.750414] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   90.751362] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   90.751764] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   92.919871] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   93.669464] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[   93.669504] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[   93.669550] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
[   95.209009] ppdev: user-space parallel port driver
[   95.698864] NET: Registered protocol family 10
[   95.700370] lo: Disabled Privacy Extensions
[   95.877917] audit(1244376085.437:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4957 profile="/usr/sbin/cupsd" namespace="default"
[   96.758339] RPC: Registered udp transport module.
[   96.758355] RPC: Registered tcp transport module.
[   96.853897] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   97.030526] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   97.043157] NFSD: starting 90-second grace period
[  101.700694] eth0: DSPCFG accepted after 0 usec.
[  101.700720] eth0: link up.
[  102.066078] Bluetooth: Core ver 2.11
[  102.067685] NET: Registered protocol family 31
[  102.067700] Bluetooth: HCI device and connection manager initialized
[  102.067712] Bluetooth: HCI socket layer initialized
[  102.269814] Bluetooth: L2CAP ver 2.9
[  102.269829] Bluetooth: L2CAP socket layer initialized
[  102.478783] Bluetooth: RFCOMM socket layer initialized
[  102.478833] Bluetooth: RFCOMM TTY layer initialized
[  102.478841] Bluetooth: RFCOMM ver 1.8
[  104.337758] NET: Registered protocol family 17
[  121.795720] eth0: no IPv6 routers present
[  518.729404] sr 1:0:0:0: [sr0] Device not ready: Sense Key : Not Ready [current] 
[  518.729428] sr 1:0:0:0: [sr0] Device not ready: Add. Sense: Medium not present
[B][  518.729450] end_request: I/O error, dev sr0, sector 0
[  518.729461] Buffer I/O error on device sr0, logical block 0
[  518.729474] Buffer I/O error on device sr0, logical block 1
[  518.729486] Buffer I/O error on device sr0, logical block 2
[  518.729495] Buffer I/O error on device sr0, logical block 3
[  518.729504] Buffer I/O error on device sr0, logical block 4
[  518.729513] Buffer I/O error on device sr0, logical block 5
[  518.729522] Buffer I/O error on device sr0, logical block 6
[  518.729531] Buffer I/O error on device sr0, logical block 7[/B]
[  518.734464] sr 1:0:0:0: [sr0] Device not ready: Sense Key : Not Ready [current] 
[  518.734486] sr 1:0:0:0: [sr0] Device not ready: Add. Sense: Medium not present
[  518.734506] end_request: I/O error, dev sr0, sector 0
[  518.734517] Buffer I/O error on device sr0, logical block 0
[  518.736949] sr 1:0:0:0: [sr0] Device not ready: Sense Key : Not Ready [current] 
[  518.736967] sr 1:0:0:0: [sr0] Device not ready: Add. Sense: Medium not present
[  518.736982] end_request: I/O error, dev sr0, sector 4
[  518.736991] Buffer I/O error on device sr0, logical block 1
[  518.776167] sr 1:0:0:0: [sr0] Device not ready: Sense Key : Not Ready [current] 
[  518.776191] sr 1:0:0:0: [sr0] Device not ready: Add. Sense: Medium not present
[  518.776213] end_request: I/O error, dev sr0, sector 0
[  518.779084] sr 1:0:0:0: [sr0] Device not ready: Sense Key : Not Ready [current] 
[  518.779105] sr 1:0:0:0: [sr0] Device not ready: Add. Sense: Medium not present
[  518.779125] end_request: I/O error, dev sr0, sector 4
[  518.781766] sr 1:0:0:0: [sr0] Device not ready: Sense Key : Not Ready [current] 
[  518.781787] sr 1:0:0:0: [sr0] Device not ready: Add. Sense: Medium not present
[  518.781806] end_request: I/O error, dev sr0, sector 0
[ 1973.188859] usb 1-2.4: reset full speed USB device using uhci_hcd and address 6
**[ 2116.355477] cdrom: This disc doesn't have any tracks I recognize!**
[ 2116.530340] usb 1-2.4: reset full speed USB device using uhci_hcd and address 6
[ 2132.562243] usb 1-2.4: reset full speed USB device using uhci_hcd and address 6
[ 2329.810259] eth0: increased tx threshold, txcfg 0x10f01004.
[ 2332.948249] eth0: increased tx threshold, txcfg 0x10f01006.
[ 3102.489602] eth0: increased tx threshold, txcfg 0x10f01008.
[ 3201.238918] eth0: increased tx threshold, txcfg 0x10f0100a.

The bolded lines seemed very interesting.

Now, sometimes, the disc will be in long enough to be mounted, so I know it's not a data error or corrupt file format. 

Another note: This drive originaly came in a USB 1.0 casing, but I removed the adapter and stuck it in as a normal Master IDE device.

---

