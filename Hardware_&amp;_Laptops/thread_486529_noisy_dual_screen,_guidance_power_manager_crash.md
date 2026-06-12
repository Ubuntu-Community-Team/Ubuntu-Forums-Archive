---
title: "noisy dual screen, guidance power manager crash"
date: 2007-06-28
forum: Hardware &amp; Laptops
---

### Post by jonim8or on 2007-06-28
Hi,

I have recently clean-installed Kubuntu Feisty. I have a compaq desktop computer with a Geforce 6200 graphics card, and 2 tft screens. I am using Xinerama (which seems to be related to the power manager crash)

At startup I have a power manager crash (see attachment).

Then I can normally work. Sometimes, however, one of my two screens starts to show noise (which I tried to reproduce with gimp in the attatchment), and after some time even stops. Rebooting solves the problem for some time.
I had this problem once or twice in Edgy, but now I've had it twice in two days in feisty.

Any solutions/ ideas of the cause of these problems?

Here is the last part of my kern.log
```

Jun 28 09:07:50 jonie-desktop kernel: [   63.167187] No dock devices found.
Jun 28 09:07:50 jonie-desktop kernel: [   63.274418] input: Power Button (FF) as /class/input/input9
Jun 28 09:07:50 jonie-desktop kernel: [   63.280216] ACPI: Power Button (FF) [PWRF]
Jun 28 09:07:50 jonie-desktop kernel: [   63.317333] input: Power Button (CM) as /class/input/input10
Jun 28 09:07:50 jonie-desktop kernel: [   63.323172] ACPI: Power Button (CM) [PWRB]
Jun 28 09:07:50 jonie-desktop kernel: [   63.363911] pcc_acpi: loading...
Jun 28 09:07:51 jonie-desktop kernel: [   64.834642] ACPI: Unable to turn cooling device [eed21dec] 'on'
Jun 28 09:07:54 jonie-desktop kernel: [   68.263084] ppdev: user-space parallel port driver
Jun 28 09:07:55 jonie-desktop kernel: [   69.084504] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Jun 28 09:07:55 jonie-desktop kernel: [   69.084511] apm: overridden by ACPI.
Jun 28 09:07:56 jonie-desktop kernel: [   70.242573] Bluetooth: Core ver 2.11
Jun 28 09:07:56 jonie-desktop kernel: [   70.242666] NET: Registered protocol family 31
Jun 28 09:07:56 jonie-desktop kernel: [   70.242669] Bluetooth: HCI device and connection manager initialized
Jun 28 09:07:56 jonie-desktop kernel: [   70.242674] Bluetooth: HCI socket layer initialized
Jun 28 09:07:56 jonie-desktop kernel: [   70.297021] Bluetooth: L2CAP ver 2.8
Jun 28 09:07:56 jonie-desktop kernel: [   70.297027] Bluetooth: L2CAP socket layer initialized
Jun 28 09:07:56 jonie-desktop kernel: [   70.397406] Bluetooth: RFCOMM socket layer initialized
Jun 28 09:07:56 jonie-desktop kernel: [   70.397427] Bluetooth: RFCOMM TTY layer initialized
Jun 28 09:07:56 jonie-desktop kernel: [   70.397430] Bluetooth: RFCOMM ver 1.8
Jun 28 09:07:57 jonie-desktop kernel: [   70.850431] ACPI: Unable to turn cooling device [eed21dec] 'on'
Jun 28 09:07:57 jonie-desktop kernel: [   71.778811] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Jun 28 09:07:57 jonie-desktop kernel: [   71.779302] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jun 28 09:07:57 jonie-desktop kernel: [   71.779641] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Jun 28 09:07:58 jonie-desktop kernel: [   72.243499] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jun 28 09:07:58 jonie-desktop kernel: [   72.281491] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun 28 09:08:03 jonie-desktop kernel: [   76.849671] ACPI: Unable to turn cooling device [eed21dec] 'on'
Jun 28 09:08:08 jonie-desktop kernel: [   82.396522] eth0: no IPv6 routers present
Jun 28 09:08:09 jonie-desktop kernel: [   82.849417] ACPI: Unable to turn cooling device [eed21dec] 'on'
Jun 28 09:08:10 jonie-desktop kernel: [   84.680328] eth1: no IPv6 routers present
Jun 28 09:08:15 jonie-desktop kernel: [   88.848807] ACPI: Unable to turn cooling device [eed21dec] 'on'
Jun 28 09:08:21 jonie-desktop kernel: [   94.848496] ACPI: Unable to turn cooling device [eed21dec] 'on'
Jun 28 09:08:27 jonie-desktop kernel: [  100.848249] ACPI: Unable to turn cooling device [eed21dec] 'on'
Jun 28 09:08:33 jonie-desktop kernel: [  106.847992] ACPI: Unable to turn cooling device [eed21dec] 'on'
...
Jun 28 09:25:44 jonie-desktop kernel: [ 1138.764028] ACPI: Unable to turn cooling device [eed21dec] 'on'
Jun 28 09:25:50 jonie-desktop kernel: [ 1144.763594] ACPI: Unable to turn cooling device [eed21dec] 'on'
Jun 28 09:25:52 jonie-desktop kernel: [ 1145.159702] NVRM: Xid (0001:00): 6, PE0002 02fc 00000003 0000d014 00000000 00000000
Jun 28 09:25:52 jonie-desktop kernel: [ 1145.161813] NVRM: Xid (0001:00): 6, PE0002 0100 00000006 00000000 00000000 00000000
Jun 28 09:25:52 jonie-desktop kernel: [ 1145.163583] NVRM: Xid (0001:00): 6, PE0002 0100 00000006 00000000 00000000 00000000
Jun 28 09:25:52 jonie-desktop kernel: [ 1145.165435] NVRM: Xid (0001:00): 6, PE0002 0400 ffa4a4a4 00000000 00000000 ffa4a4a4
Jun 28 09:25:56 jonie-desktop kernel: [ 1150.763691] ACPI: Unable to turn cooling device [eed21dec] 'on'
Jun 28 09:25:59 jonie-desktop kernel: [ 1153.830851] NVRM: Xid (0001:00): 8, Channel 00000000
Jun 28 09:26:02 jonie-desktop kernel: [ 1156.763619] ACPI: Unable to turn cooling device [eed21dec] 'on'
Jun 28 09:26:08 jonie-desktop kernel: [ 1162.763228] ACPI: Unable to turn cooling device [eed21dec] 'on'
Jun 28 09:26:14 jonie-desktop kernel: [ 1168.762905] ACPI: Unable to turn cooling device [eed21dec] 'on'
...
Jun 28 09:28:38 jonie-desktop kernel: [ 1312.734020] ACPI: Unable to turn cooling device [eed21dec] 'on'
Jun 28 09:28:44 jonie-desktop kernel: [ 1318.733784] ACPI: Unable to turn cooling device [eed21dec] 'on'
Jun 28 09:28:50 jonie-desktop kernel: [ 1324.515432] NVRM: Xid (0001:00): 1, Channel 00000000 Method 00000060 Data 0101020c
Jun 28 09:28:50 jonie-desktop kernel: [ 1324.538405] NVRM: Xid (0001:00): 1, Channel 00000002 Method 00000060 Data 0102020c
Jun 28 09:28:50 jonie-desktop kernel: [ 1324.733539] ACPI: Unable to turn cooling device [eed21dec] 'on'
Jun 28 09:28:56 jonie-desktop kernel: [ 1330.732950] ACPI: Unable to turn cooling device [eed21dec] 'on'
....
Jun 28 09:34:14 jonie-desktop kernel: [ 1648.650423] ACPI: Unable to turn cooling device [eed21dec] 'on'
Jun 28 09:34:20 jonie-desktop kernel: [ 1654.649912] ACPI: Unable to turn cooling device [eed21dec] 'on'

```

---

