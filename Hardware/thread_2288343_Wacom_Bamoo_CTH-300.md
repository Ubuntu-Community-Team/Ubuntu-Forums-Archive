---
title: "Wacom Bamoo CTH-300"
date: 2015-07-26
forum: Hardware
---

### Post by donald9 on 2015-07-26
Ubuntu 15.04 refuses to work with my little Wacom tablet. Any suggestions?

```
$ lsusb | grep Wacom
Bus 003 Device 006: ID 056a:0319 Wacom Co., Ltd
```

```
$ lsmod | grep wacom
wacom                  81920  0 
hid                   110592  2 wacom,usbhid
```

```
$ dmesg | grep Wacom
[    1.959047] usb 3-1.2: Manufacturer: Wacom Co.,Ltd.
[   10.548883] input: Wacom HID Pen as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0/0003:056A:0319.0001/input/input11
[   10.549070] wacom 0003:056A:0319.0001: hidraw0: USB HID v1.10 Device [Wacom Co.,Ltd. Bamboo Pad, wireless] on usb-0000:00:1a.0-1.2/input0
[   10.549228] input: Wacom HID Pen as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.1/0003:056A:0319.0002/input/input13
[   10.549296] wacom 0003:056A:0319.0002: hidraw1: USB HID v1.10 Mouse [Wacom Co.,Ltd. Bamboo Pad, wireless] on usb-0000:00:1a.0-1.2/input1
[   10.549382] input: Wacom HID Pen as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.2/0003:056A:0319.0003/input/input15
[   10.549443] wacom 0003:056A:0319.0003: hidraw2: USB HID v1.10 Keyboard [Waco Co.,Ltd. Bamboo Pad, wireless] on usb-0000:00:1a.0-1.2/input2
[   10.549545] input: Wacom HID Pen as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.3/0003:056A:0319.0004/input/input17
[   10.549603] wacom 0003:056A:0319.0004: hidraw3: USB HID v1.10 Device [Wacom Co.,Ltd. Bamboo Pad, wireless] on usb-0000:00:1a.0-1.2/input3
[ 2928.793106] usb 3-1.2: Manufacturer: Wacom Co.,Ltd.
[ 2928.796063] input: Wacom HID Pen as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0/0003:056A:0319.0005/input/input20
[ 2928.796317] wacom 0003:056A:0319.0005: hidraw0: USB HID v1.10 Device [Wacom Co.,Ltd. Bamboo Pad, wireless] on usb-0000:00:1a.0-1.2/input0
[ 2928.798600] input: Wacom HID Pen as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.1/0003:056A:0319.0006/input/input22
[ 2928.798856] wacom 0003:056A:0319.0006: hidraw1: USB HID v1.10 Mouse [Wacom Co.,Ltd. Bamboo Pad, wireless] on usb-0000:00:1a.0-1.2/input1
[ 2928.800234] input: Wacom HID Pen as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.2/0003:056A:0319.0007/input/input24
[ 2928.800740] wacom 0003:056A:0319.0007: hidraw2: USB HID v1.10 Keyboard [Waco Co.,Ltd. Bamboo Pad, wireless] on usb-0000:00:1a.0-1.2/input2
[ 2928.802142] input: Wacom HID Pen as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.3/0003:056A:0319.0008/input/input26
[ 2928.802481] wacom 0003:056A:0319.0008: hidraw3: USB HID v1.10 Device [Wacom Co.,Ltd. Bamboo Pad, wireless] on usb-0000:00:1a.0-1.2/input3
```

---

### Post by sudodus on 2015-07-27
My old Wacom Bamboo One works directly without any tweaks in Lubuntu 14.04.2 LTS.

I'm also isotesting the next 'buntu version, 'Wily' to become 15.10, and it works there too (I tried in a persistent live session with the current daily build). It works slightly differently in standard Ubuntu compared to Lubuntu, but works in both cases.

Maybe you can try (in a live session without installing), if your Wacom works in an Ubuntu flavour (standard Ubuntu, Lubuntu, Kubuntu, Xubuntu ...) of the ***version 14.04.1 LTS*** (with long time support) or as I did, with ***14.04.2***.

---

