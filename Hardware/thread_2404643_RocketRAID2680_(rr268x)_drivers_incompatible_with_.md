---
title: "RocketRAID2680 (rr268x) drivers incompatible with 18.04"
date: 2018-10-26
forum: Hardware
---

### Post by no-shadows on 2018-10-26
Hi

I currently trying to update my system from 17.04 to 18.04
The main problem is the RocketRAID2680 driver which can not be compiled anymore.

I'll add my current driver files, which worked under 17.04. I think they are mostly from this forum.
[ATTACH]281453[/ATTACH]
[ATTACH]281454[/ATTACH]

---

### Post by no-shadows on 2018-10-26
I was able to fix the compilation errors in
../rr268x/osm/linux/os_linux.c
[ATTACH]281455[/ATTACH]

Now I get the following errors
```

make[1]: Entering directory '/usr/src/linux-headers-4.15.0-38-generic'
  CC [M]  /home/noshadows/Raid/rr268x/product/rr2680/linux/.build/os_linux.o
  CC [M]  /home/noshadows/Raid/rr268x/product/rr2680/linux/.build/osm_linux.o
/home/noshadows/Raid/rr268x/product/rr2680/linux/.build/osm_linux.c: In function ‘hpt_detect’:
/home/noshadows/Raid/rr268x/product/rr2680/linux/.build/osm_linux.c:322:3: error: implicit declaration of function ‘init_timer’; did you mean ‘init_timers’? [-Werror=implicit-function-declaration]
   init_timer(&vbus_ext->timer);
   ^~~~~~~~~~
   init_timers
/home/noshadows/Raid/rr268x/product/rr2680/linux/.build/osm_linux.c: In function ‘hpt_flush_vdev’:
/home/noshadows/Raid/rr268x/product/rr2680/linux/.build/osm_linux.c:1523:8: error: ‘struct timer_list’ has no member named ‘data’
   timer.data = (HPT_UPTR)&sem;
        ^
/home/noshadows/Raid/rr268x/product/rr2680/linux/.build/osm_linux.c:1524:18: error: assignment from incompatible pointer type [-Werror=incompatible-pointer-types]
   timer.function = cmd_timeout_sem;
                  ^
/home/noshadows/Raid/rr268x/product/rr2680/linux/.build/osm_linux.c: In function ‘__hpt_do_ioctl’:
/home/noshadows/Raid/rr268x/product/rr2680/linux/.build/osm_linux.c:1683:8: error: ‘struct timer_list’ has no member named ‘data’
   timer.data = (HPT_UPTR)&sem;
        ^
/home/noshadows/Raid/rr268x/product/rr2680/linux/.build/osm_linux.c:1684:18: error: assignment from incompatible pointer type [-Werror=incompatible-pointer-types]
   timer.function = hpt_ioctl_timeout;
                  ^
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/home/noshadows/Raid/rr268x/product/rr2680/linux/.build/osm_linux.o' failed
make[2]: *** [/home/noshadows/Raid/rr268x/product/rr2680/linux/.build/osm_linux.o] Error 1
Makefile:1551: recipe for target '_module_/home/noshadows/Raid/rr268x/product/rr2680/linux/.build' failed
make[1]: *** [_module_/home/noshadows/Raid/rr268x/product/rr2680/linux/.build] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-38-generic'
../../../inc/linux_32mpa/Makefile.def:106: recipe for target 'rr2680.ko' failed
make: *** [rr2680.ko] Error 2

```

---

### Post by no-shadows on 2018-10-26
I was able to fix the compilation errors in
../rr268x/osm/linux/osm_linux.c
[ATTACH]281457[/ATTACH]

looks acceptable
```

make[1]: Entering directory '/usr/src/linux-headers-4.15.0-38-generic'
  CC [M]  /home/noshadows/Raid/rr268x/product/rr2680/linux/.build/os_linux.o
  CC [M]  /home/noshadows/Raid/rr268x/product/rr2680/linux/.build/osm_linux.o
  CC [M]  /home/noshadows/Raid/rr268x/product/rr2680/linux/.build/div64.o
  CC [M]  /home/noshadows/Raid/rr268x/product/rr2680/linux/.build/hptinfo.o
  CC [M]  /home/noshadows/Raid/rr268x/product/rr2680/linux/.build/config.o
  LD [M]  /home/noshadows/Raid/rr268x/product/rr2680/linux/.build/rr2680.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/noshadows/Raid/rr268x/product/rr2680/linux/.build/rr2680.o
see include/linux/module.h for more information
WARNING: could not find /home/noshadows/Raid/rr268x/product/rr2680/linux/.build/.him_rr2680.o.cmd for /home/noshadows/Raid/rr268x/product/rr2680/linux/.build/him_rr2680.o
  CC      /home/noshadows/Raid/rr268x/product/rr2680/linux/.build/rr2680.mod.o
  LD [M]  /home/noshadows/Raid/rr268x/product/rr2680/linux/.build/rr2680.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-38-generic'

```

I'll try it. Wish me luck.

---

### Post by no-shadows on 2018-10-26
Pity
modprobe rr2680 do not work

dmesg
```

[25266.817433] rr2680: module license 'unspecified' taints kernel.
[25266.817436] Disabling lock debugging due to kernel taint
[25266.817962] rr2680: Unknown symbol sev_enable_key (err 0)
[25281.455771] rr2680: Unknown symbol sev_enable_key (err 0)
[25906.302330] rr2680: Unknown symbol sev_enable_key (err 0)
[26169.502552] rr2680: Unknown symbol sev_enable_key (err 0)

```

I think the problem is on the end of ../rr268x/osm/linux/osm_linux.c
```

#if LINUX_VERSION_CODE <= KERNEL_VERSION(4, 15, 0)
#if LINUX_VERSION_CODE >= KERNEL_VERSION(2,4,10)
MODULE_LICENSE("Proprietary");
#endif
#endif

```

but I have no Idea how to fix it. without the violenting some licences.
if you write the following instead it May works but I think  that is not legal.
```

#if LINUX_VERSION_CODE <= KERNEL_VERSION(4, 15, 0)
#if LINUX_VERSION_CODE >= KERNEL_VERSION(2,4,10)
MODULE_LICENSE("Proprietary");
#endif
#else
MODULE_LICENSE("GPL");
#endif

```

Realy Helpful to comming this far was 
[https://ubuntuforums.org/showthread.php?t=2392396&highlight=RocketRaid+18](https://ubuntuforums.org/showthread.php?t=2392396&highlight=RocketRaid+18)

---

