---
title: "Mouse randomly stops working"
date: 2012-06-27
forum: Hardware
---

### Post by KenSharp on 2012-06-27
My mouse stops working for no obvious reason. Unplugging it and plugging it back again gets it working again.

> [22595.744271] usb 3-1: reset low-speed USB device number 2 using ohci_hcd
[22596.032175] usb 3-1: device descriptor read/64, error -62
[22596.424324] usb 3-1: device descriptor read/64, error -62
[22596.812256] usb 3-1: reset low-speed USB device number 2 using ohci_hcd
[22597.100250] usb 3-1: device descriptor read/64, error -62
[22597.492266] usb 3-1: device descriptor read/64, error -62
[22597.880269] usb 3-1: reset low-speed USB device number 2 using ohci_hcd
[22598.288217] usb 3-1: device not accepting address 2, error -62
[22598.572216] usb 3-1: reset low-speed USB device number 2 using ohci_hcd
[22598.980263] usb 3-1: device not accepting address 2, error -62
[22598.980368] usb 3-1: USB disconnect, device number 2
[22599.152330] usb 3-1: new low-speed USB device number 4 using ohci_hcd
[22599.292267] usb 3-1: device descriptor read/64, error -62
[22599.536243] usb 3-1: device descriptor read/64, error -62
[22599.776287] usb 3-1: new low-speed USB device number 5 using ohci_hcd
[22599.916284] usb 3-1: device descriptor read/64, error -62
[22600.160275] usb 3-1: device descriptor read/64, error -62
[22600.428252] usb 3-1: new low-speed USB device number 6 using ohci_hcd
[22600.836255] usb 3-1: device not accepting address 6, error -62
[22600.972248] usb 3-1: new low-speed USB device number 7 using ohci_hcd
[22601.380256] usb 3-1: device not accepting address 7, error -62
[22601.380290] hub 3-0:1.0: unable to enumerate USB device on port 1
I would open a bug but I have no idea what package to report it against.

Any ideas? TIA

---

### Post by fantix on 2012-07-01
It is almost the same issue for me:

```

[ 4280.256103] usb 2-5: new low-speed USB device number 80 using ohci_hcd
[ 4280.517033] input: MLK RAPOO 1800 as /devices/pci0000:00/0000:00:02.0/usb2/2-5/2-5:1.0/input/input62
[ 4280.517297] generic-usb 0003:1BCF:05C2.0049: input,hidraw1: USB HID v1.00 Keyboard [MLK RAPOO 1800] on usb-0000:00:02.0-5/input0
[ 4280.534227] input: MLK RAPOO 1800 as /devices/pci0000:00/0000:00:02.0/usb2/2-5/2-5:1.1/input/input63
[ 4280.534715] generic-usb 0003:1BCF:05C2.004A: input,hiddev0,hidraw2: USB HID v1.00 Mouse [MLK RAPOO 1800] on usb-0000:00:02.0-5/input1
[ 4287.960090] usb 2-5: reset low-speed USB device number 80 using ohci_hcd
[ 4291.640074] usb 2-5: reset low-speed USB device number 80 using ohci_hcd
[ 4292.007100] usb 2-5: device firmware changed
[ 4292.007164] usb 2-5: USB disconnect, device number 80
[ 4292.280072] usb 2-5: new low-speed USB device number 81 using ohci_hcd
[ 4292.493142] usb 2-5: unable to read config index 0 descriptor/all
[ 4292.493155] usb 2-5: can't read configurations, error -84
[ 4292.656129] usb 2-5: new low-speed USB device number 82 using ohci_hcd
[ 4292.875080] usb 2-5: unable to read config index 0 descriptor/all
[ 4292.875088] usb 2-5: can't read configurations, error -71
[ 4293.056052] usb 2-5: new low-speed USB device number 83 using ohci_hcd
[ 4293.093082] usb 2-5: unable to read config index 0 descriptor/start: -84
[ 4293.093090] usb 2-5: chopping to 0 config(s)
[ 4293.106349] usb 2-5: string descriptor 0 read error: -84
[ 4293.106568] usb 2-5: no configuration chosen from 0 choices

```

Found an old bug:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/91230](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/91230)

So maybe it should be reported against **linux-source**

---

### Post by KenSharp on 2012-07-01
Thanks for that!

I'm in Windows for a while (where it doesn't occur) but if/when it does happen again I shall certainly log it.  Thanks again.

---

### Post by KenSharp on 2012-07-02
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1019998](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1019998)

---

