---
title: "RocketRAID 2310 on 2.6.20"
date: 2007-03-28
forum: Hardware &amp; Laptops
---

### Post by hackeron on 2007-03-28
The driver compiled fine on 2.6.19 but I'm trying to compile the latest driver on 2.6.20 available from HighPoint here: [http://www.highpoint-tech.com/USA/bios_rr2310.htm#linux](http://www.highpoint-tech.com/USA/bios_rr2310.htm#linux) and I'm getting this:

```
# make KERNELDIR=/root/2.6.20.4/linux-2.6.20.4
make[1]: Entering directory `/root/2.6.20.4/linux-2.6.20.4'
  CC [M]  /root/2.6.20.4/rr2310_00-linux-src-1.14/osm/linux/os_linux.o
  CC [M]  /root/2.6.20.4/rr2310_00-linux-src-1.14/osm/linux/osm_linux.o
  CC [M]  /root/2.6.20.4/rr2310_00-linux-src-1.14/osm/linux/div64.o
  CC [M]  /root/2.6.20.4/rr2310_00-linux-src-1.14/osm/linux/hptinfo.o
  CC [M]  /root/2.6.20.4/rr2310_00-linux-src-1.14/product/rr2310/linux/config.o
  LD [M]  /root/2.6.20.4/rr2310_00-linux-src-1.14/product/rr2310/linux/.build/rr2310_00.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /root/2.6.20.4/rr2310_00-linux-src-1.14/product/rr2310/linux/.build/.os_linux.o.cmd for /root/2.6.20.4/rr2310_00-linux-src-1.14/product/rr2310/linux/.build/os_linux.o
FATAL: modpost: GPL-incompatible module rr2310_00.ko uses GPL-only symbol 'paravirt_ops'
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/root/2.6.20.4/linux-2.6.20.4'
make: *** [rr2310_00.ko] Error 2
```

If I compile with:

```
make patchkernel KERNELDIR=/root/2.6.20.4/linux-2.6.20.4
```

It compiles fine, but kernel freezes on boot after showing rr2310 version 1.14 on screen :(

Anyone had any success with this thing on 2.6.20 or later?

EDIT: Same behaviour with rr2310 version 2.0 on 2.6.21.1

---

### Post by hackeron on 2007-06-10
highpoint-tech still didn't address this problem 3 months after reporting it :( -- If anyone has a solution, help would be highly appreciated. For anyone considering purchasing this card because of the advertised open-source linux support, don't, stay far far away.

---

### Post by hackeron on 2007-07-13
I have read in the kernel changelog that this should be supported with the experimental sata_mv module, but I'm now on 2.6.21.1 and I get the following when I try to load the module:

```

[  859.163000] kobject_add failed for sata_mv with -EEXIST, don't try to register things with the same name in the same directory.
[  859.163000]  [<c01e89f2>] kobject_shadow_add+0x132/0x1c0
[  859.164000]  [<c013ff34>] mod_sysfs_setup+0x24/0xb0
[  859.164000]  [<c0141417>] sys_init_module+0x1287/0x1770
[  859.164000]  [<c0152c8d>] filemap_nopage+0x2fd/0x410
[  859.164000]  [<c026b440>] ata_device_add+0x0/0x570
[  859.164000]  [<c01e7aca>] _atomic_dec_and_lock+0x2a/0x50
[  859.164000]  [<c0188193>] mntput_no_expire+0x13/0xa0
[  859.164000]  [<c010425c>] syscall_call+0x7/0xb
[  859.164000]  =======================

```

Any ideas?

---

