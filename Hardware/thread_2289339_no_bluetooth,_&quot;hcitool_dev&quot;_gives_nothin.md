---
title: "no bluetooth, &quot;hcitool dev&quot; gives nothing, device noticable in /sys"
date: 2015-08-03
forum: Hardware
---

### Post by zhangweiwu on 2015-08-03
Hi. For the last 10 years I never managed to keep a bluetooth device connected with any linux, from Ubuntu to SuSE. Usually it's frequent disconnet that troubles me, but this time (with a new computer and new release) I can't even reach there.

Using Ubunt 15.04, 32-bit.

I fond my bluetooth device here:

```

root@kimble:~# cd /sys/devices/platform/INT33BB:00/mmc_host/mmc1/mmc1:0001/mmc1:0001:3/
root@kimble:/sys/devices/platform/INT33BB:00/mmc_host/mmc1/mmc1:0001/mmc1:0001:3# cat vendor ; cat device 
0x02d0
0xa94d
oot@kimble:/sys/devices/platform/INT33BB:00/mmc_host/mmc1/mmc1:0001/mmc1:0001:3# ls bluetooth/hci0/*
bluetooth/hci0/address  bluetooth/hci0/name  bluetooth/hci0/type  bluetooth/hci0/uevent

bluetooth/hci0/device:
bluetooth  class  device  driver  modalias  power  subsystem  uevent  vendor

bluetooth/hci0/power:
async                 control              runtime_active_time  runtime_status          runtime_usage
autosuspend_delay_ms  runtime_active_kids  runtime_enabled      runtime_suspended_time

bluetooth/hci0/rfkill0:
claim  device  hard  index  name  persistent  power  soft  state  subsystem  type  uevent

bluetooth/hci0/subsystem:
hci0

```

So it seems to be a lot of stuff about bluetooth, but if I slide the UI to turn on bluetooth in unity-control-centre, it can't discover any bluetooth devices. Also hcitool gives no output:

```

root@kimble:/sys/devices/platform/INT33BB:00/mmc_host/mmc1/mmc1:0001/mmc1:0001:3# hcitool dev
Devices:
root@kimble:/sys/devices/platform/INT33BB:00/mmc_host/mmc1/mmc1:0001/mmc1:0001:3# hcitool scan
Device is not available: No such device

```

Kernel being 
```

# uname -a
Linux kimble 4.2.0-040200rc5-generic #201508030228 SMP Mon Aug 3 02:39:07 UTC 2015 i686 i686 i686 GNU/Linux

```

It's the latest kernel I grab from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) out of the frastration the shipped kernel can't drive it neither.

Where to go from here? Thanks!

---

