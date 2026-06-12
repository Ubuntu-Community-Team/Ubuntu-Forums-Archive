---
title: "Ubuntu usb 2.0 ports don't work anymore"
date: 2014-04-13
forum: Hardware
---

### Post by tinga90 on 2014-04-13
Hi all, 

My laptop is an ASUS U36SD, I have two usb2 ports, and one usb3 port.
I installed ubuntu and everything worked, but now my usb 2.0 ports don't work anymore while usb3 still works.
I don't know if it is an Ubuntu related problem, because I tried with a live cd (of manjaro) and usb 2 don't work there too.

I tried installing Windows just to try, but it don't support installation via usb3.0, and my laptop has no cd reader.

Here is some output:

```
[user@user-U36SD ~]$ lspci | grep -i usb
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
04:00.0 USB controller: Fresco Logic FL1000G USB 3.0 Host Controller (rev 04)
```

```

[user@user-U36SD ~]$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b1b9 Chicony Electronics Co., Ltd Asus Integrated Webcam
Bus 001 Device 003: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```

[user@user-U36SD ~]$ dmesg | grep error
[    2.803674] usb 1-1.1: device descriptor read/64, error -32
[    5.605677] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[ 4288.430012] usbhid: probe of 3-1:1.1 failed with error -71
[ 4293.430354] usbhid: probe of 3-1:1.2 failed with error -110
```

Any idea?
Thanks

---

