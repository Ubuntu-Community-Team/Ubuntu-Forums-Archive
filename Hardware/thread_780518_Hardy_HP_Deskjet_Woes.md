---
title: "Hardy HP Deskjet Woes"
date: 2008-05-03
forum: Hardware
---

### Post by j2fraser on 2008-05-03
I had an HP Deskjet 722C working flawlessly under Gutsy. Since upgrading to Hardy, it has stopped working, and I'm at a bit of a loss to figure it out.

The printer is connected by a PCI parallel port card. Dmesg:

```
[   31.169034] PCI parallel port detected: 1407:8000, I/O at 0xb8d8(0x0)
[   31.169055] parport0: PC-style at 0xb8d8 [PCSPP,TRISTATE,EPP]
[   31.280870] parport0: Printer, HEWLETT-PACKARD DESKJET 720C
```

My /var/log/cups/error_log, contains a bunch of the entries like the following, although I'm not sure if it is related...:

```
E [02/May/2008:10:02:28 -0600] DNSServiceRegister failed with error -65537
E [02/May/2008:17:18:50 -0600] DNSServiceRegister failed with error -65537
E [02/May/2008:23:39:27 -0600] DNSServiceRegister failed with error -65537
E [03/May/2008:10:07:35 -0600] DNSServiceRegister failed with error -65537
```

I get a pop-up telling me "Printer 'Deskjet 722C' may not be connected," but it is connected and powered up (not that the latter has ever proven necessary).

Syslog shows the following repeating every 30 seconds:

```
May  3 13:06:16 desktop kernel: [ 2059.356230] sysctl table check failed: /dev/parport/parport0/devices/ppdev0/timeslice  Sysctl already exists
May  3 13:06:16 desktop kernel: [ 2059.356247] Pid: 7531, comm: hp Tainted: P        2.6.24-16-generic #1
May  3 13:06:16 desktop kernel: [ 2059.356249] 
May  3 13:06:16 desktop kernel: [ 2059.356250] Call Trace:
May  3 13:06:16 desktop kernel: [ 2059.356283]  [set_fail+0x4d/0x70] set_fail+0x4d/0x70
May  3 13:06:16 desktop kernel: [ 2059.356301]  [sysctl_check_table+0x2c5/0x620] sysctl_check_table+0x2c5/0x620
May  3 13:06:16 desktop kernel: [ 2059.356309]  [sysctl_check_lookup+0xc6/0xe0] sysctl_check_lookup+0xc6/0xe0
May  3 13:06:16 desktop kernel: [ 2059.356342]  [sysctl_check_table+0x2db/0x620] sysctl_check_table+0x2db/0x620
May  3 13:06:16 desktop kernel: [ 2059.356351]  [sysctl_check_lookup+0xc6/0xe0] sysctl_check_lookup+0xc6/0xe0
May  3 13:06:16 desktop kernel: [ 2059.356383]  [sysctl_check_table+0x2db/0x620] sysctl_check_table+0x2db/0x620
May  3 13:06:16 desktop kernel: [ 2059.356392]  [sysctl_check_lookup+0xc6/0xe0] sysctl_check_lookup+0xc6/0xe0
May  3 13:06:16 desktop kernel: [ 2059.356425]  [sysctl_check_table+0x2db/0x620] sysctl_check_table+0x2db/0x620
May  3 13:06:16 desktop kernel: [ 2059.356433]  [sysctl_check_lookup+0xc6/0xe0] sysctl_check_lookup+0xc6/0xe0
May  3 13:06:16 desktop kernel: [ 2059.356466]  [sysctl_check_table+0x2db/0x620] sysctl_check_table+0x2db/0x620
May  3 13:06:16 desktop kernel: [ 2059.356474]  [sysctl_check_lookup+0xc6/0xe0] sysctl_check_lookup+0xc6/0xe0
May  3 13:06:16 desktop kernel: [ 2059.356507]  [sysctl_check_table+0x2db/0x620] sysctl_check_table+0x2db/0x620
May  3 13:06:16 desktop kernel: [ 2059.356549]  [cdrom:register_sysctl_table+0x60/0xe0] register_sysctl_table+0x60/0xc0
May  3 13:06:16 desktop kernel: [ 2059.356573]  [parport:parport_device_proc_register+0xd1/0x110] :parport:parport_device_proc_register+0xd1/0x110
May  3 13:06:16 desktop kernel: [ 2059.356594]  [parport:parport_register_device+0x18f/0x2c0] :parport:parport_register_device+0x18f/0x2c0
May  3 13:06:16 desktop kernel: [ 2059.356605]  [<ffffffff88659250>] :ppdev:pp_irq+0x0/0x50
May  3 13:06:16 desktop kernel: [ 2059.356638]  [<ffffffff886597cf>] :ppdev:pp_ioctl+0x48f/0x8b0
May  3 13:06:16 desktop kernel: [ 2059.356654]  [do_filp_open+0x3a/0x50] do_filp_open+0x3a/0x50
May  3 13:06:16 desktop kernel: [ 2059.356687]  [do_ioctl+0x7d/0xa0] do_ioctl+0x7d/0xa0
May  3 13:06:16 desktop kernel: [ 2059.356703]  [vfs_ioctl+0x220/0x2c0] vfs_ioctl+0x220/0x2c0
May  3 13:06:16 desktop kernel: [ 2059.356735]  [sys_ioctl+0x91/0xb0] sys_ioctl+0x91/0xb0
May  3 13:06:16 desktop kernel: [ 2059.356768]  [system_call+0x7e/0x83] system_call+0x7e/0x83
May  3 13:06:16 desktop kernel: [ 2059.356830] 
May  3 13:06:16 desktop kernel: [ 2059.356833] ppdev0: registered pardevice
May  3 13:06:16 desktop parport0: io/hpmud/pp.c 627: unable to read device-id ret=-110 
May  3 13:06:16 desktop parport0: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
May  3 13:06:16 desktop parport0: prnt/backend/hp.c 636: INFO: open device failed; will retry in 30 seconds...
```

Any assistance would be greatly appreciated!!!

---

### Post by j2fraser on 2008-05-03
bump?

---

### Post by j2fraser on 2008-05-04
bump?

---

### Post by j2fraser on 2008-05-04
Never mind. I "re"-installed the printer, and the printer (which had previously been hanging out at Device URI "hp:/par/DESKJET_720C?device=/dev/parport0", now wants to hang out at Device URI "parallel:/dev/lp0". Works fine now.

---

