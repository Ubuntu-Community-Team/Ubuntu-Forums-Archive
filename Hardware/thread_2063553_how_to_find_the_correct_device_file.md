---
title: "how to find the correct device file"
date: 2012-09-27
forum: Hardware
---

### Post by arbiter2x on 2012-09-27
hi,
I'm trying to find the device file of a connected usb device.

I already found my device with "lsusb", so I have the device id
but how am I going to get from here to the device file?

btw: there are no device files in /dev/ starting with "usb"
there is only /dev/usb/hiddev0

there's just a bunch of /dev/tty-files....but how do i find out which one of these is for my usb-device?

---

### Post by drmrgd on 2012-09-27
Right after plugging in the device, run 'dmesg' in the terminal.  The last output should show how the device is registering and should show you where it's being linked.

You might also be able to just look at your mtab file to see where it was mounted:

```
cat /etc/mtab
```

---

### Post by arbiter2x on 2012-09-27
The problem is that I can't unplug the device.....

it's actually a UPS, it's not a mountable harddrive or anything

---

### Post by steeldriver on 2012-09-27
You could try something like

```
udevadm info --query=symlink --name="/bus/usb/006/002"
```where /006/002 are the bus and device IDs from lsusb e.g.

```
Bus **006** Device **002**: ID 04d9:a01c Holtek Semiconductor, Inc.
```(I don't know a way to get udevadm to lookup based on the actual device ID). However if there's no rule to create a symlink then it will come up blank - if you want to see all the properties that are set, you can query all

```
udevadm info --query=all --name="/bus/usb/006/002"
```

---

### Post by arbiter2x on 2012-09-27
> **steeldriver said:**
> You could try something like

```
udevadm info --query=symlink --name="/bus/usb/006/002"
```where /006/002 are the bus and device IDs from lsusb e.g.

```
Bus **006** Device **002**: ID 04d9:a01c Holtek Semiconductor, Inc.
```(I don't know a way to get udevadm to lookup based on the actual device ID). However if there's no rule to create a symlink then it will come up blank - if you want to see all the properties that are set, you can query all

```
udevadm info --query=all --name="/bus/usb/006/002"
```



I've tried --query=all ....

```

P: /devices/pci0000:00/0000:00:1a.0/usb3/3-1
N: bus/usb/003/002
S: char/189:257
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb3/3-1
E: MAJOR=189
E: MINOR=257
E: DEVNAME=/dev/bus/usb/003/002
E: DEVTYPE=usb_device
E: DRIVER=usb
E: DEVICE=/proc/bus/usb/003/002
E: PRODUCT=51d/2/6
E: TYPE=0/0/0
E: BUSNUM=003
E: DEVNUM=002
E: SUBSYSTEM=usb
E: ID_VENDOR=American_Power_Conversion
E: ID_VENDOR_ENC=American\x20Power\x20Conversion
E: ID_VENDOR_ID=051d
E: ID_MODEL=Smart-UPS_1500_RM_FW:667.19.I_USB_FW:11.03
E: ID_MODEL_ENC=Smart-UPS\x201500\x20RM\x20FW:667.19.I\x20USB\x20FW:11.03
E: ID_MODEL_ID=0002
E: ID_REVISION=0006
E: ID_SERIAL=American_Power_Conversion_Smart-UPS_1500_RM_FW:...
E: ID_SERIAL_SHORT=...
E: ID_BUS=usb
E: ID_USB_INTERFACES=:030000:
E: DEVLINKS=/dev/char/189:257


```

well, I'm not sure how that helps :)

---

### Post by matt_symes on 2012-09-27
Hi

Plug the USB device back into a USB port and read the output from the terminal. 

Open a terminal and type

```
dmesg | tail -n 30
```It should, hopefully, tell you what device file was created for the USB device.

This is from a USB pen stick.

```

[57588.100540] usb 2-1: new high-speed USB device number 4 using ehci_hcd
[57588.238905] usb 2-1: New USB device found, idVendor=0718, idProduct=0697
[57588.238917] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[57588.238925] usb 2-1: Product: TF 150 Drive
[57588.238931] usb 2-1: Manufacturer: TDKMedia
[57588.238936] usb 2-1: SerialNumber: 07B9160732A76395
[57589.228745] usbcore: registered new interface driver uas
[57589.234696] Initializing USB Mass Storage driver...
[57589.237140] scsi2 : usb-storage 2-1:1.0
[57589.237393] usbcore: registered new interface driver usb-storage
[57589.237397] USB Mass Storage support registered.
[57590.266491] scsi 2:0:0:0: Direct-Access     TDKMedia TF 150 Drive     PMAP PQ: 0 ANSI: 0 CCS
[57590.268588] sd 2:0:0:0: Attached scsi generic sg2 type 0
[57591.325578] sd 2:0:0:0: [sdb] 7806976 512-byte logical blocks: (3.99 GB/3.72 GiB)
[57591.327190] sd 2:0:0:0: [sdb] Write Protect is off
[57591.327203] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[57591.328840] sd 2:0:0:0: [sdb] No Caching mode page present
[57591.328855] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[57591.337580] sd 2:0:0:0: [sdb] No Caching mode page present
[57591.337594] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[57591.361278]  sdb: sdb1
[57591.367229] sd 2:0:0:0: [sdb] No Caching mode page present
[57591.367242] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[57591.367250] sd 2:0:0:0: [sdb] Attached SCSI removable disk
matthew-Aspire-7540:/home/matthew % 
```See if that helps you find the device file.


EDIT:

> The problem is that I can't unplug the device.....You posted this while i was crafting this reply. I would still have a root around in dmesg and syslog though.

Kind regards

---

### Post by arbiter2x on 2012-09-27
> **matt_symes said:**
> Hi

You posted this while i was crafting this reply. I would still have a root around in dmesg and syslog though.

Kind regards

I already did  a dmesg | grep /dev

but it only spits out these lines:
```

[    6.023559] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    6.026317] input: PC Speaker as /devices/platform/pcspkr/input/input1
[    7.907546] input: Avocent USB Composite Device-0 as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input2
[    7.911501] input: Avocent USB Composite Device-0 as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.1/input/input3

```

---

### Post by matt_symes on 2012-09-27
Hi

> **arbiter2x said:**
> I already did  a dmesg | grep /dev

but it only spits out these lines:
```

[    6.023559] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    6.026317] input: PC Speaker as /devices/platform/pcspkr/input/input1
[    7.907546] input: Avocent USB Composite Device-0 as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input2
[    7.911501] input: Avocent USB Composite Device-0 as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.1/input/input3

```

Don't grep for /dev but actually look though the file and see if you can find it. You may have more luck.

Kind regards

---

### Post by arbiter2x on 2012-10-05
the only appearance that is related to the ups is the following line:
```
[    7.903082] generic-usb 0003:051D:0002.0001: hiddev0,hidraw0: USB HID v1.10 Device [American Power Conversion Smart-UPS 1500 RM FW:667.19.I USB FW:11.03] on usb-0000:00:1a.0-1/input0
```

this output is actually rather confusing...
"USB HID"....it shouldn't really be a HID, should it?
it's a USB UPS

but nevertheless...it doesn't really give me a device ID

---

I've read somewhere else, that I can just get the device-ID via the lsusb-output...
which is "**Bus 003 Device 002: ID 051d:0002**"
which translates to: "**/dev/bus/usb/003/002**"



I'm trying to get **nut** running...
so I typed that into the ups.conf

```

[APC]
driver = apcsmart
port = /dev/bus/usb/003/002
desc = "American Power Conversion Uninterruptible Power Supply"

```

unfortunately it doesn't let me start the upsdrvctrl...

```
>upsdrvctl start
Network UPS Tools - UPS driver controller 2.4.3
Network UPS Tools - APC Smart protocol driver 2.03 (2.4.3)
APC command table version 2.1
tcgetattr(/dev/bus/usb/003/002): Inappropriate ioctl for device
Driver failed to start (exit status=1)
```

so I'm guessing the device-path is still wrong....right?

---

