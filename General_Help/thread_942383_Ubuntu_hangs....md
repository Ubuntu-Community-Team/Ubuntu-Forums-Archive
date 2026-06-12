---
title: "Ubuntu hangs..."
date: 2008-10-09
forum: General Help
---

### Post by martin_legion on 2008-10-09
Hello. I have a computer running Ubuntu Hardy Desktop as a simple server of ssh, apache, ftp and cups. It's a quite new PC, with 1gb of ram, and the clients really don't consume a lot of resources.
A few days ago, it hanged, and couldn't find the reason. Since then I monitor a few logs and the use of memory.
Today, it hanged again. Here's /var/log/messages:

```
Oct  9 09:45:23 laboralnuevo kernel: [228871.484350] 
Oct  9 09:45:23 laboralnuevo kernel: [228871.484352] Pid: 9731, comm: mad Not tainted (2.6.24-19-generic #1)
Oct  9 09:45:23 laboralnuevo kernel: [228871.484355] EIP: 0060:[__read_lock_failed+0x5/0x10] EFLAGS: 00000297 CPU: 1
Oct  9 09:45:23 laboralnuevo kernel: [228871.484361] EIP is at __read_lock_failed+0x5/0x10
Oct  9 09:45:23 laboralnuevo kernel: [228871.484363] EAX: f680d2fc EBX: f680d200 ECX: fffff000 EDX: f680d2d4
Oct  9 09:45:23 laboralnuevo kernel: [228871.484365] ESI: 00000000 EDI: 00000000 EBP: 00000007 ESP: f7869e28
Oct  9 09:45:23 laboralnuevo kernel: [228871.484367]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
Oct  9 09:45:23 laboralnuevo kernel: [228871.484368] CR0: 8005003b CR2: 087b4f94 CR3: 36f92000 CR4: 00000690
Oct  9 09:45:23 laboralnuevo kernel: [228871.484372] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Oct  9 09:45:23 laboralnuevo kernel: [228871.484375] DR6: ffff0ff0 DR7: 00000400
Oct  9 09:45:23 laboralnuevo kernel: [228871.484378]  [snd_seq:_read_lock+0xb/0x60] _read_lock+0xb/0x10
Oct  9 09:45:23 laboralnuevo kernel: [228871.484391]  [<f89a3125>] parport_irq_handler+0x15/0x40 [parport]
Oct  9 09:45:23 laboralnuevo kernel: [228871.484405]  [handle_IRQ_event+0x30/0x60] handle_IRQ_event+0x30/0x60
Oct  9 09:45:23 laboralnuevo kernel: [228871.484414]  [handle_edge_irq+0xba/0x120] handle_edge_irq+0xba/0x120
Oct  9 09:45:23 laboralnuevo kernel: [228871.484423]  [do_IRQ+0x3b/0x70] do_IRQ+0x3b/0x70
Oct  9 09:45:23 laboralnuevo kernel: [228871.484433]  [common_interrupt+0x23/0x30] common_interrupt+0x23/0x30
Oct  9 09:45:23 laboralnuevo kernel: [228871.484445]  [<f8a12292>] parport_pc_restore_state+0x22/0x50 [parport_pc]
Oct  9 09:45:23 laboralnuevo kernel: [228871.484457]  [<f89a3291>] parport_claim+0x141/0x1f0 [parport]
Oct  9 09:45:23 laboralnuevo kernel: [228871.484465]  [ide_core:kunmap_atomic+0x3d/0x2f30] kunmap_atomic+0x3d/0xb0
Oct  9 09:45:23 laboralnuevo kernel: [228871.484474]  [<f89a3465>] parport_release+0x125/0x150 [parport]
Oct  9 09:45:23 laboralnuevo kernel: [228871.484484]  [<f89a41bd>] parport_wait_peripheral+0x3d/0xf0 [parport]
Oct  9 09:45:23 laboralnuevo kernel: [228871.484496]  [<f89a5347>] parport_ieee1284_write_compat+0x1d7/0x1f0 [parport]
Oct  9 09:45:23 laboralnuevo kernel: [228871.484508]  [<f89a5170>] parport_ieee1284_write_compat+0x0/0x1f0 [parport]
Oct  9 09:45:23 laboralnuevo kernel: [228871.484519]  [<f89a48b4>] parport_write+0xa4/0x110 [parport]
Oct  9 09:45:23 laboralnuevo kernel: [228871.484530]  [<f8a5ce1e>] lp_write+0x23e/0x2f4 [lp]
Oct  9 09:45:23 laboralnuevo kernel: [228871.484543]  [<f8a5cbe0>] lp_write+0x0/0x2f4 [lp]
Oct  9 09:45:23 laboralnuevo kernel: [228871.484550]  [vfs_write+0xb9/0x170] vfs_write+0xb9/0x170
Oct  9 09:45:23 laboralnuevo kernel: [228871.484556]  [vfs_ioctl+0x22e/0x2b0] vfs_ioctl+0x22e/0x2b0
Oct  9 09:45:23 laboralnuevo kernel: [228871.484564]  [sys_write+0x41/0x70] sys_write+0x41/0x70
Oct  9 09:45:23 laboralnuevo kernel: [228871.484572]  [syscall_call+0x7/0x0b] syscall_call+0x7/0xb
Oct  9 09:45:23 laboralnuevo kernel: [228871.484586]  =======================
```

After it died, the printer (HP Laserjet 4250) was showing a weird error message in it's display (I didn't write it down...) and I had to turn it off and on for it to react again.

Something I noticed, but maybe is a normal thing, is that the days were passing on, and the available memory was slowly going down.

This is before the hang:

```
             total       used       free     shared    buffers     cached
Mem:        904192     864212      39980          0     173388     543336
```

And after the reboot:

```
             total       used       free     shared    buffers     cached
Mem:        904192     292708     611484          0      84812     152640
```

¿Any clues?
Thanks!

---

### Post by martin_legion on 2008-10-09
The printer died again. Here's the error message shown in the display:

```
49.4C02 Service Error
```

and /var/log/syslog:

```
Oct  9 12:49:14 laboralnuevo parport0: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Oct  9 12:49:14 laboralnuevo kernel: [10953.397517] ppdev0: registered pardevice
Oct  9 12:57:02 laboralnuevo parport0: io/hpmud/pp.c 517: compat_write_data transfer stalled 
Oct  9 12:57:02 laboralnuevo parport0: io/hpmud/musb.c 1339: unable to write data hp:/par/hp_LaserJet_4250?device=/dev/parport0: Connection refused 
Oct  9 12:57:32 laboralnuevo parport0: io/hpmud/pp.c 517: compat_write_data transfer stalled 
Oct  9 12:57:32 laboralnuevo parport0: io/hpmud/musb.c 1339: unable to write data hp:/par/hp_LaserJet_4250?device=/dev/parport0: Connection refused 
Oct  9 12:58:02 laboralnuevo parport0: io/hpmud/pp.c 517: compat_write_data transfer stalled 
Oct  9 12:58:02 laboralnuevo parport0: io/hpmud/musb.c 1339: unable to write data hp:/par/hp_LaserJet_4250?device=/dev/parport0: Connection refused 
Oct  9 12:58:32 laboralnuevo parport0: io/hpmud/pp.c 517: compat_write_data transfer stalled 
Oct  9 12:58:32 laboralnuevo parport0: io/hpmud/musb.c 1339: unable to write data hp:/par/hp_LaserJet_4250?device=/dev/parport0: Connection refused 
Oct  9 12:59:02 laboralnuevo parport0: io/hpmud/pp.c 517: compat_write_data transfer stalled 
Oct  9 12:59:02 laboralnuevo parport0: io/hpmud/musb.c 1339: unable to write data hp:/par/hp_LaserJet_4250?device=/dev/parport0: Connection refused 
Oct  9 12:59:32 laboralnuevo parport0: io/hpmud/pp.c 517: compat_write_data transfer stalled 
Oct  9 12:59:32 laboralnuevo parport0: io/hpmud/musb.c 1339: unable to write data hp:/par/hp_LaserJet_4250?device=/dev/parport0: Connection refused 

```

The computer is still alive... so far...

Note: 
When this printer error happened, they were trying to print something from a program that prints using "lpr" and, in some cases, it also prints directly into /dev/lp0.

Any help would be great!

Thanks

M.

---

