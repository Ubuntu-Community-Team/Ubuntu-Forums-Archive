---
title: "Agere et131x doesn't work"
date: 2012-05-03
forum: Hardware
---

### Post by cmavr8 on 2012-05-03
On a laptop (Ubuntu server 10.04 LTS) I did:

```
# modprobe et131x
# modprobe acpiphp
```
and I inserted an Agere et131x based Gigabit Ethernet expresscard card.

In dmesg I see the following:

```
[105793.160347] pci 0000:02:00.0: reg 10 64bit mmio: [0x000000-0x1fffff]
[105793.160403] pci 0000:02:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[105793.160499] pci 0000:02:00.0: supports D1
[105793.160505] pci 0000:02:00.0: PME# supported from D0 D1 D3hot D3cold
[105793.160515] pci 0000:02:00.0: PME# disabled
[105793.160796] pci 0000:02:00.0: no hotplug settings from platform
[105793.161478] et131x 0000:02:00.0: enabling device (0000 -> 0002)
[105793.161494] et131x 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[105793.161512] et131x 0000:02:00.0: setting latency timer to 64
[105793.165201] kacpi_notify: page allocation failure. order:5, mode:0x8020
[105793.165211] Pid: 24, comm: kacpi_notify Tainted: G         C 2.6.32-41-generic #88-Ubuntu
[105793.165216] Call Trace:
[105793.165241]  [<c058f2d4>] ? printk+0x1d/0x21
[105793.165248]  [<c01d1e3b>] __alloc_pages_slowpath+0x3bb/0x4b0
[105793.165252]  [<c01d206a>] __alloc_pages_nodemask+0x13a/0x170
[105793.165258]  [<c0107932>] dma_generic_alloc_coherent+0x62/0xc0
[105793.165265]  [<f8541bb6>] et131x_rx_dma_memory_alloc+0x6e6/0xa90 [et131x]
[105793.165270]  [<c01078d0>] ? dma_generic_alloc_coherent+0x0/0xc0
[105793.165275]  [<f85438e8>] et131x_adapter_memory_alloc+0x28/0xd0 [et131x]
[105793.165280]  [<f85451a3>] et131x_pci_setup+0x2f1/0x423 [et131x]
[105793.165285]  [<c0367db3>] local_pci_probe+0x13/0x20
[105793.165289]  [<c0368bb8>] pci_device_probe+0x68/0x90
[105793.165294]  [<c03eadad>] really_probe+0x4d/0x140
[105793.165298]  [<c03f16be>] ? pm_runtime_barrier+0x4e/0xc0
[105793.165302]  [<c03eaedc>] driver_probe_device+0x3c/0x60
[105793.165305]  [<c03eafd9>] __device_attach+0x49/0x60
[105793.165309]  [<c03ea103>] bus_for_each_drv+0x53/0x80
[105793.165313]  [<c03eb0a2>] device_attach+0x72/0x90
[105793.165316]  [<c03eaf90>] ? __device_attach+0x0/0x60
[105793.165320]  [<c03e9f45>] bus_probe_device+0x25/0x40
[105793.165325]  [<c03e89c4>] device_add+0x274/0x430
[105793.165330]  [<c037b17c>] ? acpi_os_signal_semaphore+0x26/0x2c
[105793.165335]  [<c039d349>] ? acpi_ut_release_read_lock+0x48/0x4e
[105793.165340]  [<c036220c>] pci_bus_add_device+0x1c/0x50
[105793.165344]  [<c0362288>] pci_bus_add_devices+0x48/0x130
[105793.165349]  [<f87b7706>] ? acpiphp_configure_ioapics+0x46/0x50 [acpiphp]
[105793.165354]  [<f87b7510>] ? ioapic_add+0x0/0x1b0 [acpiphp]
[105793.165359]  [<f87b8b39>] enable_device+0x219/0x30e [acpiphp]
[105793.165363]  [<f87b6889>] ? get_slot_status+0x99/0xc0 [acpiphp]
[105793.165368]  [<f87b7b27>] acpiphp_enable_slot+0xb7/0x130 [acpiphp]
[105793.165373]  [<f87b7bfc>] acpiphp_check_bridge+0x5c/0xe0 [acpiphp]
[105793.165377]  [<c0394482>] ? acpi_get_name+0x3a/0xa1
[105793.165382]  [<f87b878d>] handle_hotplug_event_bridge+0x1ed/0x2f4 [acpiphp]
[105793.165386]  [<c016d808>] ? up+0x28/0x40
[105793.165390]  [<c0392dd2>] ? acpi_get_data+0x56/0x65
[105793.165394]  [<c037d9b9>] ? acpi_bus_data_handler+0x0/0xa
[105793.165398]  [<c037d1c4>] ? acpi_bus_get_device+0x20/0x35
[105793.165403]  [<c0389979>] acpi_ev_notify_dispatch+0x54/0x5f
[105793.165407]  [<c037b20f>] acpi_os_execute_deferred+0x22/0x2d
[105793.165413]  [<c01648fe>] run_workqueue+0x8e/0x150
[105793.165417]  [<c037b1ed>] ? acpi_os_execute_deferred+0x0/0x2d
[105793.165421]  [<c0164a44>] worker_thread+0x84/0xe0
[105793.165425]  [<c01689e0>] ? autoremove_wake_function+0x0/0x50
[105793.165429]  [<c01649c0>] ? worker_thread+0x0/0xe0
[105793.165433]  [<c0168754>] kthread+0x74/0x80
[105793.165436]  [<c01686e0>] ? kthread+0x0/0x80
[105793.165440]  [<c0104087>] kernel_thread_helper+0x7/0x10
[105793.165443] Mem-Info:
[105793.165445] DMA per-cpu:
[105793.165448] CPU    0: hi:    0, btch:   1 usd:   0
[105793.165450] CPU    1: hi:    0, btch:   1 usd:   0
[105793.165452] Normal per-cpu:
[105793.165455] CPU    0: hi:  186, btch:  31 usd:  55
[105793.165458] CPU    1: hi:  186, btch:  31 usd: 179
[105793.165460] HighMem per-cpu:
[105793.165462] CPU    0: hi:  186, btch:  31 usd: 158
[105793.165465] CPU    1: hi:  186, btch:  31 usd: 119
[105793.165470] active_anon:62256 inactive_anon:31838 isolated_anon:0
[105793.165471]  active_file:172806 inactive_file:192661 isolated_file:0
[105793.165473]  unevictable:1017 dirty:23 writeback:0 unstable:0
[105793.165474]  free:19546 slab_reclaimable:21268 slab_unreclaimable:2211
[105793.165475]  mapped:7898 shmem:8848 pagetables:1561 bounce:0
[105793.165483] DMA free:3512kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:3448kB inactive_file:1048kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15852kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:228kB slab_unreclaimable:80kB kernel_stack:192kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[105793.165490] lowmem_reserve[]: 0 865 2006 2006
[105793.165499] Normal free:17936kB min:3728kB low:4660kB high:5592kB active_anon:0kB inactive_anon:2872kB active_file:363332kB inactive_file:363628kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:76kB writeback:0kB mapped:6244kB shmem:0kB slab_reclaimable:84844kB slab_unreclaimable:8764kB kernel_stack:2136kB pagetables:60kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[105793.165506] lowmem_reserve[]: 0 0 9132 9132
[105793.165515] HighMem free:56736kB min:512kB low:1740kB high:2972kB active_anon:249024kB inactive_anon:124480kB active_file:324444kB inactive_file:405968kB unevictable:4068kB isolated(anon):0kB isolated(file):0kB present:1168976kB mlocked:4068kB dirty:16kB writeback:0kB mapped:25348kB shmem:35392kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:6184kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[105793.165522] lowmem_reserve[]: 0 0 0 0
[105793.165527] DMA: 6*4kB 2*8kB 1*16kB 0*32kB 0*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3512kB
[105793.165539] Normal: 2410*4kB 667*8kB 101*16kB 22*32kB 8*64kB 1*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 17936kB
[105793.165550] HighMem: 3696*4kB 4274*8kB 383*16kB 9*32kB 5*64kB 4*128kB 2*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 56736kB
[105793.165562] 377538 total pagecache pages
[105793.165564] 2300 pages in swap cache
[105793.165567] Swap cache stats: add 10006, delete 7706, find 14289/14691
[105793.165569] Free swap  = 2233452kB
[105793.165571] Total swap = 2257124kB
[105793.174804] 521872 pages RAM
[105793.174808] 294546 pages HighMem
[105793.174809] 8842 pages reserved
[105793.174811] 357910 pages shared
[105793.174813] 173114 pages non-shared
[105793.174818] et131x 0000:02:00.0: Could not alloc memory
[105793.174822] et131x 0000:02:00.0: et131x_rx_dma_memory_alloc FAILED
[105793.174830] et131x 0000:02:00.0: Could not alloc adapater memory (DMA)
[105793.174863] et131x 0000:02:00.0: PCI INT A disabled
[105793.174885] et131x: probe of 0000:02:00.0 failed with error -12
```

Looks like something went wrong...

Ifconfig -a shows no new interface. Plugging in a network cable (connected to a router) has no effect on software (dmesg, ifconfig) but one of the card's LEDs lights up.

Any ideas?
Thanks

EDIT: I just took the card out (after 5') and it is so hot I can't touch the metal parts...

---

