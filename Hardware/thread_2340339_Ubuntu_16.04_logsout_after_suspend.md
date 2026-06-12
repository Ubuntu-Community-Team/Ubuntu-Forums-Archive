---
title: "Ubuntu 16.04 logsout after suspend"
date: 2016-10-17
forum: Hardware
---

### Post by bestoe on 2016-10-17
Hi,

so far I haven't found the solution to this:
Sometimes (not always) I get completly logout after suspend. This means all program have to be restarted. Whatever hasn't been saved is gone :confused:. There have been other suggestions for similar problems like adding in the /etc/default/grub the line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi='!Windows 2013' acpi_osi='!Windows 2012' "


```
Did not work. So I'm here now. Ok. here is the system and an output to dmesg:
```
uname -a
Linux bs 4.4.0-38-generic #57-Ubuntu SMP Tue Sep 6 15:42:33 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


```

It is a Lenovo Thinkpad T410.

```
lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation QM57 Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
0d:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
0d:00.1 System peripheral: Ricoh Co Ltd R5U2xx (R5U230 / R5U231 / R5U241) [Memory Stick Host Controller] (rev 01)
0d:00.3 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 PCIe IEEE 1394 Controller (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 02)

```

In the dmesg there is the following strange part:
```

...
[106271.381996] PM: Finishing wakeup.
[106271.381997] Restarting tasks ... done.
[106272.262823] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: 
Rx
[106273.627061] e1000e: eth0 NIC Link is Down
[106273.787523] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[106273.787622] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[106273.787844] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[106273.787935] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x1
[106274.002673] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[106274.002900] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[106274.002992] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x1
[106274.082659] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[106274.083808] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[106274.296616] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[106274.655170] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[106275.874881] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx
[106275.874941] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[106276.652426] [drm] stuck on render ring
[106276.656134] [drm] GPU HANG: ecode 5:0:0xb5cefffc, in compiz [2650], reason: Ring hung, action: reset
[106276.660293] drm/i915: Resetting chip after gpu hang
...
[106284.257739] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[106284.257740] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[106284.257742] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[106291.652513] [drm] stuck on render ring
[106291.656427] [drm] GPU HANG: ecode 5:0:0xb5cefffc, in compiz [2650], reason: Ring hung, action: reset
[106291.660536] drm/i915: Resetting chip after gpu hang
[106297.628559] [drm] stuck on render ring
[106297.636909] [drm] GPU HANG: ecode 5:0:0xb5cefffc, in compiz [2650], reason: Ring hung, action: reset
[106297.637042] [drm:i915_set_reset_status [i915]] *ERROR* gpu hanging too fast, banning!
[106297.640577] drm/i915: Resetting chip after gpu hang
[106309.224115] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

This looks like there is some problem with the drm on the GPU. Under 14.04 it worked perfectly. So something must have gone worse ...
Anybody with an idea?

---

### Post by bestoe on 2016-11-13
O.k. after several updates, the problem remains, but the error message changed. One error message was:
```
[ 5112.932763] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5115.965586] [drm] stuck on render ring
[ 5115.972313] [drm] GPU HANG: ecode 5:0:0x87f6fff8, in Xorg [1318], reason: Ring hung, action: reset
[ 5115.972317] [drm] GPU hangs can indicate a bug anywhere in the entire gfx stack, including userspace.
[ 5115.972318] [drm] Please file a _new_ bug report on bugs.freedesktop.org against DRI -> DRM/Intel
[ 5115.972319] [drm] drm/i915 developers can then reassign to the right component if it's not a kernel issue.
[ 5115.972320] [drm] The gpu crash dump is required to analyze gpu hangs, so please always attach it.
[ 5115.972322] [drm] GPU crash dump saved to /sys/class/drm/card0/error
[ 5115.975614] drm/i915: Resetting chip after gpu hang

```

Today I got:
```
[94130.207146] [drm] stuck on render ring
[94130.212672] [drm] GPU HANG: ecode 5:0:0xb5cafffb, in compiz [12158], reason: Ring hung, action: reset
[94130.215083] drm/i915: Resetting chip after gpu hang
[94136.170991] [drm] stuck on render ring
[94136.176190] [drm] GPU HANG: ecode 5:0:0xb5cafffb, in compiz [12158], reason: Ring hung, action: reset
[94136.176339] [drm:i915_set_reset_status [i915]] *ERROR* gpu hanging too fast, banning!
[94136.180454] drm/i915: Resetting chip after gpu hang


```

---

