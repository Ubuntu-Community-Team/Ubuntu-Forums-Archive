---
title: "can't connect Sony Ericsson NAITE"
date: 2010-06-10
forum: Hardware
---

### Post by higashi on 2010-06-10
i just got a Sony Ericsson NAITE phone and i'm having problems connecting it to my computer. I went through the USB settings and noticed that it was set for a Windoze machine, so i chose the setting for other OS's (and also tried the USB Mem. setting, and neither of them seemed to make any difference. 

When i plug in the phone, nothing happens on either the phone or my computer. How do i connect?

---

### Post by tgalati4 on 2010-06-10
Open a  terminal; post the output of:

dmesg | tail -50

---

### Post by higashi on 2010-06-10
```
 dmesg | tail -50
[   19.530381] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[   19.530622] agpgart-intel 0000:00:00.0: detected 892K stolen memory
[   19.545487] usbcore: registered new interface driver wacom
[   19.545493] wacom: v1.52:USB Wacom tablet driver
[   19.612173] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[   19.636271] lp0: using parport0 (interrupt-driven).
[   19.717499] dell-wmi: No known WMI GUID found
[   19.730705] ppdev: user-space parallel port driver
[   19.732125] [drm] Initialized drm 1.1.0 20060810
[   19.781443] type=1505 audit(1276191840.741:2):  operation="profile_load" pid=460 name="/sbin/dhclient3"
[   19.782040] type=1505 audit(1276191840.741:3):  operation="profile_load" pid=460 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   19.782358] type=1505 audit(1276191840.741:4):  operation="profile_load" pid=460 name="/usr/lib/connman/scripts/dhclient-script"
[   19.912805] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.912814] i915 0000:00:02.0: setting latency timer to 64
[   19.942009] [drm] set up 0M of stolen space
[   20.059425] [drm] initialized overlay support
[   20.343818] type=1505 audit(1276191841.301:5):  operation="profile_load" pid=590 name="/usr/share/gdm/guest-session/Xsession"
[   20.365111] type=1505 audit(1276191841.325:6):  operation="profile_replace" pid=591 name="/sbin/dhclient3"
[   20.365725] type=1505 audit(1276191841.325:7):  operation="profile_replace" pid=591 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   20.366057] type=1505 audit(1276191841.325:8):  operation="profile_replace" pid=591 name="/usr/lib/connman/scripts/dhclient-script"
[   20.402529] type=1505 audit(1276191841.361:9):  operation="profile_load" pid=594 name="/usr/bin/evince"
[   20.426948] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.428405] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   20.428758] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   20.434413] type=1505 audit(1276191841.393:10):  operation="profile_load" pid=594 name="/usr/bin/evince-previewer"
[   20.451401] type=1505 audit(1276191841.409:11):  operation="profile_load" pid=594 name="/usr/bin/evince-thumbnailer"
[   20.529085] fb0: inteldrmfb frame buffer device
[   20.529089] registered panic notifier
[   20.529104] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   20.529161]   alloc irq_desc for 17 on node -1
[   20.529165]   alloc kstat_irqs on node -1
[   20.529174] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   20.529211] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   20.539471] vga16fb: initializing
[   20.539479] vga16fb: mapped to 0xc00a0000
[   20.539485] vga16fb: not registering due to another framebuffer present
[   20.694185] Console: switching to colour frame buffer device 100x37
[   20.948072] intel8x0_measure_ac97_clock: measured 52096 usecs (2510 samples)
[   20.948077] intel8x0: clocking to 48000
[   22.033699] render error detected, EIR: 0x00000010
[   22.033708] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[   22.033724] render error detected, EIR: 0x00000010
[   22.281430] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   22.281436] vboxdrv: Successfully done.
[   22.281438] vboxdrv: Found 1 processor cores.
[   22.285086] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   22.285092] vboxdrv: Successfully loaded version 3.1.6_OSE (interface 0x00100001).
[   31.036016] eth0: no IPv6 routers present
[   51.996060] end_request: I/O error, dev fd0, sector 0
[   52.028055] end_request: I/O error, dev fd0, sector 0

```
In case it makes a difference, i did this while the phone was plugged in

---

### Post by tgalati4 on 2010-06-10
It doesn't appear that your USB port is working at all.  Try plugging something else into the same port and run the dmesg command again.  Just post the new stuff, not the entire dmesg.

---

### Post by higashi on 2010-06-10
I plugged my ipod into the same USB port and got the ipod popup, so it appears that everything's working fine.

Sorry, but i can't tell which part is considered "new stuff", so i'll just have to post the whole thing again :\

```


dmesg | tail -50
[   20.426948] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.428405] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   20.428758] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   20.434413] type=1505 audit(1276191841.393:10):  operation="profile_load" pid=594 name="/usr/bin/evince-previewer"
[   20.451401] type=1505 audit(1276191841.409:11):  operation="profile_load" pid=594 name="/usr/bin/evince-thumbnailer"
[   20.529085] fb0: inteldrmfb frame buffer device
[   20.529089] registered panic notifier
[   20.529104] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   20.529161]   alloc irq_desc for 17 on node -1
[   20.529165]   alloc kstat_irqs on node -1
[   20.529174] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   20.529211] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   20.539471] vga16fb: initializing
[   20.539479] vga16fb: mapped to 0xc00a0000
[   20.539485] vga16fb: not registering due to another framebuffer present
[   20.694185] Console: switching to colour frame buffer device 100x37
[   20.948072] intel8x0_measure_ac97_clock: measured 52096 usecs (2510 samples)
[   20.948077] intel8x0: clocking to 48000
[   22.033699] render error detected, EIR: 0x00000010
[   22.033708] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[   22.033724] render error detected, EIR: 0x00000010
[   22.281430] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   22.281436] vboxdrv: Successfully done.
[   22.281438] vboxdrv: Found 1 processor cores.
[   22.285086] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   22.285092] vboxdrv: Successfully loaded version 3.1.6_OSE (interface 0x00100001).
[   31.036016] eth0: no IPv6 routers present
[   51.996060] end_request: I/O error, dev fd0, sector 0
[   52.028055] end_request: I/O error, dev fd0, sector 0
[ 9653.924042] usb 1-6: new high speed USB device using ehci_hcd and address 3
[ 9654.058296] usb 1-6: configuration #1 chosen from 2 choices
[ 9654.380537] Initializing USB Mass Storage driver...
[ 9654.380693] scsi4 : SCSI emulation for USB Mass Storage devices
[ 9654.380821] usbcore: registered new interface driver usb-storage
[ 9654.380825] USB Mass Storage support registered.
[ 9654.387714] usb-storage: device found at 3
[ 9654.387718] usb-storage: waiting for device to settle before scanning
[ 9659.384368] usb-storage: device scan complete
[ 9659.385095] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 9659.388790] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 9659.391454] sd 4:0:0:0: [sdb] 14651280 2048-byte logical blocks: (30.0 GB/27.9 GiB)
[ 9659.392581] sd 4:0:0:0: [sdb] Write Protect is off
[ 9659.392588] sd 4:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 9659.392591] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 9659.394443] sd 4:0:0:0: [sdb] 14651280 2048-byte logical blocks: (30.0 GB/27.9 GiB)
[ 9659.395577] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 9659.395586]  sdb: sdb1 sdb2
[ 9659.408309] sd 4:0:0:0: [sdb] 14651280 2048-byte logical blocks: (30.0 GB/27.9 GiB)
[ 9659.416367] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 9659.416378] sd 4:0:0:0: [sdb] Attached SCSI removable disk

```

Thanks for showing interest in my post

---

### Post by higashi on 2010-06-10
k i figured out the problem... apparently i wasn't pushing the wire far enough into my phone. (feels stupid)
Sorry for wasting your time and thanks for your help. :]

---

### Post by tgalati4 on 2010-06-10
dmesg is your friend.  Enjoy.

---

### Post by ajmal_82 on 2011-01-29
so now you can connect to the internet? or just ubuntu is detecting the naite phone,what is the version of ubuntu you are using post me reply

---

