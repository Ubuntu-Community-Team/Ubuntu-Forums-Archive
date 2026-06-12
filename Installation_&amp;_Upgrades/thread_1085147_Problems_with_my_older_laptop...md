---
title: "Problems with my older laptop.."
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by andrewbrown22 on 2009-03-02
I have an older laptop, an Averatec 3150HS to be exact. Within the past year I've upgraded the hard drive to a newer, faster, and bigger 80GB drive.  After installing that upgrade, I installed Ubuntu 8.04 without any problems and it ran great.
I then decided to upgrade the RAM from the measly 256MB it came with.  I added a 512MB stick from Corsair and it all worked great, even better than before.
For some reason, I decided to ditch that install of Ubuntu I had, looking for a different route for this computer, I didn't use it much if any, and I was looking for a reason to use it more.  I decided to dabble in Fluxbox and even Kubuntu a little.
So I loaded up the Mint Fluxbox Edition live disc and went to it. I hit the install icon on the desktop and started the installation, wiping the drive.  The install got hung up at some point and wouldn't budge, it did nothing. I thought maybe it was the disc, so I gave up on that and started to try out Kubuntu 8.10.
Kubuntu 8.10 Live CD stalled, Kubuntu 8.10 Alternate CD stalled, Ubuntu 8.10 Live CD stalled, and even the exact Ubuntu 8.04 Alternate CD I had used previously on this exact computer stalled during installation.

I ran memtest86+ and didn't see any errors after the 4th test (~2hrs into the test). I even removed the new RAM, put in the old and the install still hung.

What do I even need to be checking for?  It worked flawlessly in the past, I've had every release of Ubuntu since 7.04 on it at least once one point in time.  I'm stumped.

---

### Post by Pumalite on 2009-03-02
Use Gparted Live CD. Delete everything in the drive and format it ext3. Try to install again.
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

### Post by andrewbrown22 on 2009-03-02
What about using the Ubuntu Live CD and using Gparted to delete it all? I'll go try that right now.

---

### Post by andrewbrown22 on 2009-03-02
Had problems deleting the swap partition, did some reading to find that you can't do that with the LiveCD. I'm currently downloading the Gparted disc from the link provided. I'll see how that goes.

---

### Post by andrewbrown22 on 2009-03-02
While it is downloading, I will note that the installation of all of the various versions I tried to installed hung at different points on every try.  It wasn't that it got stuck at the partitioning part or that it messed up installing the base system. It seemed random at which points it messed up.

---

### Post by andrewbrown22 on 2009-03-02
Even after deleting the swap partition and the regular partition and formatting the entire drive to ext3, the Ubuntu 8.04 install hangs, this time at 35% while "Copying files..."

The LiveCD works and everything runs like normal, it seems like it would run off of that LiveCD for as long as I want it too, I just can't install the OS!

---

### Post by pdipizzo on 2009-03-03
My old laptop has only 256 MG of RAM, which is not much, but similar to another laptop running Ubuntu, and does the same thing. I'll try some of these solutions too.

---

### Post by haiku88 on 2009-03-03
how long did you wait?  I just installed Ubuntu on a friends old laptop and it hung for literally a few minutes, then proceeded OK...first time I've seen that

---

### Post by andrewbrown22 on 2009-03-03
At least 5 minutes.  It's just strange that it hangs on various stages, sometimes it goes through one stage fine and locks up on another, then when I try it again, the first stage makes it hang.
I'll try again tonight and wait longer, but the hard drive nor the CD drive are active when these "hangs" occur.

---

### Post by Pumalite on 2009-03-03
If you have 256 MB of RAM or less, is better to use Xubuntu Alternate CD to install and run. (lighter Desktop)

---

### Post by andrewbrown22 on 2009-03-03
Right. I have used Xubuntu in the past and wasn't too pleased with it versus Ubuntu.  I've had Ubuntu 8.04 on this very laptop with 256MB of RAM and it even worked after I upgraded the RAM.  I just thought about trying fluxbox and wanted to start from scratch... and now I can't even install Ubuntu 8.04 with the exact same disc I used on the same computer before.

---

### Post by Pumalite on 2009-03-03
Clean the HH. Maybe it would be a good and cheap idea to install more memory. Do you have any OS in the HH?

---

### Post by andrewbrown22 on 2009-03-03
I have upgraded the memory from 256MB (which worked fine with Hardy Heron) to 640MB (added a 512 stick to the 128MB soldered on RAM).  This also worked fine, no problems with it at all.
Only after formatting the entire drive to ext3 upon trying to install Mint Fluxbox Edition have I ran across the issue. Now, no matter what disc I use to install with (even the same exact disc I installed with before) the installer hangs.

---

### Post by Pumalite on 2009-03-03
What did you use to format?
Post:
```
sudo fdisk -lu
```

---

### Post by andrewbrown22 on 2009-03-03
I formatted the drive first with the Mint Fluxbox installer, then again with the Ubuntu 8.04 installer, and then finally I downloaded and burnt the Gparted LiveCD to format the entire drive, removing the swap partition and all.
```
sudo fdisk -lu
``` 
gives me..
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x11251124

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   152713889    76356913+  83  Linux
/dev/sda2       152713890   156296384     1791247+   5  Extended
/dev/sda5       152713953   156296384     1791216   82  Linux swap / Solaris

```

---

### Post by ChrisMP1 on 2009-03-03
You can also do this, to remove a swap partition from the Ubuntu live CD:

(At a terminal)
```

sudo swapoff -a

```

Then remove the partition. If you have very little RAM, you should create another somewhere soon, and do:

```

sudo swapon -a

```

---

### Post by andrewbrown22 on 2009-03-03
I got it completely formatted, removed swap and all. Made one full 80GB ext3 partition and started the installer again. Still didn't work for it. Stalled at some other random spot

---

### Post by andrewbrown22 on 2009-03-04
Daily bump.
Any ideas? Anyone?

---

### Post by Pumalite on 2009-03-04
Your sudo fdisk doesn't look righ for a deleted (clean) and formated drive.

---

### Post by andrewbrown22 on 2009-03-04
That was run after I had already tried to install Ubuntu 8.04 again and the installer hung.  The drive wasn't completely formatted at that time, it was formatted by the installer.  Before I started the installation however, I used Gparted to format the entire drive.

---

### Post by Pumalite on 2009-03-04
Post your specs.
Or:
```
dmesg
```

---

### Post by andrewbrown22 on 2009-03-04
Averatec 3150HS
AMD Athlon XP-M Processor (@~1.4GHz I think)
640MB RAM
80GB Hard Drive
No wireless built in, nor do I have an adapter, I'm using wired networking only.
Need any other info?

---

### Post by andrewbrown22 on 2009-03-05
From an Ubuntu 8.04 LiveCD, I formatted the entire drive to ext3 again and here is what I get:
sudo fdisk -lu
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x11251124

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   156296384    78148161   83  Linux
```



And dmesg gives a very lengthy output, so I'll attach a text file with it.


EDIT: apparently my text file is too large. In that case, here it is...
```
ubuntu@ubuntu:~$ dmesg
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000d6000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000025ff0000 (usable)
[    0.000000]  BIOS-e820: 0000000025ff0000 - 0000000025ff8000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000025ff8000 - 0000000026000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 607MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 155632) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   155632
[    0.000000]   HighMem    155632 ->   155632
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   155632
[    0.000000] On node 0 totalpages: 155632
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1183 pages used for memmap
[    0.000000]   Normal zone: 150353 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FB5C0 checksum 0
[    0.000000] ACPI: RSDP 000FB5C0, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 25FF0000, 0028 (r1 AMIINT VIA_K7         10 MSFT       97)
[    0.000000] ACPI: FACP 25FF0030, 0081 (r1 AMIINT VIA_K7         11 MSFT       97)
[    0.000000] ACPI: DSDT 25FF00C0, 4194 (r1    VIA   VIA_K7     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 25FF8000, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 26000000:d9f80000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d0000 - 00000000000d6000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d6000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 154417
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (014ce000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1393.252 MHz processor.
[   27.722761] Console: colour VGA+ 80x25
[   27.722767] console [tty0] enabled
[   27.724356] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   27.727228] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   27.758576] Memory: 604580k/622528k available (2157k kernel code, 17440k reserved, 998k data, 364k init, 0k highmem)
[   27.758588] virtual kernel memory layout:
[   27.758590]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   27.758592]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   27.758594]     vmalloc : 0xe6800000 - 0xff7fe000   ( 399 MB)
[   27.758595]     lowmem  : 0xc0000000 - 0xe5ff0000   ( 607 MB)
[   27.758597]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   27.758599]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   27.758601]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   27.758607] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   27.758683] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   27.838614] Calibrating delay using timer specific routine.. 2790.07 BogoMIPS (lpj=5580152)
[   27.838671] Security Framework initialized
[   27.838683] SELinux:  Disabled at boot.
[   27.838717] AppArmor: AppArmor initialized
[   27.838725] Failure registering capabilities with primary security module.
[   27.838740] Mount-cache hash table entries: 512
[   27.838980] CPU: After generic identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   27.838995] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   27.838999] CPU: L2 Cache: 256K (64 bytes/line)
[   27.839004] CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 00000420 00000000 00000000 00000000 00000000
[   27.839021] Compat vDSO mapped to ffffe000.
[   27.839042] Checking 'hlt' instruction... OK.
[   27.854969] SMP alternatives: switching to UP code
[   27.856731] Freeing SMP alternatives: 11k freed
[   27.856974] Early unpacking initramfs... done
[   28.375410] ACPI: Core revision 20070126
[   28.375621] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   28.377924] ACPI: setting ELCR to 0200 (from 0c00)
[   28.389948] CPU0: AMD mobile AMD Athlon(tm) XP-M (LV) 1600+ stepping 01
[   28.389959] SMP motherboard not detected.
[   28.389963] Local APIC not detected. Using dummy APIC emulation.
[   28.390067] Brought up 1 CPUs
[   28.390119] CPU0 attaching sched-domain:
[   28.390123]  domain 0: span 01
[   28.390126]   groups: 01
[   28.390549] net_namespace: 64 bytes
[   28.390564] Booting paravirtualized kernel on bare hardware
[   28.391315] Time: 13:44:17  Date: 03/05/09
[   28.391383] NET: Registered protocol family 16
[   28.391766] EISA bus registered
[   28.391791] ACPI: bus type pci registered
[   28.393732] PCI: PCI BIOS revision 2.10 entry at 0xfdb51, last bus=1
[   28.393736] PCI: Using configuration type 1
[   28.393739] Setting up standard PCI resources
[   28.414693] ACPI: EC: Look up EC in DSDT
[   28.418007] ACPI: Interpreter enabled
[   28.418013] ACPI: (supports S0 S3 S4 S5)
[   28.418032] ACPI: Using PIC for interrupt routing
[   28.420223] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   28.422889] ACPI: EC: GPE = 0x4, I/O: command/status = 0x66, data = 0x62
[   28.422894] ACPI: EC: driver started in interrupt mode
[   28.422969] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   28.423470] PCI quirk: region 0800-087f claimed by vt8235 PM
[   28.423476] PCI quirk: region 0400-040f claimed by vt8235 SMB
[   28.423959] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   28.424156] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   28.427203] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 *11 14 15)
[   28.427326] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 5 9 14 15) *0, disabled.
[   28.427443] ACPI: PCI Interrupt Link [LNKC] (IRQs *10 12)
[   28.427557] ACPI: PCI Interrupt Link [LNKD] (IRQs 6 7) *0, disabled.
[   28.427723] Linux Plug and Play Support v0.97 (c) Adam Belay
[   28.427778] pnp: PnP ACPI init
[   28.427791] ACPI: bus type pnp registered
[   28.429562] pnp: PnP ACPI: found 9 devices
[   28.429566] ACPI: ACPI bus type pnp unregistered
[   28.429574] PnPBIOS: Disabled by ACPI PNP
[   28.430202] PCI: Using ACPI for IRQ routing
[   28.430207] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   28.441831] NET: Registered protocol family 8
[   28.441835] NET: Registered protocol family 20
[   28.441985] AppArmor: AppArmor Filesystem Enabled
[   28.445805] Time: tsc clocksource has been installed.
[   28.453863] system 00:01: ioport range 0x3f0-0x3f1 has been reserved
[   28.453868] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   28.453872] system 00:01: ioport range 0x400-0x40f has been reserved
[   28.453876] system 00:01: ioport range 0x820-0x821 has been reserved
[   28.453880] system 00:01: ioport range 0x862-0x862 has been reserved
[   28.453884] system 00:01: ioport range 0x866-0x866 has been reserved
[   28.453900] system 00:08: iomem range 0x0-0x9ffff could not be reserved
[   28.453904] system 00:08: iomem range 0xd0000-0xd5fff could not be reserved
[   28.453908] system 00:08: iomem range 0xf0000-0xfffff could not be reserved
[   28.453913] system 00:08: iomem range 0x100000-0x27ffffff could not be reserved
[   28.453917] system 00:08: iomem range 0xfff80000-0xffffffff could not be reserved
[   28.484596] PCI: Bridge: 0000:00:01.0
[   28.484599]   IO window: disabled.
[   28.484605]   MEM window: dfd00000-dfefffff
[   28.484610]   PREFETCH window: cfc00000-dfbfffff
[   28.484616] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[   28.484619]   IO window: 00001000-000010ff
[   28.484624]   IO window: 00001400-000014ff
[   28.484629]   PREFETCH window: 30000000-33ffffff
[   28.484634]   MEM window: 34000000-37ffffff
[   28.484666] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   28.484961] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   28.484967] PCI: setting IRQ 10 as level-triggered
[   28.484974] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   28.485003] NET: Registered protocol family 2
[   28.521901] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   28.522561] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   28.526629] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   28.528634] TCP: Hash tables configured (established 131072 bind 65536)
[   28.528642] TCP reno registered
[   28.538026] checking if image is initramfs... it is
[   28.985133] Switched to high resolution mode on CPU 0
[   29.502732] Freeing initrd memory: 7665k freed
[   29.503910] audit: initializing netlink socket (disabled)
[   29.503941] audit(1236260657.744:1): initialized
[   29.507310] VFS: Disk quotas dquot_6.5.1
[   29.507447] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   29.507732] io scheduler noop registered
[   29.507736] io scheduler anticipatory registered
[   29.507739] io scheduler deadline registered
[   29.507755] io scheduler cfq registered (default)
[   29.507784] PCI: VIA PCI bridge detected. Disabling DAC.
[   29.507867] Boot video device is 0000:01:00.0
[   29.508430] isapnp: Scanning for PnP cards...
[   29.862403] isapnp: No Plug & Play device found
[   29.910213] Real Time Clock Driver v1.12ac
[   29.910418] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   29.912399] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   29.912524] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   29.912691] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   29.914871] i8042.c: Detected active multiplexing controller, rev 1.1.
[   29.916028] serio: i8042 KBD port at 0x60,0x64 irq 1
[   29.916036] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   29.916040] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   29.916043] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   29.916047] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   29.927885] mice: PS/2 mouse device common for all mice
[   29.928101] EISA: Probing bus 0 at eisa.0
[   29.928115] Cannot allocate resource for EISA slot 1
[   29.928150] EISA: Detected 0 cards.
[   29.928157] cpuidle: using governor ladder
[   29.928160] cpuidle: using governor menu
[   29.928439] NET: Registered protocol family 1
[   29.928495] Using IPI No-Shortcut mode
[   29.928568] registered taskstats version 1
[   29.928721]   Magic number: 1:418:735
[   29.929114] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   29.929118] EDD information not available.
[   29.929947] Freeing unused kernel memory: 364k freed
[   29.963790] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   31.309413] fuse init (API version 7.9)
[   31.349512] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   31.377085] ACPI: Thermal Zone [THRM] (0 C)
[   32.284667] usbcore: registered new interface driver usbfs
[   32.284714] usbcore: registered new interface driver hub
[   32.297551] usbcore: registered new device driver usb
[   32.395502] SCSI subsystem initialized
[   32.401907] USB Universal Host Controller Interface driver v3.0
[   32.402340] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 7
[   32.402345] PCI: setting IRQ 7 as level-triggered
[   32.402352] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[   32.402362] PCI: VIA VLink IRQ fixup for 0000:00:10.0, from 0 to 7
[   32.402395] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   32.402903] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   32.402946] uhci_hcd 0000:00:10.0: irq 7, io base 0x0000e400
[   32.403220] usb usb1: configuration #1 chosen from 1 choice
[   32.403265] hub 1-0:1.0: USB hub found
[   32.403277] hub 1-0:1.0: 2 ports detected
[   32.504445] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[   32.504459] PCI: VIA VLink IRQ fixup for 0000:00:10.1, from 0 to 7
[   32.504494] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   32.504566] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   32.504601] uhci_hcd 0000:00:10.1: irq 7, io base 0x0000e800
[   32.504808] usb usb2: configuration #1 chosen from 1 choice
[   32.504848] hub 2-0:1.0: USB hub found
[   32.504859] hub 2-0:1.0: 2 ports detected
[   32.514040] libata version 3.00 loaded.
[   32.524795] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   32.608569] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[   32.608582] PCI: VIA VLink IRQ fixup for 0000:00:10.2, from 0 to 7
[   32.608616] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   32.608658] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   32.608689] uhci_hcd 0000:00:10.2: irq 7, io base 0x0000ec00
[   32.608884] usb usb3: configuration #1 chosen from 1 choice
[   32.608922] hub 3-0:1.0: USB hub found
[   32.608932] hub 3-0:1.0: 2 ports detected
[   32.712373] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[   32.712389] PCI: VIA VLink IRQ fixup for 0000:00:10.3, from 0 to 7
[   32.712426] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   32.712501] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   32.712570] ehci_hcd 0000:00:10.3: irq 7, io mem 0xdfffff00
[   32.723933] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   32.724178] usb usb4: configuration #1 chosen from 1 choice
[   32.724220] hub 4-0:1.0: USB hub found
[   32.724234] hub 4-0:1.0: 6 ports detected
[   32.828517] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   32.828526] PCI: setting IRQ 11 as level-triggered
[   32.828533] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   32.833305] eth0: VIA Rhine II at 0xdffffe00, 00:40:45:13:42:3a, IRQ 11.
[   32.834021] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   32.840499] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   32.840618] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   32.846768] pata_via 0000:00:11.1: version 0.3.3
[   32.846807] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   32.849758] scsi0 : pata_via
[   32.851460] scsi1 : pata_via
[   32.853655] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   32.853660] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   33.385158] ata1.00: ATA-7: WDC WD800BEVE-00UYT0, 01.04A01, max UDMA/100
[   33.385168] ata1.00: 156301488 sectors, multi 16: LBA48 
[   33.385192] ata1.00: limited to UDMA/33 due to 40-wire cable
[   33.400384] ata1.00: configured for UDMA/33
[   33.875124] ata2.00: ATAPI: UJDA740 DVD/CDRW, 1.20, max UDMA/33
[   34.046761] ata2.00: configured for UDMA/33
[   34.046988] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800BEVE-00 01.0 PQ: 0 ANSI: 5
[   34.053001] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA740 DVD/CDRW 1.20 PQ: 0 ANSI: 5
[   34.068495] Driver 'sd' needs updating - please use bus_type methods
[   34.068664] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   34.068689] sd 0:0:0:0: [sda] Write Protect is off
[   34.068693] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.068724] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.068815] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   34.068832] sd 0:0:0:0: [sda] Write Protect is off
[   34.068836] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.068862] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.068868]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   34.111492]  sda1 sda2 < sda5 >
[   34.145160] sd 0:0:0:0: [sda] Attached SCSI disk
[   34.154696] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   34.154733] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   34.155894] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   34.155906] Uniform CD-ROM driver Revision: 3.20
[   34.156002] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   34.929806] kjournald starting.  Commit interval 5 seconds
[   34.929836] EXT3-fs: mounted filesystem with ordered data mode.
[   35.668462] ISO 9660 Extensions: Microsoft Joliet Level 3
[   35.721543] ISO 9660 Extensions: RRIP_1991A
[   36.035024] Registering unionfs 1.4
[   36.035033] unionfs: debugging is not enabled
[   36.054208] loop: module loaded
[   36.389863] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[   80.501713] ACPI: Battery Slot [BAT0] (battery absent)
[  101.346190] input: PC Speaker as /devices/platform/pcspkr/input/input2
[  102.293468] Synaptics Touchpad, model: 1, fw: 5.1, id: 0x8f40b1, caps: 0x80471b/0x0
[  102.331071] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input3
[  102.496002] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  102.632581] Linux agpgart interface v0.102
[  103.324566] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  104.069611] agpgart: Detected VIA Apollo Pro266 chipset
[  104.075143] agpgart: AGP aperture is 64M @ 0xe0000000
[  104.342004] irda_init()
[  104.342047] NET: Registered protocol family 23
[  104.425227] input: Power Button (FF) as /devices/virtual/input/input4
[  104.449007] ACPI: Power Button (FF) [PWRF]
[  104.449121] input: Power Button (CM) as /devices/virtual/input/input5
[  104.472993] ACPI: Power Button (CM) [PWRB]
[  104.473113] input: Sleep Button (CM) as /devices/virtual/input/input6
[  104.492964] ACPI: Sleep Button (CM) [SLPB]
[  104.493071] input: Lid Switch as /devices/virtual/input/input7
[  104.505092] ACPI: Lid Switch [LIDD]
[  104.755826] Yenta: CardBus bridge found at 0000:00:0a.0 [14ff:c602]
[  104.755855] Yenta O2: res at 0x94/0xD4: 00/ea
[  104.755858] Yenta O2: enabling read prefetch/write burst
[  104.881126] Yenta: ISA IRQ mask 0x0038, PCI irq 10
[  104.881135] Socket status: 30000007
[  105.380530] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:06/LNXVIDEO:00/input/input8
[  105.411709] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[  105.831713] ACPI: AC Adapter [AC] (on-line)
[  106.732119] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[  106.735185] PCI: Setting latency timer of device 0000:00:11.6 to 64
[  107.242647] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[  107.242806] PCI: Setting latency timer of device 0000:00:11.5 to 64
[  109.164557] cs: IO port probe 0x100-0x3af: clean.
[  109.166706] cs: IO port probe 0x3e0-0x4ff: clean.
[  109.167551] cs: IO port probe 0x820-0x8ff: clean.
[  109.168007] cs: IO port probe 0xc00-0xcf7: clean.
[  109.168988] cs: IO port probe 0xa00-0xaff: clean.
[  111.502416] Adding 1791208k swap on /dev/sda5.  Priority:-1 extents:1 across:1791208k
[  112.374644] ip_tables: (C) 2000-2006 Netfilter Core Team
[  114.732357] No dock devices found.
[  116.236391] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[  116.240540] powernow: SGTC: 13333
[  116.240543] powernow: Minimum speed 398 MHz. Maximum speed 1393 MHz.
[  119.974592] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  119.974602] apm: overridden by ACPI.
[  120.310091] lp: driver loaded but no devices found
[  120.487920] ppdev: user-space parallel port driver
[  328.100659] Marking TSC unstable due to: cpufreq changes.
[  328.110674] Time: acpi_pm clocksource has been installed.
[  438.048899] Clocksource tsc unstable (delta = -337748547 ns)
[  127.114341] eth0: link down
[  446.699450] Bluetooth: Core ver 2.11
[  446.708248] NET: Registered protocol family 31
[  446.708269] Bluetooth: HCI device and connection manager initialized
[  446.708288] Bluetooth: HCI socket layer initialized
[  127.584318] Bluetooth: L2CAP ver 2.9
[  127.584328] Bluetooth: L2CAP socket layer initialized
[  336.139823] Bluetooth: RFCOMM socket layer initialized
[  336.141825] Bluetooth: RFCOMM TTY layer initialized
[  336.141839] Bluetooth: RFCOMM ver 1.8
[  132.673092] [drm] Initialized drm 1.1.0 20060810
[  465.148521] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[  465.148550] PCI: setting IRQ 9 as level-triggered
[  465.148563] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[  465.157354] [drm] Initialized savage 2.4.1 20050313 on minor 0
[  465.161343] mtrr: base(0xd2000000) is not aligned on a size(0x5000000) boundary
[  465.162629] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  465.162676] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[  465.162772] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[  489.112208] NET: Registered protocol family 10
[  489.115239] lo: Disabled Privacy Extensions
[  489.127418] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  198.713551] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[  204.791136] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[  216.447607] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[  277.925282] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO

```

---

### Post by Pumalite on 2009-03-05
Download a new iso and burn at 4x or less after doing md5sum.

---

### Post by andrewbrown22 on 2009-03-05
Ok, a new download is starting.  However, I've used these exact discs on this exact system with the exact same configuration.  I've tried a number of install discs known to work on this system and work on various other computers I have used around the house.
I'll try the new download/burn as soon as it completes but I'm thinking something else is at fault here

---

### Post by andrewbrown22 on 2009-03-05
Even with a new burn from a new iso it doesn't work.
It got stuck on "Select and Install Software" at 6% with the message to "Please wait..."

---

### Post by andrewbrown22 on 2009-03-06
Morning bump..
Later tonight I plan on trying to install using a USB drive I made of Ubuntu 8.10 on another computer, but any other ideas?

---

### Post by andrewbrown22 on 2009-03-08
Never got it to even boot from the USB drive, I'm not sure that it is even supported on this laptop.  I don't really know what else to try on it. Any more suggestions?

---

### Post by andrewbrown22 on 2009-03-08
I managed to get the Ubuntu 8.10 Server disc to properly install.  What do I need to do to have this computer run GNOME by default at startup, just like a normal desktop install of Ubuntu?  I've finally got it this far, to a functional server install, but I'd like to move past that and have a full Ubuntu desktop installed on here. What commands do I run to make that happen?

---

### Post by Pumalite on 2009-03-08
You have problems with your card, your display or both; so you might end up with a blank screen, but if you want to try:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by andrewbrown22 on 2009-03-08
I have problems with what?

Do I need to install an xserver or anything like that? I've done some reading online but I'm not sure what all I have to do to run the true GNOME desktop.

---

### Post by cmay on 2009-03-08
i almost left ubuntu because of a bug in the installer 
[http://ubuntuforums.org/showthread.php?p=6396249#post6396249](http://ubuntuforums.org/showthread.php?p=6396249#post6396249)

i removed the dvddrive and put in another one on the computer i had been trying to install to and problem went away for some reason.
  i also found out that if i had installed something else than linux file system such as open-solaris or bsd then no problems occured.

 maybe do as the bugreport here suggest and try to pick out the ram and put them back in. if the problem is indeed the same as file as a bug in the installer and not coursed by other things. i just read the tread and found it to look pretty much like my problems back then.
 
good luck to you.

---

### Post by andrewbrown22 on 2009-03-08
I only have the option of removing the 128MB stick and putting in the 512MB or vice versa, as this laptop has 128MB of RAM soldered in.  I've tried it with both setups and it didn't change anything.
I'm currently trying to install the ubuntu-desktop "package" through apt-get right now. I'll post back when it gets done installing with my results.

---

### Post by cmay on 2009-03-08
if it works then its great. if it fails then try to make it as it was before you put in any more ram. then upgrade the ram after reinstalling. i am not sure if it has any effect at all but i have had the same symptoms as you describe.
should it fail completly there is two options you could use. there is the minmimal ubuntu or alternative cd image with the textbased installer.
 or you try debian lenny on it and see if that works.  
good luck.

---

### Post by andrewbrown22 on 2009-03-08
I've tried it just as it was, and the installer failed. I've tried the alternate CDs (both 8.04 and 8.10) and they've all failed to install.  I've even used the same alternate CD of 8.04 I used to install on this very computer before and it didn't work.

The server disc did work and installing the "ubuntu-desktop" worked as now I can boot into Ubuntu 8.10, but it's using the server kernels now and I wonder if that will affect the use of the machine at all?  Is there any way to get it to start using the regular desktop kernels and remove the server "part" of this installation?

---

### Post by andrewbrown22 on 2009-03-09
I decided to give something else a try, and it surprised me..
I popped in a Windows XP Pro disc and it worked flawlessly, it's running fine right now.  Of course, XP isn't what I intended to run on this machine and it's really confusing me as to why none of the Linux discs would work but the Windows did.
This isn't because of hardware incompatibility either, because this computer with these exact same components has run Ubuntu 8.04 perfectly fine in the past..

---

### Post by andrewbrown22 on 2009-03-09
XP is still running great on it, even after finally finishing all of the updates and all.
Any ideas why XP installed but all versions of Ubuntu I tried didn't this time?

---

### Post by cmay on 2009-03-10
it sounds like the bug i had so many many troubles with. maybe you can get intrepid ibex to install over xp now. or try debian lenny. i am sure that if you use the alternative installer image ubuntu can install if that is what you want. i had maybe done a other thing and installed a distro like opensuse or something like that to see what happened and then gone ahead and installed ubuntu again. i dont have a windows xp disk lying around so i could not try that.

---

