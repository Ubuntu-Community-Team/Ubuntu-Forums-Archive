---
title: "suspend2 eats my swap partition"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by shotgunefx on 2007-03-27
I'm running a patched 2.6.20 kernel with version 2.2.9.10 of suspend2 on my Dell Inspirion 8600.

When suspending, everything seems to go ok. No errors in the hibernate.log

When the computer comes back, it just boots normally and my swap partition (/dev/hda5)  is missing.

So I fire up gparted and set it to swap again. Turn it on, all is good. I try hibernating again and sure enough, it's gone again. Happens every single time.

Anyone have any ideas or suggestions? I can't find anything like this when googling or looking through the faqs/mailing-lists.

FYI, I've got the resume2=swap:/dev/hdxy set correctly to my swap in menu.1st.

---

### Post by shotgunefx on 2007-03-28
No suggestions?

Rebuilt the kernel with the extra debugging and call traces and I still can't figure out why it's happening.

Also with splash disabled and quiet, I'm not getting boot messages.

---

### Post by Nigel_C on 2007-03-28
You probably have an initrd or initramfs, and haven't followed the instructions for setting it up to fire the resume. The script in the initrd/ramfs that runs when you boot needs to mount /sys and /proc and then do echo > /sys/power/suspend2/do_resume, prior to your normal (ie root, home etc) filesystems being mounted.

---

### Post by shotgunefx on 2007-03-29
> **Nigel_C said:**
> You probably have an initrd or initramfs, and haven't followed the instructions for setting it up to fire the resume. The script in the initrd/ramfs that runs when you boot needs to mount /sys and /proc and then do echo > /sys/power/suspend2/do_resume, prior to your normal (ie root, home etc) filesystems being mounted.

Hi Nigel,

I used the info here [http://wiki.suspend2.net/DistroAndHardwareSetup/Ubuntu_Breezy_Badger](http://wiki.suspend2.net/DistroAndHardwareSetup/Ubuntu_Breezy_Badger) and get the same behavior. (I reinstalled my kernel image after updating btw)

I'm using v1.94 of the Hibernate script. One problem on install is that it is looking for this file and it's not in the archive.

ususpend.conf

I simply commented out the occurence in two places and everything else installs. Could this be the problem?

**hibernate.log**
```

Starting suspend at Thu Mar 29 18:15:10 EDT 2007
hibernate: [01] Executing CheckLastResume ... 
hibernate: [01] Executing CheckRunlevel ... 
hibernate: [01] Executing LockFileGet ... 
hibernate: [01] Executing NewKernelFileCheck ... 
hibernate: [10] Executing EnsureSwsusp2Capable ... 
hibernate: [11] Executing XHacksSuspendHook1 ... 
hibernate: [59] Executing RemountXFSBootRO ... 
hibernate: [89] Executing SaveKernelModprobe ... 
hibernate: [91] Executing ModulesUnloadBlacklist ... 
hibernate: [95] Executing XHacksSuspendHook2 ... 
hibernate: [97] Executing ChangeToSwsuspVT ... 
hibernate: [98] Executing CheckRunlevel ... 
hibernate: [98] Executing FullSpeedCPUSuspend ... 
hibernate: [98] Executing Swsusp2ConfigSet ... 
hibernate: [99] Executing DoSwsusp2 ... 

```

**kern.log**
```

Mar 29 18:01:24 localhost kernel: [   10.750868] Suspend v2.2.9.10
Mar 29 18:01:24 localhost kernel: [   10.750889] Suspend2 Userspace Storage Manager support registered.
Mar 29 18:01:24 localhost kernel: [   10.750918] Suspend2 Userspace UI support registered.
Mar 29 18:01:24 localhost kernel: [   10.750948] Suspend2 Compressor support registered.
Mar 29 18:01:24 localhost kernel: [   10.750975] Suspend2 Encryptor support registered.
Mar 29 18:01:24 localhost kernel: [   10.751003] Suspend2 Block I/O support registered.
Mar 29 18:01:24 localhost kernel: [   10.751009] Suspend2 Swap Allocator support registered.
Mar 29 18:01:24 localhost kernel: [   10.751037] Suspend2 File Allocator support registered.

```

**hibernate --bug-report** (Lists 1.93 even though I installed 1.94)
```

System information follows. (Please include with bug reports).
--- Hibernate script version: 1.93
--- kernel config not compiled into kernel. Please attach this separately.
--- Modules loaded: lzf binfmt_misc video sbs i2c_ec dock battery container ac asus_acpi backlight af_packet sbp2 scsi_mod lp saa7134_alsa tuner joydev nvidia saa7134 video_buf compat_ioctl32 ir_kbd_i2c i2c_core tsdev ir_common videodev v4l2_common v4l1_compat usbtouchscreen snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss pcmcia shpchp snd_pcm snd_timer snd soundcore pci_hotplug pcspkr intel_agp agpgart rng_core snd_page_alloc serio_raw b44 ieee80211 ieee80211_crypt parport_pc parport evdev mii yenta_socket rsrc_nonstatic pcmcia_core usbhid ext3 jbd mbcache ohci1394 ieee1394 ehci_hcd uhci_hcd usbcore ide_generic ide_cd cdrom ide_disk piix generic thermal processor fan
--- Active swaps:
Filename                                Type            Size    Used    Priority
/dev/hda5                               partition       634528  0       -1
--- /proc/cmdline: root=/dev/hda4 ro vga=788 resume2=swap:/dev/hda5
--- /proc/cpuinfo:
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 9
model name      : Intel(R) Pentium(R) M processor 1400MHz
stepping        : 5
cpu MHz         : 1398.842
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe up est tm2
bogomips        : 2799.64
clflush size    : 64

--- lspci:
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
03:00.0 Multimedia controller: Philips Semiconductors SAA7134 Video Broadcast Decoder (rev 01)

Message from syslogd@localhost at Thu Mar 29 18:42:59 2007 ...
localhost kernel: [ 2520.876000] Freezing processes & syncing filesystems.

Message from syslogd@localhost at Thu Mar 29 18:42:59 2007 ...
localhost kernel: [ 2520.924000] Preparing Image. Try 1.

Message from syslogd@localhost at Thu Mar 29 18:42:59 2007 ...
localhost kernel: [ 2521.192000] Cleaning up...

```

So I wipe out everything related to hibernate-scripts and do a reinstall (have the same problem with ususpend.conf), but now when I try and hibernate, complains that common.conf is missing, had an older version and copied it over. 

Seems to suspend ok, but then same thing, swap is missing.

Any suggestions?

---

### Post by Nigel_C on 2007-03-29
Hi.

Could you post your dmesg from when you expect it to have resumed?

Thanks in advance!

---

### Post by shotgunefx on 2007-03-29
> **Nigel_C said:**
> Hi.

Could you post your dmesg from when you expect it to have resumed?

Thanks in advance!

Sure thing. It's a bit long with all the debugging that's enabled. Removed the "No Bus" messages. Appreciate the help.

-Lee

```

root@coupe:~# dmesg | grep -v "Adding info for No Bus"
[    0.000000] Linux version 2.6.20s2newsuspend2 (root@coupe) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #1 SMP Tue Mar 27 08:34:33 EDT 2007
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001feae000 end: 000000001ffae000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001ffae000 size: 0000000000052000 end: 0000000020000000 type: 2
[    0.000000] copy_e820_map() start: 00000000feda0000 size: 0000000000060000 end: 00000000fee00000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffae000 (usable)
[    0.000000]  BIOS-e820: 000000001ffae000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 130990) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130990
[    0.000000]   HighMem    130990 ->   130990
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130990
[    0.000000] On node 0 totalpages: 130990
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125903 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fdf00
[    0.000000] ACPI: RSDT (v001 DELL    CPi R   0x27d5061e ASL  0x00000061) @ 0x1fff0000
[    0.000000] ACPI: FADT (v001 DELL    CPi R   0x27d5061e ASL  0x00000061) @ 0x1fff0400
[    0.000000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:deda0000)
[    0.000000] Detected 1398.859 MHz processor.
[    9.619442] Built 1 zonelists.  Total pages: 129967
[    9.619447] Kernel command line: root=/dev/hda4 ro  vga=788 resume2=swap:/dev/hda5
[    9.619672] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    9.619680] mapped APIC to ffffd000 (0140b000)
[    9.619684] Enabling fast FPU save and restore... done.
[    9.619687] Enabling unmasked SIMD FPU exception support... done.
[    9.619696] Initializing CPU#0
[    9.619756] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    9.619858] Console: colour dummy device 80x25
[    9.620222] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    9.620538] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.636707] Memory: 510128k/523960k available (2096k kernel code, 13288k reserved, 1069k data, 316k init, 0k highmem)
[    9.636728] virtual kernel memory layout:
[    9.636729]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    9.636731]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    9.636733]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[    9.636734]     lowmem  : 0xc0000000 - 0xdffae000   ( 511 MB)
[    9.636736]       .init : 0xc041e000 - 0xc046d000   ( 316 kB)
[    9.636738]       .data : 0xc030c110 - 0xc04176d4   (1069 kB)
[    9.636739]       .text : 0xc0100000 - 0xc030c110   (2096 kB)
[    9.636763] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    9.715760] Calibrating delay using timer specific routine.. 2799.63 BogoMIPS (lpj=5599272)
[    9.715817] Security Framework v1.0.0 initialized
[    9.715827] SELinux:  Disabled at boot.
[    9.715850] Mount-cache hash table entries: 512
[    9.716008] CPU: After generic identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[    9.716021] CPU: L1 I cache: 32K, L1 D cache: 32K
[    9.716028] CPU: L2 cache: 1024K
[    9.716033] CPU: After all inits, caps: a7e9f9bf 00000000 00000000 00002040 00000180 00000000 00000000
[    9.716044] Compat vDSO mapped to ffffe000.
[    9.716059] Checking 'hlt' instruction... OK.
[    9.731862] SMP alternatives: switching to UP code
[    9.732062] ACPI: Core revision 20060707
[    9.738934]  tbxface-0107 [01] load_tables           : ACPI Tables successfully acquired
[    9.742944] Parsing all Control Methods:
[    9.743058] Table [DSDT](id 0005) - 436 Objects with 69 Devices 181 Methods 5 Regions
[    9.743068] ACPI Namespace successfully loaded at root c049b770
[    9.743076] ACPI: setting ELCR to 0200 (from 0800)
[    9.745172] evxfevnt-0089 [02] enable                : Transition to ACPI mode successful
[    9.745206] CPU0: Intel(R) Pentium(R) M processor 1400MHz stepping 05
[    9.745214] SMP motherboard not detected.
[    9.745219] Local APIC not detected. Using dummy APIC emulation.
[    9.745260] Brought up 1 CPUs
[    9.745323] Device driver platform lacks bus and class support for being resumed.
[    9.745587] Time: 23:55:10  Date: 02/29/107
[    9.745621] NET: Registered protocol family 16
[    9.745718] EISA bus registered
[    9.745725] ACPI: bus type pci registered
[    9.779299] PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=2
[    9.779304] PCI: Using configuration type 1
[    9.779309] Setting up standard PCI resources
[    9.780694] evgpeblk-0951 [04] ev_create_gpe_block   : GPE 00 to 1F [_GPE] 4 regs on int 0x9
[    9.781619] evgpeblk-1048 [03] ev_initialize_gpe_bloc: Found 7 Wake, Enabled 2 Runtime GPEs in this block
[    9.788654] Completing Region/Field/Buffer/Package initialization:......................................................
[    9.790646] Initialized 5/5 Regions 10/11 Fields 22/23 Buffers 17/26 Packages (445 nodes)
[    9.790656] Initializing Device/Processor/Thermal objects by executing _INI methods:...
[    9.806597] Executed 3 _INI methods requiring 0 _STA executions (examined 73 objects)
[    9.806617] ACPI: Interpreter enabled
[    9.806621] ACPI: Using PIC for interrupt routing
[    9.808011] PM: Adding info for acpi:acpi
[    9.809125] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.809139] PCI: Probing PCI hardware (bus 00)
[    9.809424] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    9.821606] Device driver pci0000:00 lacks bus and class support for being resumed.
[    9.821976] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    9.821983] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[    9.822148] Boot video device is 0000:01:00.0
[    9.822407] PCI: Transparent bridge - 0000:00:1e.0
[    9.822463] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[    9.822471] Please report the result to linux-kernel to fix this permanently
[    9.822496] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.824286] PM: Adding info for pci:0000:00:00.0
[    9.825308] PM: Adding info for pci:0000:00:01.0
[    9.826325] PM: Adding info for pci:0000:00:1d.0
[    9.827341] PM: Adding info for pci:0000:00:1d.1
[    9.828381] PM: Adding info for pci:0000:00:1d.2
[    9.829397] PM: Adding info for pci:0000:00:1d.7
[    9.830413] PM: Adding info for pci:0000:00:1e.0
[    9.831432] PM: Adding info for pci:0000:00:1f.0
[    9.832454] PM: Adding info for pci:0000:00:1f.1
[    9.833470] PM: Adding info for pci:0000:00:1f.5
[    9.833539] PM: Adding info for pci:0000:01:00.0
[    9.847692] PM: Adding info for pci:0000:02:00.0
[    9.862040] PM: Adding info for pci:0000:02:01.0
[    9.876012] PM: Adding info for pci:0000:02:01.1
[    9.889867] PM: Adding info for pci:0000:02:03.0
[    9.907811] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    9.908413] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    9.909007] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    9.909601] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[    9.910156] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    9.910757] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    9.912761] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    9.914183] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    9.939523] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.939537] pnp: PnP ACPI init
[    9.939550] Device driver pnp0 lacks bus and class support for being resumed.
[    9.951188] PM: Adding info for pnp:00:00
[    9.963350] PM: Adding info for pnp:00:01
[    9.963458] PM: Adding info for pnp:00:02
[    9.963566] PM: Adding info for pnp:00:03
[    9.963666] PM: Adding info for pnp:00:04
[    9.963771] PM: Adding info for pnp:00:05
[    9.963872] PM: Adding info for pnp:00:06
[    9.963975] PM: Adding info for pnp:00:07
[    9.964073] PM: Adding info for pnp:00:08
[    9.964186] PM: Adding info for pnp:00:09
[    9.964287] PM: Adding info for pnp:00:0a
[    9.978835] PM: Adding info for pnp:00:0b
[    9.999711] PM: Adding info for pnp:00:0c
[   10.014601] pnp: PnP ACPI: found 13 devices
[   10.014610] PnPBIOS: Disabled by ACPI PNP
[   10.014661] PCI: Using ACPI for IRQ routing
[   10.014667] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   10.032595] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   10.032602] pnp: 00:02: ioport range 0x800-0x805 could not be reserved
[   10.032609] pnp: 00:02: ioport range 0x808-0x80f could not be reserved
[   10.032619] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
[   10.032625] pnp: 00:03: ioport range 0x806-0x807 has been reserved
[   10.032631] pnp: 00:03: ioport range 0x810-0x85f could not be reserved
[   10.032637] pnp: 00:03: ioport range 0x860-0x87f has been reserved
[   10.032643] pnp: 00:03: ioport range 0x880-0x8bf has been reserved
[   10.032649] pnp: 00:03: ioport range 0x8c0-0x8df has been reserved
[   10.032659] pnp: 00:08: ioport range 0x900-0x97f has been reserved
[   10.032946] PCI: Bridge: 0000:00:01.0
[   10.032951]   IO window: c000-cfff
[   10.032958]   MEM window: fc000000-fdffffff
[   10.032964]   PREFETCH window: d0000000-dfffffff
[   10.032975] PCI: Bus 3, cardbus bridge: 0000:02:01.0
[   10.032981]   IO window: 0000d000-0000d0ff
[   10.032987]   IO window: 0000d400-0000d4ff
[   10.032994]   PREFETCH window: 30000000-33ffffff
[   10.033001]   MEM window: 38000000-3bffffff
[   10.033007] PCI: Bridge: 0000:00:1e.0
[   10.033012]   IO window: d000-efff
[   10.033020]   MEM window: f6000000-fbffffff
[   10.033027]   PREFETCH window: 30000000-33ffffff
[   10.033045] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   10.033058] PCI: Enabling device 0000:02:01.0 (0000 -> 0003)
[   10.033503] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   10.033510] PCI: setting IRQ 11 as level-triggered
[   10.033514] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   10.033558] NET: Registered protocol family 2
[   10.067829] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   10.067925] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   10.068052] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   10.068119] TCP: Hash tables configured (established 16384 bind 8192)
[   10.068126] TCP reno registered
[   10.079898] checking if image is initramfs... it is
[   10.614760] PM: Adding info for platform:pcspkr
[   10.615002] audit: initializing netlink socket (disabled)
[   10.615029] audit(1175212511.132:1): initialized
[   10.615196] VFS: Disk quotas dquot_6.5.1
[   10.615229] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.615302] io scheduler noop registered
[   10.615308] io scheduler anticipatory registered
[   10.615314] io scheduler deadline registered
[   10.615333] io scheduler cfq registered (default)
[   10.615678] Device driver pnp1 lacks bus and class support for being resumed.
[   10.615686] isapnp: Scanning for PnP cards...
[   10.968534] isapnp: No Plug & Play device found
[   11.006409] Real Time Clock Driver v1.12ac
[   11.006483] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   11.006510] PM: Adding info for platform:serial8250
[   11.006611] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   11.007396] PM: Removing info for No Bus:ttyS0
[   11.007494] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   11.007711] Device driver isa lacks bus and class support for being resumed.
[   11.008320] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   11.008546] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   11.008554] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   11.008756] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   11.008815] PM: Adding info for platform:i8042
[   11.014324] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.014335] serio: i8042 AUX port at 0x60,0x64 irq 12
[   11.014375] PM: Adding info for serio:serio0
[   11.014435] PM: Adding info for serio:serio1
[   11.014499] mice: PS/2 mouse device common for all mice
[   11.014577] PCI driver pci_eisa lacks driver specific resume support.
[   11.014590] PM: Adding info for platform:eisa.0
[   11.014623] EISA: Probing bus 0 at eisa.0
[   11.014653] EISA: Detected 0 cards.
[   11.044767] TCP cubic registered
[   11.044782] NET: Registered protocol family 1
[   11.044790] NET: Registered protocol family 8
[   11.044795] NET: Registered protocol family 20
[   11.044877] Using IPI No-Shortcut mode
[   11.044882] Suspend v2.2.9.10
[   11.044904] Suspend2 Userspace Storage Manager support registered.
[   11.044932] Suspend2 Userspace UI support registered.
[   11.044962] Suspend2 Compressor support registered.
[   11.044989] Suspend2 Encryptor support registered.
[   11.045017] Suspend2 Block I/O support registered.
[   11.045022] Suspend2 Swap Allocator support registered.
[   11.045050] Suspend2 File Allocator support registered.
[   11.045165] ACPI: (supports S0 S1 S3 S4 S5)
[   11.045239]   Magic number: 15:492:960
[   11.045260]   hash matches device ttyb1
[   11.046831] input: AT Translated Set 2 keyboard as /class/input/input0
[   11.047747] Time: tsc clocksource has been installed.
[   11.137274] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[   11.137290] ACPI: Processor [CPU0] (supports 8 throttling states)
[   11.143769] ACPI: Thermal Zone [THM] (63 C)
[   11.449697] PCI driver PCI_IDE lacks driver specific resume support.
[   11.451529] ICH4: IDE controller at PCI slot 0000:00:1f.1
[   11.451543] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   11.452103] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   11.452110] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   11.452128] ICH4: chipset revision 1
[   11.452132] ICH4: not 100% native mode: will probe irqs later
[   11.452146]     ide0: BM-DMA at 0xbfa0-0xbfa7, BIOS settings: hda:DMA, hdb:pio
[   11.452164]     ide1: BM-DMA at 0xbfa8-0xbfaf, BIOS settings: hdc:DMA, hdd:pio
[   11.452179] Probing IDE interface ide0...
[    1.844000] Time: acpi_pm clocksource has been installed.
[    2.076000] hda: IC25N060ATMR04-0, ATA DISK drive
[    2.076000] Device driver ide0 lacks bus and class support for being resumed.
[    2.748000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    2.748000] PM: Adding info for ide:0.0
[    2.748000] Probing IDE interface ide1...
[    3.484000] hdc: QSI CD-RW/DVD-ROM SBW-242, ATAPI CD/DVD-ROM drive
[    3.484000] Device driver ide1 lacks bus and class support for being resumed.
[    4.156000] ide1 at 0x170-0x177,0x376 on irq 15
[    4.156000] PM: Adding info for ide:1.0
[    4.156000] PCI driver PIIX_IDE lacks driver specific resume support.
[    4.160000] hda: max request size: 512KiB
[    4.188000] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
[    4.188000] hda: cache flushes supported
[    4.188000]  hda: hda1 hda2 < hda5 > hda4
[    4.256000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    4.256000] Uniform CD-ROM driver Revision: 3.20
[    4.600000] usbcore: registered new interface driver usbfs
[    4.600000] usbcore: registered new interface driver hub
[    4.600000] usbcore: registered new device driver usb
[    4.600000] USB Universal Host Controller Interface driver v3.0
[    4.600000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    4.600000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    4.600000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.604000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    4.604000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[    4.604000] PM: Adding info for usb:usb1
[    4.604000] Device driver usbdev1.1_ep00 lacks bus and class support for being resumed.
[    4.604000] usb usb1: configuration #1 chosen from 1 choice
[    4.604000] PM: Adding info for usb:1-0:1.0
[    4.604000] hub 1-0:1.0: USB hub found
[    4.604000] hub 1-0:1.0: 2 ports detected
[    4.668000] ieee1394: Initialized config rom entry `ip1394'
[    4.708000] Device driver usbdev1.1_ep81 lacks bus and class support for being resumed.
[    4.708000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    4.708000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    4.708000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.708000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    4.708000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[    4.708000] PM: Adding info for usb:usb2
[    4.708000] Device driver usbdev2.1_ep00 lacks bus and class support for being resumed.
[    4.708000] usb usb2: configuration #1 chosen from 1 choice
[    4.708000] PM: Adding info for usb:2-0:1.0
[    4.708000] hub 2-0:1.0: USB hub found
[    4.708000] hub 2-0:1.0: 2 ports detected
[    4.812000] Device driver usbdev2.1_ep81 lacks bus and class support for being resumed.
[    4.812000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    4.812000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    4.812000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    4.812000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.812000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    4.812000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[    4.812000] PM: Adding info for usb:usb3
[    4.812000] Device driver usbdev3.1_ep00 lacks bus and class support for being resumed.
[    4.812000] usb usb3: configuration #1 chosen from 1 choice
[    4.812000] PM: Adding info for usb:3-0:1.0
[    4.812000] hub 3-0:1.0: USB hub found
[    4.812000] hub 3-0:1.0: 2 ports detected
[    4.916000] Device driver usbdev3.1_ep81 lacks bus and class support for being resumed.
[    4.916000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    4.916000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[    4.916000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.916000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.916000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    4.916000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.916000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.916000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
[    4.920000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.920000] PM: Adding info for usb:usb4
[    4.920000] Device driver usbdev4.1_ep00 lacks bus and class support for being resumed.
[    4.920000] usb usb4: configuration #1 chosen from 1 choice
[    4.920000] PM: Adding info for usb:4-0:1.0
[    4.920000] hub 4-0:1.0: USB hub found
[    4.920000] hub 4-0:1.0: 6 ports detected
[    5.024000] Device driver usbdev4.1_ep81 lacks bus and class support for being resumed.
[    5.024000] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    5.024000] PM: Adding info for ieee1394:fw-host0
[    5.024000] Device driver fw-host0 lacks bus and class support for being resumed.
[    5.084000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[faffd800-faffdfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    5.196000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.196000] EXT3-fs: write access will be enabled during recovery.
[    5.344000] usb 4-6: new high speed USB device using ehci_hcd and address 2
[    5.476000] PM: Adding info for usb:4-6
[    5.476000] Device driver usbdev4.2_ep00 lacks bus and class support for being resumed.
[    5.476000] usb 4-6: configuration #1 chosen from 1 choice
[    5.476000] PM: Adding info for usb:4-6:1.0
[    5.476000] hub 4-6:1.0: USB hub found
[    5.476000] hub 4-6:1.0: 4 ports detected
[    5.476000] Device driver usbdev4.2_ep81 lacks bus and class support for being resumed.
[    5.580000] PM: Removing info for No Bus:usbdev4.2_ep81
[    5.780000] usb 4-6.1: new low speed USB device using ehci_hcd and address 3
[    5.880000] PM: Adding info for usb:4-6.1
[    5.880000] Device driver usbdev4.3_ep00 lacks bus and class support for being resumed.
[    5.880000] usb 4-6.1: configuration #1 chosen from 1 choice
[    5.880000] PM: Adding info for usb:4-6.1:1.0
[    5.880000] Device driver usbdev4.3_ep81 lacks bus and class support for being resumed.
[    6.080000] usb 4-6.2: new full speed USB device using ehci_hcd and address 4
[    6.172000] PM: Adding info for usb:4-6.2
[    6.172000] Device driver usbdev4.4_ep00 lacks bus and class support for being resumed.
[    6.172000] usb 4-6.2: configuration #1 chosen from 1 choice
[    6.172000] PM: Adding info for usb:4-6.2:1.0
[    6.172000] hub 4-6.2:1.0: USB hub found
[    6.172000] hub 4-6.2:1.0: 3 ports detected
[    6.276000] Device driver usbdev4.4_ep81 lacks bus and class support for being resumed.
[    6.356000] PM: Adding info for ieee1394:464fc00009068c81
[    6.356000] Device driver 464fc00009068c81 lacks bus and class support for being resumed.
[    6.356000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[464fc00009068c81]
[    6.356000] PM: Adding info for ieee1394:464fc00009068c81-0
[    6.356000] Device driver 464fc00009068c81-0 lacks bus and class support for being resumed.
[    6.476000] usb 4-6.3: new low speed USB device using ehci_hcd and address 5
[    6.572000] PM: Adding info for usb:4-6.3
[    6.572000] Device driver usbdev4.5_ep00 lacks bus and class support for being resumed.
[    6.572000] usb 4-6.3: configuration #1 chosen from 1 choice
[    6.572000] PM: Adding info for usb:4-6.3:1.0
[    6.572000] Device driver usbdev4.5_ep81 lacks bus and class support for being resumed.
[    6.776000] usb 4-6.2.1: new full speed USB device using ehci_hcd and address 6
[    6.868000] PM: Adding info for usb:4-6.2.1
[    6.868000] Device driver usbdev4.6_ep00 lacks bus and class support for being resumed.
[    6.868000] usb 4-6.2.1: configuration #1 chosen from 1 choice
[    6.868000] PM: Adding info for usb:4-6.2.1:1.0
[    6.868000] Device driver usbdev4.6_ep81 lacks bus and class support for being resumed.
[    6.868000] PM: Adding info for usb:4-6.2.1:1.1
[    6.868000] Device driver usbdev4.6_ep82 lacks bus and class support for being resumed.
[    6.868000] usbcore: registered new interface driver hiddev
[    6.872000] input: Kensington Kensington PocketMouse Pro as /class/input/input1
[    6.872000] input: USB HID v1.00 Mouse [Kensington Kensington PocketMouse Pro] on usb-0000:00:1d.7-6.3
[    6.872000] input: Mitsumi Electric Apple Extended USB Keyboard as /class/input/input2
[    6.872000] input: USB HID v1.10 Keyboard [Mitsumi Electric Apple Extended USB Keyboard] on usb-0000:00:1d.7-6.2.1
[    6.872000] input: Mitsumi Electric Apple Extended USB Keyboard as /class/input/input3
[    6.872000] input: USB HID v1.10 Device [Mitsumi Electric Apple Extended USB Keyboard] on usb-0000:00:1d.7-6.2.1
[    6.872000] usbcore: registered new interface driver usbhid
[    6.872000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    7.484000] kjournald starting.  Commit interval 5 seconds
[    7.484000] EXT3-fs: hda4: orphan cleanup on readonly fs
[    7.484000] ext3_orphan_cleanup: deleting unreferenced inode 227214
[    7.484000] ext3_orphan_cleanup: deleting unreferenced inode 227217
[    7.484000] EXT3-fs: hda4: 2 orphan inodes deleted
[    7.484000] EXT3-fs: recovery complete.
[    7.512000] EXT3-fs: mounted filesystem with ordered data mode.
[    8.988000] PM: Removing info for No Bus:vcs2
[    8.988000] PM: Removing info for No Bus:vcsa2
[    8.988000] PM: Removing info for No Bus:vcs3
[    8.988000] PM: Removing info for No Bus:vcsa3
[    8.988000] PM: Removing info for No Bus:vcs4
[    8.988000] PM: Removing info for No Bus:vcsa4
[    8.992000] PM: Removing info for No Bus:vcs5
[    8.992000] PM: Removing info for No Bus:vcsa5
[    8.992000] PM: Removing info for No Bus:vcs6
[    8.992000] PM: Removing info for No Bus:vcsa6
[   12.688000] b44.c:v1.01 (Jun 16, 2006)
[   12.688000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   12.692000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:0d:56:b2:3a:cc
[   12.920000] parport: PnPBIOS parport detected.
[   12.920000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   13.020000] PCI driver parport_pc lacks driver specific resume support.
[   13.212000] input: PC Speaker as /class/input/input4
[   13.240000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.288000] PCI driver shpchp lacks driver specific resume support.
[   13.288000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.344000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:016a]
[   13.344000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   13.344000] Yenta: Routing CardBus interrupts to PCI
[   13.344000] Yenta TI: socket 0000:02:01.0, mfunc 0x012c1202, devctl 0x64
[   13.364000] ieee80211_crypt: registered algorithm 'NULL'
[   13.368000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   13.368000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   13.460000] intel_rng: FWH not detected
[   13.564000] Linux agpgart interface v0.101 (c) Dave Jones
[   13.576000] Yenta: ISA IRQ mask 0x0478, PCI irq 11
[   13.576000] Socket status: 30000020
[   13.576000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   13.576000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   13.576000] cs: IO port probe 0xd000-0xefff: clean.
[   13.576000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[   13.576000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   13.580000] agpgart: Detected an Intel 855PM Chipset.
[   13.588000] agpgart: AGP aperture is 128M @ 0xe0000000
[   13.612000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   13.612000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   13.612000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[   13.612000] PCI: setting IRQ 5 as level-triggered
[   13.612000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   13.612000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   13.612000] Device driver 0000:02:03.0 lacks bus and class support for being resumed.
[   13.772000] input: PS/2 Mouse as /class/input/input5
[   13.796000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input6
[   14.156000] input: eGalax Inc. as /class/input/input7
[   14.156000] usbcore: registered new interface driver usbtouchscreen
[   14.212000] pccard: CardBus card inserted into slot 0
[   14.212000] PM: Adding info for pci:0000:03:00.0
[   14.360000] PM: Removing info for No Bus:0000:02:03.0
[   14.360000] ipw2100: eth1: Firmware 'ipw2100-1.3.fw' not available or load failed.
[   14.360000] ipw2100: eth1: ipw2100_get_firmware failed: -2
[   14.360000] ipw2100: eth1: Failed to power on the adapter.
[   14.360000] ipw2100: eth1: Failed to start the firmware.
[   14.360000] ipw2100Error calling register_netdev.
[   14.360000] ACPI: PCI interrupt for device 0000:02:03.0 disabled
[   14.360000] ipw2100: probe of 0000:02:03.0 failed with error -5
[   14.360000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   14.360000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   15.008000] cs: IO port probe 0x100-0x3af: clean.
[   15.008000] cs: IO port probe 0x3e0-0x4ff: clean.
[   15.008000] cs: IO port probe 0x820-0x8ff: clean.
[   15.008000] cs: IO port probe 0xc00-0xcf7: clean.
[   15.008000] cs: IO port probe 0xa00-0xaff: clean.
[   15.180000] intel8x0_measure_ac97_clock: measured 55447 usecs
[   15.180000] intel8x0: clocking to 48000
[   15.180000] PM: Adding info for ac97:0-0:STAC9750,51
[   15.428000] nvidia: module license 'NVIDIA' taints kernel.
[   15.684000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   15.684000] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9746  Fri Dec 15 09:54:45 PST 2006
[   15.864000] Linux video capture interface: v2.00
[   16.064000] b44: eth0: Link is up at 100 Mbps, full duplex.
[   16.064000] b44: eth0: Flow control is off for TX and off for RX.
[   16.076000] saa7130/34: v4l2 driver version 0.2.14 loaded
[   16.112000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[   16.112000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   16.112000] saa7134[0]: found at 0000:03:00.0, rev: 1, irq: 11, latency: 0, mmio: 0x38000000
[   16.112000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   16.112000] saa7134[0]: subsystem: 1131:2004, board: Typhoon TV+Radio 90031 [card=13,insmod option]
[   16.112000] saa7134[0]: board init: gpio is 40000
[   16.216000] Device driver i2c-0 lacks bus and class support for being resumed.
[   16.248000] saa7134[0]: i2c eeprom 00: 31 11 04 20 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   16.248000] saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   16.248000] saa7134[0]: i2c eeprom 20: 01 40 01 02 02 00 01 03 08 ff 00 b0 ff ff ff ff
[   16.248000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.248000] saa7134[0]: i2c eeprom 40: ff 22 00 c2 96 ff 02 30 15 ff ff ff ff ff ff ff
[   16.248000] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.248000] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.248000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.352000] tuner 0-004b: chip found @ 0x96 (saa7134[0])
[   16.352000] PM: Adding info for i2c:0-004b
[   16.400000] tuner 0-004b: setting tuner address to 61
[   16.440000] tuner 0-004b: type set to tda8290+75a
[   16.552000] tuner 0-004b: setting tuner address to 61
[   16.592000] tuner 0-004b: type set to tda8290+75a
[   16.656000] saa7134[0]: registered device video0 [v4l2]
[   16.656000] saa7134[0]: registered device vbi0
[   16.656000] saa7134[0]: registered device radio0
[   16.656000] PCI driver saa7134 lacks driver specific resume support.
[   16.692000] saa7134 ALSA driver for DMA sound loaded
[   16.692000] saa7134[0]/alsa: saa7134[0] at 0x38000000 irq 11 registered as card -1
[   17.016000] lp0: using parport0 (interrupt-driven).
[   17.104000] SCSI subsystem initialized
[   17.308000] Unable to find swap-space signature
[   17.448000] EXT3 FS on hda4, internal journal
[   17.888000] kjournald starting.  Commit interval 5 seconds
[   17.888000] EXT3 FS on hda1, internal journal
[   17.888000] EXT3-fs: mounted filesystem with ordered data mode.
[   17.940000] Unable to find swap-space signature
[   19.848000] NET: Registered protocol family 17
[   23.644000] PM: Removing info for No Bus:vcs2
[   23.644000] PM: Removing info for No Bus:vcsa2
[   23.652000] PM: Removing info for No Bus:vcs2
[   23.656000] PM: Removing info for No Bus:vcsa2
[   23.656000] PM: Removing info for No Bus:vcs3
[   23.656000] PM: Removing info for No Bus:vcsa3
[   23.664000] PM: Removing info for No Bus:vcs3
[   23.664000] PM: Removing info for No Bus:vcsa3
[   23.668000] PM: Removing info for No Bus:vcs4
[   23.668000] PM: Removing info for No Bus:vcsa4
[   23.672000] PM: Removing info for No Bus:vcs4
[   23.672000] PM: Removing info for No Bus:vcsa4
[   23.676000] PM: Removing info for No Bus:vcs5
[   23.676000] PM: Removing info for No Bus:vcsa5
[   23.684000] PM: Removing info for No Bus:vcs5
[   23.684000] PM: Removing info for No Bus:vcsa5
[   23.684000] PM: Removing info for No Bus:vcs6
[   23.688000] PM: Removing info for No Bus:vcsa6
[   23.692000] PM: Removing info for No Bus:vcs6
[   23.692000] PM: Removing info for No Bus:vcsa6
[   23.700000] PM: Removing info for No Bus:vcs2
[   23.700000] PM: Removing info for No Bus:vcsa2
[   23.704000] PM: Removing info for No Bus:vcs3
[   23.704000] PM: Removing info for No Bus:vcsa3
[   23.708000] PM: Removing info for No Bus:vcs4
[   23.708000] PM: Removing info for No Bus:vcsa4
[   23.712000] PM: Removing info for No Bus:vcs5
[   23.712000] PM: Removing info for No Bus:vcsa5
[   23.716000] PM: Removing info for No Bus:vcs6
[   23.716000] PM: Removing info for No Bus:vcsa6
[   25.156000] ACPI: AC Adapter [AC] (on-line)
[   25.508000] ACPI: Battery Slot [BAT0] (battery present)
[   25.508000] ACPI: Battery Slot [BAT1] (battery absent)
[   25.600000] input: Lid Switch as /class/input/input8
[   25.628000] ACPI: Lid Switch [LID]
[   25.700000] input: Power Button (CM) as /class/input/input9
[   25.728000] ACPI: Power Button (CM) [PBTN]
[   25.792000] input: Sleep Button (CM) as /class/input/input10
[   25.792000] ACPI: Sleep Button (CM) [SBTN]
[   25.824000] Using specific hotkey driver
[   25.872000] PM: Adding info for platform:dock.0
[   25.888000] ACPI: ACPI Dock Station Driver 
[   25.932000] ibm_acpi: ec object not found
[   26.004000] toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
[   26.024000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   27.096000] apm: BIOS not found.
[   33.292000] NVRM: not using NVAGP, an AGPGART backend is loaded!
[   34.220000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 1:00.0] forgot to specify physical device; fix it!
[   34.220000] Device driver i2c-1 lacks bus and class support for being resumed.
[   34.220000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 1:00.0] forgot to specify physical device; fix it!
[   34.220000] Device driver i2c-2 lacks bus and class support for being resumed.
[   34.220000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 1:00.0] forgot to specify physical device; fix it!
[   34.224000] Device driver i2c-3 lacks bus and class support for being resumed.
```

---

### Post by Nigel_C on 2007-03-29
Thanks. If you look particularly for Suspend2 messages, you'll see that the various components of Suspend2 get registered, but the code to check whether to resume never gets run. It will output lines that look like this:

Suspend2: SwapAllocator: Signature found.
Suspend2: Resuming enabled.
Suspend2: Normal swapspace found.

To get those lines, you must have the echo > /sys/power/suspend2/do_resume line I mentioned previously. The fact that they're missing indicates that your initrd/ramfs needs updating to do this. I think the particular part of the Howto that you mentioned which you need to recheck is "/etc/mkinitramfs/scripts/local-premount/suspend2". Perhaps you missed the note below that, where it says this and the previous scripts need to be given execute permissions?

Regards,

Nigel

---

### Post by shotgunefx on 2007-03-29
> **Nigel_C said:**
> Thanks. If you look particularly for Suspend2 messages, you'll see that the various components of Suspend2 get registered, but the code to check whether to resume never gets run. It will output lines that look like this:

Suspend2: SwapAllocator: Signature found.
Suspend2: Resuming enabled.
Suspend2: Normal swapspace found.

To get those lines, you must have the echo > /sys/power/suspend2/do_resume line I mentioned previously. The fact that they're missing indicates that your initrd/ramfs needs updating to do this. I think the particular part of the Howto that you mentioned which you need to recheck is "/etc/mkinitramfs/scripts/local-premount/suspend2". Perhaps you missed the note below that, where it says this and the previous scripts need to be given execute permissions?

Regards,

Nigel
Hi Nigel,

I made a mistake and created suspend2 in scripts instead of scripts/local-premount :( 

Anyway, fixed that but  still losing the swap. Also looks like I'm getting an exception

```

[   11.026181] Suspend v2.2.9.10
[   11.026204] Suspend2 Userspace Storage Manager support registered.
[   11.026233] Suspend2 Userspace UI support registered.
[   11.026263] Suspend2 Compressor support registered.
[   11.026305] Suspend2 Encryptor support registered.
[   11.026334] Suspend2 Block I/O support registered.
[   11.026339] Suspend2 Swap Allocator support registered.
[   11.026367] Suspend2 File Allocator support registered.
[    5.188000] Suspend2: SwapAllocator: Signature found.
[    5.188000] Suspend2: Resuming enabled.
[    5.220000] suspend_userui: program not configured. suspend_userui disabled.
[    5.320000] usb 4-6: new high speed USB device using ehci_hcd and address 2
[    5.452000] PM: Adding info for usb:4-6
[    5.452000] Device driver usbdev4.2_ep00 lacks bus and class support for being resumed.
[    5.452000] usb 4-6: configuration #1 chosen from 1 choice
[    5.452000] PM: Adding info for usb:4-6:1.0
[    5.452000] hub 4-6:1.0: USB hub found
[    5.452000] hub 4-6:1.0: 4 ports detected
[    5.452000] Device driver usbdev4.2_ep81 lacks bus and class support for being resumed.
[    5.756000] usb 4-6.1: new low speed USB device using ehci_hcd and address 3
[    5.872000] Reading kernel & process data...
[    5.896000] PM: Adding info for usb:4-6.1
[    5.896000] Device driver usbdev4.3_ep00 lacks bus and class support for being resumed.
[    5.896000] usb 4-6.1: configuration #1 chosen from 1 choice
[    5.900000] PM: Adding info for usb:4-6.1:1.0
[    5.900000] Device driver usbdev4.3_ep81 lacks bus and class support for being resumed.
[    5.932000] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000006
[    5.932000]  printing eip:
[    5.932000] c014ea39
[    5.932000] *pde = 00000000
[    5.932000] Oops: 0000 [#1]
[    5.932000] SMP 
[    5.932000] Modules linked in: ohci1394 ieee1394 ehci_hcd uhci_hcd usbcore ide_generic ide_cd cdrom ide_disk piix generic thermal processor fan
[    5.932000] CPU:    0
[    5.932000] EIP:    0060:[<c014ea39>]    Not tainted VLI
[    5.932000] EFLAGS: 00010202   (2.6.20s2newsuspend2 #1)
[    5.932000] EIP is at suspend_compress_read_chunk+0xb9/0x160
[    5.932000] eax: fffffffe   ebx: fffffffe   ecx: 000001a5   edx: deec6000
[    5.932000] esi: dec5e1a5   edi: deec61a5   ebp: c1405de4   esp: deaa1df0
[    5.932000] ds: 007b   es: 007b   ss: 0068
[    5.932000] Process exe (pid: 2027, ti=deaa0000 task=deca3560 task.ti=deaa0000)
[    5.932000] Stack: dec5e000 deaa1e08 c03cee94 00020020 deaa1e5c c13d8bc0 00001000 000001a5 
[    5.932000]        c014e980 00000000 c046bd58 00002ac4 c0148b97 00000000 00000044 c03ccd20 
[    5.932000]        0000000f c01e1f71 00000000 c03ccc60 c13d8bc0 00000000 c046bd58 00002ac4 
[    5.932000] Call Trace:
[    5.932000]  [<c014e980>] suspend_compress_read_chunk+0x0/0x160
[    5.932000]  [<c0148b97>] worker_rw_loop+0x3c7/0x630
[    5.932000]  [<c01e1f71>] crypto_alg_mod_lookup+0x1e1/0x260
[    5.932000]  [<c01f31d2>] __next_cpu+0x12/0x20
[    5.932000]  [<c0148e63>] start_other_threads+0x63/0x90
[    5.932000]  [<c0149064>] do_rw_loop+0x1d4/0x2c0
[    5.932000]  [<c014fdec>] suspend_rw_init+0x2c/0x70
[    5.932000]  [<c01486e5>] rw_init_modules+0x65/0x150
[    5.932000]  [<c0149260>] read_pageset+0x110/0x180
[    5.932000]  [<c0150340>] suspend_rw_header_chunk+0x0/0x80
[    5.932000]  [<c0149fd4>] read_pageset1+0x6b4/0x720
[    5.932000]  [<c0140000>] sys_lchown16+0x30/0x50
[    5.932000]  [<c014786d>] do_load_atomic_copy+0x2d/0xb0
[    5.932000]  [<c0147f2a>] __suspend_try_resume+0x4a/0x70
[    5.932000]  [<c0146ea1>] suspend2_attr_store+0x61/0x210
[    5.932000]  [<c01be58f>] sysfs_write_file+0x9f/0x100
[    5.932000]  [<c017e45e>] vfs_write+0xbe/0x190
[    5.932000]  [<c01be4f0>] sysfs_write_file+0x0/0x100
[    5.932000]  [<c017ebe1>] sys_write+0x41/0x70
[    5.932000]  [<c0103170>] syscall_call+0x7/0xb
[    5.932000]  [<c0300033>] sigd_attach+0x23/0x50
[    5.932000]  =======================
[    5.932000] Code: 24 1c 89 d6 89 c1 c1 e9 02 f3 a5 89 c1 83 e1 03 74 02 f3 a4 8b 5d 04 8d 44 24 18 89 44 24 04 8b 4c 24 1c 89 14 24 8b 55 00 89 d8 <ff> 53 08 85 c0 89 c3 75 74 8b 44 24 18 3d 00 10 00 00 74 2f 89 
[    5.932000] EIP: [<c014ea39>] suspend_compress_read_chunk+0xb9/0x160 SS:ESP 0068:deaa1df0
[    5.932000]  <6>EXT3-fs: INFO: recovery required on readonly filesystem.
[    6.020000] EXT3-fs: write access will be enabled during recovery.

```

Don't know if suspend_userui being disabled could cause this?

Again, much appreciate the help. This is a carpc, so anything I can do to speed up resuming is hugely beneficial.

---

### Post by Nigel_C on 2007-03-29
Hi again.

That looks like a genuine bug that I need to look at. Do you have LZF configured as the compressor? Assuming you do, is it compiled in or built as a module? If it's modular, it will need to be included in the initramfs and modprobe'd prior to the echo > do_resume. A simpler solution is to compile it in to the kernel.

Nigel

---

### Post by shotgunefx on 2007-03-29
> **Nigel_C said:**
> Hi again.

That looks like a genuine bug that I need to look at. Do you have LZF configured as the compressor? Assuming you do, is it compiled in or built as a module? If it's modular, it will need to be included in the initramfs and modprobe'd prior to the echo > do_resume. A simpler solution is to compile it in to the kernel.

Nigel

Hi Nigel, 

Good catch. I added lzf to the modules list and modified the suspend2 script to insert it before the do_resume and it's working! (I'll probably recompile with it included in the near future).

I get to playing music in 35 seconds (including bios post, 1 or 2 seconds for the grub menu). A 10 second improvement from vanilla suspend and everything seems to be working ok (video/audio/etc). I'll have to see now what I can do to speed it up.

I much appreciate the help. I never would have figured this out.

Thanks,
-Lee

---

### Post by Nigel_C on 2007-04-10
> **shotgunefx said:**
> Good catch. I added lzf to the modules list and modified the suspend2 script to insert it before the do_resume and it's working! (I'll probably recompile with it included in the near future).

I get to playing music in 35 seconds (including bios post, 1 or 2 seconds for the grub menu). A 10 second improvement from vanilla suspend and everything seems to be working ok (video/audio/etc). I'll have to see now what I can do to speed it up.

I much appreciate the help. I never would have figured this out.

You're welcome.

I found the bug and will have it working right in the next release.

Regarding speed, if you're using LZF already, that will account for a good part of the speed improvement. The other thing you could try is setting the image_size_limit variable. Putting it to -2 will tell Suspend2 to drop caches; you can also set it to a positive value, and Suspend2 will ask the vm to free memory until that image size is reached (but not fail if the VM can't free enough memory). Freeing memory may make the computer a little slower post-resume (it will have to read from disk things that would have already been in memory).

Regards,

Nigel

---

