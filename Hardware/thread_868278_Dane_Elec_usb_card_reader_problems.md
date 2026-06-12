---
title: "Dane Elec usb card reader problems"
date: 2008-07-23
forum: Hardware
---

### Post by Marinodimare on 2008-07-23
I have a dane elec usb card reader, that converts an SD card into a usb pen. It doesn't show up as a removable device in Gnome, and mounting it gives the following respons:
```

sudo mount -t vfat /dev/sdd /mnt
mount: /dev/sdd: can't read superblock

```

However, when I insert the SD card that's inside directly into the PC card reader, the problem doesn't occur.

I've tried it on two computers, both running Hardy. The one from which the code in this post comes runs kernel 2.6.24-16-generic

Back to the usb card reader: after pluging it in, dmes | tail returns the following:

```
$ dmesg | tail
[ 1764.193201] end_request: I/O error, dev sdd, sector 0
[ 1764.193219]  unable to read partition table
[ 1764.193317] sd 8:0:0:0: [sdd] Attached SCSI removable disk
[ 1764.193395] sd 8:0:0:0: Attached scsi generic sg3 type 0
[ 1764.260041] end_request: I/O error, dev sdd, sector 0
[ 1764.264355] end_request: I/O error, dev sdd, sector 0
[ 1764.287838] end_request: I/O error, dev sdd, sector 0
[ 1764.292251] end_request: I/O error, dev sdd, sector 0
[ 1764.851861] end_request: I/O error, dev sdd, sector 0
[ 1764.855946] end_request: I/O error, dev sdd, sector 0
```


furthermore, sudo udevmonitor -e yields the following when it is plugged in:

```
$ sudo udevmonitor -e
udevmonitor will print the received events for:
UDEV the event which udev sends out after rule processing
UEVENT the kernel uevent

UEVENT[1216852318.773772] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-4 (usb)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-4
SUBSYSTEM=usb
MAJOR=189
MINOR=521
DEVTYPE=usb_device
DEVICE=/proc/bus/usb/005/010
PRODUCT=90c/6000/100
TYPE=0/0/0
BUSNUM=005
DEVNUM=010
SEQNUM=2920

UEVENT[1216852318.817620] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-4/usb_endpoint/usbdev5.10_ep00 (usb_endpoint)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-4/usb_endpoint/usbdev5.10_ep00
SUBSYSTEM=usb_endpoint
MAJOR=254
MINOR=15
SEQNUM=2921

UEVENT[1216852318.817687] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0 (usb)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0
SUBSYSTEM=usb
DEVTYPE=usb_interface
DEVICE=/proc/bus/usb/005/010
PRODUCT=90c/6000/100
TYPE=0/0/0
INTERFACE=8/6/80
MODALIAS=usb:v090Cp6000d0100dc00dsc00dp00ic08isc06ip50
SEQNUM=2922

UDEV  [1216852318.820443] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-4 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-4
SUBSYSTEM=usb
MAJOR=189
MINOR=521
DEVTYPE=usb_device
DEVICE=/proc/bus/usb/005/010
PRODUCT=90c/6000/100
TYPE=0/0/0
BUSNUM=005
DEVNUM=010
SEQNUM=2920
UDEVD_EVENT=1
DEVNAME=/dev/bus/usb/005/010

UDEV  [1216852318.830714] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-4/usb_endpoint/usbdev5.10_ep00 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-4/usb_endpoint/usbdev5.10_ep00
SUBSYSTEM=usb_endpoint
MAJOR=254
MINOR=15
SEQNUM=2921
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.10_ep00

UEVENT[1216852318.831475] add      /class/scsi_host/host9 (scsi_host)
ACTION=add
DEVPATH=/class/scsi_host/host9
SUBSYSTEM=scsi_host
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/host9
SEQNUM=2923

UEVENT[1216852318.839386] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/usb_endpoint/usbdev5.10_ep81 (usb_endpoint)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/usb_endpoint/usbdev5.10_ep81
SUBSYSTEM=usb_endpoint
MAJOR=254
MINOR=16
SEQNUM=2924

UEVENT[1216852318.839472] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/usb_endpoint/usbdev5.10_ep02 (usb_endpoint)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/usb_endpoint/usbdev5.10_ep02
SUBSYSTEM=usb_endpoint
MAJOR=254
MINOR=17
SEQNUM=2925

UDEV  [1216852319.028022] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0 (usb)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0
SUBSYSTEM=usb
DEVTYPE=usb_interface
DEVICE=/proc/bus/usb/005/010
PRODUCT=90c/6000/100
TYPE=0/0/0
INTERFACE=8/6/80
MODALIAS=usb:v090Cp6000d0100dc00dsc00dp00ic08isc06ip50
SEQNUM=2922
UDEVD_EVENT=1

UDEV  [1216852319.030236] add      /class/scsi_host/host9 (scsi_host)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/scsi_host/host9
SUBSYSTEM=scsi_host
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/host9
SEQNUM=2923
UDEVD_EVENT=1

UDEV  [1216852319.037579] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/usb_endpoint/usbdev5.10_ep81 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/usb_endpoint/usbdev5.10_ep81
SUBSYSTEM=usb_endpoint
MAJOR=254
MINOR=16
SEQNUM=2924
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.10_ep81

UDEV  [1216852319.047999] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/usb_endpoint/usbdev5.10_ep02 (usb_endpoint)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/usb_endpoint/usbdev5.10_ep02
SUBSYSTEM=usb_endpoint
MAJOR=254
MINOR=17
SEQNUM=2925
UDEVD_EVENT=1
DEVNAME=/dev/usbdev5.10_ep02

UEVENT[1216852323.837395] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/host9/target9:0:0/9:0:0:0 (scsi)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/host9/target9:0:0/9:0:0:0
SUBSYSTEM=scsi
DEVTYPE=scsi_device
MODALIAS=scsi:t-0x00
SEQNUM=2926

UEVENT[1216852323.837475] add      /class/scsi_disk/9:0:0:0 (scsi_disk)
ACTION=add
DEVPATH=/class/scsi_disk/9:0:0:0
SUBSYSTEM=scsi_disk
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/host9/target9:0:0/9:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd
SEQNUM=2927

UEVENT[1216852324.009220] add      /block/sdd (block)
ACTION=add
DEVPATH=/block/sdd
SUBSYSTEM=block
MINOR=48
MAJOR=8
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/host9/target9:0:0/9:0:0:0
PHYSDEVBUS=scsi
sd
SEQNUM=2928

UEVENT[1216852324.010480] add      /class/scsi_device/9:0:0:0 (scsi_device)
ACTION=add
DEVPATH=/class/scsi_device/9:0:0:0
SUBSYSTEM=scsi_device
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/host9/target9:0:0/9:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd
SEQNUM=2929

UEVENT[1216852324.010881] add      /class/scsi_generic/sg3 (scsi_generic)
ACTION=add
DEVPATH=/class/scsi_generic/sg3
SUBSYSTEM=scsi_generic
MAJOR=21
MINOR=3
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/host9/target9:0:0/9:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd
SEQNUM=2930

UDEV  [1216852324.129305] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/host9/target9:0:0/9:0:0:0 (scsi)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/host9/target9:0:0/9:0:0:0
SUBSYSTEM=scsi
DEVTYPE=scsi_device
MODALIAS=scsi:t-0x00
SEQNUM=2926
UDEVD_EVENT=1

UDEV  [1216852324.135564] add      /class/scsi_disk/9:0:0:0 (scsi_disk)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/scsi_disk/9:0:0:0
SUBSYSTEM=scsi_disk
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/host9/target9:0:0/9:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd
SEQNUM=2927
UDEVD_EVENT=1

UDEV  [1216852324.168579] add      /class/scsi_device/9:0:0:0 (scsi_device)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/scsi_device/9:0:0:0
SUBSYSTEM=scsi_device
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/host9/target9:0:0/9:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd
SEQNUM=2929
UDEVD_EVENT=1

UDEV  [1216852324.188000] add      /class/scsi_generic/sg3 (scsi_generic)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/scsi_generic/sg3
SUBSYSTEM=scsi_generic
MAJOR=21
MINOR=3
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/host9/target9:0:0/9:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd
SEQNUM=2930
UDEVD_EVENT=1
DEVNAME=/dev/sg3

UEVENT[1216852324.210622] add      /kernel/uids/65534 (kernel)
ACTION=add
DEVPATH=/kernel/uids/65534
SUBSYSTEM=kernel
SEQNUM=2931

UDEV  [1216852324.213789] add      /kernel/uids/65534 (kernel)
UDEV_LOG=3
ACTION=add
DEVPATH=/kernel/uids/65534
SUBSYSTEM=kernel
SEQNUM=2931
UDEVD_EVENT=1

UEVENT[1216852324.228235] remove   /kernel/uids/65534 (kernel)
ACTION=remove
DEVPATH=/kernel/uids/65534
SUBSYSTEM=kernel
SEQNUM=2932

UDEV  [1216852324.230437] remove   /kernel/uids/65534 (kernel)
UDEV_LOG=3
ACTION=remove
DEVPATH=/kernel/uids/65534
SUBSYSTEM=kernel
SEQNUM=2932
UDEVD_EVENT=1

UDEV  [1216852324.242913] add      /block/sdd (block)
UDEV_LOG=3
ACTION=add
DEVPATH=/block/sdd
SUBSYSTEM=block
MINOR=48
MAJOR=8
PHYSDEVPATH=/devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/host9/target9:0:0/9:0:0:0
PHYSDEVBUS=scsi
SEQNUM=2928
UDEVD_EVENT=1
DEVTYPE=disk
ID_VENDOR=Generic
ID_MODEL=USB2.0_Card_Reader
ID_REVISION=6000
ID_SERIAL=Generic_USB2.0_Card_Reader_12345678901234567890-0:0
ID_SERIAL_SHORT=12345678901234567890
ID_TYPE=disk
ID_INSTANCE=0:0
ID_BUS=usb
ID_PATH=pci-0000:00:1d.7-usb-0:4:1.0-scsi-0:0:0:0
DEVNAME=/dev/sdd
DEVLINKS=/dev/disk/by-id/usb-Generic_USB2.0_Card_Reader_12345678901234567890-0:0 /dev/disk/by-path/pci-0000:00:1d.7-usb-0:4:1.0-scsi-0:0:0:0



```

---

