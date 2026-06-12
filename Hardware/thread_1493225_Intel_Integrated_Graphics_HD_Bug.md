---
title: "Intel Integrated Graphics HD Bug"
date: 2010-05-25
forum: Hardware
---

### Post by SirKonstantine on 2010-05-25
I been using Ubuntu 10.04 on a Gateway NV 5972u for a few months. It had this problem for awhile, but it was pretty rare and I just ignored it. Since I update from 2.6.32-21 to 2.6.32-22, the problem happens REALLY often now, especially when I hook my laptop to my 25.5'' HD LCD.

The problem is that I would be in GNOME, and it'll just kick me to gdm without warning. Here is the thing from kernel.log:

```

konstantine@sheep:~$ tail /var/log/kern.log
May 25 10:30:52 sheep kernel: [   60.005219]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
May 25 10:30:52 sheep kernel: [   60.005221]  [<ffffffff81080850>] ? worker_thread+0x0/0x110
May 25 10:30:52 sheep kernel: [   60.005224]  [<ffffffff81084fa6>] kthread+0x96/0xa0
May 25 10:30:52 sheep kernel: [   60.005227]  [<ffffffff810141ea>] child_rip+0xa/0x20
May 25 10:30:52 sheep kernel: [   60.005229]  [<ffffffff81084f10>] ? kthread+0x0/0xa0
May 25 10:30:52 sheep kernel: [   60.005231]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
May 25 10:30:52 sheep kernel: [   60.005233] ---[ end trace 784e7c9f04e0a7b6 ]---
May 25 10:30:52 sheep kernel: [   60.084779] wlan0: deauthenticating from 94:44:52:3b:c1:13 by local choice (reason=3)
May 25 13:41:10 sheep kernel: [11453.553054] [drm:i915_gem_do_execbuffer] *ERROR* Failed to pin buffer 2 of 3, total 70352896 bytes: -28
May 25 13:41:10 sheep kernel: [11453.553059] [drm:i915_gem_do_execbuffer] *ERROR* 1576 objects [6 pinned], 299589632 object bytes [56324096 pinned], 56324096/134217728 gtt bytes

```

here is lspci:

```

konstantine@sheep:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
04:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

I looked on google, and it seemed that this is a kernel bug. Do I just sit around and wait for this kernel but to be fixed, then wait until ubuntu adopts the fixed kernel? or is there another way to fix this problem?

I think I'll be forced to use win7 and have Ubuntu run in virtualbox if I can't find a fix for this. Thanks.

---

### Post by Saghaulor on 2010-05-31
> **SirKonstantine said:**
> I been using Ubuntu 10.04 on a Gateway NV 5972u for a few months. It had this problem for awhile, but it was pretty rare and I just ignored it. Since I update from 2.6.32-21 to 2.6.32-22, the problem happens REALLY often now, especially when I hook my laptop to my 25.5'' HD LCD.

The problem is that I would be in GNOME, and it'll just kick me to gdm without warning. Here is the thing from kernel.log:

```

konstantine@sheep:~$ tail /var/log/kern.log
May 25 10:30:52 sheep kernel: [   60.005219]  [<ffffffff81085320>] ? autoremove_wake_function+0x0/0x40
May 25 10:30:52 sheep kernel: [   60.005221]  [<ffffffff81080850>] ? worker_thread+0x0/0x110
May 25 10:30:52 sheep kernel: [   60.005224]  [<ffffffff81084fa6>] kthread+0x96/0xa0
May 25 10:30:52 sheep kernel: [   60.005227]  [<ffffffff810141ea>] child_rip+0xa/0x20
May 25 10:30:52 sheep kernel: [   60.005229]  [<ffffffff81084f10>] ? kthread+0x0/0xa0
May 25 10:30:52 sheep kernel: [   60.005231]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
May 25 10:30:52 sheep kernel: [   60.005233] ---[ end trace 784e7c9f04e0a7b6 ]---
May 25 10:30:52 sheep kernel: [   60.084779] wlan0: deauthenticating from 94:44:52:3b:c1:13 by local choice (reason=3)
May 25 13:41:10 sheep kernel: [11453.553054] [drm:i915_gem_do_execbuffer] *ERROR* Failed to pin buffer 2 of 3, total 70352896 bytes: -28
May 25 13:41:10 sheep kernel: [11453.553059] [drm:i915_gem_do_execbuffer] *ERROR* 1576 objects [6 pinned], 299589632 object bytes [56324096 pinned], 56324096/134217728 gtt bytes

```

here is lspci:

```

konstantine@sheep:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
04:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

I looked on google, and it seemed that this is a kernel bug. Do I just sit around and wait for this kernel but to be fixed, then wait until ubuntu adopts the fixed kernel? or is there another way to fix this problem?

I think I'll be forced to use win7 and have Ubuntu run in virtualbox if I can't find a fix for this. Thanks.

I've had a lot of problems with that chipset and Compiz. Have you tried turning off compiz?

---

### Post by nono240 on 2010-10-29
Please add yourself to the [bug ]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/528432")list to help raise the interest.

---

