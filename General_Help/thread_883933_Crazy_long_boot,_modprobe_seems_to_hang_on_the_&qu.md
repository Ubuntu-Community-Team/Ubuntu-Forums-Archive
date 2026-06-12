---
title: "Crazy long boot, modprobe seems to hang on the &quot;loop&quot; module"
date: 2008-08-08
forum: General Help
---

### Post by goldfish654 on 2008-08-08
... or I may just be reading it wrong

Here's what dmesg says:
```

[   28.380132] Pid: 3687, comm: modprobe Not tainted 2.6.24-19-generic #1
[   28.380136]  [<c02159c3>] kobject_add+0x113/0x1b0
[   28.380144]  [<c0215af1>] kobject_register+0x21/0x50
[   28.380149]  [<c0281ff1>] bus_add_driver+0x71/0x1e0
[   28.380158]  [<c01507c6>] sys_init_module+0x126/0x19c0
[   28.380183]  [<c013f260>] param_get_int+0x0/0x20
[   28.380194]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[   28.380206]  =======================
[   29.960818] cs: IO port probe 0x100-0x3af: clean.
[   29.961811] cs: IO port probe 0x3e0-0x4ff: clean.
[   29.962240] cs: IO port probe 0x820-0x8ff: clean.
[   29.962610] cs: IO port probe 0xc00-0xcf7: clean.
[   29.963131] cs: IO port probe 0xa00-0xaff: clean.
[   29.963728] cs: IO port probe 0x100-0x3af: clean.
[   29.964727] cs: IO port probe 0x3e0-0x4ff: clean.
[   29.965156] cs: IO port probe 0x820-0x8ff: clean.
[   29.965525] cs: IO port probe 0xc00-0xcf7: clean.
[   29.966047] cs: IO port probe 0xa00-0xaff: clean.
[  206.964392] loop: module loaded
[  207.032758] lp0: using parport0 (interrupt-driven).
[  207.218967] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
[  207.791839] EXT3 FS on sda1, internal journal
[  209.242839] ip_tables: (C) 2000-2006 Netfilter Core Team
[  211.476888] NET: Registered protocol family 10
[  211.477452] lo: Disabled Privacy Extensions
[  212.506859] IBM machine detected. Enabling interrupts during APM calls.
[  212.506867] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  212.805601] ppdev: user-space parallel port driver
[  213.055323] audit(1218212926.249:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=16634 profile="/usr/sbin/cupsd" namespace="default"
[  213.352760] Non-volatile memory driver v1.2

```

Note the giant gap between 
```

[   29.966047] cs: IO port probe 0xa00-0xaff: clean.

```
and
```

[  206.964392] loop: module loaded

```

I may be reading this wrong - though.  I realise there is a bit of paralellism going on so it's a bit difficult to see really, but given that the loop module is loaded a good 180 seconds after everything else has, I don't know what else to go on.  

Any ideas?

---

