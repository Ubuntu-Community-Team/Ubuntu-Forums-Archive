---
title: "Nvidia card not being detected in Ubuntu 20.04"
date: 2020-05-12
forum: Hardware
---

### Post by collin80 on 2020-05-12
I have an Acer Nitro 5 laptop with a 9300H i5 processor, intel 630 graphics, and an nVidia 1650 graphics adapter as well. Prior to Ubuntu 20.04 it all worked fine. On both 18.04 and 19.10 I could switch between the two GPUs and both worked fine. Now I find that the nVidia card is not detected by the nvidia driver nor does it even show up with lspci or lshw. I have Windows installed to dual boot and the nVidia card still works perfectly well in Windows and is in fact detected. I had been running with secure boot enabled. I signed the nvidia drivers toward this purpose. It worked fine previously. But, I have since tried turning secure boot off. It doesn't help. I tried the 5.6 kernel available in the repo. It doesn't help either. Any way I go lspci does not even show the nvidia card at all even though it's installed properly and does in fact enumerate on the bus when I use WIndows. This seems to suggest that something is broken in Ubuntu 20.04 since it didn't start until then. I'm at a loss for how a working system suddenly quits listing perfectly working hardware in the device list. It's there, it works, I promise. What am I missing? Does anyone know what could have happened? I'm seeing another report of someone who has the exact same issue.

The complete lspci:
```
00:00.0 Host bridge: Intel Corporation 8th Gen Core 4-core Processor Host Bridge/DRAM Registers [Coffee Lake H] (rev 07)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 630 (Mobile)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
00:12.0 Signal processing controller: Intel Corporation Cannon Lake PCH Thermal Controller (rev 10)
00:14.0 USB controller: Intel Corporation Cannon Lake PCH USB 3.1 xHCI Host Controller (rev 10)
00:14.2 RAM memory: Intel Corporation Cannon Lake PCH Shared SRAM (rev 10)
00:14.3 Network controller: Intel Corporation Wireless-AC 9560 [Jefferson Peak] (rev 10)
00:15.0 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH Serial IO I2C Controller #0 (rev 10)
00:15.1 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH Serial IO I2C Controller #1 (rev 10)
00:16.0 Communication controller: Intel Corporation Cannon Lake PCH HECI Controller (rev 10)
00:17.0 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 10)
00:1d.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #14 (rev f0)
00:1e.0 Communication controller: Intel Corporation Cannon Lake PCH Serial IO UART Host Controller (rev 10)
00:1f.0 ISA bridge: Intel Corporation HM470 Chipset LPC/eSPI Controller (rev 10)
00:1f.3 Audio device: Intel Corporation Cannon Lake PCH cAVS (rev 10)
00:1f.4 SMBus: Intel Corporation Cannon Lake PCH SMBus Controller (rev 10)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH SPI Controller (rev 10)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 25)

uname -a:
Linux <MyMachineName> 5.4.0-29-generic #33-Ubuntu SMP Wed Apr 29 14:32:27 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

dmesg | grep nvidia
[    2.845986] nvidia: loading out-of-tree module taints kernel.
[    2.845992] nvidia: module license 'NVIDIA' taints kernel.
[    2.857147] nvidia-nvlink: Nvlink Core is being initialized, major device number 235
[    2.859762] nvidia-nvlink: Unregistered the Nvlink Core, major device number 235
[    3.338999] nvidia-nvlink: Nvlink Core is being initialized, major device number 235
[    3.339269] nvidia-nvlink: Unregistered the Nvlink Core, major device number 235

dmesg | grep NV
[    0.000000] BIOS-e820: [mem 0x000000008959e000-0x0000000089c8dfff] ACPI NVS
[    0.000000] reserve setup_data: [mem 0x000000008959e000-0x0000000089c8dfff] ACPI NVS
[    0.119814] PM: Registering ACPI NVS region [mem 0x8959e000-0x89c8dfff] (7274496 bytes)
[    0.122919] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.905459] ahci 0000:00:17.0: Found 1 remapped NVMe devices.
[    2.845992] nvidia: module license 'NVIDIA' taints kernel.
[    2.859669] NVRM: No NVIDIA graphics adapter found!
```
[    3.339200] NVRM: No NVIDIA graphics adapter found!

I noticed that vgaarb seems to find two graphics cards and the missing one is at 0000:01:00.0 so here's more output:

```
sudo journalctl -b | grep 01:00.0
May 12 17:51:59 <MachineName> kernel: pci 0000:01:00.0: [10de:1f91] type 00 class 0x030000
May 12 17:51:59 <MachineName> kernel: pci 0000:01:00.0: reg 0x10: [mem 0xa3000000-0xa3ffffff]
May 12 17:51:59 <MachineName> kernel: pci 0000:01:00.0: reg 0x14: [mem 0x90000000-0x9fffffff 64bit pref]
May 12 17:51:59 <MachineName> kernel: pci 0000:01:00.0: reg 0x1c: [mem 0xa0000000-0xa1ffffff 64bit pref]
May 12 17:51:59 <MachineName> kernel: pci 0000:01:00.0: reg 0x24: [io  0x4000-0x407f]
May 12 17:51:59 <MachineName> kernel: pci 0000:01:00.0: reg 0x30: [mem 0xfff80000-0xffffffff pref]
May 12 17:51:59 <MachineName> kernel: pci 0000:01:00.0: Enabling HDA controller
May 12 17:51:59 <MachineName> kernel: pci 0000:01:00.0: PME# supported from D0 D3hot
May 12 17:51:59 <MachineName> kernel: pci 0000:01:00.0: vgaarb: VGA device added: decodes=io+mem,owns=none,locks=none
May 12 17:51:59 <MachineName> kernel: pci 0000:01:00.0: vgaarb: bridge control possible
May 12 17:51:59 <MachineName> kernel: pci 0000:01:00.0: can't claim BAR 6 [mem 0xfff80000-0xffffffff pref]: no compatible bridge window
May 12 17:51:59 <MachineName> kernel: pci 0000:01:00.0: BAR 6: assigned [mem 0xa4080000-0xa40fffff pref]
May 12 17:51:59 <MachineName> kernel: pci 0000:01:00.1: D0 power state depends on 0000:01:00.0
```

---

### Post by collin80 on 2020-05-17
I still have no resolution of this problem. It's odd to me that the card shows up fine and works in Ubuntu 19.10 but suddenly quit showing up or working at all in Ubuntu 20.04. Any tips or other suggestions for how I could resolve this?

---

### Post by CelticWarrior on 2020-05-17
Please check UEFI settings before anything else. There's a possibility the UEFI settings were changed or even reset and the dGPU is disabled.

---

### Post by collin80 on 2020-05-17
It's not that. But, I found something interesting. If I use Advanced boot settings in the boot menu to instead boot an older kernel then lspci find the nvidia card. 5.4.0-28 will find the card but freezes when trying to bring up the GUI (I'm using Kubuntu so KDE). But I can bring up a text terminal and use lspci and it shows the nvidia card. Booting to the current 5.4.0-29 kernel does not find the nvidia card. So, it seems to be some sort of change in the linux kernel causing this. As referenced above, I tried the 5.6.0 kernel found in the repo and the nvidia card doesn't show up there either.

I wonder why 5.4.0-28 freezes though.

---

### Post by collin80 on 2020-05-17
An additional update, while messing around I managed to reinstall the nvidia drivers. This causes the -29 kernel to freeze exactly like the -28 kernel. So it seems that if I install the drivers the nvidia card shows up in lspci but then something is broken and the system can't start the GUI. If the drivers are not installed then the card does not show up in the lspci list. So, people who say that hardware shows up whether the drivers are installed or not lie like cheap rugs. Apparently that is just NOT true. At least some hardware requires kernel level support before it will enumerate. Perhaps this is due to the nvidia card being a secondary card that is supposed to be used on-demand. 

So, my problem has changed. Now it enumerates but crashes something and the GUI will not display. I have to uninstall the nvidia drivers to be able to boot back to the GUI. Some day I'll try to post the relevant logs from boot up in case that helps to figure this out.

---

### Post by collin80 on 2020-05-25
More updates. Loading Ubuntu 20.04 onto a USB thumb drive and booting works. It uses the Nouveau driver and I get video. The problem is that this laptop has a GTX1650 graphics card which is the absolute newest hardware platform. As such, Nouveau has basically no support for any sort of acceleration at all. But, the display works and the card enumerates on the bus. 

Here is what it looks like in dmesg when the nvidia 440 driver loads:

```
[    1.089529] nvidia: loading out-of-tree module taints kernel.
[    1.089535] nvidia: module license 'NVIDIA' taints kernel.
[    1.089535] Disabling lock debugging due to kernel taint
[    1.102749] input: SYNA7DB5:01 06CB:CD41 Mouse as /devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-2/i2c-SYNA7DB5:01/0018:06CB:CD41.0001/input/input5
[    1.102810] input: SYNA7DB5:01 06CB:CD41 Touchpad as /devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-2/i2c-SYNA7DB5:01/0018:06CB:CD41.0001/input/input6
[    1.102853] hid-generic 0018:06CB:CD41.0001: input,hidraw0: I2C HID v1.00 Mouse [SYNA7DB5:01 06CB:CD41] on i2c-SYNA7DB5:01
[    1.105075] checking generic (b0000000 7e9000) vs hw (b0000000 10000000)
[    1.105076] fb0: switching to inteldrmfb from EFI VGA
[    1.105119] i915 0000:00:02.0: vgaarb: deactivate vga console
[    1.106274] nvidia-nvlink: Nvlink Core is being initialized, major device number 238
[    1.106616] nvidia 0000:01:00.0: enabling device (0106 -> 0107)
[    1.106715] nvidia 0000:01:00.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=none:owns=none
[    1.115240] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.115241] [drm] Driver supports precise vblank timestamp query.
[    1.119939] [drm] Finished loading DMC firmware i915/kbl_dmc_ver1_04.bin (v1.4)
[    1.155454] usb 1-14: new full-speed USB device number 3 using xhci_hcd
[    1.155493] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  435.21  Sun Aug 25 08:17:57 CDT 2019
[    1.155963] [drm] Initialized i915 1.6.0 20190822 for 0000:00:02.0 on minor 0
[    1.161307] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[    1.161318] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[    1.161507] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input8
[    1.166132] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    1.166273] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input9
[    1.167365] fbcon: i915drmfb (fb0) is primary device
[    1.167366] fbcon: Deferring console take-over
[    1.167368] i915 0000:00:02.0: fb0: i915drmfb frame buffer device
[    1.179941] nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  435.21  Sun Aug 25 08:07:52 CDT 2019
[    1.181098] [drm] [nvidia-drm] [GPU ID 0x00000100] Loading driver
[    1.198459] ACPI Warning: \_SB.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20190816/nsarguments-59)
[    1.254231] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.258176] ata5.00: ATA-9: SanDisk Ultra II 480GB, X41100RL, max UDMA/133
[    1.258177] ata5.00: 937703088 sectors, multi 1: LBA48 NCQ (depth 32), AA
[    1.259791] ata5.00: configured for UDMA/133
[    1.259953] scsi 4:0:0:0: Direct-Access     ATA      SanDisk Ultra II 00RL PQ: 0 ANSI: 5
[    1.260207] sd 4:0:0:0: Attached scsi generic sg0 type 0
[    1.260513] sd 4:0:0:0: [sda] 937703088 512-byte logical blocks: (480 GB/447 GiB)
[    1.260557] sd 4:0:0:0: [sda] Write Protect is off
[    1.260558] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.260673] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.312242] usb 1-14: New USB device found, idVendor=8087, idProduct=0aaa, bcdDevice= 0.02
[    1.312243] usb 1-14: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.367017]  sda: sda1 sda2
[    1.367313] sd 4:0:0:0: [sda] Attached SCSI disk
[    1.527236] tsc: Refined TSC clocksource calibration: 2399.999 MHz
[    1.527239] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2298364cab5, max_idle_ns: 440795214892 ns
[    1.527396] clocksource: Switched to clocksource tsc
[    1.857657] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.857657] [drm] No driver support for vblank timestamp query.
[    1.857710] [drm] Initialized nvidia-drm 0.0.0 20160202 for 0000:01:00.0 on minor 1
```


Then there is a crash:

```
[    3.110358] ------------[ cut here ]------------
[    3.110525] WARNING: CPU: 2 PID: 588 at /var/lib/dkms/nvidia/435.21/build/nvidia/nv-pci.c:584 nv_pci_remove+0x357/0x380 [nvidia]
[    3.110526] Modules linked in: fjes(-) acpi_pad mac_hid acer_wireless nvidia_uvm(O) nf_log_ipv6 ip6t_REJECT nf_reject_ipv6 xt_hl ip6t_rt nf_log_ipv4 nf_log_common ipt_REJECT nf_reject_ipv4 xt_LOG xt_multiport xt_limit xt_addrtype xt_tcpudp sch_fq_codel xt_conntrack nf_conntrack nf_defrag_ipv6 nf_defrag_ipv4 libcrc32c parport_pc ip6table_filter ppdev ip6_tables iptable_filter lp bpfilter parport binder_linux ip_tables x_tables autofs4 nvidia_drm(PO) nvidia_modeset(PO) crct10dif_pclmul crc32_pclmul hid_generic ghash_clmulni_intel nvidia(PO) i915 i2c_algo_bit aesni_intel crypto_simd cryptd glue_helper drm_kms_helper syscopyarea sysfillrect sysimgblt i2c_hid fb_sys_fops ipmi_devintf hid ipmi_msghandler drm i2c_i801 intel_lpss_pci r8169 intel_lpss ahci idma64 realtek libahci virt_dma wmi video pinctrl_cannonlake pinctrl_intel
[    3.110553] CPU: 2 PID: 588 Comm: systemd-udevd Tainted: P           O      5.4.0-31-generic #35-Ubuntu
[    3.110553] Hardware name: Acer Nitro AN517-51/Superb_CFS, BIOS V1.01 03/06/2019
[    3.110713] RIP: 0010:nv_pci_remove+0x357/0x380 [nvidia]
[    3.110714] Code: 48 c7 c7 e0 01 d0 c1 e8 17 a6 ff ff e9 2d fe ff ff 41 8b 94 24 70 04 00 00 48 c7 c6 08 91 ca c1 bf 04 00 00 00 e8 d9 8a 00 00 <0f> 0b e8 d2 90 00 00 eb f9 4c 89 e6 4c 89 ef e8 65 18 75 00 e9 10
[    3.110715] RSP: 0018:ffffb3d100573d18 EFLAGS: 00010246
[    3.110716] RAX: 0000000000000044 RBX: ffff90d55b132000 RCX: 0000000000000000
[    3.110717] RDX: ffff90d55e2a7740 RSI: ffff90d55e2978c8 RDI: ffff90d55e2978c8
[    3.110717] RBP: ffffb3d100573d58 R08: ffff90d55e2978c8 R09: 0000000000000004
[    3.110718] R10: 0000000000000000 R11: 0000000000000001 R12: ffff90d547b1a000
[    3.110718] R13: ffff90d54b523000 R14: ffff90d55b132000 R15: ffff90d55a1377a0
[    3.110720] FS:  00007fbe01940880(0000) GS:ffff90d55e280000(0000) knlGS:0000000000000000
[    3.110720] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[    3.110721] CR2: 00007fbe01821c07 CR3: 000000044b4a0005 CR4: 00000000003606e0
[    3.110722] Call Trace:
[    3.110726]  pci_device_remove+0x3e/0xb0
[    3.110729]  device_release_driver_internal+0xf0/0x1d0
[    3.110730]  device_release_driver+0x12/0x20
[    3.110731]  pci_stop_bus_device+0x70/0xa0
[    3.110733]  pci_stop_and_remove_bus_device_locked+0x1b/0x30
[    3.110735]  remove_store+0x7b/0x90
[    3.110736]  dev_attr_store+0x17/0x30
[    3.110738]  sysfs_kf_write+0x3e/0x50
[    3.110739]  kernfs_fop_write+0xda/0x1b0
[    3.110741]  __vfs_write+0x1b/0x40
[    3.110742]  vfs_write+0xb9/0x1a0
[    3.110743]  ksys_write+0x67/0xe0
[    3.110745]  __x64_sys_write+0x1a/0x20
[    3.110747]  do_syscall_64+0x57/0x190
[    3.110749]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
[    3.110751] RIP: 0033:0x7fbe01eb6057
[    3.110752] Code: 64 89 02 48 c7 c0 ff ff ff ff eb bb 0f 1f 80 00 00 00 00 f3 0f 1e fa 64 8b 04 25 18 00 00 00 85 c0 75 10 b8 01 00 00 00 0f 05 <48> 3d 00 f0 ff ff 77 51 c3 48 83 ec 28 48 89 54 24 18 48 89 74 24
[    3.110753] RSP: 002b:00007ffdc3a37c28 EFLAGS: 00000246 ORIG_RAX: 0000000000000001
[    3.110754] RAX: ffffffffffffffda RBX: 0000000000000001 RCX: 00007fbe01eb6057
[    3.110755] RDX: 0000000000000001 RSI: 00007ffdc3a381d0 RDI: 0000000000000006
[    3.110755] RBP: 00007ffdc3a381d0 R08: 0000000000000001 R09: 0000000000000000
[    3.110756] R10: 0000000000000000 R11: 0000000000000246 R12: 0000000000000001
[    3.110756] R13: 000055eed3bcc5b0 R14: 0000000000000001 R15: 00007fbe01f918a0
[    3.110758] ---[ end trace 7495c417889fd792 ]---
```

Thereafter, some display related processes freeze and the kernel will ever 120 seconds warn me of this:

```
[  243.061232] INFO: task systemd-udevd:589 blocked for more than 120 seconds.
[  243.061792]       Tainted: P        W  O      5.4.0-31-generic #35-Ubuntu
[  243.062329] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  243.062867] systemd-udevd   D    0   589    539 0x00000324
[  243.062869] Call Trace:
[  243.062873]  __schedule+0x2e3/0x740
[  243.062874]  schedule+0x42/0xb0
[  243.062875]  schedule_preempt_disabled+0xe/0x10
[  243.062875]  __mutex_lock.isra.0+0x182/0x4f0
[  243.062877]  __mutex_lock_slowpath+0x13/0x20
[  243.062877]  mutex_lock+0x2e/0x40
[  243.062879]  pci_lock_rescan_remove+0x15/0x20
[  243.062881]  pci_stop_and_remove_bus_device_locked+0x13/0x30
[  243.062882]  remove_store+0x7b/0x90
[  243.062884]  dev_attr_store+0x17/0x30
[  243.062885]  sysfs_kf_write+0x3e/0x50
[  243.062886]  kernfs_fop_write+0xda/0x1b0
[  243.062887]  __vfs_write+0x1b/0x40
[  243.062888]  vfs_write+0xb9/0x1a0
[  243.062889]  ksys_write+0x67/0xe0
[  243.062890]  __x64_sys_write+0x1a/0x20
[  243.062892]  do_syscall_64+0x57/0x190
[  243.062893]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
[  243.062894] RIP: 0033:0x7fbe01eb6057
[  243.062897] Code: Bad RIP value.
[  243.062897] RSP: 002b:00007ffdc3a37c28 EFLAGS: 00000246 ORIG_RAX: 0000000000000001
[  243.062899] RAX: ffffffffffffffda RBX: 0000000000000001 RCX: 00007fbe01eb6057
[  243.062899] RDX: 0000000000000001 RSI: 00007ffdc3a381d0 RDI: 0000000000000006
[  243.062899] RBP: 00007ffdc3a381d0 R08: 0000000000000001 R09: 0000000000000000
[  243.062900] R10: 0000000000000000 R11: 0000000000000246 R12: 0000000000000001
[  243.062900] R13: 000055eed3bcc5b0 R14: 0000000000000001 R15: 00007fbe01f918a0
[  243.062906] INFO: task gpu-manager:937 blocked for more than 120 seconds.
[  243.063456]       Tainted: P        W  O      5.4.0-31-generic #35-Ubuntu
[  243.063991] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  243.064527] gpu-manager     D    0   937      1 0x00000000
[  243.064527] Call Trace:
[  243.064529]  __schedule+0x2e3/0x740
[  243.064529]  schedule+0x42/0xb0
[  243.064530]  schedule_preempt_disabled+0xe/0x10
[  243.064531]  __mutex_lock.isra.0+0x182/0x4f0
[  243.064532]  __mutex_lock_slowpath+0x13/0x20
[  243.064533]  mutex_lock+0x2e/0x40
[  243.064534]  control_store+0x28/0x90
[  243.064535]  dev_attr_store+0x17/0x30
[  243.064535]  sysfs_kf_write+0x3e/0x50
[  243.064536]  kernfs_fop_write+0xda/0x1b0
[  243.064537]  __vfs_write+0x1b/0x40
[  243.064538]  vfs_write+0xb9/0x1a0
[  243.064538]  ksys_write+0x67/0xe0
[  243.064539]  __x64_sys_write+0x1a/0x20
[  243.064540]  do_syscall_64+0x57/0x190
[  243.064541]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
[  243.064542] RIP: 0033:0x7fc77653d057
[  243.064543] Code: Bad RIP value.
[  243.064544] RSP: 002b:00007ffe3b6bdd78 EFLAGS: 00000246 ORIG_RAX: 0000000000000001
[  243.064544] RAX: ffffffffffffffda RBX: 0000000000000003 RCX: 00007fc77653d057
[  243.064545] RDX: 0000000000000003 RSI: 0000561223f080e0 RDI: 0000000000000005
[  243.064545] RBP: 0000561223f080e0 R08: 0000000000000001 R09: 00007fc776618220
[  243.064545] R10: 0000561223efe010 R11: 0000000000000246 R12: 0000000000000003
[  243.064546] R13: 0000561223f09e20 R14: 00007fc7766194a0 R15: 00007fc7766188a0
[  243.064548] INFO: task nvidia-persiste:954 blocked for more than 120 seconds.
[  243.065082]       Tainted: P        W  O      5.4.0-31-generic #35-Ubuntu
[  243.065647] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  243.066224] nvidia-persiste D    0   954      1 0x00000004
[  243.066225] Call Trace:
[  243.066226]  __schedule+0x2e3/0x740
[  243.066329]  ? os_get_current_tick+0x30/0x60 [nvidia]
[  243.066330]  schedule+0x42/0xb0
[  243.066331]  schedule_timeout+0x203/0x2f0
[  243.066440]  ? rm_ioctl+0x63/0xb0 [nvidia]
[  243.066441]  __down+0x82/0xd0
[  243.066442]  ? _cond_resched+0x19/0x30
[  243.066443]  down+0x47/0x60
[  243.066504]  nvidia_ioctl+0x63a/0x8a0 [nvidia]
[  243.066505]  ? get_max_files+0x20/0x20
[  243.066574]  nvidia_frontend_unlocked_ioctl+0x3b/0x50 [nvidia]
[  243.066575]  do_vfs_ioctl+0x407/0x670
[  243.066576]  ksys_ioctl+0x67/0x90
[  243.066577]  __x64_sys_ioctl+0x1a/0x20
[  243.066578]  do_syscall_64+0x57/0x190
[  243.066579]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
[  243.066580] RIP: 0033:0x7f30e546537b
[  243.066582] Code: Bad RIP value.
[  243.066582] RSP: 002b:00007fffc6ad80d8 EFLAGS: 00000246 ORIG_RAX: 0000000000000010
[  243.066583] RAX: ffffffffffffffda RBX: 00007f30e5335920 RCX: 00007f30e546537b
[  243.066583] RDX: 00007f30e5335920 RSI: 00000000ca0046c8 RDI: 0000000000000002
[  243.066584] RBP: 00007f30e53358a0 R08: 00007f30e5335920 R09: 0000000000000000
[  243.066584] R10: 00007f30e54ecac0 R11: 0000000000000246 R12: 00007fffc6ad832c
[  243.066584] R13: 0000000000000000 R14: 00007f30e5336340 R15: 00007f30e5335870
```

So, looks to me that the nvidia driver in the kernel is crashing for some reason. I'm not sure how to resolve it. But, that's where I'm at in this process.

---

### Post by slickymaster on 2020-05-26
_@collin80_:

Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting terminal output.

---

### Post by lediableboiteux on 2020-07-28
I think I may have a similar issue, I had a pause from gaming for some time (this spanned across one or more system upgrades, i.e. Ubuntu version) and now I couldn&#8217;t get Bumblebee to work (I have a laptop). I thought that maybe my card just doesn&#8217;t work with the default nvidia driver version in Ubuntu, but after some troubleshooting I discovered that lspci doesn&#8217;t even show my Optimus card (GeForce GTX 660M). Brushing through system logs led me to discover a similar &#8220;can't claim BAR&#8221; message. I can&#8217;t think about anything that may cause this on my end other than the fact that I added another SSD drive (mSATA) to my laptop on top of my main one, but for now I can&#8217;t afford to troubleshoot the issue by removing the disk. Any thoughts?

---

### Post by mastablasta on 2020-07-30
drivers are on 440 ?

what's this then?
```
[    3.110525] WARNING: CPU: 2 PID: 588 at /var/lib/dkms/nvidia/[COLOR=#ff0000]**435.21**[/COLOR]/build/nvidia/nv-pci.c:584 nv_pci_remove+0x357/0x380 [nvidia]
```

purge the old driver, install the new one.

@lediableboiteux
it is not the same issue - but also purge any old remaining driver, install the new one. your will likely be legacy (3.90 something).

use nvidia prime for switching if you have optimus laptop.

heh rather then optimise power usage of the GPU they just added another one. what a silly idea.

---

### Post by lediableboiteux on 2020-08-05
Thank you for your reply! Well, I have tried PRIME besides Bumblebee, and two or three different driver versions (I checked which version is recommended for my card on nvidia website). I also tried the MATE Optimus applet. The thing is, my card is not detected, so nvidia drivers and prime don&#8217;t work &#8212; my system seems to detect only the Intel card. And the detection does not depend on drivers being installed.

---

### Post by manuxuser on 2020-08-23
Hi,
same here with Dell G7 I7+GTX2060, no card detected. It was working on 18.04. Additionnaly, on dell latitude 7260 so only Intel HD graphics, big issues with second monitor wich is not recognize in parameters. So il y a bien quelque chose de pourri avec ce noyau ^^

---

