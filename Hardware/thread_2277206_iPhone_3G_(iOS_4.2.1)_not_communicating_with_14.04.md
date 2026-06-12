---
title: "iPhone 3G (iOS 4.2.1) not communicating with 14.04.2 LTS"
date: 2015-05-07
forum: Hardware
---

### Post by jason177 on 2015-05-07
Hi there,

I've tried chasing a few threads around but I'm not getting anywhere and people *seem* to think this shouldn't be complicated...

I've got an old iPhone 3G which I thought might be nice to use as an mp3 player to listen to podcasts.  I tried on a different machine setting up gtkpod and copying the files across to the filesystem, but then learned that you need to do it differently to that.  I've since built a new machine but it doesn't seem to want to communicate with the iPhone.

I just reformatted the phone on the weekend using a Windows laptop (as some people seem to recommend), so it's running a fresh install of iOS 4.2.1.

My Xubuntu machine has libimobiledevice4 v1.1.5 on it, as well as libusbmuxd2 and libplist1, so from what I've read they're the main things I need to talk to the device, right?  When I plug the device in to the USB port an icon appears on the desktop but it doesn't mount.

Here's what comes up in the syslog when I plug it in:

May  7 13:42:45 BeeHouse kernel: [46734.892585] usb 3-10: new high-speed USB device number 6 using xhci_hcd
May  7 13:42:45 BeeHouse kernel: [46735.025982] usb 3-10: New USB device found, idVendor=05ac, idProduct=1292
May  7 13:42:45 BeeHouse kernel: [46735.025991] usb 3-10: New USB device strings: Mfr=1, Product=2, SerialNumber=3
May  7 13:42:45 BeeHouse kernel: [46735.025997] usb 3-10: Product: iPhone
May  7 13:42:45 BeeHouse kernel: [46735.026001] usb 3-10: Manufacturer: Apple Inc.
May  7 13:42:45 BeeHouse kernel: [46735.026006] usb 3-10: SerialNumber: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
May  7 13:42:45 BeeHouse kernel: [46735.026323] usb 3-10: ep 0x2 - rounding interval to 8 microframes, ep desc says 10 microframes
May  7 13:42:45 BeeHouse kernel: [46735.026334] usb 3-10: ep 0x81 - rounding interval to 8 microframes, ep desc says 10 microframes
May  7 13:42:45 BeeHouse mtp-probe: checking bus 3, device 6: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-10"
May  7 13:42:45 BeeHouse mtp-probe: bus: 3, device: 6 was not an MTP device
May  7 13:42:45 BeeHouse kernel: [46735.037253] usb 3-10: ep 0x2 - rounding interval to 8 microframes, ep desc says 10 microframes
May  7 13:42:45 BeeHouse kernel: [46735.037262] usb 3-10: ep 0x81 - rounding interval to 8 microframes, ep desc says 10 microframes
May  7 13:42:45 BeeHouse kernel: [46735.066057] ipheth 3-10:4.2: Apple iPhone USB Ethernet device attached
May  7 13:42:45 BeeHouse NetworkManager[1112]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:4.2/net/eth1, iface: eth1)
May  7 13:42:45 BeeHouse NetworkManager[1112]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:4.2/net/eth1, iface: eth1): no ifupdown configuration found.
May  7 13:42:45 BeeHouse NetworkManager[1112]: <warn> failed to allocate link cache: (-12) Object not found
May  7 13:42:45 BeeHouse NetworkManager[1112]: <info> (eth1): carrier is OFF
May  7 13:42:45 BeeHouse NetworkManager[1112]: <info> (eth1): new Ethernet device (driver: 'ipheth' ifindex: 7)
May  7 13:42:45 BeeHouse NetworkManager[1112]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/5
May  7 13:42:45 BeeHouse NetworkManager[1112]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May  7 13:42:45 BeeHouse NetworkManager[1112]: <info> (eth1): bringing up device.
May  7 13:42:45 BeeHouse NetworkManager[1112]: <info> (eth1): preparing device.
May  7 13:42:45 BeeHouse NetworkManager[1112]: <info> (eth1): deactivating device (reason 'managed') [2]
May  7 13:42:45 BeeHouse NetworkManager[1112]: <info> Added default wired connection 'Wired connection 2' for /sys/devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:4.2/net/eth1
May  7 13:42:45 BeeHouse kernel: [46735.092019] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
May  7 12:54:28 BeeHouse ModemManager[920]: message repeated 2 times: [ <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:14.0/usb3/3-2': not supported by any plugin]
May  7 13:42:47 BeeHouse ModemManager[920]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:14.0/usb3/3-10': not supported by any plugin
May  7 13:42:48 BeeHouse gpod: Client creation/handshake failed: -5


Trying to run ideviceinfo gives me a TLS error, presumably because of something that's gone wrong during the connection attempt.

I tried the steps listed in this post:[http://ubuntuforums.org/showthread.php?t=1637361](http://ubuntuforums.org/showthread.php?t=1637361) however I couldn't build the latest libimobiledevice from source due to the config not being able to find the version of libusbmuxd it was looking for.  I'm a bit of a n00b at this so wasn't comfortable going through the configure script and changing all references in there...

Is there anything obvious I should try?

Many thanks,

Jason

---

