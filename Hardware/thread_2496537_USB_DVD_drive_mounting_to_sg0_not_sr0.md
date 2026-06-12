---
title: "USB DVD drive mounting to sg0 not sr0"
date: 2024-04-02
forum: Hardware
---

### Post by kenny-astbury on 2024-04-02
So, I have a raspberry pi 5 with a fresh install of Ubuntu. I have bought a USB dvd drive to attach. This drive works on my windows machine, and this machine when running raspbian. So I am assuming that there is an issue with Ubuntu. I had some issues with running updates as the ARM64 updates weren't found in the repository, and so I updated the source.list to:
```
deb http://ports.ubuntu.com/ubuntu-ports mantic main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ mantic-updates main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ mantic-security main restricted universe multiverse
```

when I plug in my dvd drive it is allocated the scsi generic (sg0) not sr0, so the drive cannot be mounted.
dsmeg:
```
[ 8870.546277] usb 4-2: USB disconnect, device number 6
[ 8873.588356] usb 4-1: USB disconnect, device number 5
[ 8874.064906] usb 4-1: new full-speed USB device number 7 using xhci-hcd
[ 8874.215321] usb 4-1: New USB device found, idVendor=046d, idProduct=c52b, bcdDevice=12.01
[ 8874.215333] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 8874.215337] usb 4-1: Product: USB Receiver
[ 8874.215341] usb 4-1: Manufacturer: Logitech
[ 8874.257795] logitech-djreceiver 0003:046D:C52B.0011: hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-xhci-hcd.1-1/input2
[ 8874.661350] logitech-hidpp-device 0003:046D:4024.0012: HID++ 2.0 device connected.
[ 8874.992896] usb 4-2: new high-speed USB device number 8 using xhci-hcd
[ 8875.141464] usb 4-2: New USB device found, idVendor=13fd, idProduct=0840, bcdDevice= 1.14
[ 8875.141475] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 8875.141479] usb 4-2: Product: External
[ 8875.141483] usb 4-2: Manufacturer: Generic
[ 8875.141486] usb 4-2: SerialNumber: 393035323530303930383834
[ 8875.142033] usb-storage 4-2:1.0: USB Mass Storage device detected
[ 8875.142245] scsi host0: usb-storage 4-2:1.0
[ 8876.175298] scsi 0:0:0:0: CD-ROM            PLDS     DVD+-RW DS-8A3S  HD13 PQ: 0 ANSI: 0
[ 8876.175625] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[ 8881.611912] input: Logitech K400 as /devices/platform/axi/1000120000.pcie/1f00300000.usb/xhci-hcd.1/usb4/4-1/4-1:1.2/0003:046D:C52B.0011/0003:046D:4024.0012/input/input21

```
lsscsi:
```
[0:0:0:0]    cd/dvd  PLDS     DVD+-RW DS-8A3S  HD13  -        
  state=running queue_depth=1 scsi_level=0 type=5 device_blocked=0 timeout=30

```

The question is. How do I tell the system that the drive is a scsi dvdrom (sr0) not a scsi general (sg0)?

NOTE: I am about to go away for a week, so will not likely be able to answer questions quickly

---

### Post by yancek on 2024-04-03
I'm not familiar with raspberry devices and have never used ARM64 but would be curious as to what actually happens when you try to mount.  Could you post the exact command and output of your attempt to mount?  Someone may be able to assist with that information.

---

### Post by kenny-astbury on 2024-04-03
Linux doesn't like cdroms mounted to scsi general:

```
kenny@pi5-desktop:~$ sudo mount /dev/sg0 /media/kenny/cdrom/
mount: /media/kenny/cdrom: /dev/sg0 is not a block device.
       dmesg(1) may have more information after failed mount system call.

```
dmesg:
```
[  645.217552] /dev/sg0: Can't open blockdev
```

---

### Post by kenny-astbury on 2024-04-10
Just got back from being away. Does anyone have any ideas about this? I was thinking that I may need to use a different repository to [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) for the update... maybe ...

---

### Post by kenny-astbury on 2024-04-18
I have resorted to raspbian with a KDE plasma UI in order to use my DVD  with a nice interface, however, I am still wanting to use Ubuntu. Does  anyone have an idea why the DVD USB drive is acquiring sg0 and not sr0  as described above?

---

### Post by him610 on 2024-04-18
@kennypastbury
On a search of "raspberry pi sg0"...
> The Raspberry Pi sg0 is a physical SCSI device that is the raw SCSI device for a drive. When a USB hard drive is inserted into a Raspberry Pi, three additional entries appear in /dev: sda, sda1, and sg0. When the card is unplugged, these entries disappear.
Furthermore...
> Here are some steps to format an external hard drive for Raspberry Pi in Raspbian:
Get the drive's path using $ sudo fdisk -l
Enter fdisk to edit the disk's partition table: $ sudo fdisk /dev/sda *
Format the partition: $ sudo mkfs -t ext4 /dev/sda1 *
Create a directory to use as the filesystem mount: (e.g. sudo mkdir /ssd 

---

### Post by kenny-astbury on 2024-04-22
Hi him610,

The problem is that Ubuntu is allocating /dev/sg0 to the dvd-rom instead of /dev/sr0. This is not correct as when I try to mount the dvd-rom, the system is expecting a block device and not the dvd device:

```
kenny@pi5-desktop:~$ sudo mount /dev/sg0 /media/kenny/cdrom/
mount: /media/kenny/cdrom: /dev/sg0 is not a block device.
```

---

