---
title: "USB Device problems"
date: 2010-08-19
forum: Hardware
---

### Post by tosszyx on 2010-08-19
Hi there,

I recently (relatively) moved from Kubuntu to Xubuntu, due to the fact that my laptop is not getting any younger. But I have been having troubles with the USB devices. **If I turn the computer on with them connected (HDD,Mouse,Printer) everything runs fine, if I turn the computer without them and I want to connnect them later, it doesn't work**. So far, I have found many post with similar problems, but no many solutions. 

To test, I disconnected my mouse, turn the computer on and try to connect the mouse later, the red light (optical mouse) goes on, but if I move the mouse the cursor is static.

I read that issuing *update-usbids* would help, but although later, when I execute a *lsusb* I can see the mouse, the cursor still doesn't react.

```
sudo update-usbids
--2010-08-19 12:28:24--  http://www.linux-usb.org/usb.ids
Resolving www.linux-usb.org... 216.34.181.97
Connecting to www.linux-usb.org|216.34.181.97|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 425596 (416K) [text/plain]
Saving to: `/var/lib/usbutils/usb.ids.new'

100%[======================================>] 425,596      327K/s   in 1.3s    

2010-08-19 12:28:27 (327 KB/s) - `/var/lib/usbutils/usb.ids.new' saved [425596/425596]

Done.

```


```
lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 03f0:c402 Hewlett-Packard PhotoSmart D5100 series
Bus 001 Device 008: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 007: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 003: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. transcend storejet 25P
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Does anybody has a suggestion ? I really want to understand what is happening, instead of just making "a little magic dance" to make stuff work. Below is more information about my system, let me know if more is needed. I will appreciate any help, thanks !

```
lsb_release -a
Linux Coatl 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux

```

```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.1 LTS
Release:	10.04
Codename:	lucid

```

---

### Post by anubhavrocks on 2010-08-19
See if this helps:
sudo apt-get install usbmount

---

### Post by tosszyx on 2010-08-19
Hi Anubhavrocks, thanks for your help, I did try installing with *sudo apt-get install usbmount*, everything went fine except the mouse didn't work, I executed *lsusb* and *sudo update-usbids* and still no response from the mouse.

After restarting the computer, I got a screen saying that "Ubuntu is running in low-graphics mode", that never have had before, I choose to restart X and everything seem fine again, but the mouse still didn't work.

Restarting the computer with the mouse connected (and after receiving the same screen) the mouse works (as before). Restarting without connecting the mouse, and connecting it later, still doesn't make it work.

From the log of X I got what went wrong, I'm assuming it has something to do with the new package, any ideas ? 

```
cat /var/log/Xorg.0.log
.
.
.
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(II) FBDEV(0): using default device

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e938b]
1: /usr/bin/X (0x8048000+0x61c8d) [0x80a9c8d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0x473410]
3: /usr/lib/libpciaccess.so.0 (pci_device_find_by_slot+0x43) [0x369403]
4: /usr/lib/libpciaccess.so.0 (pci_device_vgaarb_init+0xfa) [0x36bf9a]
5: /usr/bin/X (0x8048000+0x75647) [0x80bd647]
6: /usr/bin/X (InitOutput+0x3ec) [0x80b9abc]
7: /usr/bin/X (0x8048000+0x1ebbb) [0x8066bbb]
8: /lib/tls/i686/cmov/libc.so.6 (__libc_start_main+0xe6) [0xc13bd6]
9: /usr/bin/X (0x8048000+0x1e961) [0x8066961]
Segmentation fault at address (nil)

Caught signal 11 (Segmentation fault). Server aborting
.
.
.

```

---

### Post by anubhavrocks on 2010-08-19
Are you trying to say that you have two problems now:
1> Mouse still does not work when it is connected after system boots up?

2> The X server crashing everytime.

---

### Post by tosszyx on 2010-08-19
More or less, it crashes at startup, but after I restart it in this "Low graphics" dialog, it comes up 'normally' ( I did notice that the session open by it was not the current one -old files opened,etc.-). And the mouse is still not responding when connecting when Xubuntu is already fully loaded.

---

### Post by anubhavrocks on 2010-08-19
> **tosszyx said:**
> More or less, it crashes at startup, but after I restart it in this "Low graphics" dialog, it comes up 'normally' ( I did notice that the session open by it was not the current one -old files opened,etc.-). And the mouse is still not responding when connecting when Xubuntu is already fully loaded.

First lets try to get the mouse working:
Try this:
sudo modprobe usbhid

---

### Post by sadiepaige01 on 2010-08-19
As a follow-on, my USB devices, for example a flash drive, show as "captured" in vboxmanage prior to and after starting the VM, however none of the devices show in the VM. If I go to the USB icon on the bottom of the Window and click on the flash drive, I get the busy message as noted in my previous post.

---

### Post by tosszyx on 2010-08-19
@anubhavrocks: Well, it worked! After I executed the command, the tooltip under the cursor showed and I could move it with the optic mouse.

Here is the corresponding *dmesg* output:

```
[  380.916074] usb 2-1: new low speed USB device using uhci_hcd and address 2
[  381.099118] usb 2-1: configuration #1 chosen from 1 choice
[ 1102.022547] usbcore: registered new interface driver hiddev
[ 1102.043258] input: Microsoft Microsoft Wheel Mouse Optical® as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input8
[ 1102.046514] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft Wheel Mouse Optical®] on usb-0000:00:1d.0-1/input0
[ 1102.046608] usbcore: registered new interface driver usbhid
[ 1102.048649] usbhid: v2.6:USB HID core driver

```

But now my question is, how come that it was detected if it was connected on startup? What would be the difference?

Anyway I added *usbhid* to my */etc/modules* already. Thanks a lot!

```
lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. transcend storejet 25P
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by houndi on 2010-08-19
go to group policies and change the usb setting to detect the usb and change the settings of ports. it might be disabled. try to change the usb settings in tjhat

---

### Post by tosszyx on 2010-08-19
Well, after using the computer a while, I noticed that my external hard disk, that used to be mounted as in */media/BACKUP*, is now mounting in */media/usb0* and it is suffering from the same quirks of the mouse (although it could be that it was already like that.), meaning that when is connected on startup, is loaded, otherwise not. Maybe I need to load another module ?

In regard to X, it still gives me and error while starting up, but I sometimes no.

But the mouse is working just fine ! :)

EDIT: I just notice that the external hard disk (and any USB key for the matter) are mounting as "root" =/ . Any ideas??

---

### Post by anubhavrocks on 2010-08-20
Can you please post the output of dmesg.

---

### Post by tosszyx on 2010-08-20
Well, I will post two, the first one is the one where at the beginning I did **not** got the "low graphics" error, nor I restart X. The second one is when I did got the error.

```
dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 (Ubuntu 2.6.32-24.41-generic 2.6.32.15+drm33.5)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004ffae000 (usable)
[    0.000000]  BIOS-e820: 000000004ffae000 - 0000000050000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x4ffae max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 040000000 mask FF0000000 write-back
[    0.000000]   2 base 0FEDA0000 mask FFFFE0000 write-combining
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000004ffae000 (usable)
[    0.000000]  modified: 000000004ffae000 - 0000000050000000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 3785a000 - 37fefc01
[    0.000000] Allocated new RAMDISK: 008e2000 - 01077c01
[    0.000000] Move RAMDISK from 000000003785a000 - 0000000037fefc00 to 008e2000 - 01077c00
[    0.000000] ACPI: RSDP 000fdf00 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 4fff0000 0002C (v01 DELL    CPi R   27D5061E ASL  00000061)
[    0.000000] ACPI: FACP 4fff0400 00074 (v01 DELL    CPi R   27D5061E ASL  00000061)
[    0.000000] ACPI: DSDT 4fff0c00 02C70 (v01 INT430 SYSFexxx 00001001 MSFT 0100000E)
[    0.000000] ACPI: FACS 4ffff800 00040
[    0.000000] ACPI: BOOT 4fff07c0 00028 (v01 DELL    CPi R   27D5061E ASL  00000061)
[    0.000000] 391MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ddeb8]    TEXT DATA BSS ==> [0000100000 - 00008ddeb8]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00008de000 - 00008e1198]              BRK ==> [00008de000 - 00008e1198]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008e2000 - 0001077c01]      NEW RAMDISK ==> [00008e2000 - 0001077c01]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0004ffae
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0004ffae
[    0.000000] On node 0 totalpages: 327497
[    0.000000] free_area_init_node: node 0, pgdat c079a780, node_mem_map c1079000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 784 pages used for memmap
[    0.000000]   HighMem zone: 99488 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 50000000:aeda0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1c00000 s36056 r0 d21288 u4194304
[    0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 324937
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=657b49ee-94fd-4251-8e54-9068e6904e18 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 6551960 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0004ffae)
[    0.000000] Memory: 1275608k/1310392k available (4679k kernel code, 33384k reserved, 2124k data, 660k init, 401088k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc084a000   ( 660 kB)
[    0.000000]       .data : 0xc0591e33 - 0xc07a4e88   (2124 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591e33   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2192.890 MHz processor.
[    0.008011] Calibrating delay loop (skipped), value calculated using timer frequency.. 4385.78 BogoMIPS (lpj=8771560)
[    0.008043] Security Framework initialized
[    0.008098] AppArmor: AppArmor initialized
[    0.008110] Mount-cache hash table entries: 512
[    0.008358] Initializing cgroup subsys ns
[    0.008368] Initializing cgroup subsys cpuacct
[    0.008375] Initializing cgroup subsys memory
[    0.008393] Initializing cgroup subsys devices
[    0.008398] Initializing cgroup subsys freezer
[    0.008402] Initializing cgroup subsys net_cls
[    0.008445] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.008451] CPU: L2 cache: 512K
[    0.008455] CPU: Hyper-Threading is disabled
[    0.008462] mce: CPU supports 4 MCE banks
[    0.008496] Performance Events: no PMU driver, software events only.
[    0.008510] Checking 'hlt' instruction... OK.
[    0.025301] SMP alternatives: switching to UP code
[    0.039796] Freeing SMP alternatives: 19k freed
[    0.039836] ACPI: Core revision 20090903
[    0.048864] ACPI: setting ELCR to 0200 (from 0800)
[    0.051420] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.051430] ftrace: allocating 21780 entries in 43 pages
[    0.052135] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.052141] weird, boot CPU (#0) not listed by the BIOS.
[    0.052144] SMP motherboard not detected.
[    0.052148] Local APIC not detected. Using dummy APIC emulation.
[    0.052151] SMP disabled
[    0.052460] Brought up 1 CPUs
[    0.052465] Total of 1 processors activated (4385.78 BogoMIPS).
[    0.052864] CPU0 attaching NULL sched-domain.
[    0.053090] devtmpfs: initialized
[    0.056247] regulator: core version 0.5
[    0.056275] Time: 11:41:13  Date: 08/20/10
[    0.056346] NET: Registered protocol family 16
[    0.056526] EISA bus registered
[    0.056541] ACPI: bus type pci registered
[    0.090887] PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=2
[    0.090891] PCI: Using configuration type 1 for base access
[    0.092382] bio: create slab <bio-0> at 0
[    0.093037] ACPI: EC: Look up EC in DSDT
[    0.106727] ACPI: Interpreter enabled
[    0.106754] ACPI: (supports S0 S1 S3 S4 S5)
[    0.106790] ACPI: Using PIC for interrupt routing
[    0.133392] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.140380] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.140454] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xe0000000-0xe7ffffff]
[    0.140613] pci 0000:00:1d.0: reg 20 io port: [0xbf80-0xbf9f]
[    0.140680] pci 0000:00:1d.1: reg 20 io port: [0xbf40-0xbf5f]
[    0.140747] pci 0000:00:1d.2: reg 20 io port: [0xbf20-0xbf3f]
[    0.140824] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf4fffc00-0xf4ffffff]
[    0.140893] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.140900] pci 0000:00:1d.7: PME# disabled
[    0.141016] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.141022] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
[    0.141055] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
[    0.141064] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
[    0.141073] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
[    0.141082] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
[    0.141091] pci 0000:00:1f.1: reg 20 io port: [0xbfa0-0xbfaf]
[    0.141100] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.141157] pci 0000:00:1f.5: reg 10 io port: [0xb800-0xb8ff]
[    0.141166] pci 0000:00:1f.5: reg 14 io port: [0xbc40-0xbc7f]
[    0.141175] pci 0000:00:1f.5: reg 18 32bit mmio: [0xf4fff800-0xf4fff9ff]
[    0.141184] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xf4fff400-0xf4fff4ff]
[    0.141221] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.141227] pci 0000:00:1f.5: PME# disabled
[    0.141267] pci 0000:00:1f.6: reg 10 io port: [0xb400-0xb4ff]
[    0.141276] pci 0000:00:1f.6: reg 14 io port: [0xb080-0xb0ff]
[    0.141322] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.141328] pci 0000:00:1f.6: PME# disabled
[    0.141381] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xe8000000-0xefffffff]
[    0.141389] pci 0000:01:00.0: reg 14 io port: [0xc000-0xc0ff]
[    0.141397] pci 0000:01:00.0: reg 18 32bit mmio: [0xfcff0000-0xfcffffff]
[    0.141417] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x80000000-0x8001ffff]
[    0.141443] pci 0000:01:00.0: supports D1 D2
[    0.141489] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.141496] pci 0000:00:01.0: bridge 32bit mmio: [0xfc000000-0xfdffffff]
[    0.141501] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe8000000-0xefffffff]
[    0.141545] pci 0000:02:00.0: reg 10 32bit mmio: [0xfaffe000-0xfaffffff]
[    0.141597] pci 0000:02:00.0: supports D1 D2
[    0.141601] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.141607] pci 0000:02:00.0: PME# disabled
[    0.141650] pci 0000:02:01.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.141674] pci 0000:02:01.0: supports D1 D2
[    0.141677] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.141682] pci 0000:02:01.0: PME# disabled
[    0.141726] pci 0000:02:01.1: reg 10 32bit mmio: [0xfaffd800-0xfaffdfff]
[    0.141736] pci 0000:02:01.1: reg 14 32bit mmio: [0xfaff8000-0xfaffbfff]
[    0.141785] pci 0000:02:01.1: supports D1 D2
[    0.141788] pci 0000:02:01.1: PME# supported from D0 D1 D2 D3hot
[    0.141794] pci 0000:02:01.1: PME# disabled
[    0.141852] pci 0000:00:1e.0: transparent bridge
[    0.141858] pci 0000:00:1e.0: bridge io port: [0xd000-0xefff]
[    0.141864] pci 0000:00:1e.0: bridge 32bit mmio: [0xf6000000-0xfbffffff]
[    0.141901] pci_bus 0000:00: on NUMA node 0
[    0.141908] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.142187] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.142259] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.158612] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.158784] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    0.158953] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    0.159122] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[    0.159269] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.159444] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.159636] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.159642] vgaarb: loaded
[    0.159858] SCSI subsystem initialized
[    0.160064] libata version 3.00 loaded.
[    0.160190] usbcore: registered new interface driver usbfs
[    0.160211] usbcore: registered new interface driver hub
[    0.160249] usbcore: registered new device driver usb
[    0.160461] ACPI: WMI: Mapper loaded
[    0.160465] PCI: Using ACPI for IRQ routing
[    0.160684] NetLabel: Initializing
[    0.160688] NetLabel:  domain hash size = 128
[    0.160690] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.160710] NetLabel:  unlabeled traffic allowed by default
[    0.160779] Switching to clocksource tsc
[    0.163765] AppArmor: AppArmor Filesystem Enabled
[    0.163799] pnp: PnP ACPI init
[    0.163833] ACPI: bus type pnp registered
[    0.177093] pnp 00:02: io resource (0x800-0x805) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.177099] pnp 00:02: io resource (0x808-0x80f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.177197] pnp 00:03: io resource (0x806-0x807) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.177203] pnp 00:03: io resource (0x810-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.177208] pnp 00:03: io resource (0x860-0x87f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.214579] pnp: PnP ACPI: found 14 devices
[    0.214583] ACPI: ACPI bus type pnp unregistered
[    0.214591] PnPBIOS: Disabled by ACPI PNP
[    0.214611] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.214617] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.214622] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.214627] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.214631] system 00:00: iomem range 0x100000-0x4ffeffff could not be reserved
[    0.214636] system 00:00: iomem range 0x4fff0000-0x4fffffff has been reserved
[    0.214641] system 00:00: iomem range 0xfeda0000-0xfedfffff has been reserved
[    0.214645] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.214657] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.214670] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.214676] system 00:03: ioport range 0x880-0x8bf has been reserved
[    0.214681] system 00:03: ioport range 0x8c0-0x8df has been reserved
[    0.214685] system 00:03: ioport range 0x8e0-0x8ff has been reserved
[    0.214697] system 00:08: ioport range 0x900-0x97f has been reserved
[    0.249524] pci 0000:01:00.0: BAR 6: no parent found for of device [0x80000000-0x8001ffff]
[    0.249561] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.249566] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.249572] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfdffffff
[    0.249578] pci 0000:00:01.0:   PREFETCH window: 0xe8000000-0xefffffff
[    0.249591] pci 0000:02:01.0: CardBus bridge, secondary bus 0000:03
[    0.249595] pci 0000:02:01.0:   IO window: 0x00d000-0x00d0ff
[    0.249601] pci 0000:02:01.0:   IO window: 0x00d400-0x00d4ff
[    0.249607] pci 0000:02:01.0:   PREFETCH window: 0x50000000-0x53ffffff
[    0.249614] pci 0000:02:01.0:   MEM window: 0x58000000-0x5bffffff
[    0.249620] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.249624] pci 0000:00:1e.0:   IO window: 0xd000-0xefff
[    0.249632] pci 0000:00:1e.0:   MEM window: 0xf6000000-0xfbffffff
[    0.249638] pci 0000:00:1e.0:   PREFETCH window: 0x50000000-0x53ffffff
[    0.249661] pci 0000:00:1e.0: setting latency timer to 64
[    0.249672] pci 0000:02:01.0: enabling device (0000 -> 0003)
[    0.249924] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.249928] PCI: setting IRQ 11 as level-triggered
[    0.249935] pci 0000:02:01.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.249946] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.249950] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.249954] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.249957] pci_bus 0000:01: resource 1 mem: [0xfc000000-0xfdffffff]
[    0.249961] pci_bus 0000:01: resource 2 pref mem [0xe8000000-0xefffffff]
[    0.249965] pci_bus 0000:02: resource 0 io:  [0xd000-0xefff]
[    0.249969] pci_bus 0000:02: resource 1 mem: [0xf6000000-0xfbffffff]
[    0.249973] pci_bus 0000:02: resource 2 pref mem [0x50000000-0x53ffffff]
[    0.249977] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.249980] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.249984] pci_bus 0000:03: resource 0 io:  [0xd000-0xd0ff]
[    0.249988] pci_bus 0000:03: resource 1 io:  [0xd400-0xd4ff]
[    0.249992] pci_bus 0000:03: resource 2 pref mem [0x50000000-0x53ffffff]
[    0.249996] pci_bus 0000:03: resource 3 mem: [0x58000000-0x5bffffff]
[    0.250054] NET: Registered protocol family 2
[    0.250207] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.250823] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.252349] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.253312] TCP: Hash tables configured (established 131072 bind 65536)
[    0.253318] TCP reno registered
[    0.253559] NET: Registered protocol family 1
[    0.253695] pci 0000:01:00.0: Boot video device
[    0.253889] Simple Boot Flag at 0x79 set to 0x1
[    0.254180] cpufreq-nforce2: No nForce2 chipset.
[    0.254220] Scanning for low memory corruption every 60 seconds
[    0.254416] audit: initializing netlink socket (disabled)
[    0.254436] type=2000 audit(1282304473.251:1): initialized
[    0.265103] Trying to unpack rootfs image as initramfs...
[    0.279218] highmem bounce pool size: 64 pages
[    0.279229] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.281495] VFS: Disk quotas dquot_6.5.2
[    0.281599] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.287290] fuse init (API version 7.13)
[    0.287490] msgmni has been set to 1710
[    0.287877] alg: No test for stdrng (krng)
[    0.287981] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.287987] io scheduler noop registered
[    0.287989] io scheduler anticipatory registered
[    0.287992] io scheduler deadline registered
[    0.288055] io scheduler cfq registered (default)
[    0.288232] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.288270] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.288889] ACPI: AC Adapter [AC] (on-line)
[    0.289007] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.289454] ACPI: Lid Switch [LID]
[    0.289526] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.289533] ACPI: Power Button [PBTN]
[    0.289603] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.289608] ACPI: Sleep Button [SBTN]
[    0.290069] Marking TSC unstable due to TSC halts in idle
[    0.290131] processor LNXCPU:00: registered as cooling_device0
[    0.294875] Switching to clocksource acpi_pm
[    0.319187] thermal LNXTHERM:01: registered as thermal_zone0
[    0.319204] ACPI: Thermal Zone [THM] (70 C)
[    0.332382] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.332507] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.332625] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.333143] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.333330] isapnp: Scanning for PnP cards...
[    0.425562] ACPI: Battery Slot [BAT1] (battery absent)
[    0.425737] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[    0.425743] PCI: setting IRQ 5 as level-triggered
[    0.425751] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    0.425767] serial 0000:00:1f.6: PCI INT B disabled
[    0.427354] brd: module loaded
[    0.431498] loop: module loaded
[    0.431679] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.431858] ata_piix 0000:00:1f.1: version 2.13
[    0.431877] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.432184] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.432191] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.432271] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.436183] scsi0 : ata_piix
[    0.436401] scsi1 : ata_piix
[    0.437621] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.437626] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.438234] Fixed MDIO Bus: probed
[    0.438293] PPP generic driver version 2.4.2
[    0.438404] tun: Universal TUN/TAP device driver, 1.6
[    0.438408] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.438553] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.438849] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    0.438857] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    0.438884] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.438890] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.438946] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.438997] ehci_hcd 0000:00:1d.7: debug port 1
[    0.442900] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.458654] ACPI: Battery Slot [BAT0] (battery present)
[    0.458685] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
[    0.472134] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.472368] usb usb1: configuration #1 chosen from 1 choice
[    0.472418] hub 1-0:1.0: USB hub found
[    0.472440] hub 1-0:1.0: 6 ports detected
[    0.472551] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.472579] uhci_hcd: USB Universal Host Controller Interface driver
[    0.472659] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.472676] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.472682] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.472747] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.472780] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[    0.472917] usb usb2: configuration #1 chosen from 1 choice
[    0.472959] hub 2-0:1.0: USB hub found
[    0.472975] hub 2-0:1.0: 2 ports detected
[    0.473046] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.473056] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.473060] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.473116] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.473143] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[    0.473273] usb usb3: configuration #1 chosen from 1 choice
[    0.473319] hub 3-0:1.0: USB hub found
[    0.473332] hub 3-0:1.0: 2 ports detected
[    0.473689] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.473695] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.473706] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.473711] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.473781] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.473811] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[    0.473970] usb usb4: configuration #1 chosen from 1 choice
[    0.474017] hub 4-0:1.0: USB hub found
[    0.474032] hub 4-0:1.0: 2 ports detected
[    0.474193] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.484715] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.484738] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.485017] mice: PS/2 mouse device common for all mice
[    0.485325] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.485350] rtc0: alarms up to one day, 114 bytes nvram
[    0.485539] device-mapper: uevent: version 1.0.3
[    0.485759] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.531494] device-mapper: multipath: version 1.1.0 loaded
[    0.531501] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.532826] EISA: Probing bus 0 at eisa.0
[    0.532860] EISA: Detected 0 cards.
[    0.533573] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.536527] cpuidle: using governor ladder
[    0.536656] cpuidle: using governor menu
[    0.537401] TCP cubic registered
[    0.537597] NET: Registered protocol family 10
[    0.538306] lo: Disabled Privacy Extensions
[    0.538806] NET: Registered protocol family 17
[    0.538893] Using IPI No-Shortcut mode
[    0.539063] PM: Resume from disk failed.
[    0.539083] registered taskstats version 1
[    0.539387]   Magic number: 6:812:681
[    0.539533] rtc_cmos 00:06: setting system clock to 2010-08-20 11:41:13 UTC (1282304473)
[    0.539538] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.539542] EDD information not available.
[    0.632873] ata2.00: ATAPI: QSI CD-RW/DVD-ROM SBW-242, UD22, max UDMA/33
[    0.633039] ata1.00: ATA-5: HITACHI_DK23FB-60, 00M0A0C1, max UDMA/100
[    0.633044] ata1.00: 117210240 sectors, multi 8: LBA 
[    0.633650] ata2.00: configured for UDMA/33
[    0.640675] ata1.00: configured for UDMA/100
[    0.799771] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    0.993826] Freeing initrd memory: 7767k freed
[    1.052507] isapnp: No Plug & Play device found
[    1.052831] scsi 0:0:0:0: Direct-Access     ATA      HITACHI_DK23FB-6 00M0 PQ: 0 ANSI: 5
[    1.053171] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.053476] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.053579] sd 0:0:0:0: [sda] Write Protect is off
[    1.053584] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.053622] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.053904]  sda:
[    1.054291] usb 1-3: configuration #1 chosen from 1 choice
[    1.056794] scsi 1:0:0:0: CD-ROM            QSI      CDRW/DVD SBW-242 UD22 PQ: 0 ANSI: 5
[    1.059782] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
[    1.059788] Uniform CD-ROM driver Revision: 3.20
[    1.059951] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.060079] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.064719]  sda1 sda2 < sda5 sda6 >
[    1.081473] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.081498] Freeing unused kernel memory: 660k freed
[    1.082643] Write protecting the kernel text: 4680k
[    1.082681] Write protecting the kernel read-only data: 1844k
[    1.119827] udev: starting version 151
[    1.599912] Initializing USB Mass Storage driver...
[    1.605033] b44 0000:02:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    1.605604] scsi2 : SCSI emulation for USB Mass Storage devices
[    1.605863] usbcore: registered new interface driver usb-storage
[    1.605869] USB Mass Storage support registered.
[    1.606488] usb-storage: device found at 2
[    1.606493] usb-storage: waiting for device to settle before scanning
[    1.664243] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[    1.664333] ohci1394 0000:02:01.1: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    1.664823] b44.c:v2.0
[    1.685178] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0d:56:35:78:b5
[    1.720098] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[faffd800-faffdfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.843040] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.992248] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[484fc00030cbbc61]
[    6.604334] usb-storage: device scan complete
[    6.646537] scsi 2:0:0:0: Direct-Access     WDC WD10 EAVS-00D7B0           PQ: 0 ANSI: 2 CCS
[    6.647260] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    6.647997] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    6.648865] sd 2:0:0:0: [sdb] Write Protect is off
[    6.648870] sd 2:0:0:0: [sdb] Mode Sense: 34 00 00 00
[    6.648874] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.650541] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.650549]  sdb: sdb1 sdb2
[    6.672239] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.672245] sd 2:0:0:0: [sdb] Attached SCSI disk
[   24.487229] Adding 1799240k swap on /dev/sda5.  Priority:-1 extents:1 across:1799240k 
[   24.502729] udev: starting version 151
[   24.713207] lp: driver loaded but no devices found
[   24.903791] parport_pc 00:0c: reported by Plug and Play ACPI
[   24.903851] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   24.953804] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:1d/LNXVIDEO:00/input/input5
[   24.953974] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   25.001913] lp0: using parport0 (interrupt-driven).
[   25.084623] Linux agpgart interface v0.103
[   25.091387] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.397081] Disabling lock debugging due to kernel taint
[   25.415135] irda_init()
[   25.415163] NET: Registered protocol family 23
[   25.443037] intel_rng: FWH not detected
[   25.527364] ppdev: user-space parallel port driver
[   25.530875] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   25.559712] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   25.559822] agpgart-intel 0000:00:00.0: Intel 845G Chipset
[   25.633373] dell-wmi: No known WMI GUID found
[   25.636812] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[   25.767161] EXT4-fs (sda6): mounted filesystem with ordered data mode
[   25.783203] [drm] Initialized drm 1.1.0 20060810
[   25.786891] type=1505 audit(1282304498.744:2):  operation="profile_load" pid=582 name="/sbin/dhclient3"
[   25.787601] type=1505 audit(1282304498.744:3):  operation="profile_load" pid=582 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   25.787988] type=1505 audit(1282304498.744:4):  operation="profile_load" pid=582 name="/usr/lib/connman/scripts/dhclient-script"
[   25.818147] yenta_cardbus 0000:02:01.0: CardBus bridge found [1028:013e]
[   25.818173] yenta_cardbus 0000:02:01.0: Using CSCINT to route CSC interrupts to PCI
[   25.818178] yenta_cardbus 0000:02:01.0: Routing CardBus interrupts to PCI
[   25.818185] yenta_cardbus 0000:02:01.0: TI: mfunc 0x012c1202, devctl 0x64
[   26.051240] yenta_cardbus 0000:02:01.0: ISA IRQ mask 0x0458, PCI irq 11
[   26.051249] yenta_cardbus 0000:02:01.0: Socket status: 30000020
[   26.051255] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   26.051278] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   26.051285] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xd000-0xefff: clean.
[   26.052419] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[   26.052425] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   26.055783] usbcore: registered new interface driver ndiswrapper
[   26.097066] [drm] radeon defaulting to kernel modesetting.
[   26.097074] [drm] radeon kernel modesetting enabled.
[   26.097165] radeon 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   26.121789] [drm] radeon: Initializing kernel modesetting.
[   26.122110] [drm] register mmio base: 0xFCFF0000
[   26.122115] [drm] register mmio size: 65536
[   26.122448] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   26.122479] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   26.122503] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   26.122549] radeon 0000:01:00.0: putting AGP V2 device into 4x mode
[   26.122572] [drm] radeon: VRAM 64M
[   26.122575] [drm] radeon: VRAM from 0x00000000 to 0x03FFFFFF
[   26.122578] [drm] radeon: GTT 128M
[   26.122581] [drm] radeon: GTT from 0xE0000000 to 0xE7FFFFFF
[   26.122622] [drm] radeon: irq initialized.
[   26.122765] [drm] Detected VRAM RAM=64M, BAR=128M
[   26.122771] [drm] RAM width 64bits DDR
[   26.122907] [TTM] Zone  kernel: Available graphics memory: 441980 kiB.
[   26.122911] [TTM] Zone highmem: Available graphics memory: 642524 kiB.
[   26.122940] [drm] radeon: 32M of VRAM memory ready
[   26.122944] [drm] radeon: 128M of GTT memory ready.
[   26.123194] [drm] radeon: cp idle (0x02000603)
[   26.123364] [drm] Loading R200 Microcode
[   26.124119] platform radeon_cp.0: firmware: requesting radeon/R200_cp.bin
[   26.165217] [drm] radeon: ring at 0x00000000E0000000
[   26.165243] [drm] ring test succeeded in 1 usecs
[   26.185420] [drm] radeon: ib pool ready.
[   26.185577] [drm] ib test succeeded in 0 usecs
[   26.188138] [drm] DFP table revision: 3
[   26.189970] [drm] Panel ID String: W
[   26.189976] [drm] Panel Size 1280x800
[   26.190210] [drm] Default TV standard: NTSC
[   26.190214] [drm] 27.000000000 MHz TV ref clk
[   26.190220] [drm] Default TV standard: NTSC
[   26.190222] [drm] 27.000000000 MHz TV ref clk
[   26.190399] [drm] Radeon Display Connectors
[   26.190403] [drm] Connector 0:
[   26.190406] [drm]   VGA
[   26.190410] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   26.190413] [drm]   Encoders:
[   26.190416] [drm]     CRT1: INTERNAL_DAC1
[   26.190418] [drm] Connector 1:
[   26.190420] [drm]   DVI-D
[   26.190423] [drm]   HPD1
[   26.190426] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   26.190429] [drm]   Encoders:
[   26.190431] [drm]     DFP1: INTERNAL_TMDS1
[   26.190434] [drm] Connector 2:
[   26.190436] [drm]   LVDS
[   26.190438] [drm]   Encoders:
[   26.190440] [drm]     LCD1: INTERNAL_LVDS
[   26.190442] [drm] Connector 3:
[   26.190444] [drm]   S-video
[   26.190446] [drm]   Encoders:
[   26.190449] [drm]     TV1: INTERNAL_DAC2
[   26.246308] [drm] fb mappable at 0xE8040000
[   26.246314] [drm] vram apper at 0xE8000000
[   26.246316] [drm] size 1024000
[   26.246319] [drm] fb depth is 8
[   26.246321] [drm]    pitch is 1280
[   26.255722] fb0: radeondrmfb frame buffer device
[   26.255728] registered panic notifier
[   26.255739] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   26.266647] vga16fb: initializing
[   26.266657] vga16fb: mapped to 0xc00a0000
[   26.266665] vga16fb: not registering due to another framebuffer present
[   26.328819] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input6
[   26.375624] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input7
[   26.461910] Console: switching to colour frame buffer device 160x50
[   26.508709] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   26.508774] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   26.692057] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[   26.692114] pci 0000:03:00.0: reg 10 io port: [0x00-0x1f]
[   26.692125] pci 0000:03:00.0: reg 14 32bit mmio: [0x000000-0x000fff]
[   26.692135] pci 0000:03:00.0: reg 18 32bit mmio: [0x000000-0x00ffff]
[   26.692192] pci 0000:03:00.0: supports D1 D2
[   26.692196] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
[   26.692203] pci 0000:03:00.0: PME# disabled
[   27.336050] intel8x0_measure_ac97_clock: measured 55226 usecs (2661 samples)
[   27.336056] intel8x0: clocking to 48000
[   29.252672] usbcore: registered new interface driver hiddev
[   29.254381] usbcore: registered new interface driver usbhid
[   29.255432] usbhid: v2.6:USB HID core driver
[   29.282382] ndiswrapper: driver airplus (D-Link,09/08/2003,4.15.5.1) loaded
[   29.282772] ndiswrapper 0000:03:00.0: enabling device (0000 -> 0003)
[   29.282793] ndiswrapper 0000:03:00.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[   29.283054] ndiswrapper 0000:03:00.0: setting latency timer to 64
[   29.283653] ndiswrapper: using IRQ 11
[   30.366084] type=1505 audit(1282304503.324:5):  operation="profile_replace" pid=812 name="/sbin/dhclient3"
[   30.366829] type=1505 audit(1282304503.324:6):  operation="profile_replace" pid=812 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   30.367231] type=1505 audit(1282304503.324:7):  operation="profile_replace" pid=812 name="/usr/lib/connman/scripts/dhclient-script"
[   30.404786] type=1505 audit(1282304503.364:8):  operation="profile_load" pid=813 name="/usr/bin/evince"
[   30.447049] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.511372] type=1505 audit(1282304503.468:9):  operation="profile_load" pid=813 name="/usr/bin/evince-previewer"
[   30.567235] type=1505 audit(1282304503.524:10):  operation="profile_load" pid=813 name="/usr/bin/evince-thumbnailer"
[   30.634527] type=1505 audit(1282304503.592:11):  operation="profile_load" pid=904 name="/usr/lib/cups/backend/cups-pdf"
[   30.846368] pnp 00:0d: disabled
[   30.964638] pnp 00:0d: activated
[   31.021345] pnp 00:0d: disabled
[   31.103908] pnp 00:0d: activated
[   31.730482] __ratelimit: 12 callbacks suppressed
[   31.730488] type=1505 audit(1282304504.688:16):  operation="profile_replace" pid=1105 name="/usr/sbin/mysqld"
[   31.966423] wlan0: ethernet device 00:80:c8:b2:4b:fa using NDIS driver: airplus, version: 0x4000f, NDIS version: 0x501, vendor: 'D-Link AirPlus 22 Mbps Wireless Network Adapter', 104C:8400.5.conf
[   31.966947] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C00000BB)
[   31.966957] wlan0: encryption modes supported: WEP; TKIP with WPA
[   31.993261] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.996266] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x280-0x287
[   31.997458] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   31.997982] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   31.998060] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   31.998727] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   35.703275] kjournald starting.  Commit interval 5 seconds
[   35.703305] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   35.704468] EXT3 FS on sdb1, internal journal
[   35.704478] EXT3-fs: mounted filesystem with ordered data mode.
[   42.995174] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
[   73.905077] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[   74.545087] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   85.084043] wlan0: no IPv6 routers present

```

```
dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 (Ubuntu 2.6.32-24.41-generic 2.6.32.15+drm33.5)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004ffae000 (usable)
[    0.000000]  BIOS-e820: 000000004ffae000 - 0000000050000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x4ffae max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 040000000 mask FF0000000 write-back
[    0.000000]   2 base 0FEDA0000 mask FFFFE0000 write-combining
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000004ffae000 (usable)
[    0.000000]  modified: 000000004ffae000 - 0000000050000000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 3785a000 - 37fefc01
[    0.000000] Allocated new RAMDISK: 008e2000 - 01077c01
[    0.000000] Move RAMDISK from 000000003785a000 - 0000000037fefc00 to 008e2000 - 01077c00
[    0.000000] ACPI: RSDP 000fdf00 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 4fff0000 0002C (v01 DELL    CPi R   27D5061E ASL  00000061)
[    0.000000] ACPI: FACP 4fff0400 00074 (v01 DELL    CPi R   27D5061E ASL  00000061)
[    0.000000] ACPI: DSDT 4fff0c00 02C70 (v01 INT430 SYSFexxx 00001001 MSFT 0100000E)
[    0.000000] ACPI: FACS 4ffff800 00040
[    0.000000] ACPI: BOOT 4fff07c0 00028 (v01 DELL    CPi R   27D5061E ASL  00000061)
[    0.000000] 391MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ddeb8]    TEXT DATA BSS ==> [0000100000 - 00008ddeb8]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00008de000 - 00008e1198]              BRK ==> [00008de000 - 00008e1198]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008e2000 - 0001077c01]      NEW RAMDISK ==> [00008e2000 - 0001077c01]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0004ffae
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0004ffae
[    0.000000] On node 0 totalpages: 327497
[    0.000000] free_area_init_node: node 0, pgdat c079a780, node_mem_map c1079000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 784 pages used for memmap
[    0.000000]   HighMem zone: 99488 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 50000000:aeda0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1c00000 s36056 r0 d21288 u4194304
[    0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 324937
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=657b49ee-94fd-4251-8e54-9068e6904e18 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 6551960 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0004ffae)
[    0.000000] Memory: 1275608k/1310392k available (4679k kernel code, 33384k reserved, 2124k data, 660k init, 401088k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc084a000   ( 660 kB)
[    0.000000]       .data : 0xc0591e33 - 0xc07a4e88   (2124 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591e33   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2192.890 MHz processor.
[    0.008011] Calibrating delay loop (skipped), value calculated using timer frequency.. 4385.78 BogoMIPS (lpj=8771560)
[    0.008043] Security Framework initialized
[    0.008098] AppArmor: AppArmor initialized
[    0.008110] Mount-cache hash table entries: 512
[    0.008358] Initializing cgroup subsys ns
[    0.008368] Initializing cgroup subsys cpuacct
[    0.008375] Initializing cgroup subsys memory
[    0.008393] Initializing cgroup subsys devices
[    0.008398] Initializing cgroup subsys freezer
[    0.008402] Initializing cgroup subsys net_cls
[    0.008445] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.008451] CPU: L2 cache: 512K
[    0.008455] CPU: Hyper-Threading is disabled
[    0.008462] mce: CPU supports 4 MCE banks
[    0.008496] Performance Events: no PMU driver, software events only.
[    0.008510] Checking 'hlt' instruction... OK.
[    0.025301] SMP alternatives: switching to UP code
[    0.039796] Freeing SMP alternatives: 19k freed
[    0.039836] ACPI: Core revision 20090903
[    0.048864] ACPI: setting ELCR to 0200 (from 0800)
[    0.051420] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.051430] ftrace: allocating 21780 entries in 43 pages
[    0.052135] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.052141] weird, boot CPU (#0) not listed by the BIOS.
[    0.052144] SMP motherboard not detected.
[    0.052148] Local APIC not detected. Using dummy APIC emulation.
[    0.052151] SMP disabled
[    0.052460] Brought up 1 CPUs
[    0.052465] Total of 1 processors activated (4385.78 BogoMIPS).
[    0.052864] CPU0 attaching NULL sched-domain.
[    0.053090] devtmpfs: initialized
[    0.056247] regulator: core version 0.5
[    0.056275] Time: 11:41:13  Date: 08/20/10
[    0.056346] NET: Registered protocol family 16
[    0.056526] EISA bus registered
[    0.056541] ACPI: bus type pci registered
[    0.090887] PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=2
[    0.090891] PCI: Using configuration type 1 for base access
[    0.092382] bio: create slab <bio-0> at 0
[    0.093037] ACPI: EC: Look up EC in DSDT
[    0.106727] ACPI: Interpreter enabled
[    0.106754] ACPI: (supports S0 S1 S3 S4 S5)
[    0.106790] ACPI: Using PIC for interrupt routing
[    0.133392] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.140380] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.140454] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xe0000000-0xe7ffffff]
[    0.140613] pci 0000:00:1d.0: reg 20 io port: [0xbf80-0xbf9f]
[    0.140680] pci 0000:00:1d.1: reg 20 io port: [0xbf40-0xbf5f]
[    0.140747] pci 0000:00:1d.2: reg 20 io port: [0xbf20-0xbf3f]
[    0.140824] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf4fffc00-0xf4ffffff]
[    0.140893] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.140900] pci 0000:00:1d.7: PME# disabled
[    0.141016] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.141022] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
[    0.141055] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
[    0.141064] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
[    0.141073] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
[    0.141082] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
[    0.141091] pci 0000:00:1f.1: reg 20 io port: [0xbfa0-0xbfaf]
[    0.141100] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.141157] pci 0000:00:1f.5: reg 10 io port: [0xb800-0xb8ff]
[    0.141166] pci 0000:00:1f.5: reg 14 io port: [0xbc40-0xbc7f]
[    0.141175] pci 0000:00:1f.5: reg 18 32bit mmio: [0xf4fff800-0xf4fff9ff]
[    0.141184] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xf4fff400-0xf4fff4ff]
[    0.141221] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.141227] pci 0000:00:1f.5: PME# disabled
[    0.141267] pci 0000:00:1f.6: reg 10 io port: [0xb400-0xb4ff]
[    0.141276] pci 0000:00:1f.6: reg 14 io port: [0xb080-0xb0ff]
[    0.141322] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.141328] pci 0000:00:1f.6: PME# disabled
[    0.141381] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xe8000000-0xefffffff]
[    0.141389] pci 0000:01:00.0: reg 14 io port: [0xc000-0xc0ff]
[    0.141397] pci 0000:01:00.0: reg 18 32bit mmio: [0xfcff0000-0xfcffffff]
[    0.141417] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x80000000-0x8001ffff]
[    0.141443] pci 0000:01:00.0: supports D1 D2
[    0.141489] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.141496] pci 0000:00:01.0: bridge 32bit mmio: [0xfc000000-0xfdffffff]
[    0.141501] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe8000000-0xefffffff]
[    0.141545] pci 0000:02:00.0: reg 10 32bit mmio: [0xfaffe000-0xfaffffff]
[    0.141597] pci 0000:02:00.0: supports D1 D2
[    0.141601] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.141607] pci 0000:02:00.0: PME# disabled
[    0.141650] pci 0000:02:01.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.141674] pci 0000:02:01.0: supports D1 D2
[    0.141677] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.141682] pci 0000:02:01.0: PME# disabled
[    0.141726] pci 0000:02:01.1: reg 10 32bit mmio: [0xfaffd800-0xfaffdfff]
[    0.141736] pci 0000:02:01.1: reg 14 32bit mmio: [0xfaff8000-0xfaffbfff]
[    0.141785] pci 0000:02:01.1: supports D1 D2
[    0.141788] pci 0000:02:01.1: PME# supported from D0 D1 D2 D3hot
[    0.141794] pci 0000:02:01.1: PME# disabled
[    0.141852] pci 0000:00:1e.0: transparent bridge
[    0.141858] pci 0000:00:1e.0: bridge io port: [0xd000-0xefff]
[    0.141864] pci 0000:00:1e.0: bridge 32bit mmio: [0xf6000000-0xfbffffff]
[    0.141901] pci_bus 0000:00: on NUMA node 0
[    0.141908] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.142187] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.142259] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.158612] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.158784] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    0.158953] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    0.159122] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[    0.159269] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.159444] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.159636] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.159642] vgaarb: loaded
[    0.159858] SCSI subsystem initialized
[    0.160064] libata version 3.00 loaded.
[    0.160190] usbcore: registered new interface driver usbfs
[    0.160211] usbcore: registered new interface driver hub
[    0.160249] usbcore: registered new device driver usb
[    0.160461] ACPI: WMI: Mapper loaded
[    0.160465] PCI: Using ACPI for IRQ routing
[    0.160684] NetLabel: Initializing
[    0.160688] NetLabel:  domain hash size = 128
[    0.160690] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.160710] NetLabel:  unlabeled traffic allowed by default
[    0.160779] Switching to clocksource tsc
[    0.163765] AppArmor: AppArmor Filesystem Enabled
[    0.163799] pnp: PnP ACPI init
[    0.163833] ACPI: bus type pnp registered
[    0.177093] pnp 00:02: io resource (0x800-0x805) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.177099] pnp 00:02: io resource (0x808-0x80f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.177197] pnp 00:03: io resource (0x806-0x807) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.177203] pnp 00:03: io resource (0x810-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.177208] pnp 00:03: io resource (0x860-0x87f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.214579] pnp: PnP ACPI: found 14 devices
[    0.214583] ACPI: ACPI bus type pnp unregistered
[    0.214591] PnPBIOS: Disabled by ACPI PNP
[    0.214611] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.214617] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.214622] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.214627] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.214631] system 00:00: iomem range 0x100000-0x4ffeffff could not be reserved
[    0.214636] system 00:00: iomem range 0x4fff0000-0x4fffffff has been reserved
[    0.214641] system 00:00: iomem range 0xfeda0000-0xfedfffff has been reserved
[    0.214645] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.214657] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.214670] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.214676] system 00:03: ioport range 0x880-0x8bf has been reserved
[    0.214681] system 00:03: ioport range 0x8c0-0x8df has been reserved
[    0.214685] system 00:03: ioport range 0x8e0-0x8ff has been reserved
[    0.214697] system 00:08: ioport range 0x900-0x97f has been reserved
[    0.249524] pci 0000:01:00.0: BAR 6: no parent found for of device [0x80000000-0x8001ffff]
[    0.249561] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.249566] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.249572] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfdffffff
[    0.249578] pci 0000:00:01.0:   PREFETCH window: 0xe8000000-0xefffffff
[    0.249591] pci 0000:02:01.0: CardBus bridge, secondary bus 0000:03
[    0.249595] pci 0000:02:01.0:   IO window: 0x00d000-0x00d0ff
[    0.249601] pci 0000:02:01.0:   IO window: 0x00d400-0x00d4ff
[    0.249607] pci 0000:02:01.0:   PREFETCH window: 0x50000000-0x53ffffff
[    0.249614] pci 0000:02:01.0:   MEM window: 0x58000000-0x5bffffff
[    0.249620] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.249624] pci 0000:00:1e.0:   IO window: 0xd000-0xefff
[    0.249632] pci 0000:00:1e.0:   MEM window: 0xf6000000-0xfbffffff
[    0.249638] pci 0000:00:1e.0:   PREFETCH window: 0x50000000-0x53ffffff
[    0.249661] pci 0000:00:1e.0: setting latency timer to 64
[    0.249672] pci 0000:02:01.0: enabling device (0000 -> 0003)
[    0.249924] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.249928] PCI: setting IRQ 11 as level-triggered
[    0.249935] pci 0000:02:01.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.249946] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.249950] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.249954] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.249957] pci_bus 0000:01: resource 1 mem: [0xfc000000-0xfdffffff]
[    0.249961] pci_bus 0000:01: resource 2 pref mem [0xe8000000-0xefffffff]
[    0.249965] pci_bus 0000:02: resource 0 io:  [0xd000-0xefff]
[    0.249969] pci_bus 0000:02: resource 1 mem: [0xf6000000-0xfbffffff]
[    0.249973] pci_bus 0000:02: resource 2 pref mem [0x50000000-0x53ffffff]
[    0.249977] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.249980] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.249984] pci_bus 0000:03: resource 0 io:  [0xd000-0xd0ff]
[    0.249988] pci_bus 0000:03: resource 1 io:  [0xd400-0xd4ff]
[    0.249992] pci_bus 0000:03: resource 2 pref mem [0x50000000-0x53ffffff]
[    0.249996] pci_bus 0000:03: resource 3 mem: [0x58000000-0x5bffffff]
[    0.250054] NET: Registered protocol family 2
[    0.250207] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.250823] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.252349] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.253312] TCP: Hash tables configured (established 131072 bind 65536)
[    0.253318] TCP reno registered
[    0.253559] NET: Registered protocol family 1
[    0.253695] pci 0000:01:00.0: Boot video device
[    0.253889] Simple Boot Flag at 0x79 set to 0x1
[    0.254180] cpufreq-nforce2: No nForce2 chipset.
[    0.254220] Scanning for low memory corruption every 60 seconds
[    0.254416] audit: initializing netlink socket (disabled)
[    0.254436] type=2000 audit(1282304473.251:1): initialized
[    0.265103] Trying to unpack rootfs image as initramfs...
[    0.279218] highmem bounce pool size: 64 pages
[    0.279229] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.281495] VFS: Disk quotas dquot_6.5.2
[    0.281599] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.287290] fuse init (API version 7.13)
[    0.287490] msgmni has been set to 1710
[    0.287877] alg: No test for stdrng (krng)
[    0.287981] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.287987] io scheduler noop registered
[    0.287989] io scheduler anticipatory registered
[    0.287992] io scheduler deadline registered
[    0.288055] io scheduler cfq registered (default)
[    0.288232] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.288270] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.288889] ACPI: AC Adapter [AC] (on-line)
[    0.289007] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.289454] ACPI: Lid Switch [LID]
[    0.289526] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.289533] ACPI: Power Button [PBTN]
[    0.289603] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.289608] ACPI: Sleep Button [SBTN]
[    0.290069] Marking TSC unstable due to TSC halts in idle
[    0.290131] processor LNXCPU:00: registered as cooling_device0
[    0.294875] Switching to clocksource acpi_pm
[    0.319187] thermal LNXTHERM:01: registered as thermal_zone0
[    0.319204] ACPI: Thermal Zone [THM] (70 C)
[    0.332382] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.332507] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.332625] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.333143] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.333330] isapnp: Scanning for PnP cards...
[    0.425562] ACPI: Battery Slot [BAT1] (battery absent)
[    0.425737] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[    0.425743] PCI: setting IRQ 5 as level-triggered
[    0.425751] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    0.425767] serial 0000:00:1f.6: PCI INT B disabled
[    0.427354] brd: module loaded
[    0.431498] loop: module loaded
[    0.431679] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.431858] ata_piix 0000:00:1f.1: version 2.13
[    0.431877] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.432184] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.432191] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.432271] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.436183] scsi0 : ata_piix
[    0.436401] scsi1 : ata_piix
[    0.437621] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.437626] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.438234] Fixed MDIO Bus: probed
[    0.438293] PPP generic driver version 2.4.2
[    0.438404] tun: Universal TUN/TAP device driver, 1.6
[    0.438408] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.438553] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.438849] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    0.438857] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    0.438884] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.438890] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.438946] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.438997] ehci_hcd 0000:00:1d.7: debug port 1
[    0.442900] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.458654] ACPI: Battery Slot [BAT0] (battery present)
[    0.458685] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
[    0.472134] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.472368] usb usb1: configuration #1 chosen from 1 choice
[    0.472418] hub 1-0:1.0: USB hub found
[    0.472440] hub 1-0:1.0: 6 ports detected
[    0.472551] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.472579] uhci_hcd: USB Universal Host Controller Interface driver
[    0.472659] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.472676] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.472682] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.472747] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.472780] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[    0.472917] usb usb2: configuration #1 chosen from 1 choice
[    0.472959] hub 2-0:1.0: USB hub found
[    0.472975] hub 2-0:1.0: 2 ports detected
[    0.473046] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.473056] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.473060] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.473116] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.473143] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[    0.473273] usb usb3: configuration #1 chosen from 1 choice
[    0.473319] hub 3-0:1.0: USB hub found
[    0.473332] hub 3-0:1.0: 2 ports detected
[    0.473689] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.473695] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.473706] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.473711] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.473781] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.473811] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[    0.473970] usb usb4: configuration #1 chosen from 1 choice
[    0.474017] hub 4-0:1.0: USB hub found
[    0.474032] hub 4-0:1.0: 2 ports detected
[    0.474193] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.484715] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.484738] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.485017] mice: PS/2 mouse device common for all mice
[    0.485325] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.485350] rtc0: alarms up to one day, 114 bytes nvram
[    0.485539] device-mapper: uevent: version 1.0.3
[    0.485759] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.531494] device-mapper: multipath: version 1.1.0 loaded
[    0.531501] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.532826] EISA: Probing bus 0 at eisa.0
[    0.532860] EISA: Detected 0 cards.
[    0.533573] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.536527] cpuidle: using governor ladder
[    0.536656] cpuidle: using governor menu
[    0.537401] TCP cubic registered
[    0.537597] NET: Registered protocol family 10
[    0.538306] lo: Disabled Privacy Extensions
[    0.538806] NET: Registered protocol family 17
[    0.538893] Using IPI No-Shortcut mode
[    0.539063] PM: Resume from disk failed.
[    0.539083] registered taskstats version 1
[    0.539387]   Magic number: 6:812:681
[    0.539533] rtc_cmos 00:06: setting system clock to 2010-08-20 11:41:13 UTC (1282304473)
[    0.539538] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.539542] EDD information not available.
[    0.632873] ata2.00: ATAPI: QSI CD-RW/DVD-ROM SBW-242, UD22, max UDMA/33
[    0.633039] ata1.00: ATA-5: HITACHI_DK23FB-60, 00M0A0C1, max UDMA/100
[    0.633044] ata1.00: 117210240 sectors, multi 8: LBA 
[    0.633650] ata2.00: configured for UDMA/33
[    0.640675] ata1.00: configured for UDMA/100
[    0.799771] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    0.993826] Freeing initrd memory: 7767k freed
[    1.052507] isapnp: No Plug & Play device found
[    1.052831] scsi 0:0:0:0: Direct-Access     ATA      HITACHI_DK23FB-6 00M0 PQ: 0 ANSI: 5
[    1.053171] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.053476] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.053579] sd 0:0:0:0: [sda] Write Protect is off
[    1.053584] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.053622] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.053904]  sda:
[    1.054291] usb 1-3: configuration #1 chosen from 1 choice
[    1.056794] scsi 1:0:0:0: CD-ROM            QSI      CDRW/DVD SBW-242 UD22 PQ: 0 ANSI: 5
[    1.059782] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
[    1.059788] Uniform CD-ROM driver Revision: 3.20
[    1.059951] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.060079] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.064719]  sda1 sda2 < sda5 sda6 >
[    1.081473] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.081498] Freeing unused kernel memory: 660k freed
[    1.082643] Write protecting the kernel text: 4680k
[    1.082681] Write protecting the kernel read-only data: 1844k
[    1.119827] udev: starting version 151
[    1.599912] Initializing USB Mass Storage driver...
[    1.605033] b44 0000:02:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    1.605604] scsi2 : SCSI emulation for USB Mass Storage devices
[    1.605863] usbcore: registered new interface driver usb-storage
[    1.605869] USB Mass Storage support registered.
[    1.606488] usb-storage: device found at 2
[    1.606493] usb-storage: waiting for device to settle before scanning
[    1.664243] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[    1.664333] ohci1394 0000:02:01.1: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    1.664823] b44.c:v2.0
[    1.685178] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0d:56:35:78:b5
[    1.720098] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[faffd800-faffdfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.843040] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.992248] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[484fc00030cbbc61]
[    6.604334] usb-storage: device scan complete
[    6.646537] scsi 2:0:0:0: Direct-Access     WDC WD10 EAVS-00D7B0           PQ: 0 ANSI: 2 CCS
[    6.647260] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    6.647997] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    6.648865] sd 2:0:0:0: [sdb] Write Protect is off
[    6.648870] sd 2:0:0:0: [sdb] Mode Sense: 34 00 00 00
[    6.648874] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.650541] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.650549]  sdb: sdb1 sdb2
[    6.672239] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.672245] sd 2:0:0:0: [sdb] Attached SCSI disk
[   24.487229] Adding 1799240k swap on /dev/sda5.  Priority:-1 extents:1 across:1799240k 
[   24.502729] udev: starting version 151
[   24.713207] lp: driver loaded but no devices found
[   24.903791] parport_pc 00:0c: reported by Plug and Play ACPI
[   24.903851] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   24.953804] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:1d/LNXVIDEO:00/input/input5
[   24.953974] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   25.001913] lp0: using parport0 (interrupt-driven).
[   25.084623] Linux agpgart interface v0.103
[   25.091387] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.397081] Disabling lock debugging due to kernel taint
[   25.415135] irda_init()
[   25.415163] NET: Registered protocol family 23
[   25.443037] intel_rng: FWH not detected
[   25.527364] ppdev: user-space parallel port driver
[   25.530875] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   25.559712] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   25.559822] agpgart-intel 0000:00:00.0: Intel 845G Chipset
[   25.633373] dell-wmi: No known WMI GUID found
[   25.636812] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[   25.767161] EXT4-fs (sda6): mounted filesystem with ordered data mode
[   25.783203] [drm] Initialized drm 1.1.0 20060810
[   25.786891] type=1505 audit(1282304498.744:2):  operation="profile_load" pid=582 name="/sbin/dhclient3"
[   25.787601] type=1505 audit(1282304498.744:3):  operation="profile_load" pid=582 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   25.787988] type=1505 audit(1282304498.744:4):  operation="profile_load" pid=582 name="/usr/lib/connman/scripts/dhclient-script"
[   25.818147] yenta_cardbus 0000:02:01.0: CardBus bridge found [1028:013e]
[   25.818173] yenta_cardbus 0000:02:01.0: Using CSCINT to route CSC interrupts to PCI
[   25.818178] yenta_cardbus 0000:02:01.0: Routing CardBus interrupts to PCI
[   25.818185] yenta_cardbus 0000:02:01.0: TI: mfunc 0x012c1202, devctl 0x64
[   26.051240] yenta_cardbus 0000:02:01.0: ISA IRQ mask 0x0458, PCI irq 11
[   26.051249] yenta_cardbus 0000:02:01.0: Socket status: 30000020
[   26.051255] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   26.051278] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   26.051285] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xd000-0xefff: clean.
[   26.052419] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[   26.052425] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   26.055783] usbcore: registered new interface driver ndiswrapper
[   26.097066] [drm] radeon defaulting to kernel modesetting.
[   26.097074] [drm] radeon kernel modesetting enabled.
[   26.097165] radeon 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   26.121789] [drm] radeon: Initializing kernel modesetting.
[   26.122110] [drm] register mmio base: 0xFCFF0000
[   26.122115] [drm] register mmio size: 65536
[   26.122448] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   26.122479] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   26.122503] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   26.122549] radeon 0000:01:00.0: putting AGP V2 device into 4x mode
[   26.122572] [drm] radeon: VRAM 64M
[   26.122575] [drm] radeon: VRAM from 0x00000000 to 0x03FFFFFF
[   26.122578] [drm] radeon: GTT 128M
[   26.122581] [drm] radeon: GTT from 0xE0000000 to 0xE7FFFFFF
[   26.122622] [drm] radeon: irq initialized.
[   26.122765] [drm] Detected VRAM RAM=64M, BAR=128M
[   26.122771] [drm] RAM width 64bits DDR
[   26.122907] [TTM] Zone  kernel: Available graphics memory: 441980 kiB.
[   26.122911] [TTM] Zone highmem: Available graphics memory: 642524 kiB.
[   26.122940] [drm] radeon: 32M of VRAM memory ready
[   26.122944] [drm] radeon: 128M of GTT memory ready.
[   26.123194] [drm] radeon: cp idle (0x02000603)
[   26.123364] [drm] Loading R200 Microcode
[   26.124119] platform radeon_cp.0: firmware: requesting radeon/R200_cp.bin
[   26.165217] [drm] radeon: ring at 0x00000000E0000000
[   26.165243] [drm] ring test succeeded in 1 usecs
[   26.185420] [drm] radeon: ib pool ready.
[   26.185577] [drm] ib test succeeded in 0 usecs
[   26.188138] [drm] DFP table revision: 3
[   26.189970] [drm] Panel ID String: W
[   26.189976] [drm] Panel Size 1280x800
[   26.190210] [drm] Default TV standard: NTSC
[   26.190214] [drm] 27.000000000 MHz TV ref clk
[   26.190220] [drm] Default TV standard: NTSC
[   26.190222] [drm] 27.000000000 MHz TV ref clk
[   26.190399] [drm] Radeon Display Connectors
[   26.190403] [drm] Connector 0:
[   26.190406] [drm]   VGA
[   26.190410] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   26.190413] [drm]   Encoders:
[   26.190416] [drm]     CRT1: INTERNAL_DAC1
[   26.190418] [drm] Connector 1:
[   26.190420] [drm]   DVI-D
[   26.190423] [drm]   HPD1
[   26.190426] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   26.190429] [drm]   Encoders:
[   26.190431] [drm]     DFP1: INTERNAL_TMDS1
[   26.190434] [drm] Connector 2:
[   26.190436] [drm]   LVDS
[   26.190438] [drm]   Encoders:
[   26.190440] [drm]     LCD1: INTERNAL_LVDS
[   26.190442] [drm] Connector 3:
[   26.190444] [drm]   S-video
[   26.190446] [drm]   Encoders:
[   26.190449] [drm]     TV1: INTERNAL_DAC2
[   26.246308] [drm] fb mappable at 0xE8040000
[   26.246314] [drm] vram apper at 0xE8000000
[   26.246316] [drm] size 1024000
[   26.246319] [drm] fb depth is 8
[   26.246321] [drm]    pitch is 1280
[   26.255722] fb0: radeondrmfb frame buffer device
[   26.255728] registered panic notifier
[   26.255739] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   26.266647] vga16fb: initializing
[   26.266657] vga16fb: mapped to 0xc00a0000
[   26.266665] vga16fb: not registering due to another framebuffer present
[   26.328819] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input6
[   26.375624] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input7
[   26.461910] Console: switching to colour frame buffer device 160x50
[   26.508709] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   26.508774] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   26.692057] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[   26.692114] pci 0000:03:00.0: reg 10 io port: [0x00-0x1f]
[   26.692125] pci 0000:03:00.0: reg 14 32bit mmio: [0x000000-0x000fff]
[   26.692135] pci 0000:03:00.0: reg 18 32bit mmio: [0x000000-0x00ffff]
[   26.692192] pci 0000:03:00.0: supports D1 D2
[   26.692196] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
[   26.692203] pci 0000:03:00.0: PME# disabled
[   27.336050] intel8x0_measure_ac97_clock: measured 55226 usecs (2661 samples)
[   27.336056] intel8x0: clocking to 48000
[   29.252672] usbcore: registered new interface driver hiddev
[   29.254381] usbcore: registered new interface driver usbhid
[   29.255432] usbhid: v2.6:USB HID core driver
[   29.282382] ndiswrapper: driver airplus (D-Link,09/08/2003,4.15.5.1) loaded
[   29.282772] ndiswrapper 0000:03:00.0: enabling device (0000 -> 0003)
[   29.282793] ndiswrapper 0000:03:00.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[   29.283054] ndiswrapper 0000:03:00.0: setting latency timer to 64
[   29.283653] ndiswrapper: using IRQ 11
[   30.366084] type=1505 audit(1282304503.324:5):  operation="profile_replace" pid=812 name="/sbin/dhclient3"
[   30.366829] type=1505 audit(1282304503.324:6):  operation="profile_replace" pid=812 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   30.367231] type=1505 audit(1282304503.324:7):  operation="profile_replace" pid=812 name="/usr/lib/connman/scripts/dhclient-script"
[   30.404786] type=1505 audit(1282304503.364:8):  operation="profile_load" pid=813 name="/usr/bin/evince"
[   30.447049] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.511372] type=1505 audit(1282304503.468:9):  operation="profile_load" pid=813 name="/usr/bin/evince-previewer"
[   30.567235] type=1505 audit(1282304503.524:10):  operation="profile_load" pid=813 name="/usr/bin/evince-thumbnailer"
[   30.634527] type=1505 audit(1282304503.592:11):  operation="profile_load" pid=904 name="/usr/lib/cups/backend/cups-pdf"
[   30.846368] pnp 00:0d: disabled
[   30.964638] pnp 00:0d: activated
[   31.021345] pnp 00:0d: disabled
[   31.103908] pnp 00:0d: activated
[   31.730482] __ratelimit: 12 callbacks suppressed
[   31.730488] type=1505 audit(1282304504.688:16):  operation="profile_replace" pid=1105 name="/usr/sbin/mysqld"
[   31.966423] wlan0: ethernet device 00:80:c8:b2:4b:fa using NDIS driver: airplus, version: 0x4000f, NDIS version: 0x501, vendor: 'D-Link AirPlus 22 Mbps Wireless Network Adapter', 104C:8400.5.conf
[   31.966947] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C00000BB)
[   31.966957] wlan0: encryption modes supported: WEP; TKIP with WPA
[   31.993261] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.996266] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x280-0x287
[   31.997458] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   31.997982] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   31.998060] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   31.998727] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   35.703275] kjournald starting.  Commit interval 5 seconds
[   35.703305] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   35.704468] EXT3 FS on sdb1, internal journal
[   35.704478] EXT3-fs: mounted filesystem with ordered data mode.
[   42.995174] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
[   73.905077] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[   74.545087] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   85.084043] wlan0: no IPv6 routers present
[  103.460077] usb 2-1: new low speed USB device using uhci_hcd and address 2
[  103.641544] usb 2-1: configuration #1 chosen from 1 choice
[  103.692214] input: Microsoft Microsoft Wheel Mouse Optical® as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input8
[  103.693309] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft Wheel Mouse Optical®] on usb-0000:00:1d.0-1/input0

```

---

### Post by tosszyx on 2010-08-20
I also noticed that in my media folder I have folder name usb0 up to usb7 already present, even when I'm using only usb0 and usb1 for my external harddisk.

ps. I'm attaching the *dmesg* output as files, maybe is easier this way.

EDIT: Well, it seems I can not attach "big" text files "Your file of 41.0 KB bytes exceeds the forum's limit of 19.5 KB for this filetype."

---

### Post by anubhavrocks on 2010-08-20
tosszyx can you enable apic. I heard that SMP without APIC support has issues.

Also post output of:
sudo lshw

---

### Post by tosszyx on 2010-08-20
Well, I would do it gladly, but you went beyond my knowledge of Linux :P How could I do that ? The output of *lshw* is below. Thanks a lot !

```
sudo lshw
coatl
    description: Portable Computer
    product: Inspiron 8500
    vendor: Dell Computer Corporation
    serial: HSDRH31
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-5300-1044-8052-C8C04F483331
  *-core
       description: Motherboard
       product: 00U838
       vendor: Dell Computer Corporation
       physical id: 0
       serial: .HSDRH31.CN1296138S3629.
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A08 (06/30/2005)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Mobile Intel(R) Pentium(R) 4 - M CPU 2.20GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.9
          slot: Microprocessor
          size: 2200MHz
          capacity: 2200MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KiB
             capacity: 512KiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1280MiB
        *-bank:0
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 0
             slot: DIMM_A
             size: 1GiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 1
             slot: DIMM_B
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e0000000-e7ffffff(prefetchable)
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:c000(size=4096) memory:fc000000-fdffffff memory:e8000000-efffffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: Radeon RV250 [Mobility FireGL 9000]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm bus_master vga_palette cap_list rom
                configuration: driver=radeon latency=32 mingnt=8
                resources: irq:11 memory:e8000000-efffffff(prefetchable) ioport:c000(size=256) memory:fcff0000-fcffffff memory:fc000000-fc01ffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:bf80(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:bf40(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:bf20(size=32)
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:11 memory:f4fffc00-f4ffffff
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:d000(size=8192) memory:f6000000-fbffffff memory:50000000-53ffffff(prefetchable)
           *-network
                description: Ethernet interface
                product: BCM4401 100Base-T
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: 00:0d:56:35:78:b5
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no multicast=yes port=twisted pair speed=10MB/s
                resources: irq:11 memory:faffe000-faffffff
           *-pcmcia
                description: CardBus bridge
                product: PCI4510 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                resources: irq:11 memory:f6000000-f6000fff ioport:d000(size=256) ioport:d400(size=256) memory:50000000-53ffffff(prefetchable) memory:58000000-5bffffff
              *-pccard UNCLAIMED
                   description: Global
                   vendor: Wireless Network CardBus PC Card
                   physical id: 0
                   slot: Socket 0
                   resources: irq:11
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCI4510 IEEE-1394 Controller
                vendor: Texas Instruments
                physical id: 1.1
                bus info: pci@0000:02:01.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
                resources: irq:11 memory:faffd800-faffdfff memory:faff8000-faffbfff
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:11 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16) memory:54000000-540003ff
           *-disk
                description: ATA Disk
                product: HITACHI_DK23FB-6
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 00M0
                serial: 1DZ013
                size: 55GiB (60GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=fd478bc7
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 657b49ee-94fd-4251-8e54-9068e6904e18
                   size: 11GiB
                   capacity: 11GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-05-24 16:18:02 filesystem=ext4 lastmountpoint=/&#65533;&#65533;&#65533;6+%&#65533;HJ&#65533;&#65533;l&#65533;&#65533;p&#1938;&#65533;h &#65533;&#65533;h/&#65533;d&#1938;&#65533;!&#65533;&#65533;n&#65533;&#65533;&#65533;n&#65533;&#65533;+%&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;]k modified=2010-08-20 13:19:05 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-08-20 13:41:38 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 44GiB
                   capacity: 44GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1757MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /home
                      capacity: 42GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
           *-cdrom
                description: DVD reader
                product: CDRW/DVD SBW-242
                vendor: QSI
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: UD22
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:5 ioport:b800(size=256) ioport:bc40(size=64) memory:f4fff800-f4fff9ff memory:f4fff400-f4fff4ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: ioport:b400(size=256) ioport:b080(size=128)
     *-network
          description: Wireless interface
          product: ACX 100 22Mbps Wireless Interface
          vendor: Texas Instruments
          physical id: 1
          bus info: pci@0000:03:00.0
          logical name: wlan0
          version: 00
          serial: 00:80:c8:b2:4b:fa
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=ndiswrapper+airplus driverversion=1.55+D-Link,09/08/2003,4.15.5.1 ip=192.168.1.102 latency=64 link=yes multicast=yes wireless=IEEE 802.11b
          resources: irq:11 ioport:d000(size=32) memory:58010000-58010fff memory:58000000-5800ffff
     *-scsi:0
          physical id: 2
          bus info: usb@1:3
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: signature=2a3680f2
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/usb1
                version: 1.0
                serial: 8beccb20-4e02-4581-8262-849880b2b9dc
                size: 409GiB
                capacity: 409GiB
                capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                configuration: created=2008-12-16 17:51:39 filesystem=ext3 label=BACKUP modified=2010-08-20 13:41:48 mount.fstype=ext3 mount.options=rw,sync,nodev,noexec,noatime,nodiratime,errors=continue,data=ordered mounted=2010-08-20 13:41:48 state=mounted
           *-volume:1
                description: Windows FAT volume
                vendor: mkdosfs
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sdb2
                logical name: /media/usb0
                version: FAT32
                serial: 4947-dbff
                size: 465GiB
                capacity: 465GiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat label=STORAGE mount.fstype=vfat mount.options=rw,sync,nodev,noexec,noatime,nodiratime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
     *-scsi:1
          physical id: 3
          bus info: usb@1:1.3
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Photosmart D5100
             vendor: HP
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdc
             version: 1.00
             capabilities: removable
             configuration: ansiversion=2
           *-medium
                physical id: 0
                logical name: /dev/sdc
  *-battery
       product: DELL 1P745 3
       vendor: Panasonic
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 71990mWh
       configuration: voltage=11.1V

```

---

### Post by tosszyx on 2010-08-20
After searching a bit, I got with this instructions in Gentoo on how to enable APIC by recompiling the kernel, is it the right path or I've just to edit a couple of files ?

[http://forums.gentoo.org/viewtopic.php?t=194312]("http://forums.gentoo.org/viewtopic.php?t=194312")

---

