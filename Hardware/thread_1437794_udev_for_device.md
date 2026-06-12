---
title: "udev for device"
date: 2010-03-24
forum: Hardware
---

### Post by hselvaggi on 2010-03-24
Hi,

I'm trying to setup a device using udev. The device is mounting 3 ports /dev/ttyUSB0, /dev/ttyUSB1 and /dev/ttyUSB2.

P: /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.2/ttyUSB0/tty/ttyUSB0
N: ttyUSB0
S: char/188:0
S: serial/by-path/pci-0000:00:1d.7-usb-0:4:1.2-port0
S: serial/by-id/usb-HUAWEI_Technology_HUAWEI_Mobile-if02-port0
S: gsmmodem
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.2/ttyUSB0/tty/ttyUSB0
E: MAJOR=188
E: MINOR=0
E: DEVNAME=/dev/ttyUSB0
E: SUBSYSTEM=tty
E: ID_PORT=0
E: ID_PATH=pci-0000:00:1d.7-usb-0:4:1.2
E: ID_VENDOR=HUAWEI_Technology
E: ID_VENDOR_ENC=HUAWEI\x20Technology
E: ID_VENDOR_ID=12d1
E: ID_MODEL=HUAWEI_Mobile
E: ID_MODEL_ENC=HUAWEI\x20Mobile
E: ID_MODEL_ID=141e
E: ID_REVISION=0000
E: ID_SERIAL=HUAWEI_Technology_HUAWEI_Mobile
E: ID_TYPE=generic
E: ID_BUS=usb
E: ID_USB_INTERFACES=:ffffff:080650:
E: ID_USB_INTERFACE_NUM=02
E: ID_USB_DRIVER=option
E: ID_IFACE=02
E: ID_VENDOR_FROM_DATABASE=Huawei Technologies Co., Ltd.
E: DEVLINKS=/dev/char/188:0 /dev/serial/by-path/pci-0000:00:1d.7-usb-0:4:1.2-port0 /dev/serial/by-id/usb-HUAWEI_Technology_HUAWEI_Mobile-if02-port0 /dev/gsmmodem


the diference each port has is the ID_USB_INTERFACE_NUM it is 00, 01 and 02 and the port they mount in (ttyUSB0, ttyUSB1 and ttyUSB2) . I want to load the device at /dev/gsmmodem but I get a randome ID_USB_INTERACE_NUM there (00, 01 or 02).

I write down a rule like this

SUBSYSTEM=="tty", ENV(ID_USB_INTERFACE_NUM)=="01", ENV(ID_SERIAL)=="HUAWEI_Technology_HUAWEI_Mobile",SYMLINK+="gsmmodem",MODE="0777"

but it doesn't work, it loads 01 or 02 not 01 all the time. I've search for information on udev but I didn't find anything about when to use ENV, ATTR or SYSF so I tried all of them for those attributes

Can anybody help me with this please?.

A lot of information I have read tell about udevinfo but that command doesn't exist on ubuntu 9.10 and udevadm doesn't say things like SYSFS, etc as I have seen on the output of udevinfo.

Regards:
Harold.

---

### Post by dev.khan on 2011-04-26
Hi,

I am facing the same problem... 
Have you got any solution ???
can you please share me ??

Regards

---

