---
title: "Magellan GPS via USB (how do I mount it?)"
date: 2012-03-11
forum: Hardware
---

### Post by strider22 on 2012-03-11
Is there anything I can do to access a Magellan GPS (Trition)?

When the device is connected and configured to connect to the PC it is only partly detected.

lsusb and udevadm info --export-db both show a new device however the device does not get linked into media and I have no access.

Is there anything I can do to mount the device?

Thanks... info follows.

lsusb shows this device
Bus 004 Device 010: ID 120f:5260 

udevadm shows more info
P: /devices/pci0000:00/0000:00:1d.2/usb4/4-1
N: bus/usb/004/010
S: char/189:393
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb4/4-1
E: MAJOR=189
E: MINOR=393
E: DEVNAME=/dev/bus/usb/004/010
E: DEVTYPE=usb_device
E: DRIVER=usb
E: PRODUCT=120f/5260/0
E: TYPE=0/0/0
E: BUSNUM=004
E: DEVNUM=010
E: SUBSYSTEM=usb
E: ID_VENDOR=MAGELLAN
E: ID_VENDOR_ENC=MAGELLAN
E: ID_VENDOR_ID=120f     ************
E: ID_MODEL=TRITON
E: ID_MODEL_ENC=TRITON
E: ID_MODEL_ID=5260      ************
E: ID_REVISION=0000
E: ID_SERIAL=MAGELLAN_TRITON_0140100110725
E: ID_SERIAL_SHORT=0140100110725
E: ID_BUS=usb
E: ID_USB_INTERFACES=:ffffff:
E: DEVLINKS=/dev/char/189:393

---

