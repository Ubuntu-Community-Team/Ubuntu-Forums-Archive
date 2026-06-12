---
title: "Toshiba Portege M750 suspend doesn't work"
date: 2008-12-12
forum: Hardware
---

### Post by arestivo on 2008-12-12
Hi,

I just installed ubuntu into my new Portege 750 Tablet PC (basically an upgraded version of the M700). After some tweaking everything is working except suspending to RAM. 

Suspend seems to work but coming out of suspend gives me a blank screen, a mouse pointer that doesn't move and, after a while, a spinning like crazy fan.

Here is my pm-suspend.log (which seems fine):

```

Initial commandline parameters: 
Fri Dec 12 19:18:02 WET 2008: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/00clear suspend: success.
/usr/lib/pm-utils/sleep.d/05led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/10NetworkManager suspend: success.
/usr/lib/pm-utils/sleep.d/48hid2hci suspend: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend: not applicable.
/usr/lib/pm-utils/sleep.d/50modules suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend: success.
/usr/lib/pm-utils/sleep.d/95led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend: success.
Fri Dec 12 19:18:06 WET 2008: performing suspend

```

Is there anything more I can do? I'm totally lost here.

Thanks,

Andre Restivo

---

### Post by arestivo on 2008-12-18
I've been searching for a solution for this problem and this is what I found so far:

I followed the [DebuggingKernelSuspend]("https://wiki.ubuntu.com/DebuggingKernelSuspend") tutorial but the only "hash matches" line I get on dmesg is:

[1.501712] hash matches /build/buildd/linux-2.6.27/drivers/base/power/main.c:390

If I switch to a text console and run "sudo pm-suspend" I can successfully return from suspend but when I try to switch to gnome the computer freezes. Doing this and killing X before switching back to gnome works but I lose my gnome session.

---

### Post by arestivo on 2008-12-19
I opened a bug in lauchpad [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/309535]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/309535")

---

### Post by MORDOCtheGREAT on 2008-12-21
I have a similar problem on my Toshiba Satellite L355D.  The computer seems to suspend properly, with the power light doing its little slow flash thing.  But when I try to return from it all I get is a black screen.  Here is my suspend log output. 
 ```
 Initial commandline parameters: 
Sun Dec 21 09:21:13 CST 2008: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/00clear suspend: success.
/usr/lib/pm-utils/sleep.d/05led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/10NetworkManager suspend: success.
/usr/lib/pm-utils/sleep.d/48hid2hci suspend: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend: not applicable.
/usr/lib/pm-utils/sleep.d/50modules suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend: success.
/usr/lib/pm-utils/sleep.d/95led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend: success.
Sun Dec 21 09:21:16 CST 2008: performing suspend
```
I am also at a loss as to what to do.  I guess I'll watch the launchpad page to see if something comes up.

---

### Post by arestivo on 2009-01-12
Just found out that suspend works with my M750 on Fedora 10 live cd.

---

### Post by arestivo on 2009-02-11
It seems to be working now. Probably one of the updates corrected something. No idea which one did it.

---

### Post by X-Kent on 2009-05-13
Can you confirm that touch screen and pen is working ? If so would you mind to help me with your xorg.conf file and "dmesg | grep ttyS' command output ?

---

### Post by arestivo on 2009-05-14
It's all working. I just followed [this]("https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700") tutorial.

Here goes my xorg.conf

```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option 		"MonitorLayout"	"CRT,LFP" 
	Option 		"Clone" 	"true"
EndSection

Section "InputDevice"
	Identifier      "stylus"
	Driver          "wacom"
	Option          "Device"        "/dev/ttyS0"
	Option          "Type"          "stylus"
	Option          "ForceDevice"   "ISDV4"
	Option          "Mode"          "absolute"
	Option          "SendCoreEvents"        "true"
	Option		"Button2"	"3"
EndSection

Section "InputDevice"
	Identifier      "eraser"
	Driver          "wacom"
	Option          "Device"        "/dev/ttyS0"
	Option          "Type"          "eraser"
	Option          "ForceDevice"   "ISDV4"
	Option          "Mode"          "absolute"
	Option          "SendCoreEvents"        "true"
	Option		"Button1"	"2"	
EndSection

Section "InputDevice"
	Identifier      "touch"
	Driver          "wacom"
	Option          "Device"        "/dev/ttyS0"
	Option          "Type"          "touch"
	Option          "ForceDevice"   "ISDV4"
	Option          "Mode"          "absolute"
	Option          "SendCoreEvents"        "true"
EndSection

Section "ServerLayout"
	Identifier    "Default Layout"
	Screen        "Default Screen"
	InputDevice     "stylus"        "SendCoreEvents"
	InputDevice     "touch"        "SendCoreEvents"
	InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option          "RandRRotation" "true"
EndSection

```

dmesg doesn't have any lines with ttyS on it. Hope it helps.

---

### Post by Favux on 2009-05-14
Hi arestivo,

Thank you for helping us out.  Do you mean that when you type in a terminal:
```
dmesg | grep ttyS
```
you don't get any output?  If so on your 750 did you use the setserial line for the 700 in the tutorial ie:
```
/bin/setserial /dev/ttyS0 port 0x338 irq 4 autoconfig
```
And did you put it in "/bin/setserial" like the guy in the tutorial did?

---

### Post by arestivo on 2009-05-17
> **Favux said:**
> 
Do you mean that when you type in a terminal:
```
dmesg | grep ttyS
```
you don't get any output?  

Exactly. I can post my complete dmesg if you want.
> **Favux said:**
> 
If so on your 750 did you use the setserial line for the 700 in the tutorial ie:
```
/bin/setserial /dev/ttyS0 port 0x338 irq 4 autoconfig
```
And did you put it in "/bin/setserial" like the guy in the tutorial did?

If I remember correctly I did everything exactly as specified in the tutorial without a single problem. I'm still using 8.10 btw.

Are you getting any error messages or is it simply not working?

---

### Post by arestivo on 2009-05-17
Just checked and I have the setserial line in rc.local exactly as in the tutorial.

---

### Post by Favux on 2009-05-17
Hi arestivo,

Yes please post your dmesg output.  Thank you.  OK, so the 700's setserial line does work for the 750, at least in Intrepid.  Very good to know.

---

### Post by X-Kent on 2009-05-19
I am currently trying to setup the same on my m750 but I am using Jaunty.
Seems our configurations are the same but once I add the "input" lines to the "server layout" section X server crashes. 

I found some errors about segfaults in wacom_drv but I am not sure if that's the problem but is seems very suspicious.

May you check what version of wacom-tools and xinput-wacom you are using ?
I am on 0.8.2.2 and my X crashes :-(.

---

### Post by arestivo on 2009-05-20
> **X-Kent said:**
> I found some errors about segfaults in wacom_drv but I am not sure if that's the problem but is seems very suspicious.

May you check what version of wacom-tools and xinput-wacom you are using ?
I am on 0.8.2.2 and my X crashes :-(.

I'm on 0.8.1.4. I was thinking about upgrading to jaunty and now I'm not so sure it's a good idea :-(

Where did you find the errors? I can take a look to see if I have them too.

---

### Post by arestivo on 2009-05-20
Here goes my complete dmesg. I do have some tty related lines after all. The first time I tried to look for them I had the computer up for to long and did to much suspend and resumes so the dmesg wasn't complete anymore.

tty related lines:

```

[    0.004000] console [tty0] enabled
[    1.505360] tty ttyyc: hash matches
[    1.505370] tty tty48: hash matches
[   13.963533] cdc_acm 4-4:1.1: ttyACM0: USB ACM device
[   13.964414] cdc_acm 4-4:1.3: ttyACM1: USB ACM device
[   13.964986] cdc_acm 4-4:1.9: ttyACM2: USB ACM device
```

Complete dmesg:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-14-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) ) #1 SMP Wed Apr 15 18:59:16 UTC 2009 (Ubuntu 2.6.27-14.33-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009bc00 (usable)
[    0.000000]  BIOS-e820: 000000000009bc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 00000000000eee00 (reserved)
[    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7990000 (usable)
[    0.000000]  BIOS-e820: 00000000b7990000 - 00000000b79a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000b79a0000 - 00000000b79a2000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b79b0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec18000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec20000 - 00000000fec28000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00500 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed94000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffa00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffd00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000013c000000 (usable)
[    0.000000] DMI 2.5 present.
[    0.000000] last_pfn = 0xb7990 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 377e8000 - 37fefa14
[    0.000000] ACPI: RSDP 000F00B0, 0014 (r0 TOSHIB)
[    0.000000] ACPI: RSDT B7990000, 0058 (r1 TOSHIB A0069    20080729 TASM  4010000)
[    0.000000] ACPI: FACP B7990084, 0084 (r2 TOSHIB A0069    20080729 TASM  4010000)
[    0.000000] ACPI: DSDT B7990108, 6E95 (r2 TOSHIB A0069    20080729 MSFT  3000000)
[    0.000000] ACPI: FACS 000EEE00, 0040
[    0.000000] ACPI: SSDT B7996F9D, 0506 (r2 TOSHIB A0069    20070720 MSFT  3000000)
[    0.000000] ACPI: DBGP B7997B53, 0034 (r1 TOSHIB A0069    20080729 TASM  4010000)
[    0.000000] ACPI: BOOT B799005C, 0028 (r1 TOSHIB A0069    20080729 TASM  4010000)
[    0.000000] ACPI: APIC B7997A77, 0068 (r1 TOSHIB A0069    20080729 TASM  4010000)
[    0.000000] ACPI: MCFG B7997ADF, 003C (r1 TOSHIB A0069    20080729 TASM  4010000)
[    0.000000] ACPI: HPET B7997B1B, 0038 (r1 TOSHIB A0069    20080729 TASM  4010000)
[    0.000000] ACPI: TCPA B7997E20, 0032 (r2 TOSHIB A0069    20080729 TASM  4010000)
[    0.000000] ACPI: SLIC B7997E52, 0176 (r1 TOSHIB A0069    20080729 TASM  4010000)
[    0.000000] ACPI: ASF! B7997B87, 0075 (r16 TOSHIB A0069    20080729 TASM  4010000)
[    0.000000] ACPI: SSDT B7998D1D, 03ED (r2 TOSHIB A0069    20080317 MSFT  3000000)
[    0.000000] ACPI: SSDT B79982F4, 0A29 (r2 TOSHIB A0069    20080729 MSFT  3000000)
[    0.000000] ACPI: SSDT B7997FC8, 0076 (r2 TOSHIB A0069    20080310 MSFT  3000000)
[    0.000000] ACPI: DMI detected: Toshiba
[    0.000000] 2041MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c39e0]    TEXT DATA BSS ==> [0000100000 - 00005c39e0]
[    0.000000]   #4 [00377e8000 - 0037fefa14]          RAMDISK ==> [00377e8000 - 0037fefa14]
[    0.000000]   #5 [00005c4000 - 00005c7000]    INIT_PG_TABLE ==> [00005c4000 - 00005c7000]
[    0.000000]   #6 [000009bc00 - 0000100000]    BIOS reserved ==> [000009bc00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x000b7990
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x000b7990
[    0.000000] On node 0 totalpages: 751915
[    0.000000] free_area_init_node: node 0, pgdat c048c700, node_mem_map c1000000
[    0.000000]   DMA zone: 3959 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 518046 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0xd808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e8000
[    0.000000] PM: Registered nosave memory: 00000000000e8000 - 00000000000ee000
[    0.000000] PM: Registered nosave memory: 00000000000ee000 - 00000000000ef000
[    0.000000] PM: Registered nosave memory: 00000000000ef000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:3ec00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 745305
[    0.000000] Kernel command line: root=UUID=09eef246-5cb8-449b-b545-a2e913f3d744 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 2526.988 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2966356k/3008064k available (2578k kernel code, 40524k reserved, 1162k data, 428k init, 2090560k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0518000   ( 428 kB)
[    0.004000]       .data : 0xc0384a8a - 0xc04a7680   (1162 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0384a8a   (2578 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5053.97 BogoMIPS (lpj=10107952)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017570] ACPI: Core revision 20080609
[    0.019769] ACPI: Checking initramfs for custom DSDT
[    0.298039] ENABLING IO-APIC IRQs
[    0.298220] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.337916] CPU0: Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz stepping 06
[    0.340021] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5053.96 BogoMIPS (lpj=10107924)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.424845] CPU1: Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz stepping 06
[    0.424858] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.428042] Brought up 2 CPUs
[    0.428044] Total of 2 processors activated (10107.93 BogoMIPS).
[    0.428063] CPU0 attaching sched-domain:
[    0.428065]  domain 0: span 0-1 level MC
[    0.428067]   groups: 0 1
[    0.428072] CPU1 attaching sched-domain:
[    0.428073]  domain 0: span 0-1 level MC
[    0.428075]   groups: 1 0
[    0.428136] net_namespace: 840 bytes
[    0.428136] Booting paravirtualized kernel on bare hardware
[    0.428231] Time:  9:20:54  Date: 05/20/09
[    0.428251] NET: Registered protocol family 16
[    0.428266] EISA bus registered
[    0.428266] ACPI: bus type pci registered
[    0.428266] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.428266] PCI: Not using MMCONFIG.
[    0.448029] PCI: PCI BIOS revision 2.10 entry at 0xfa4a1, last bus=4
[    0.448031] PCI: Using configuration type 1 for base access
[    0.448786] ACPI: EC: Look up EC in DSDT
[    0.452337] ACPI Warning (dsobject-0501): Package List length (C) larger than NumElements count (4), truncated
[    0.452341]  [20080609]
[    0.455705] ACPI: Interpreter enabled
[    0.455708] ACPI: (supports S0 S3 S4 S5)
[    0.455719] ACPI: Using IOAPIC for interrupt routing
[    0.455762] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.460076] PCI: MCFG area at f0000000 reserved in ACPI motherboard resources
[    0.460078] PCI: Using MMCONFIG for extended config space
[    0.465055] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.465055] PCI: 0000:00:02.0 reg 10 64bit mmio: [ff400000, ff7fffff]
[    0.465055] PCI: 0000:00:02.0 reg 18 64bit mmio: [e0000000, efffffff]
[    0.465055] PCI: 0000:00:02.0 reg 20 io port: [cff8, cfff]
[    0.465055] PCI: 0000:00:02.1 reg 10 64bit mmio: [0, fffff]
[    0.465055] PCI: 0000:00:03.0 reg 10 64bit mmio: [ffcffff0, ffcfffff]
[    0.465055] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.465055] pci 0000:00:03.0: PME# disabled
[    0.465055] PCI: 0000:00:19.0 reg 10 32bit mmio: [ffcc0000, ffcdffff]
[    0.465055] PCI: 0000:00:19.0 reg 14 32bit mmio: [ffcfe000, ffcfefff]
[    0.465055] PCI: 0000:00:19.0 reg 18 io port: [cf80, cf9f]
[    0.465055] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.465055] pci 0000:00:19.0: PME# disabled
[    0.465055] PCI: 0000:00:1a.0 reg 20 io port: [cf60, cf7f]
[    0.465055] PCI: 0000:00:1a.1 reg 20 io port: [cf40, cf5f]
[    0.468104] PCI: 0000:00:1a.2 reg 20 io port: [cf20, cf3f]
[    0.468194] PCI: 0000:00:1a.7 reg 10 32bit mmio: [ffcff800, ffcffbff]
[    0.468272] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.468277] pci 0000:00:1a.7: PME# disabled
[    0.468319] PCI: 0000:00:1b.0 reg 10 64bit mmio: [0, 3fff]
[    0.468388] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.468392] pci 0000:00:1b.0: PME# disabled
[    0.468475] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.468479] pci 0000:00:1c.0: PME# disabled
[    0.468764] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.468768] pci 0000:00:1c.2: PME# disabled
[    0.468828] PCI: 0000:00:1d.0 reg 20 io port: [cf00, cf1f]
[    0.468917] PCI: 0000:00:1d.1 reg 20 io port: [cee0, ceff]
[    0.469005] PCI: 0000:00:1d.2 reg 20 io port: [cec0, cedf]
[    0.469095] PCI: 0000:00:1d.7 reg 10 32bit mmio: [ffcff400, ffcff7ff]
[    0.469172] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.469177] pci 0000:00:1d.7: PME# disabled
[    0.469408] PCI: 0000:00:1f.2 reg 10 io port: [ceb8, cebf]
[    0.469416] PCI: 0000:00:1f.2 reg 14 io port: [ceb4, ceb7]
[    0.469423] PCI: 0000:00:1f.2 reg 18 io port: [cea8, ceaf]
[    0.469429] PCI: 0000:00:1f.2 reg 1c io port: [cea4, cea7]
[    0.469436] PCI: 0000:00:1f.2 reg 20 io port: [ce80, ce9f]
[    0.469443] PCI: 0000:00:1f.2 reg 24 32bit mmio: [ffcfd800, ffcfdfff]
[    0.469503] pci 0000:00:1f.2: PME# supported from D3hot
[    0.469507] pci 0000:00:1f.2: PME# disabled
[    0.469622] PCI: 0000:01:00.0 reg 10 64bit mmio: [ff9fe000, ff9fffff]
[    0.469767] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold
[    0.469778] pci 0000:01:00.0: PME# disabled
[    0.469829] PCI: bridge 0000:00:1c.0 32bit mmio: [ff900000, ff9fffff]
[    0.469958] PCI: 0000:03:0b.0 reg 10 32bit mmio: [0, fff]
[    0.469988] pci 0000:03:0b.0: supports D1
[    0.469989] pci 0000:03:0b.0: supports D2
[    0.469990] pci 0000:03:0b.0: PME# supported from D0 D1 D2 D3hot
[    0.469995] pci 0000:03:0b.0: PME# disabled
[    0.470029] PCI: 0000:03:0b.1 reg 10 32bit mmio: [0, 7ff]
[    0.470092] pci 0000:03:0b.1: PME# supported from D0 D3hot D3cold
[    0.470097] pci 0000:03:0b.1: PME# disabled
[    0.470132] PCI: 0000:03:0b.2 reg 10 32bit mmio: [0, ff]
[    0.470194] pci 0000:03:0b.2: supports D1
[    0.470196] pci 0000:03:0b.2: supports D2
[    0.470197] pci 0000:03:0b.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.470201] pci 0000:03:0b.2: PME# disabled
[    0.470236] PCI: 0000:03:0b.3 reg 10 32bit mmio: [0, ff]
[    0.470299] pci 0000:03:0b.3: supports D1
[    0.470301] pci 0000:03:0b.3: supports D2
[    0.470302] pci 0000:03:0b.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.470306] pci 0000:03:0b.3: PME# disabled
[    0.470339] PCI: 0000:03:0b.4 reg 10 32bit mmio: [0, ff]
[    0.470404] pci 0000:03:0b.4: supports D1
[    0.470405] pci 0000:03:0b.4: supports D2
[    0.470406] pci 0000:03:0b.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.470411] pci 0000:03:0b.4: PME# disabled
[    0.470444] PCI: 0000:03:0b.5 reg 10 32bit mmio: [0, ff]
[    0.470711] pci 0000:03:0b.5: supports D1
[    0.470712] pci 0000:03:0b.5: supports D2
[    0.470714] pci 0000:03:0b.5: PME# supported from D0 D1 D2 D3hot D3cold
[    0.470718] pci 0000:03:0b.5: PME# disabled
[    0.470757] pci 0000:00:1e.0: transparent bridge
[    0.470805] bus 00 -> node 0
[    0.470810] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.471007] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.471131] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.MPEX._PRT]
[    0.471229] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.476853] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[    0.476853] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
[    0.476853] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
[    0.476853] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
[    0.476941] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
[    0.477093] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
[    0.477245] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *11)
[    0.477399] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
[    0.477471] ACPI Warning (tbutils-0217): Incorrect checksum in table [ASF!] - D2, should be 6A [20080609]
[    0.477471] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.477471] pnp: PnP ACPI init
[    0.477471] ACPI: bus type pnp registered
[    0.481332] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:00:02.1 BAR 0 (0x0-0xfffff), disabling
[    0.481335] pnp 00:00: mem resource (0xe8000-0xfffff) overlaps 0000:00:02.1 BAR 0 (0x0-0xfffff), disabling
[    0.485635] pnp: PnP ACPI: found 13 devices
[    0.485635] ACPI: ACPI bus type pnp unregistered
[    0.485635] PnPBIOS: Disabled by ACPI PNP
[    0.485635] PCI: Using ACPI for IRQ routing
[    0.492038] NET: Registered protocol family 8
[    0.492040] NET: Registered protocol family 20
[    0.492051] NetLabel: Initializing
[    0.492051] NetLabel:  domain hash size = 128
[    0.492051] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.492056] NetLabel:  unlabeled traffic allowed by default
[    0.492063] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.492067] hpet0: 4 64-bit timers, 14318180 Hz
[    0.493445] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.493448]    actual entries 65620
[    0.493504] AppArmor: AppArmor Filesystem Enabled
[    0.493529] ACPI: RTC can wake from S4
[    0.500050] system 00:00: iomem range 0x100000-0xb798ffff could not be reserved
[    0.500053] system 00:00: iomem range 0xb7990000-0xb799ffff could not be reserved
[    0.500055] system 00:00: iomem range 0xb79a0000-0xb79a1fff could not be reserved
[    0.500058] system 00:00: iomem range 0xb79b0000-0xb7cfffff could not be reserved
[    0.500060] system 00:00: iomem range 0xb7d00000-0xb7dfffff could not be reserved
[    0.500062] system 00:00: iomem range 0xb7e00000-0xbfffffff could not be reserved
[    0.500065] system 00:00: iomem range 0xfec00000-0xfec17fff could not be reserved
[    0.500067] system 00:00: iomem range 0xfec20000-0xfec27fff could not be reserved
[    0.500069] system 00:00: iomem range 0xfed00400-0xfed004ff could not be reserved
[    0.500071] system 00:00: iomem range 0xfed10000-0xfed19fff could not be reserved
[    0.500074] system 00:00: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    0.500076] system 00:00: iomem range 0xfed20000-0xfed3ffff could not be reserved
[    0.500078] system 00:00: iomem range 0xfed45000-0xfed8ffff could not be reserved
[    0.500081] system 00:00: iomem range 0xfed90000-0xfed93fff could not be reserved
[    0.500083] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.500085] system 00:00: iomem range 0xffa00000-0xffbfffff could not be reserved
[    0.500088] system 00:00: iomem range 0xffd00000-0xffffffff could not be reserved
[    0.500090] system 00:00: iomem range 0x0-0x3bffffff could not be reserved
[    0.500095] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.500103] system 00:09: ioport range 0x1e0-0x1ef has been reserved
[    0.500106] system 00:09: ioport range 0x480-0x48f has been reserved
[    0.500108] system 00:09: ioport range 0xe000-0xe07f has been reserved
[    0.500110] system 00:09: ioport range 0xe080-0xe0ff has been reserved
[    0.500112] system 00:09: ioport range 0xe400-0xe47f has been reserved
[    0.500114] system 00:09: ioport range 0xe480-0xe4ff has been reserved
[    0.500117] system 00:09: ioport range 0xe800-0xe87f has been reserved
[    0.500119] system 00:09: ioport range 0xe880-0xe8ff has been reserved
[    0.500121] system 00:09: ioport range 0xec00-0xec7f has been reserved
[    0.500123] system 00:09: ioport range 0xec80-0xecff has been reserved
[    0.500126] system 00:09: ioport range 0xd800-0xd87f has been reserved
[    0.500128] system 00:09: ioport range 0xd880-0xd89f has been reserved
[    0.500130] system 00:09: ioport range 0xee80-0xeeff has been reserved
[    0.500132] system 00:09: ioport range 0x690-0x6ff has been reserved
[    0.500136] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.500878] Switched to high resolution mode on CPU 1
[    0.504033] Switched to high resolution mode on CPU 0
[    0.535068] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.535070] pci 0000:00:1c.0:   IO window: disabled
[    0.535076] pci 0000:00:1c.0:   MEM window: 0xff900000-0xff9fffff
[    0.535080] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.535087] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:02
[    0.535088] pci 0000:00:1c.2:   IO window: disabled
[    0.535094] pci 0000:00:1c.2:   MEM window: disabled
[    0.535098] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.535125] pci 0000:03:0b.0: CardBus bridge, secondary bus 0000:04
[    0.535127] pci 0000:03:0b.0:   IO window: 0x001000-0x0010ff
[    0.535131] pci 0000:03:0b.0:   IO window: 0x001400-0x0014ff
[    0.535136] pci 0000:03:0b.0:   PREFETCH window: 0xc4000000-0xc7ffffff
[    0.535140] pci 0000:03:0b.0:   MEM window: 0xc8000000-0xcbffffff
[    0.535145] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.535148] pci 0000:00:1e.0:   IO window: 0x1000-0x1fff
[    0.535153] pci 0000:00:1e.0:   MEM window: 0xc8000000-0xcdffffff
[    0.535158] pci 0000:00:1e.0:   PREFETCH window: 0x000000c4000000-0x000000c7ffffff
[    0.535173] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.535178] pci 0000:00:1c.0: setting latency timer to 64
[    0.535186] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.535191] pci 0000:00:1c.2: setting latency timer to 64
[    0.535198] pci 0000:00:1e.0: setting latency timer to 64
[    0.535207] pci 0000:03:0b.0: enabling device (0000 -> 0003)
[    0.535211] pci 0000:03:0b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.535217] bus: 00 index 0 io port: [0, ffff]
[    0.535219] bus: 00 index 1 mmio: [0, ffffffff]
[    0.535220] bus: 01 index 0 mmio: [0, 0]
[    0.535222] bus: 01 index 1 mmio: [ff900000, ff9fffff]
[    0.535224] bus: 01 index 2 mmio: [0, 0]
[    0.535225] bus: 01 index 3 mmio: [0, 0]
[    0.535226] bus: 02 index 0 mmio: [0, 0]
[    0.535228] bus: 02 index 1 mmio: [0, 0]
[    0.535229] bus: 02 index 2 mmio: [0, 0]
[    0.535230] bus: 02 index 3 mmio: [0, 0]
[    0.535232] bus: 03 index 0 io port: [1000, 1fff]
[    0.535234] bus: 03 index 1 mmio: [c8000000, cdffffff]
[    0.535235] bus: 03 index 2 mmio: [c4000000, c7ffffff]
[    0.535237] bus: 03 index 3 io port: [0, ffff]
[    0.535238] bus: 03 index 4 mmio: [0, ffffffff]
[    0.535240] bus: 04 index 0 io port: [1000, 10ff]
[    0.535241] bus: 04 index 1 io port: [1400, 14ff]
[    0.535243] bus: 04 index 2 mmio: [c4000000, c7ffffff]
[    0.535245] bus: 04 index 3 mmio: [c8000000, cbffffff]
[    0.535251] NET: Registered protocol family 2
[    0.548037] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.548200] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.548440] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.548560] TCP: Hash tables configured (established 131072 bind 65536)
[    0.548562] TCP reno registered
[    0.552042] NET: Registered protocol family 1
[    0.552119] checking if image is initramfs... it is
[    1.106318] Freeing initrd memory: 8222k freed
[    1.106465] Simple Boot Flag value 0xb read from CMOS RAM was invalid
[    1.106467] Simple Boot Flag at 0x7c set to 0x1
[    1.107173] audit: initializing netlink socket (disabled)
[    1.107193] type=2000 audit(1242811254.105:1): initialized
[    1.111369] highmem bounce pool size: 64 pages
[    1.111373] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.113147] VFS: Disk quotas dquot_6.5.1
[    1.113210] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.113284] msgmni has been set to 1728
[    1.113372] io scheduler noop registered
[    1.113375] io scheduler anticipatory registered
[    1.113377] io scheduler deadline registered
[    1.113386] io scheduler cfq registered (default)
[    1.113397] pci 0000:00:02.0: Boot video device
[    1.113626] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.113670] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.113716] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.113746] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.113839] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.113882] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.113925] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.113957] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.114218] isapnp: Scanning for PnP cards...
[    1.467985] isapnp: No Plug & Play device found
[    1.492215] hpet_resources: 0xfed00000 is busy
[    1.492274] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.493904] brd: module loaded
[    1.493954] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.494045] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.499364] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.499368] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.504083] mice: PS/2 mouse device common for all mice
[    1.504177] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.504204] rtc0: alarms up to one year, hpet irqs
[    1.504298] EISA: Probing bus 0 at eisa.0
[    1.504304] Cannot allocate resource for EISA slot 1
[    1.504328] EISA: Detected 0 cards.
[    1.504331] cpuidle: using governor ladder
[    1.504333] cpuidle: using governor menu
[    1.504898] TCP cubic registered
[    1.504918] Using IPI No-Shortcut mode
[    1.505247] registered taskstats version 1
[    1.505354]   Magic number: 9:719:323
[    1.505360] tty ttyyc: hash matches
[    1.505370] tty tty48: hash matches
[    1.505406] rtc_cmos 00:08: setting system clock to 2009-05-20 09:20:55 UTC (1242811255)
[    1.505409] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.505410] EDD information not available.
[    1.505601] Freeing unused kernel memory: 428k freed
[    1.505631] Write protecting the kernel text: 2580k
[    1.505651] Write protecting the kernel read-only data: 940k
[    1.514993] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.649028] fuse init (API version 7.9)
[    1.721284] ACPI: SSDT B79977E9, 00F3 (r2 TOSHIB A0069    20070720 MSFT  3000000)
[    1.721501] ACPI: SSDT B7997952, 006C (r2 TOSHIB A0069    20070720 MSFT  3000000)
[    1.721845] Monitor-Mwait will be used to enter C-1 state
[    1.721847] Monitor-Mwait will be used to enter C-2 state
[    1.721849] Monitor-Mwait will be used to enter C-3 state
[    1.721987] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.722028] processor ACPI0007:00: registered as cooling_device0
[    1.722238] ACPI: SSDT B79978DC, 0076 (r2 TOSHIB A0069    20060921 MSFT  3000000)
[    1.722449] ACPI: SSDT B79979BE, 0079 (r2 TOSHIB A0069    20070720 MSFT  3000000)
[    1.722876] Marking TSC unstable due to TSC halts in idle
[    1.722969] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.723005] processor ACPI0007:01: registered as cooling_device1
[    1.724937] thermal LNXTHERM:01: registered as thermal_zone0
[    1.725061] ACPI: Thermal Zone [THRM] (38 C)
[    1.930073] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    1.930076] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    1.930116] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.930125] e1000e 0000:00:19.0: setting latency timer to 64
[    1.989613] usbcore: registered new interface driver usbfs
[    1.989631] usbcore: registered new interface driver hub
[    1.989660] usbcore: registered new device driver usb
[    1.992113] USB Universal Host Controller Interface driver v3.0
[    2.016230] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    2.019446] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1c:7e:88:78:b7
[    2.019448] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.019475] 0000:00:19.0: eth0: MAC: 5, PHY: 8, PBA No: ffffff-0ff
[    2.019532] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.019539] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.019543] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.019572] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.019603] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000cf60
[    2.019707] usb usb1: configuration #1 chosen from 1 choice
[    2.019729] hub 1-0:1.0: USB hub found
[    2.019733] hub 1-0:1.0: 2 ports detected
[    2.083292] ACPI: ACPI Dock Station Driver
[    2.106363] SCSI subsystem initialized
[    2.119378] libata version 3.00 loaded.
[    2.122738] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.122745] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.122749] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.122767] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.122798] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000cf40
[    2.122868] usb usb2: configuration #1 chosen from 1 choice
[    2.122888] hub 2-0:1.0: USB hub found
[    2.122894] hub 2-0:1.0: 2 ports detected
[    2.328314] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    2.328323] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.328326] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.328345] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    2.328378] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000cf20
[    2.328447] usb usb3: configuration #1 chosen from 1 choice
[    2.328467] hub 3-0:1.0: USB hub found
[    2.328472] hub 3-0:1.0: 2 ports detected
[    2.432492] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    2.432504] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.432507] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.432526] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    2.436418] ehci_hcd 0000:00:1a.7: debug port 1
[    2.436424] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.436428] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xffcff800
[    2.441106] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    2.453106] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.453185] usb usb4: configuration #1 chosen from 1 choice
[    2.453219] hub 4-0:1.0: USB hub found
[    2.453226] hub 4-0:1.0: 6 ports detected
[    2.500096] Clocksource tsc unstable (delta = -172312100 ns)
[    2.509137] hub 2-0:1.0: unable to enumerate USB device on port 2
[    2.660493] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.660499] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.660502] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.660521] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.660549] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000cf00
[    2.660620] usb usb5: configuration #1 chosen from 1 choice
[    2.660640] hub 5-0:1.0: USB hub found
[    2.660644] hub 5-0:1.0: 2 ports detected
[    2.764476] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.764482] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.764485] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.764507] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.764531] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000cee0
[    2.764595] usb usb6: configuration #1 chosen from 1 choice
[    2.764615] hub 6-0:1.0: USB hub found
[    2.764619] hub 6-0:1.0: 2 ports detected
[    2.773110] usb 4-4: new high speed USB device using ehci_hcd and address 2
[    2.972285] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.972291] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.972295] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.972312] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.972341] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000cec0
[    2.972407] usb usb7: configuration #1 chosen from 1 choice
[    2.972426] hub 7-0:1.0: USB hub found
[    2.972430] hub 7-0:1.0: 2 ports detected
[    3.002306] usb 4-4: configuration #1 chosen from 2 choices
[    3.076234] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.076241] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.076244] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.076262] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    3.080153] ehci_hcd 0000:00:1d.7: debug port 1
[    3.080159] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.080163] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffcff400
[    3.156113] usb 6-1: new full speed USB device using uhci_hcd and address 2
[    3.168114] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.168198] usb usb8: configuration #1 chosen from 1 choice
[    3.168230] hub 8-0:1.0: USB hub found
[    3.168235] hub 8-0:1.0: 6 ports detected
[    3.224157] hub 6-0:1.0: unable to enumerate USB device on port 1
[    3.377493] ohci1394 0000:03:0b.1: enabling device (0000 -> 0002)
[    3.377498] ohci1394 0000:03:0b.1: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    3.377579] ahci 0000:00:1f.2: version 3.0
[    3.377588] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.377680] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x13 impl SATA mode
[    3.377683] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    3.377688] ahci 0000:00:1f.2: setting latency timer to 64
[    3.377993] scsi0 : ahci
[    3.378060] scsi1 : ahci
[    3.378101] scsi2 : ahci
[    3.378315] scsi3 : ahci
[    3.378462] scsi4 : ahci
[    3.378571] ata1: SATA max UDMA/133 abar m2048@0xffcfd800 port 0xffcfd900 irq 221
[    3.378574] ata2: SATA max UDMA/133 abar m2048@0xffcfd800 port 0xffcfd980 irq 221
[    3.378576] ata3: DUMMY
[    3.378577] ata4: DUMMY
[    3.378579] ata5: SATA max UDMA/133 abar m2048@0xffcfd800 port 0xffcfdb00 irq 221
[    3.430169] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[23]  MMIO=[cc001000-cc0017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.488109] usb 8-3: new high speed USB device using ehci_hcd and address 2
[    3.664460] usb 8-3: configuration #1 chosen from 1 choice
[    3.696082] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.697131] ata1.00: ATA-8: Hitachi HTS543225L9SA00, FBEOC43C, max UDMA/133
[    3.697135] ata1.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    3.698406] ata1.00: configured for UDMA/133
[    4.112111] usb 6-2: new full speed USB device using uhci_hcd and address 3
[    4.273670] usb 6-2: configuration #1 chosen from 1 choice
[    4.437118] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.439329] ata2.00: ATAPI: MATSHITADVD-RAM UJ862AS, 1.00, max UDMA/33
[    4.442190] ata2.00: configured for UDMA/33
[    4.704209] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000390000ba42bc]
[    4.776118] ata5: SATA link down (SStatus 0 SControl 300)
[    4.792211] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54322 FBEO PQ: 0 ANSI: 5
[    4.794438] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ862AS  1.00 PQ: 0 ANSI: 5
[    4.803178] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.803205] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.814841] Driver 'sd' needs updating - please use bus_type methods
[    4.814898] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    4.814911] sd 0:0:0:0: [sda] Write Protect is off
[    4.814913] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.814933] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.814987] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    4.814998] sd 0:0:0:0: [sda] Write Protect is off
[    4.815000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.815020] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.815023]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.841143]  sda1 sda2 < sda5 sda6 >
[    4.874071] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.885715] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.885718] Uniform CD-ROM driver Revision: 3.20
[    4.885767] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.056586] PM: Starting manual resume from disk
[    5.056588] PM: Resume from partition 8:6
[    5.056590] PM: Checking hibernation image.
[    5.056755] PM: Resume from disk failed.
[    5.059374] PM: Marking nosave pages: 000000000009b000 - 0000000000100000
[    5.059379] PM: Basic memory bitmaps created
[    5.072536] PM: Basic memory bitmaps freed
[    5.127498] kjournald starting.  Commit interval 5 seconds
[    5.127532] EXT3-fs: mounted filesystem with ordered data mode.
[   12.775562] udevd version 124 started
[   13.188538] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.234946] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.320065] Linux agpgart interface v0.103
[   13.414349] ACPI: Battery Slot [BAT1] (battery present)
[   13.414396] ACPI: Battery Slot [BAT2] (battery absent)
[   13.455941] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   13.464871] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[   13.466378] agpgart-intel 0000:00:00.0: detected 131068K stolen memory
[   13.469750] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   13.477032] ACPI: Power Button (FF) [PWRF]
[   13.477118] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[   13.477174] ACPI: Lid Switch [LID]
[   13.477211] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   13.509927] ACPI: Power Button (CM) [PWRB]
[   13.510061] ACPI: AC Adapter [ADP1] (on-line)
[   13.527695] tpm_inf_pnp 00:0a: Found TPM with ID IFX0102
[   13.527739] tpm_inf_pnp 00:0a: TPM found: config base 0x4e, data base 0x680, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)
[   13.565208] ACPI: \_SB_.PCI0.FNC2.PRT1: found ejectable bay
[   13.565211] ACPI: \_SB_.PCI0.FNC2.PRT1: Adding notify handler
[   13.565436] ACPI: Error installing bay notify handler
[   13.821942] cfg80211: Using static regulatory domain info
[   13.821944] cfg80211: Regulatory domain: US
[   13.821946] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.821948] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
[   13.821950] 	(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   13.821952] 	(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   13.821954] 	(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   13.821956] 	(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   13.821958] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
[   13.821965] cfg80211: Calling CRDA for country: US
[   13.832563] ricoh-mmc: Ricoh MMC Controller disabling driver
[   13.832565] ricoh-mmc: Copyright(c) Philip Langdale
[   13.834525] ricoh-mmc: Ricoh MMC controller found at 0000:03:0b.3 [1180:0843] (rev 11)
[   13.834544] ricoh-mmc: Controller is now disabled.
[   13.963533] cdc_acm 4-4:1.1: ttyACM0: USB ACM device
[   13.964414] cdc_acm 4-4:1.3: ttyACM1: USB ACM device
[   13.964986] cdc_acm 4-4:1.9: ttyACM2: USB ACM device
[   13.965425] usbcore: registered new interface driver cdc_acm
[   13.965438] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[   14.101617] sdhci: Secure Digital Host Controller Interface driver
[   14.101620] sdhci: Copyright(c) Pierre Ossman
[   14.111036] sdhci-pci 0000:03:0b.2: SDHCI controller found [1180:0822] (rev 21)
[   14.111051] sdhci-pci 0000:03:0b.2: enabling device (0000 -> 0002)
[   14.111057] sdhci-pci 0000:03:0b.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[   14.112064] sdhci-pci 0000:03:0b.2: Will use DMA mode even though HW doesn't fully claim to support it.
[   14.114093] mmc0: SDHCI controller on PCI [0000:03:0b.2] using DMA
[   14.274991] cdc_wdm 4-4:1.5: cdc-wdm0: USB WDM device
[   14.275188] cdc_wdm 4-4:1.6: cdc-wdm1: USB WDM device
[   14.275209] usbcore: registered new interface driver cdc_wdm
[   14.307267] usbcore: registered new interface driver cdc_ether
[   14.340880] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   14.405628] usb 4-4: unsupported MDLM descriptors
[   14.406145] usbcore: registered new interface driver zaurus
[   14.429940] Yenta: CardBus bridge found at 0000:03:0b.0 [1179:0001]
[   14.452196] Linux video capture interface: v2.00
[   14.475442] acpi device:0f: registered as cooling_device2
[   14.475605] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0e/input/input6
[   14.507571] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   14.557990] Yenta: ISA IRQ mask 0x0cb8, PCI irq 22
[   14.557994] Socket status: 30000006
[   14.557996] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   14.558002] pcmcia: parent PCI bridge I/O window: 0x1000 - 0x1fff
[   14.558004] cs: IO port probe 0x1000-0x1fff: clean.
[   14.558171] pcmcia: parent PCI bridge Memory window: 0xc8000000 - 0xcdffffff
[   14.558173] pcmcia: parent PCI bridge Memory window: 0xc4000000 - 0xc7ffffff
[   14.667711] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   14.667713] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   14.667789] iwlagn 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.667819] iwlagn 0000:01:00.0: setting latency timer to 64
[   14.667863] iwlagn 0000:01:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   14.689881] iwlagn 0000:01:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   14.691922] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.788744] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input7
[   14.826030] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
[   14.903124] uvcvideo: Found UVC 1.00 device CNA7157 (04f2:b096)
[   14.904633] input: CNA7157 as /devices/pci0000:00/0000:00:1d.7/usb8/8-3/8-3:1.0/input/input9
[   14.905128] usbcore: registered new interface driver uvcvideo
[   14.905147] USB Video Class driver (v0.1.0)
[   15.375394] cs: IO port probe 0x100-0x3af: excluding 0x338-0x33f
[   15.377088] cs: IO port probe 0x3e0-0x4ff: clean.
[   15.377753] cs: IO port probe 0x820-0x8ff: clean.
[   15.378322] cs: IO port probe 0xc00-0xcf7: clean.
[   15.379024] cs: IO port probe 0xa00-0xaff: clean.
[   15.548452] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   15.548459] HDA Intel 0000:00:1b.0: enabling device (0000 -> 0002)
[   15.548465] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.548483] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.670048] lp: driver loaded but no devices found
[   16.766936] Adding 8241304k swap on /dev/sda6.  Priority:-1 extents:1 across:8241304k
[   17.287615] EXT3 FS on sda5, internal journal
[   18.500187] type=1505 audit(1242807672.963:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4246
[   18.500314] type=1505 audit(1242807672.963:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4246
[   18.544438] type=1505 audit(1242807673.004:4): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4250
[   18.593906] type=1505 audit(1242807673.055:5): operation="profile_load" name="/usr/sbin/mysqld-akonadi" name2="default" pid=4254
[   18.748223] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.343128] ACPI: \_SB_.PCI0.FNC2.PRT1: found ejectable bay
[   19.343131] ACPI: \_SB_.PCI0.FNC2.PRT1: Adding notify handler
[   19.343153] ACPI: Error installing bay notify handler
[   19.375444] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[   19.375447] toshiba_acpi:     HCI method: \_SB_.VALZ.GHCI
[   19.376021] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[   19.376023] toshiba_acpi: ktoshkeyd will check 2 times per second
[   19.376553] toshiba_acpi: Dropped 0 keys from the queue on startup
[   19.408234] ACPI: WMI: Mapper loaded
[   20.273026] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   20.671781] NET: Registered protocol family 10
[   20.672178] lo: Disabled Privacy Extensions
[   29.312558] apm: BIOS not found.
[   29.484141] ppdev: user-space parallel port driver
[   31.164166] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   31.164172] vboxdrv: Successfully done.
[   31.164174] vboxdrv: Found 2 processor cores.
[   31.165915] vboxdrv: fAsync=0 offMin=0x260 offMax=0x7fa8
[   31.165922] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   31.165925] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
[   38.032432] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.033435] firmware: requesting lbm-iwlwifi-5000-1.ucode
[   38.770166] [drm] Initialized drm 1.1.0 20060810
[   38.846664] pci 0000:00:02.0: power state changed by ACPI to D0
[   38.846691] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   38.846701] pci 0000:00:02.0: setting latency timer to 64
[   38.847193] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   38.868493] iwlagn 0000:01:00.0: loaded firmware version 5.4.1.16
[   39.028448] Registered led device: iwl-phy0::radio
[   39.028467] Registered led device: iwl-phy0::assoc
[   39.028479] Registered led device: iwl-phy0::RX
[   39.028491] Registered led device: iwl-phy0::TX
[   39.064625] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.273531] NET: Registered protocol family 17
[   40.207591] set status page addr 0x07fff000
[  100.371163] CPU0 attaching NULL sched-domain.
[  100.371190] CPU1 attaching NULL sched-domain.
[  100.372895] CPU0 attaching sched-domain:
[  100.372904]  domain 0: span 0-1 level MC
[  100.372911]   groups: 0 1
[  100.372923] CPU1 attaching sched-domain:
[  100.372928]  domain 0: span 0-1 level MC
[  100.372934]   groups: 1 0
[  106.443825] wlan0: authenticate with AP f7578e28
[  106.445847] wlan0: authenticated
[  106.445859] wlan0: associate with AP f7578e28
[  106.448641] wlan0: RX AssocResp from f5ac8016 (capab=0x411 status=0 aid=1)
[  106.448652] wlan0: associated
[  106.450575] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  117.064270] wlan0: no IPv6 routers present
```

---

### Post by arestivo on 2009-05-20
By the way, does suspend and resume work correctly with jaunty?

---

### Post by arestivo on 2009-05-20
> **arestivo said:**
> I'm on 0.8.1.4. I was thinking about upgrading to jaunty and now I'm not so sure it's a good idea :-(

Where did you find the errors? I can take a look to see if I have them too.

Sorry, wrong again. I'm also on 0.8.2 as recommended by the tutorial (I followed the instructions on compiling the drivers). I'm not using the drivers in the repositories as those are still on 0.8.1.4.

With the previous wacom tools (0.8.1.4) the stylus worked correctly but the screen would not respond to finger interaction.

---

### Post by Favux on 2009-05-20
Hi arestivo,

Thank you for all your help.  Knowing the M700 line worked for your M750 in Intrepid was crucial.

X-Kent got the M750 working in Jaunty.  Please see post #78 here:  [http://ubuntuforums.org/showthread.php?t=1055845&page=8](http://ubuntuforums.org/showthread.php?t=1055845&page=8)

Thanks again.

---

### Post by arestivo on 2009-05-20
Cool. Nice to know it works on Jaunty too. I think I'll upgrade my Intrepid in a few days :-)

---

