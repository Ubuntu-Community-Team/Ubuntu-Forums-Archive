---
title: "pcmcia cf card"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by dksdk on 2006-06-06
hi great work by dapper team, well done. is working great except a few problems. the pcmcia cf card reader dose'nt mount. the card seems to be recognised but fails to be read.
i upgraded from breezy to dapper, it use to work fine. but i was trying to get suspend to work and some how ended up deleting pcmcia-cs since it said it is outdated. since then i have reinstalled it and also tried reinstalling pcmciautils.
here is the output of my dmesg. i cant make out what is wrong and how to correct it. any help is much appriciated. thank you.

[4294811.604000] pccard: PCMCIA card inserted into slot 0
[4294811.604000] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[4294811.611000] pcmcia: registering new device pcmcia0.0
[4294811.879000] Probing IDE interface ide2...
[4294812.144000] hde: LEXAR ATA FLASH, CFA DISK drive
[4294813.162000] irq 3: nobody cared (try booting with the "irqpoll" option)
[4294813.162000]  [<c014c73a>] __report_bad_irq+0x2a/0xa0
[4294813.162000]  [<c014befd>] handle_IRQ_event+0x3d/0x70
[4294813.162000]  [<c014c857>] note_interrupt+0x87/0xf0
[4294813.162000]  [<c014c02d>] __do_IRQ+0xfd/0x110
[4294813.162000]  [<c0105c99>] do_IRQ+0x19/0x30
[4294813.162000]  [<c0103ef6>] common_interrupt+0x1a/0x20
[4294813.162000]  [<c012a76f>] __do_softirq+0x5f/0xe0
[4294813.162000]  [<c014bffc>] __do_IRQ+0xcc/0x110
[4294813.162000]  [<c012a825>] do_softirq+0x35/0x40
[4294813.162000]  [<c012a905>] irq_exit+0x45/0x50
[4294813.162000]  [<c0105c9e>] do_IRQ+0x1e/0x30
[4294813.162000]  [<c0103ef6>] common_interrupt+0x1a/0x20
[4294813.162000]  [<c030caa6>] _spin_unlock_irqrestore+0x6/0x20
[4294813.162000]  [<c014c389>] setup_irq+0xc9/0x120
[4294813.162000]  [<c014c59a>] request_irq+0xaa/0xd0
[4294813.162000]  [<c0274713>] init_irq+0x1b3/0x460
[4294813.162000]  [<c0270110>] ide_intr+0x0/0x1f0
[4294813.162000]  [<c01ea7e1>] register_blkdev+0x81/0x130
[4294813.162000]  [<c0274ebf>] hwif_init+0xdf/0x2b0
[4294813.162000]  [<c0273d10>] ide_undecoded_slave+0x0/0xc0
[4294813.162000]  [<c0273d10>] ide_undecoded_slave+0x0/0xc0
[4294813.162000]  [<c0274316>] probe_hwif_init_with_fixup+0x26/0x90
[4294813.162000]  [<c026cad8>] ide_register_hw_with_fixup+0x1a8/0x1c0
[4294813.162000]  [<c0273d10>] ide_undecoded_slave+0x0/0xc0
[4294813.162000]  [<f13ee209>] idecs_register+0x89/0x90 [ide_cs]
[4294813.162000]  [<c0273d10>] ide_undecoded_slave+0x0/0xc0
[4294813.162000]  [<f13ee60b>] ide_config+0x3fb/0x650 [ide_cs]
[4294813.162000]  [<f0e3eed1>] pccard_read_tuple+0x71/0xc0 [pcmcia_core]
[4294813.162000]  [<f13ee9ac>] ide_event+0xdc/0xf0 [ide_cs]
[4294813.162000]  [<f0fdb7e6>] pcmcia_register_client+0x1d6/0x2a0 [pcmcia]
[4294813.162000]  [<c011f5be>] __wake_up+0x3e/0x60
[4294813.162000]  [<c0157f3f>] kzalloc+0x1f/0x50
[4294813.162000]  [<f13ee093>] ide_attach+0x93/0xd0 [ide_cs]
[4294813.162000]  [<c01f6217>] kobject_get+0x17/0x20
[4294813.162000]  [<f0fda4ab>] pcmcia_device_probe+0x8b/0x160 [pcmcia]
[4294813.162000]  [<c0260bd4>] driver_probe_device+0x54/0xf0
[4294813.162000]  [<c0260cf0>] __driver_attach+0x0/0x50
[4294813.162000]  [<c0260d33>] __driver_attach+0x43/0x50
[4294813.162000]  [<c02600ed>] bus_for_each_dev+0x5d/0x80
[4294813.162000]  [<c0260d65>] driver_attach+0x25/0x30
[4294813.162000]  [<c0260cf0>] __driver_attach+0x0/0x50
[4294813.162000]  [<c0260649>] bus_add_driver+0x89/0xf0
[4294813.162000]  [<f13f200f>] init_ide_cs+0xf/0x11 [ide_cs]
[4294813.162000]  [<c0144a6c>] sys_init_module+0xdc/0x240
[4294813.162000]  [<c0103457>] sysenter_past_esp+0x54/0x75
[4294813.162000]  [<c0142080>] free_modinfo_version+0x20/0x30
[4294813.162000] handlers:
[4294813.162000] [<c0270110>] (ide_intr+0x0/0x1f0)
[4294813.162000] Disabling IRQ #3
[4294813.173000] ide2 at 0x100-0x107,0x10e on irq 3
[4294813.173000] hde: max request size: 128KiB
[4294813.173000] hde: 251904 sectors (128 MB) w/1KiB Cache, CHS=984/8/32
[4294813.173000] hde: cache flushes not supported
[4294813.173000]  hde:<4>hde: lost interrupt
[4294843.883000] irq 3: nobody cared (try booting with the "irqpoll" option)
[4294843.883000]  [<c014c73a>] __report_bad_irq+0x2a/0xa0
[4294843.883000]  [<c014befd>] handle_IRQ_event+0x3d/0x70
[4294843.883000]  [<c014c857>] note_interrupt+0x87/0xf0
[4294843.883000]  [<c014c02d>] __do_IRQ+0xfd/0x110
[4294843.883000]  [<c0105c99>] do_IRQ+0x19/0x30
[4294843.883000]  [<c0103ef6>] common_interrupt+0x1a/0x20
[4294843.883000]  [<c026fb9a>] ide_do_request+0x30a/0x410
[4294843.883000]  [<c02756d0>] set_geometry_intr+0x0/0xe0
[4294843.883000]  [<c026feba>] ide_timer_expiry+0xda/0x270
[4294843.883000]  [<c026fde0>] ide_timer_expiry+0x0/0x270
[4294843.883000]  [<c012f533>] run_timer_softirq+0xe3/0x1e0
[4294843.883000]  [<c014befd>] handle_IRQ_event+0x3d/0x70
[4294843.883000]  [<c012a782>] __do_softirq+0x72/0xe0
[4294843.883000]  [<c012a825>] do_softirq+0x35/0x40
[4294843.883000]  [<c012a905>] irq_exit+0x45/0x50
[4294843.883000]  [<c0105c9e>] do_IRQ+0x1e/0x30
[4294843.883000]  [<c0103ef6>] common_interrupt+0x1a/0x20
[4294843.883000]  [<f084be9b>] acpi_processor_idle+0x184/0x32d [processor]
[4294843.883000]  [<c010111f>] cpu_idle+0x6f/0xc0
[4294843.883000]  [<c03a8a3a>] start_kernel+0x19a/0x200
[4294843.883000]  [<c03a83c0>] unknown_bootoption+0x0/0x1f0
[4294843.883000] handlers:
[4294843.883000] [<c0270110>] (ide_intr+0x0/0x1f0)
[4294843.883000] Disabling IRQ #3
[4294873.884000] hde: lost interrupt
[4294874.595000] irq 3: nobody cared (try booting with the "irqpoll" option)
[4294874.595000]  [<c014c73a>] __report_bad_irq+0x2a/0xa0
[4294874.595000]  [<c014befd>] handle_IRQ_event+0x3d/0x70
[4294874.595000]  [<c014c857>] note_interrupt+0x87/0xf0
[4294874.595000]  [<c014c02d>] __do_IRQ+0xfd/0x110
[4294874.595000]  [<c0105c99>] do_IRQ+0x19/0x30
[4294874.595000]  [<c0103ef6>] common_interrupt+0x1a/0x20
[4294874.595000]  [<c026fb9a>] ide_do_request+0x30a/0x410
[4294874.595000]  [<c02757b0>] recal_intr+0x0/0x50
[4294874.595000]  [<c026feba>] ide_timer_expiry+0xda/0x270
[4294874.595000]  [<c026fde0>] ide_timer_expiry+0x0/0x270
[4294874.595000]  [<c012f533>] run_timer_softirq+0xe3/0x1e0
[4294874.595000]  [<c014befd>] handle_IRQ_event+0x3d/0x70
[4294874.595000]  [<c012a782>] __do_softirq+0x72/0xe0
[4294874.595000]  [<c012a825>] do_softirq+0x35/0x40
[4294874.595000]  [<c012a905>] irq_exit+0x45/0x50
[4294874.595000]  [<c0105c9e>] do_IRQ+0x1e/0x30
[4294874.595000]  [<c0103ef6>] common_interrupt+0x1a/0x20
[4294874.595000]  [<f084be9b>] acpi_processor_idle+0x184/0x32d [processor]
[4294874.595000]  [<c030ac34>] schedule+0x5c4/0xd60
[4294874.595000]  [<c010111f>] cpu_idle+0x6f/0xc0
[4294874.595000]  [<c03a8a3a>] start_kernel+0x19a/0x200
[4294874.595000]  [<c03a83c0>] unknown_bootoption+0x0/0x1f0
[4294874.595000] handlers:
[4294874.595000] [<c0270110>] (ide_intr+0x0/0x1f0)
[4294874.595000] Disabling IRQ #3
[4294884.596000] hde: lost interrupt

---

### Post by ranf on 2006-06-06
How about this?

```
[4294813.162000] irq 3: nobody cared (try booting with the "irqpoll" option)
```

If you don't know how to do this, please ask.

---

### Post by dksdk on 2006-06-06
yes please, i cant figure out how to do it. it will of great help if you can tell me how to set it right. thanx in advance.

---

### Post by ranf on 2006-06-06
For testing purposes we edit the kernel parameter in the boot menu (Grub):

when the boot menu appears press E to edit your default kernel, cursor down one line at the line named Kernel (or so) press E to edit again. You already are at the end of the line. Now add " irqpoll" without the quotes. Press Enter. Then press B to boot it.

See if it helped.

---

### Post by dksdk on 2006-06-06
[QUOTE=ranf]For testing purposes we edit the kernel parameter in the boot menu (Grub):

when the boot menu appears press E to edit your default kernel, cursor down one line at the line named Kernel (or so) press E to edit again. You already are at the end of the line. Now add " irqpoll" without the quotes. Press Enter. Then press B to boot it.

See if it helped.[/QUOTE]
hi ranf i tried booting with irgpoll and when i inserted the card the laptop was erozen, no keyboard response, no mouse so i had to do a hard reboot.
this time i booted normally and when i inserted the card it again did not get recognised, not i removed the card. but after removing an icon came up in the for the card so i reinserted the card and it frozen again as soon as i inserted the card. i had to hard reboot.

i inserted the card again and this is the dmesg

[4295521.218000] pccard: PCMCIA card inserted into slot 0
[4295521.218000] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[4295521.226000] pcmcia: registering new device pcmcia0.0
[4295521.912000] Probing IDE interface ide2...
[4295522.180000] hde: LEXAR ATA FLASH, CFA DISK drive
[4295523.198000] irq 3: nobody cared (try booting with the "irqpoll" option)
[4295523.198000]  [<c014c73a>] __report_bad_irq+0x2a/0xa0
[4295523.198000]  [<c014befd>] handle_IRQ_event+0x3d/0x70
[4295523.198000]  [<c014c857>] note_interrupt+0x87/0xf0
[4295523.198000]  [<c014c02d>] __do_IRQ+0xfd/0x110
[4295523.198000]  [<c0105c99>] do_IRQ+0x19/0x30
[4295523.198000]  [<c0103ef6>] common_interrupt+0x1a/0x20
[4295523.198000]  [<c012a76f>] __do_softirq+0x5f/0xe0
[4295523.198000]  [<c014bffc>] __do_IRQ+0xcc/0x110
[4295523.198000]  [<c012a825>] do_softirq+0x35/0x40
[4295523.198000]  [<c012a905>] irq_exit+0x45/0x50
[4295523.198000]  [<c0105c9e>] do_IRQ+0x1e/0x30
[4295523.198000]  [<c0103ef6>] common_interrupt+0x1a/0x20
[4295523.198000]  [<c030caa6>] _spin_unlock_irqrestore+0x6/0x20
[4295523.198000]  [<c014c389>] setup_irq+0xc9/0x120
[4295523.198000]  [<c014c59a>] request_irq+0xaa/0xd0
[4295523.198000]  [<c0274713>] init_irq+0x1b3/0x460
[4295523.198000]  [<c0270110>] ide_intr+0x0/0x1f0
[4295523.198000]  [<c01ea7e1>] register_blkdev+0x81/0x130
[4295523.198000]  [<c0274ebf>] hwif_init+0xdf/0x2b0
[4295523.198000]  [<c0273d10>] ide_undecoded_slave+0x0/0xc0
[4295523.198000]  [<c0273d10>] ide_undecoded_slave+0x0/0xc0
[4295523.198000]  [<c0274316>] probe_hwif_init_with_fixup+0x26/0x90
[4295523.198000]  [<c026cad8>] ide_register_hw_with_fixup+0x1a8/0x1c0
[4295523.198000]  [<c0273d10>] ide_undecoded_slave+0x0/0xc0
[4295523.198000]  [<f13b4209>] idecs_register+0x89/0x90 [ide_cs]
[4295523.198000]  [<c0273d10>] ide_undecoded_slave+0x0/0xc0
[4295523.198000]  [<f13b460b>] ide_config+0x3fb/0x650 [ide_cs]
[4295523.198000]  [<f0f7bed1>] pccard_read_tuple+0x71/0xc0 [pcmcia_core]
[4295523.198000]  [<f13b49ac>] ide_event+0xdc/0xf0 [ide_cs]
[4295523.198000]  [<f0fda7e6>] pcmcia_register_client+0x1d6/0x2a0 [pcmcia]
[4295523.198000]  [<c011f5be>] __wake_up+0x3e/0x60
[4295523.198000]  [<c0157f3f>] kzalloc+0x1f/0x50
[4295523.198000]  [<f13b4093>] ide_attach+0x93/0xd0 [ide_cs]
[4295523.198000]  [<c01f6217>] kobject_get+0x17/0x20
[4295523.198000]  [<f0fd94ab>] pcmcia_device_probe+0x8b/0x160 [pcmcia]
[4295523.198000]  [<c0260bd4>] driver_probe_device+0x54/0xf0
[4295523.198000]  [<c0260cf0>] __driver_attach+0x0/0x50
[4295523.198000]  [<c0260d33>] __driver_attach+0x43/0x50
[4295523.198000]  [<c02600ed>] bus_for_each_dev+0x5d/0x80
[4295523.198000]  [<c0260d65>] driver_attach+0x25/0x30
[4295523.198000]  [<c0260cf0>] __driver_attach+0x0/0x50
[4295523.198000]  [<c0260649>] bus_add_driver+0x89/0xf0
[4295523.198000]  [<f135500f>] init_ide_cs+0xf/0x11 [ide_cs]
[4295523.198000]  [<c0144a6c>] sys_init_module+0xdc/0x240
[4295523.198000]  [<c0103457>] sysenter_past_esp+0x54/0x75
[4295523.198000] handlers:
[4295523.198000] [<c0270110>] (ide_intr+0x0/0x1f0)
[4295523.198000] Disabling IRQ #3
[4295523.207000] ide2 at 0x100-0x107,0x10e on irq 3
[4295523.207000] hde: max request size: 128KiB
[4295523.207000] hde: 251904 sectors (128 MB) w/1KiB Cache, CHS=984/8/32
[4295523.207000] hde: cache flushes not supported
[4295523.207000]  hde:<4>hde: lost interrupt
[4295553.924000] irq 3: nobody cared (try booting with the "irqpoll" option)
[4295553.924000]  [<c014c73a>] __report_bad_irq+0x2a/0xa0
[4295553.924000]  [<c014befd>] handle_IRQ_event+0x3d/0x70
[4295553.924000]  [<c014c857>] note_interrupt+0x87/0xf0
[4295553.924000]  [<c014c02d>] __do_IRQ+0xfd/0x110
[4295553.924000]  [<c0105c99>] do_IRQ+0x19/0x30
[4295553.924000]  [<c0103ef6>] common_interrupt+0x1a/0x20
[4295553.924000]  [<c014bed8>] handle_IRQ_event+0x18/0x70
[4295553.924000]  [<c0109b56>] mask_and_ack_8259A+0x26/0x110
[4295553.924000]  [<c014bfcd>] __do_IRQ+0x9d/0x110
[4295553.924000]  [<c0105c99>] do_IRQ+0x19/0x30
[4295553.924000]  [<c0103ef6>] common_interrupt+0x1a/0x20
[4295553.924000]  [<c026fb9a>] ide_do_request+0x30a/0x410
[4295553.924000]  [<c02756d0>] set_geometry_intr+0x0/0xe0
[4295553.924000]  [<c026feba>] ide_timer_expiry+0xda/0x270
[4295553.924000]  [<c026fde0>] ide_timer_expiry+0x0/0x270
[4295553.924000]  [<c012f533>] run_timer_softirq+0xe3/0x1e0
[4295553.924000]  [<c014befd>] handle_IRQ_event+0x3d/0x70
[4295553.924000]  [<c012a782>] __do_softirq+0x72/0xe0
[4295553.924000]  [<c012a825>] do_softirq+0x35/0x40
[4295553.924000]  [<c012a905>] irq_exit+0x45/0x50
[4295553.924000]  [<c0105c9e>] do_IRQ+0x1e/0x30
[4295553.924000]  [<c0103ef6>] common_interrupt+0x1a/0x20
[4295553.924000]  [<f084be9b>] acpi_processor_idle+0x184/0x32d [processor]
[4295553.924000]  [<c010111f>] cpu_idle+0x6f/0xc0
[4295553.924000]  [<c03a8a3a>] start_kernel+0x19a/0x200
[4295553.924000]  [<c03a83c0>] unknown_bootoption+0x0/0x1f0
[4295553.924000] handlers:
[4295553.924000] [<c0270110>] (ide_intr+0x0/0x1f0)
[4295553.924000] Disabling IRQ #3
[4295583.925000] hde: lost interrupt
[4295584.636000] irq 3: nobody cared (try booting with the "irqpoll" option)
[4295584.636000]  [<c014c73a>] __report_bad_irq+0x2a/0xa0
[4295584.636000]  [<c014befd>] handle_IRQ_event+0x3d/0x70
[4295584.636000]  [<c014c857>] note_interrupt+0x87/0xf0
[4295584.636000]  [<c014c02d>] __do_IRQ+0xfd/0x110
[4295584.636000]  [<c0105c99>] do_IRQ+0x19/0x30
[4295584.636000]  [<c0103ef6>] common_interrupt+0x1a/0x20
[4295584.636000]  [<c026fb9a>] ide_do_request+0x30a/0x410
[4295584.636000]  [<c02757b0>] recal_intr+0x0/0x50
[4295584.636000]  [<c026feba>] ide_timer_expiry+0xda/0x270
[4295584.636000]  [<c026fde0>] ide_timer_expiry+0x0/0x270
[4295584.636000]  [<c012f533>] run_timer_softirq+0xe3/0x1e0
[4295584.636000]  [<c014befd>] handle_IRQ_event+0x3d/0x70
[4295584.636000]  [<c012a782>] __do_softirq+0x72/0xe0
[4295584.636000]  [<c012a825>] do_softirq+0x35/0x40
[4295584.636000]  [<c012a905>] irq_exit+0x45/0x50
[4295584.636000]  [<c0105c9e>] do_IRQ+0x1e/0x30
[4295584.636000]  [<c0103ef6>] common_interrupt+0x1a/0x20
[4295584.636000]  [<f084be9b>] acpi_processor_idle+0x184/0x32d [processor]
[4295584.636000]  [<c010111f>] cpu_idle+0x6f/0xc0
[4295584.636000]  [<c03a8a3a>] start_kernel+0x19a/0x200
[4295584.636000]  [<c03a83c0>] unknown_bootoption+0x0/0x1f0
[4295584.636000] handlers:
[4295584.636000] [<c0270110>] (ide_intr+0x0/0x1f0)
[4295584.636000] Disabling IRQ #3
[4295594.637000] hde: lost interrupt
[4295624.638000] hde: lost interrupt
[4295625.351000] irq 3: nobody cared (try booting with the "irqpoll" option)
[4295625.351000]  [<c014c73a>] __report_bad_irq+0x2a/0xa0
[4295625.351000]  [<c014befd>] handle_IRQ_event+0x3d/0x70
[4295625.351000]  [<c014c857>] note_interrupt+0x87/0xf0
[4295625.351000]  [<c014c02d>] __do_IRQ+0xfd/0x110
[4295625.351000]  [<c026fde0>] ide_timer_expiry+0x0/0x270
[4295625.351000]  [<c0105c99>] do_IRQ+0x19/0x30
[4295625.351000]  [<c0103ef6>] common_interrupt+0x1a/0x20
[4295625.351000]  [<c026fde0>] ide_timer_expiry+0x0/0x270
[4295625.351000]  [<c030caa6>] _spin_unlock_irqrestore+0x6/0x20
[4295625.351000]  [<c012f533>] run_timer_softirq+0xe3/0x1e0
[4295625.351000]  [<c014befd>] handle_IRQ_event+0x3d/0x70
[4295625.351000]  [<c012a782>] __do_softirq+0x72/0xe0
[4295625.351000]  [<c012a825>] do_softirq+0x35/0x40
[4295625.351000]  [<c012a905>] irq_exit+0x45/0x50
[4295625.351000]  [<c0105c9e>] do_IRQ+0x1e/0x30
[4295625.351000]  [<c0103ef6>] common_interrupt+0x1a/0x20
[4295625.351000]  [<f084be9b>] acpi_processor_idle+0x184/0x32d [processor]
[4295625.351000]  [<c010111f>] cpu_idle+0x6f/0xc0
[4295625.351000]  [<c03a8a3a>] start_kernel+0x19a/0x200
[4295625.351000]  [<c03a83c0>] unknown_bootoption+0x0/0x1f0
[4295625.351000] handlers:
[4295625.351000] [<c0270110>] (ide_intr+0x0/0x1f0)
[4295625.351000] Disabling IRQ #3
[4295625.371000]  hde1
[4295625.372000] ide-cs: hde: Vcc = 3.3, Vpp = 0.0
[4295626.043000]  hde:<4>hde: lost interrupt
[4295666.044000] hde: lost interrupt
[4295666.758000] irq 3: nobody cared (try booting with the "irqpoll" option)
[4295666.758000]  [<c014c73a>] __report_bad_irq+0x2a/0xa0
[4295666.758000]  [<c014befd>] handle_IRQ_event+0x3d/0x70
[4295666.758000]  [<c014c857>] note_interrupt+0x87/0xf0
[4295666.758000]  [<c014c02d>] __do_IRQ+0xfd/0x110
[4295666.758000]  [<c026fde0>] ide_timer_expiry+0x0/0x270
[4295666.758000]  [<c0105c99>] do_IRQ+0x19/0x30
[4295666.758000]  [<c0103ef6>] common_interrupt+0x1a/0x20
[4295666.758000]  [<c026fde0>] ide_timer_expiry+0x0/0x270
[4295666.758000]  [<c030caa6>] _spin_unlock_irqrestore+0x6/0x20
[4295666.758000]  [<c012f533>] run_timer_softirq+0xe3/0x1e0
[4295666.758000]  [<c014befd>] handle_IRQ_event+0x3d/0x70
[4295666.758000]  [<c012a782>] __do_softirq+0x72/0xe0
[4295666.758000]  [<c012a825>] do_softirq+0x35/0x40
[4295666.758000]  [<c012a905>] irq_exit+0x45/0x50
[4295666.758000]  [<c0105c9e>] do_IRQ+0x1e/0x30
[4295666.758000]  [<c0103ef6>] common_interrupt+0x1a/0x20
[4295666.758000]  [<f084be9b>] acpi_processor_idle+0x184/0x32d [processor]
[4295666.758000]  [<c010111f>] cpu_idle+0x6f/0xc0
[4295666.758000]  [<c03a8a3a>] start_kernel+0x19a/0x200
[4295666.758000]  [<c03a83c0>] unknown_bootoption+0x0/0x1f0
[4295666.758000] handlers:
[4295666.758000] [<c0270110>] (ide_intr+0x0/0x1f0)
[4295666.758000] Disabling IRQ #3
[4295666.778000]  hde1
[4295666.801000]  hde:<4>hde: lost interrupt
[4295677.517000] irq 3: nobody cared (try booting with the "irqpoll" option)
[4295677.517000]  [<c014c73a>] __report_bad_irq+0x2a/0xa0
[4295677.517000]  [<c014befd>] handle_IRQ_event+0x3d/0x70
[4295677.517000]  [<c014c857>] note_interrupt+0x87/0xf0
[4295677.517000]  [<c014c02d>] __do_IRQ+0xfd/0x110
[4295677.517000]  [<c026fde0>] ide_timer_expiry+0x0/0x270
[4295677.517000]  [<c0105c99>] do_IRQ+0x19/0x30
[4295677.517000]  [<c0103ef6>] common_interrupt+0x1a/0x20
[4295677.517000]  [<c026fde0>] ide_timer_expiry+0x0/0x270
[4295677.517000]  [<c030caa6>] _spin_unlock_irqrestore+0x6/0x20
[4295677.517000]  [<c012f533>] run_timer_softirq+0xe3/0x1e0
[4295677.517000]  [<c014befd>] handle_IRQ_event+0x3d/0x70
[4295677.517000]  [<c012a782>] __do_softirq+0x72/0xe0
[4295677.517000]  [<c012a825>] do_softirq+0x35/0x40
[4295677.517000]  [<c012a905>] irq_exit+0x45/0x50
[4295677.517000]  [<c0105c9e>] do_IRQ+0x1e/0x30
[4295677.517000]  [<c0103ef6>] common_interrupt+0x1a/0x20
[4295677.517000]  [<f084bd10>] acpi_safe_halt+0x16/0x1d [processor]
[4295677.517000]  [<f084be78>] acpi_processor_idle+0x161/0x32d [processor]
[4295677.517000]  [<c010111f>] cpu_idle+0x6f/0xc0
[4295677.517000]  [<c03a8a3a>] start_kernel+0x19a/0x200
[4295677.517000]  [<c03a83c0>] unknown_bootoption+0x0/0x1f0
[4295677.517000] handlers:
[4295677.517000] [<c0270110>] (ide_intr+0x0/0x1f0)
[4295677.517000] Disabling IRQ #3
[4295677.530000]  hde1
[4295677.544000]  hde:<4>hde: lost interrupt
[4295717.545000] hde: lost interrupt
[4295747.545000] hde: lost interrupt
[4295748.259000] irq 3: nobody cared (try booting with the "irqpoll" option)
[4295748.259000]  [<c014c73a>] __report_bad_irq+0x2a/0xa0
[4295748.259000]  [<c014befd>] handle_IRQ_event+0x3d/0x70
[4295748.259000]  [<c014c857>] note_interrupt+0x87/0xf0
[4295748.259000]  [<c014c02d>] __do_IRQ+0xfd/0x110
[4295748.259000]  [<c026fde0>] ide_timer_expiry+0x0/0x270
[4295748.259000]  [<c0105c99>] do_IRQ+0x19/0x30
[4295748.259000]  [<c0103ef6>] common_interrupt+0x1a/0x20
[4295748.259000]  [<c026fde0>] ide_timer_expiry+0x0/0x270
[4295748.259000]  [<c030caa6>] _spin_unlock_irqrestore+0x6/0x20
[4295748.259000]  [<c012f533>] run_timer_softirq+0xe3/0x1e0
[4295748.259000]  [<c014befd>] handle_IRQ_event+0x3d/0x70
[4295748.259000]  [<c012a782>] __do_softirq+0x72/0xe0
[4295748.259000]  [<c012a825>] do_softirq+0x35/0x40
[4295748.259000]  [<c012a905>] irq_exit+0x45/0x50
[4295748.259000]  [<c0105c9e>] do_IRQ+0x1e/0x30
[4295748.259000]  [<c0103ef6>] common_interrupt+0x1a/0x20
[4295748.259000]  [<f084be9b>] acpi_processor_idle+0x184/0x32d [processor]
[4295748.259000]  [<c010111f>] cpu_idle+0x6f/0xc0
[4295748.259000]  [<c03a8a3a>] start_kernel+0x19a/0x200
[4295748.259000]  [<c03a83c0>] unknown_bootoption+0x0/0x1f0
[4295748.259000] handlers:
[4295748.259000] [<c0270110>] (ide_intr+0x0/0x1f0)
[4295748.259000] Disabling IRQ #3
[4295748.277000]  hde1

the card is still in the slot.

i am sure if i remove the card, the icon will appear on the desktop and if i reinsert the card the laptop will freez.

is there anything more i can do.
please let me know.
thnnk u for ur help

---

### Post by ranf on 2006-06-06
[QUOTE=dksdk]hi ranf i tried booting with irgpoll[/QUOTE]
Did you write it with a G instead of Q? You have to seperate it from the last parameter with space.
If you did it right and it still doesn't work then I'm out of ideas. Sorry.

---

### Post by dksdk on 2006-06-06
hi sorry i did try it with correct spell and space.
anyway thank you for ur help

---

### Post by James Keating on 2006-06-08
When I tried the irqpoll option, I got messages starting with 
     BUG: soft lockup detected on CPU#0!
     disabling IRQ#11
and soon the kernel freaked out, spewing out a message about the hard drive, and I had to do a hard reboot. 

I'm just going to boot with an older kernel.

(Later ...) This seems to be due to a kernel bug. After three days and much frustration, the solution for my problem came from Daniel Carrera on another thread. You have to insert the modules by hand, then start cardmgr to watch the card.

sudo modprobe pcmcia && modprobe pcmcia_core
sudo cardmgr

Some people say you need to eject and insert the card after activating the modules, but I didn't need to.

Hope something like this works for your situation too.

---

