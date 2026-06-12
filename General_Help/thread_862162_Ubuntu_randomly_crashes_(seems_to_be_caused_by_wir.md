---
title: "Ubuntu randomly crashes (seems to be caused by wireless driver)"
date: 2008-07-17
forum: General Help
---

### Post by parabolee on 2008-07-17
I have a broadcom b43 wireless card in my Dell 6400 and installed the driver for it with NDISwrapper. And everything works perfectly.

However I have two major problems, and I am hoping someone can help me with them, please?

The first being that my OS randomly crashes on me. There does not seem to be anything obvious that causes it (from what i am doing) but I get this read out on screen when it happens :-

ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43 does not exist in /proc/modules

Yes it says it twice.

And my second major problem is that my system will sometimes not sleep correctly. As it goes to sleep it turns to a screen with lines down it and usually after a few seconds goes into sleep. But sometimes it gets to the screen with line (and a visible text prompt that I can type into) and stays there, it will not wake up or respond in anyway untill I force it to turn off.

Also last night it went to sleep fine and then in the morning it crashed right away after waking from sleep. This is the read out I got on the crash -

* Starting aroc(h)ronistic cron anacron                         (ok)
* Starting deferred execution scheduler atd                     (ok)
* Starting periodic command scheduler crond                     (ok)
* Enabling additional executable binary formats binfmt-support  (ok)
* Checking battery state...                                     (ok)
* Running local boot scripts (/etc/rc.local)

ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43 does not exist in /proc/modules

Also here is part of my log output for the sleep and then wake in the morning (let me know if I should post more after this) :-

Jul 16 22:48:44 lee-laptop-linux NetworkManager: <info>  Going to sleep. 
Jul 16 22:48:44 lee-laptop-linux dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 16529
Jul 16 22:48:44 lee-laptop-linux dhclient: killed old client process, removed PID file
Jul 16 22:48:44 lee-laptop-linux dhclient: DHCPRELEASE on wlan0 to 192.168.0.1 port 67
Jul 16 22:48:44 lee-laptop-linux avahi-daemon[5048]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jul 16 22:48:44 lee-laptop-linux avahi-daemon[5048]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.105.
Jul 16 22:48:44 lee-laptop-linux avahi-daemon[5048]: Withdrawing address record for fe80::21a:92ff:fec2:612c on wlan0.
Jul 16 22:48:44 lee-laptop-linux avahi-daemon[5048]: Withdrawing address record for 192.168.0.105 on wlan0.
Jul 16 22:48:44 lee-laptop-linux NetworkManager: <debug> [1216262924.910562] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_19_b9_68_2e_68'). 
Jul 16 22:48:44 lee-laptop-linux NetworkManager: <info>  Deactivating device eth0. 
Jul 16 22:48:44 lee-laptop-linux kernel: [ 7695.376065] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Jul 16 22:48:44 lee-laptop-linux kernel: [ 7695.380561] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 16 22:48:45 lee-laptop-linux kernel: [ 7695.550161] ndiswrapper: device wlan0 removed
Jul 16 22:48:45 lee-laptop-linux kernel: [ 7695.550194] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
Jul 16 22:48:45 lee-laptop-linux kernel: [ 7695.550310] usbcore: deregistering interface driver ndiswrapper
Jul 16 22:48:45 lee-laptop-linux NetworkManager: <debug> [1216262925.261277] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/ssb__null_'). 
Jul 16 22:48:45 lee-laptop-linux NetworkManager: <debug> [1216262925.261347] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/ssb__null_'). 
Jul 16 22:48:45 lee-laptop-linux NetworkManager: <debug> [1216262925.261385] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_1a_92_c2_61_2c'). 
Jul 16 22:48:45 lee-laptop-linux NetworkManager: <info>  Deactivating device wlan0. 
Jul 16 22:48:45 lee-laptop-linux kernel: [ 7695.829889] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Jul 16 22:48:45 lee-laptop-linux kernel: [ 7695.958448] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Jul 16 22:48:45 lee-laptop-linux kernel: [ 7695.959119] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 16 22:48:45 lee-laptop-linux kernel: [ 7695.959183] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Jul 16 22:48:45 lee-laptop-linux kernel: [ 7695.964715] ndiswrapper: using IRQ 16
Jul 16 22:48:45 lee-laptop-linux kernel: [ 7696.328017] wlan0: ethernet device 00:1a:92:c2:61:2c using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
Jul 16 22:48:45 lee-laptop-linux kernel: [ 7696.328098] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Jul 16 22:48:45 lee-laptop-linux kernel: [ 7696.365788] usbcore: registered new interface driver ndiswrapper
Jul 16 22:48:45 lee-laptop-linux NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Jul 16 22:48:45 lee-laptop-linux NetworkManager: <debug> [1216262925.915858] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_1a_92_c2_61_2c'). 
Jul 16 22:48:45 lee-laptop-linux kernel: [ 7696.375993] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 16 22:48:45 lee-laptop-linux NetworkManager: <info>  wlan0: Device is fully-supported using driver 'ndiswrapper'. 
Jul 16 22:48:45 lee-laptop-linux NetworkManager: <info>  wlan0: driver does not support SSID scans (scan_capa 0x00). 
Jul 16 22:48:45 lee-laptop-linux NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jul 16 22:48:45 lee-laptop-linux NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jul 16 22:48:45 lee-laptop-linux NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Jul 16 22:48:45 lee-laptop-linux NetworkManager: <info>  Deactivating device wlan0. 
Jul 16 22:48:45 lee-laptop-linux NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Jul 17 08:42:45 lee-laptop-linux kernel: [ 7697.093621] Syncing filesystems ... done.
Jul 17 08:42:45 lee-laptop-linux kernel: [ 7697.094651] PM: Preparing system for mem sleep
Jul 17 08:42:45 lee-laptop-linux kernel: [ 7697.094810] Freezing user space processes ... (elapsed 0.00 seconds) done.
Jul 17 08:42:45 lee-laptop-linux kernel: [ 7697.095771] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Jul 17 08:42:45 lee-laptop-linux kernel: [ 7697.095825] PM: Entering mem sleep
Jul 17 08:42:45 lee-laptop-linux kernel: [ 7697.095827] Suspending console(s)
Jul 17 08:42:45 lee-laptop-linux kernel: [ 7697.095876] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Jul 17 08:42:45 lee-laptop-linux kernel: [ 7697.569223] sd 0:0:0:0: [sda] Stopping disk
Jul 17 08:42:45 lee-laptop-linux kernel: [ 7698.539043] ACPI handle has no context!
Jul 17 08:42:45 lee-laptop-linux kernel: [ 7698.539069] ACPI: PCI interrupt for device 0000:03:01.1 disabled
Jul 17 08:42:45 lee-laptop-linux kernel: [ 7698.539075] ACPI handle has no context!
Jul 17 08:42:45 lee-laptop-linux kernel: [ 7698.590415] [fglrx] firegl_gps_setpowerdown .
Jul 17 08:42:45 lee-laptop-linux kernel: [ 7698.621544] pm-suspend: page allocation failure. order:10, mode:0x4020
Jul 17 08:42:45 lee-laptop-linux kernel: [ 7698.621548] Pid: 31672, comm: pm-suspend Tainted: P        2.6.24-19-generic #1
Jul 17 08:42:45 lee-laptop-linux kernel: [ 7698.621570]  [agpgart:__alloc_pages+0x2c2/0x3a0] __alloc_pages+0x2c2/0x3a0
Jul 17 08:42:45 lee-laptop-linux kernel: [ 7698.621586]  [fglrx:__get_free_pages+0x37/0x200] __get_free_pages+0x37/0x50
Jul 17 08:42:45 lee-laptop-linux kernel: [ 7698.621591]  [<f8c9026e>] firegl_cmmqs_save_fb+0x8e/0x200 [fglrx]
Jul 17 08:42:45 lee-laptop-linux kernel: [ 7698.621680]  [<f8c869a6>] firegl_pm_save_framebuffer+0x66/0x70 [fglrx]
Jul 17 08:42:45 lee-laptop-linux kernel: [ 7698.621749]  [<f8c90668>] firegl_cmmqs_recoverable_surface_info+0x38/0x90 [fglrx]
Jul 17 08:42:45 lee-laptop-linux kernel: [ 7698.621820]  [<f8c880b3>] firegl_cail_powerdown+0x93/0x120 [fglrx]
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.621892]  [<f8c760b4>] fglrx_pci_suspend+0x44/0xd0 [fglrx]
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.621958]  [pci_device_suspend+0x23/0x60] pci_device_suspend+0x23/0x60
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.621965]  [device_suspend+0x14b/0x210] device_suspend+0x14b/0x210
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.621974]  [snd_hda_intel:printk+0x1b/0x100] printk+0x1b/0x20
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.621979]  [suspend_devices_and_enter+0x35/0x100] suspend_devices_and_enter+0x35/0x100
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.621988]  [enter_state+0x15e/0x190] enter_state+0x15e/0x190
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.621995]  [state_store+0x92/0xe0] state_store+0x92/0xe0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622000]  [state_store+0x0/0xe0] state_store+0x0/0xe0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622006]  [subsys_attr_store+0x32/0x50] subsys_attr_store+0x32/0x50
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622014]  [sysfs_write_file+0xc1/0x110] sysfs_write_file+0xc1/0x110
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622022]  [sysfs_write_file+0x0/0x110] sysfs_write_file+0x0/0x110
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622027]  [vfs_write+0xb9/0x170] vfs_write+0xb9/0x170
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622034]  [sys_write+0x41/0x70] sys_write+0x41/0x70
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622042]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622049]  [unix_stream_sendmsg+0x160/0x390] unix_stream_sendmsg+0x160/0x390
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622057]  =======================
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622059] Mem-info:
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622061] DMA per-cpu:
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622063] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622066] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622068] Normal per-cpu:
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622070] CPU    0: Hot: hi:  186, btch:  31 usd:  52   Cold: hi:   62, btch:  15 usd:  55
Jul 17 08:42:46 lee-laptop-linux gnome-power-manager: (lee) Resuming computer
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622073] CPU    1: Hot: hi:  186, btch:  31 usd: 165   Cold: hi:   62, btch:  15 usd:   2
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622076] HighMem per-cpu:
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622078] CPU    0: Hot: hi:  186, btch:  31 usd: 156   Cold: hi:   62, btch:  15 usd:   3
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622081] CPU    1: Hot: hi:  186, btch:  31 usd: 144   Cold: hi:   62, btch:  15 usd:   1
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622085] Active:244302 inactive:126709 dirty:0 writeback:0 unstable:0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622086]  free:419465 slab:38548 mapped:21163 pagetables:678 bounce:0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622090] DMA free:3712kB min:68kB low:84kB high:100kB active:748kB inactive:5724kB present:16256kB pages_scanned:0 all_unreclaimable? no
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622093] lowmem_reserve[]: 0 873 3284 3284
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622097] Normal free:5648kB min:3744kB low:4680kB high:5616kB active:260896kB inactive:407152kB present:894080kB pages_scanned:0 all_unreclaimable? no
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622100] lowmem_reserve[]: 0 0 19294 19294
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622105] HighMem free:1668500kB min:512kB low:3100kB high:5688kB active:715564kB inactive:93960kB present:2469720kB pages_scanned:0 all_unreclaimable? no
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622108] lowmem_reserve[]: 0 0 0 0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622110] DMA: 18*4kB 3*8kB 4*16kB 1*32kB 1*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3712kB
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622118] Normal: 112*4kB 134*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 1*4096kB = 5616kB
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622125] HighMem: 51*4kB 5*8kB 2*16kB 4*32kB 632*64kB 706*128kB 467*256kB 291*512kB 197*1024kB 85*2048kB 218*4096kB = 1668500kB
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622134] Swap cache: add 9235, delete 283, find 119/144, race 0+0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622136] Free swap  = 2213252kB
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622138] Total swap = 2249060kB
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.622139] Free swap:       2213252kB
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.635748] 851667 pages of RAM
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.635750] 622291 pages of HIGHMEM
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.635752] 16663 reserved pages
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.635754] 258385 pages shared
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.635755] 8952 pages swap cached
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.635757] 0 pages dirty
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.635758] 0 pages writeback
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.635760] 21163 pages mapped
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.635762] 38548 pages slab
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7698.635763] 678 pages pagetables
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.123469] pm-suspend: page allocation failure. order:10, mode:0x4020
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.123474] Pid: 31672, comm: pm-suspend Tainted: P        2.6.24-19-generic #1
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.123505]  [agpgart:__alloc_pages+0x2c2/0x3a0] __alloc_pages+0x2c2/0x3a0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.123522]  [fglrx:__get_free_pages+0x37/0x200] __get_free_pages+0x37/0x50
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.123527]  [<f8c9026e>] firegl_cmmqs_save_fb+0x8e/0x200 [fglrx]
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.123630]  [<f8c869a6>] firegl_pm_save_framebuffer+0x66/0x70 [fglrx]
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.123700]  [<f8c90668>] firegl_cmmqs_recoverable_surface_info+0x38/0x90 [fglrx]
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.123771]  [<f8c880b3>] firegl_cail_powerdown+0x93/0x120 [fglrx]
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.123843]  [<f8c760b4>] fglrx_pci_suspend+0x44/0xd0 [fglrx]
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.123910]  [pci_device_suspend+0x23/0x60] pci_device_suspend+0x23/0x60
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.123917]  [device_suspend+0x14b/0x210] device_suspend+0x14b/0x210
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.123926]  [snd_hda_intel:printk+0x1b/0x100] printk+0x1b/0x20
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.123933]  [suspend_devices_and_enter+0x35/0x100] suspend_devices_and_enter+0x35/0x100
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.123943]  [enter_state+0x15e/0x190] enter_state+0x15e/0x190
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.123950]  [state_store+0x92/0xe0] state_store+0x92/0xe0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.123955]  [state_store+0x0/0xe0] state_store+0x0/0xe0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.123960]  [subsys_attr_store+0x32/0x50] subsys_attr_store+0x32/0x50
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.123969]  [sysfs_write_file+0xc1/0x110] sysfs_write_file+0xc1/0x110
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.123977]  [sysfs_write_file+0x0/0x110] sysfs_write_file+0x0/0x110
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.123982]  [vfs_write+0xb9/0x170] vfs_write+0xb9/0x170
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.123990]  [sys_write+0x41/0x70] sys_write+0x41/0x70
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.123998]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124006]  [unix_stream_sendmsg+0x160/0x390] unix_stream_sendmsg+0x160/0x390
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124015]  =======================
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124016] Mem-info:
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124018] DMA per-cpu:
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124020] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124023] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124025] Normal per-cpu:
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124027] CPU    0: Hot: hi:  186, btch:  31 usd:  48   Cold: hi:   62, btch:  15 usd:  55
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124031] CPU    1: Hot: hi:  186, btch:  31 usd: 162   Cold: hi:   62, btch:  15 usd:   2
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124033] HighMem per-cpu:
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124035] CPU    0: Hot: hi:  186, btch:  31 usd: 156   Cold: hi:   62, btch:  15 usd:   3
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124038] CPU    1: Hot: hi:  186, btch:  31 usd: 144   Cold: hi:   62, btch:  15 usd:   1
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124042] Active:244302 inactive:126709 dirty:0 writeback:0 unstable:0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124044]  free:418483 slab:38548 mapped:21163 pagetables:678 bounce:0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124047] DMA free:3568kB min:68kB low:84kB high:100kB active:748kB inactive:5724kB present:16256kB pages_scanned:0 all_unreclaimable? no
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124050] lowmem_reserve[]: 0 873 3284 3284
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124055] Normal free:1864kB min:3744kB low:4680kB high:5616kB active:260896kB inactive:407152kB present:894080kB pages_scanned:0 all_unreclaimable? no
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124058] lowmem_reserve[]: 0 0 19294 19294
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124062] HighMem free:1668500kB min:512kB low:3100kB high:5688kB active:715564kB inactive:93960kB present:2469720kB pages_scanned:0 all_unreclaimable? no
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124065] lowmem_reserve[]: 0 0 0 0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124068] DMA: 0*4kB 0*8kB 1*16kB 1*32kB 1*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3568kB
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124076] Normal: 30*4kB 2*8kB 0*16kB 1*32kB 1*64kB 1*128kB 0*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 1896kB
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124083] HighMem: 51*4kB 5*8kB 2*16kB 4*32kB 632*64kB 706*128kB 467*256kB 291*512kB 197*1024kB 85*2048kB 218*4096kB = 1668500kB
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124093] Swap cache: add 9235, delete 283, find 119/144, race 0+0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124095] Free swap  = 2213252kB
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124096] Total swap = 2249060kB
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.124097] Free swap:       2213252kB
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.137869] 851667 pages of RAM
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.137871] 622291 pages of HIGHMEM
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.137873] 16663 reserved pages
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.137875] 258385 pages shared
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.137876] 8952 pages swap cached
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.137878] 0 pages dirty
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.137879] 0 pages writeback
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.137881] 21163 pages mapped
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.137882] 38548 pages slab
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.137884] 678 pages pagetables
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.137975] pm-suspend: page allocation failure. order:0, mode:0x20
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.137979] Pid: 31672, comm: pm-suspend Tainted: P        2.6.24-19-generic #1
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.137998]  [agpgart:__alloc_pages+0x2c2/0x3a0] __alloc_pages+0x2c2/0x3a0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138012]  [__vmalloc_area_node+0xcb/0x150] __vmalloc_area_node+0xcb/0x150
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138022]  [fglrx:__vmalloc+0xf/0x60] __vmalloc+0xf/0x20
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138026]  [<f8c90398>] firegl_cmmqs_save_fb+0x1b8/0x200 [fglrx]
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138123]  [<f8c869a6>] firegl_pm_save_framebuffer+0x66/0x70 [fglrx]
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138191]  [<f8c90668>] firegl_cmmqs_recoverable_surface_info+0x38/0x90 [fglrx]
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138262]  [<f8c880b3>] firegl_cail_powerdown+0x93/0x120 [fglrx]
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138332]  [<f8c760b4>] fglrx_pci_suspend+0x44/0xd0 [fglrx]
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138398]  [pci_device_suspend+0x23/0x60] pci_device_suspend+0x23/0x60
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138406]  [device_suspend+0x14b/0x210] device_suspend+0x14b/0x210
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138413]  [snd_hda_intel:printk+0x1b/0x100] printk+0x1b/0x20
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138419]  [suspend_devices_and_enter+0x35/0x100] suspend_devices_and_enter+0x35/0x100
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138427]  [enter_state+0x15e/0x190] enter_state+0x15e/0x190
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138433]  [state_store+0x92/0xe0] state_store+0x92/0xe0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138438]  [state_store+0x0/0xe0] state_store+0x0/0xe0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138442]  [subsys_attr_store+0x32/0x50] subsys_attr_store+0x32/0x50
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138450]  [sysfs_write_file+0xc1/0x110] sysfs_write_file+0xc1/0x110
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138457]  [sysfs_write_file+0x0/0x110] sysfs_write_file+0x0/0x110
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138462]  [vfs_write+0xb9/0x170] vfs_write+0xb9/0x170
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138470]  [sys_write+0x41/0x70] sys_write+0x41/0x70
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138477]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138485]  [unix_stream_sendmsg+0x160/0x390] unix_stream_sendmsg+0x160/0x390
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138492]  =======================
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138494] Mem-info:
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138495] DMA per-cpu:
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138497] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138500] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138502] Normal per-cpu:
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138505] CPU    0: Hot: hi:  186, btch:  31 usd:  63   Cold: hi:   62, btch:  15 usd:  55
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138508] CPU    1: Hot: hi:  186, btch:  31 usd: 162   Cold: hi:   62, btch:  15 usd:   2
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138510] HighMem per-cpu:
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138512] CPU    0: Hot: hi:  186, btch:  31 usd: 156   Cold: hi:   62, btch:  15 usd:   3
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138515] CPU    1: Hot: hi:  186, btch:  31 usd: 144   Cold: hi:   62, btch:  15 usd:   1
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138519] Active:244302 inactive:126709 dirty:0 writeback:0 unstable:0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138521]  free:418345 slab:38548 mapped:21163 pagetables:678 bounce:0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138524] DMA free:3520kB min:68kB low:84kB high:100kB active:748kB inactive:5724kB present:16256kB pages_scanned:0 all_unreclaimable? no
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138527] lowmem_reserve[]: 0 873 3284 3284
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138531] Normal free:1360kB min:3744kB low:4680kB high:5616kB active:260896kB inactive:407152kB present:894080kB pages_scanned:0 all_unreclaimable? no
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138534] lowmem_reserve[]: 0 0 19294 19294
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138539] HighMem free:1668500kB min:512kB low:3100kB high:5688kB active:715564kB inactive:93960kB present:2469720kB pages_scanned:0 all_unreclaimable? no
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138542] lowmem_reserve[]: 0 0 0 0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138545] DMA: 0*4kB 0*8kB 0*16kB 0*32kB 1*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3520kB
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138552] Normal: 0*4kB 1*8kB 1*16kB 1*32kB 1*64kB 0*128kB 1*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1400kB
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138559] HighMem: 51*4kB 5*8kB 2*16kB 4*32kB 632*64kB 706*128kB 467*256kB 291*512kB 197*1024kB 85*2048kB 218*4096kB = 1668500kB
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138568] Swap cache: add 9235, delete 283, find 119/144, race 0+0
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138570] Free swap  = 2213252kB
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138572] Total swap = 2249060kB
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.138573] Free swap:       2213252kB
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.151988] 851667 pages of RAM
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.151990] 622291 pages of HIGHMEM
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.151991] 16663 reserved pages
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.151992] 258385 pages shared
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.151994] 8952 pages swap cached
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.151995] 0 pages dirty
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.151997] 0 pages writeback
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.151998] 21163 pages mapped
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.151999] 38548 pages slab
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.152000] 678 pages pagetables
Jul 17 08:42:46 lee-laptop-linux kernel: [ 7699.152093] [fglrx:firegl_cmmqs_save_fb] *ERROR* Failed to allocate 4000 KB for saving CMMQS frame buffer object.

----------------------------------------------------------------------


Really hoping someone can help me with this! 

THANKS!

---

### Post by parabolee on 2008-07-17
Can nobody help me? Or at least point me somewhere I may be able to get help?

I also tried the new auto installer for NDSWrapper but it failed to download my driver and said to check my internet connection.

HELP!

---

