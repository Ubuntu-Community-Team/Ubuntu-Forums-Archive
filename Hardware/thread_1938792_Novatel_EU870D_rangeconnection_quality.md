---
title: "Novatel EU870D range/connection quality"
date: 2012-03-10
forum: Hardware
---

### Post by ironhalik on 2012-03-10
Hello,

I'm using a Dell Latitude D430 laptop, with a Dell WWAN 5520 3G modem - it's a rebranded Novatel EU870D miniPCIe card. The OS is latest Ubuntu.

The question, what kind of performance should I expect out of the card?
As a reference, I use a Motorola Defy phone, that I previously used as my modem. The networks are both the same, and the range, and connectivity on the Dell's is considerably worse then the on the phone.
The range is poor, and after I loose the connection, its hard to reconnect.
I'm not sure if its what I should expect from the onboard Dell card, or is it some resolvable issue with drivers, etc.

lsusb returns:
Bus 001 Device 007: ID 413c:8137 Dell Computer Corp. Wireless 5520 Voda L Mobile Broadband (3G HSDPA) Minicard Status Port

Also, during connection issues, these are the logs:
```

Mar  9 17:56:09 grumpy kernel: [  697.384073] ehci_hcd 0000:00:1d.7: BAR 0: set to [mem 0xffa80000-0xffa803ff] (PCI address [0xffa80000-0xffa803ff])
Mar  9 17:56:09 grumpy kernel: [  697.384102] ehci_hcd 0000:00:1d.7: restoring config space at offset 0xf (was 0x100, writing 0x109)
Mar  9 17:56:09 grumpy kernel: [  697.384135] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900102)
Mar  9 17:56:09 grumpy kernel: [  697.387046] ehci_hcd 0000:00:1d.7: PME# disabled
Mar  9 17:56:09 grumpy kernel: [  697.387069] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Mar  9 17:56:09 grumpy kernel: [  697.387080] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Mar  9 17:56:10 grumpy modem-manager[670]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
Mar  9 17:56:10 grumpy modem-manager[670]: <info>  (ttyUSB0) opening serial port...
Mar  9 17:56:10 grumpy modem-manager[670]: <info>  (ttyUSB1): using text mode for SMS
Mar  9 17:56:10 grumpy modem-manager[670]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> registered)
Mar  9 17:56:10 grumpy NetworkManager[943]: <info> WWAN now enabled by management service
Mar  9 17:56:10 grumpy modem-manager[670]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (registered -> connecting)
Mar  9 17:56:10 grumpy modem-manager[670]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (connecting -> connected)
Mar  9 17:56:10 grumpy NetworkManager[943]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) scheduled...
Mar  9 17:56:10 grumpy NetworkManager[943]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) starting...
Mar  9 17:56:10 grumpy NetworkManager[943]: <info> (ttyUSB1): device state change: prepare -> config (reason 'none') [40 50 0]
Mar  9 17:56:10 grumpy NetworkManager[943]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) successful.
Mar  9 17:56:10 grumpy NetworkManager[943]: <info> Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) scheduled.
Mar  9 17:56:10 grumpy NetworkManager[943]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) complete.
Mar  9 17:56:10 grumpy NetworkManager[943]: <info> Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) started...
Mar  9 17:56:10 grumpy NetworkManager[943]: <info> (ttyUSB1): device state change: config -> ip-config (reason 'none') [50 70 0]
Mar  9 17:56:10 grumpy NetworkManager[943]: <info> starting PPP connection
Mar  9 17:56:10 grumpy NetworkManager[943]: <info> pppd started with pid 3877
Mar  9 17:56:10 grumpy NetworkManager[943]: <info> Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) complete.
Mar  9 17:56:10 grumpy pppd[3877]: Plugin /usr/lib/pppd/2.4.5/nm-pppd-plugin.so loaded.
Mar  9 17:56:10 grumpy pppd[3877]: pppd 2.4.5 started by root, uid 0
Mar  9 17:56:10 grumpy pppd[3877]: Removed stale lock on ttyUSB1 (pid 3333)
Mar  9 17:56:10 grumpy pppd[3877]: Using interface ppp0
Mar  9 17:56:10 grumpy NetworkManager[943]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Mar  9 17:56:10 grumpy NetworkManager[943]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Mar  9 17:56:10 grumpy pppd[3877]: Connect: ppp0 <--> /dev/ttyUSB1
Mar  9 17:56:13 grumpy kernel: [  700.816820] option: option_instat_callback: error -2
Mar  9 17:56:16 grumpy kernel: [  703.824403] option: option_instat_callback: error -2
Mar  9 17:56:19 grumpy kernel: [  706.824468] option: option_instat_callback: error -2
Mar  9 17:56:22 grumpy kernel: [  709.824474] option: option_instat_callback: error -2
Mar  9 17:56:25 grumpy kernel: [  712.824985] option: option_instat_callback: error -2
Mar  9 17:56:28 grumpy kernel: [  715.824430] option: option_instat_callback: error -2
Mar  9 17:56:30 grumpy NetworkManager[943]: <warn> pppd timed out or didn't initialize our dbus module
Mar  9 17:56:30 grumpy NetworkManager[943]: <info> (ttyUSB1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Mar  9 17:56:30 grumpy NetworkManager[943]: <info> Marking connection 'Orange Standard access - with image compression' invalid.
Mar  9 17:56:30 grumpy NetworkManager[943]: <warn> Activation (ttyUSB1) failed.
Mar  9 17:56:30 grumpy NetworkManager[943]: <info> (ttyUSB1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar  9 17:56:30 grumpy NetworkManager[943]: <info> (ttyUSB1): deactivating device (reason 'none') [0]
Mar  9 17:56:30 grumpy NetworkManager[943]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Mar  9 17:56:30 grumpy NetworkManager[943]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
Mar  9 17:56:30 grumpy pppd[3877]: Terminating on signal 15
Mar  9 17:56:30 grumpy modem-manager[670]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (connected -> disconnecting)
Mar  9 17:56:32 grumpy avahi-daemon[673]: Withdrawing workstation service for ppp0.
Mar  9 17:56:32 grumpy NetworkManager[943]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Mar  9 17:56:32 grumpy kernel: [  720.036583] option: option_instat_callback: error -2

```

The card is connected to two behind-the-screen antennas.

Thanks for any suggestions.

---

