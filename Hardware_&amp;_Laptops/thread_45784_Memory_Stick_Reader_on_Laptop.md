---
title: "Memory Stick Reader on Laptop"
date: 2005-07-01
forum: Hardware &amp; Laptops
---

### Post by jkrolen5500 on 2005-07-01
Hello, I am running Ubuntu Hoary 5.04 with a custom kernel 2.6.11-12 and I am having a problem getting the memory stick to mount.

When I compiled the kernel I selected SCSI disk support as a module, MMC/SD support compiled in, MMC block device driver compiled in as a module, USB Mass Storage Support compiled in, 

Here is the output from /var/log/messages when i put the stick in the drive:

Jul  1 11:25:42 localhost kernel: usb 3-1: new full speed USB device using uhci_hcd and address 9
Jul  1 11:25:42 localhost kernel: scsi7 : SCSI emulation for USB Mass Storage devices
Jul  1 11:25:47 localhost kernel:   Vendor: Generic   Model: CF Reader         Rev: 1.01
Jul  1 11:25:47 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
Jul  1 11:25:47 localhost kernel: Attached scsi removable disk sda at scsi7, channel 0, id 0, lun 0
Jul  1 11:25:47 localhost scsi.agent[7508]:      sd_mod: loaded sucessfully

/etc/udev/udev.conf says :
# udev_root - where in the filesystem to place the device nodes
udev_root="/dev/"

the only new devices in /dev when I put the stick in are :

brw-r-----  1 root plugdev   8,   0 Jul  1 11:42 sda

if i attemped to mount that:
root@jerlaptop:/usr/src/linux # mount -t vfat /dev/sda /mnt/mstick/
mount: No medium found

here is udevinfo :
root@jerlaptop:/usr/src/linux # udevinfo -a  -p /sys/block/sda
  looking at the device chain at '/sys/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/host8/target8:0:0/8:0:0:0':
    BUS="scsi"
    ID="8:0:0:0"
    SYSFS{detach_state}="0"
    SYSFS{device_blocked}="0"
    SYSFS{max_sectors}="240"
    SYSFS{model}="CF Reader       "
    SYSFS{queue_depth}="1"
    SYSFS{queue_type}="none"
    SYSFS{rev}="1.01"
    SYSFS{scsi_level}="3"
    SYSFS{state}="running"
    SYSFS{timeout}="30"
    SYSFS{type}="0"
    SYSFS{vendor}="Generic "


Everything seems to check out fine! But /dev/sda1 isn't being created and I get the no medium found.  Even if I do 

#mknod /dev/sda1 b 8 1 

I get a no medium found error.   If anyone can help, please do! Thanks!

---

### Post by monchichi on 2005-07-01
interesting. i don't know anything about memory sticks.. do you have to format them? if not, what type of filesystem do they have on them?

Because it appears to me that the device is detected without a hitch, but the partition & filesystem is not. try playing in parted and fdisk with sda and see what it reports as far as partitions and filesystems go...

---

### Post by jkrolen5500 on 2005-07-01
fdisk -l /dev/sda shows nothing.

The memory stick is formated and works in mepis mounted in a camera.

---

### Post by jkrolen5500 on 2005-07-01
I commented out :
#BUS="scsi", KERNEL="sd[a-z]*", PROGRAM="/etc/udev/scripts/removable.sh %k", RESULT="1", NAME="%k", MODE="0640", GROUP="plugdev"

and left in 

# Memory Stick
BUS="scsi", SYSFS_vendor="Generic ", NAME="mstick%n"
 
at the end and now it appears as /dev/mstick

Still no device numbers though!

#fdisk -l /dev/mstick 

shows nothing and 

#mount -t vfat /dev/mstick /mnt/mstick 
mount: No medium found

The mount works fine in mepis using a similar setup.

---

### Post by jkrolen5500 on 2005-07-01
output from dmesg



usb 3-1: new full speed USB device using uhci_hcd and address 16
DEV: registering device: ID = '3-1'
PM: Adding info for usb:3-1
bus usb: add device 3-1
bound device '3-1' to driver 'usb'
DEV: registering device: ID = '3-1:1.0'
PM: Adding info for usb:3-1:1.0
bus usb: add device 3-1:1.0
usb-storage: USB Mass Storage device detected
usb-storage: -- associate_dev
usb-storage: Vendor: 0x058f, Product: 0x9361, Revision: 0x0100
usb-storage: Interface Subclass: 0x06, Protocol: 0x50
usb-storage: Vendor:  ,  Product: USB Reader
usb-storage: Transport: Bulk
usb-storage: Protocol: Transparent SCSI
usb-storage: usb_stor_control_msg: rq=fe rqtype=a1 value=0000 index=00 len=1
usb-storage: GetMaxLUN command result is 1, data is 1
usb-storage: *** thread sleeping.
scsi14 : SCSI emulation for USB Mass Storage devices
DEV: registering device: ID = 'host14'
PM: Adding info for No Bus:host14
CLASS: registering class device: ID = 'host14'
class_hotplug - name = host14
bound device '3-1:1.0' to driver 'usb-storage'
usb-storage: device found at 16
usb-storage: waiting for device to settle before scanning
usb-storage: queuecommand called
usb-storage: *** thread awakened.
usb-storage: Command INQUIRY (6 bytes)
usb-storage:  12 00 00 00 24 00
usb-storage: Bulk Command S 0x43425355 T 0x3fd3 L 36 F 128 Trg 0 LUN 0 CL 6
usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
usb-storage: Status code 0; transferred 31/31
usb-storage: -- transfer complete
usb-storage: Bulk command transfer result=0
usb-storage: usb_stor_bulk_transfer_buf: xfer 36 bytes
usb-storage: Status code 0; transferred 36/36
usb-storage: -- transfer complete
usb-storage: Bulk data transfer result 0x0
usb-storage: Attempting to get CSW...
usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
usb-storage: Status code 0; transferred 13/13
usb-storage: -- transfer complete
usb-storage: Bulk status result = 0
usb-storage: Bulk Status S 0x53425355 T 0x3fd3 R 0 Stat 0x0
usb-storage: scsi cmd done, result=0x0
usb-storage: *** thread sleeping.
  Vendor: Generic   Model: CF Reader         Rev: 1.01
  Type:   Direct-Access                      ANSI SCSI revision: 00
DEV: registering device: ID = 'target14:0:0'
PM: Adding info for No Bus:target14:0:0
DEV: registering device: ID = '14:0:0:0'
PM: Adding info for scsi:14:0:0:0
bus scsi: add device 14:0:0:0
usb-storage: queuecommand called
usb-storage: *** thread awakened.
usb-storage: Command TEST_UNIT_READY (6 bytes)
usb-storage:  00 00 00 00 00 00
usb-storage: Bulk Command S 0x43425355 T 0x3fd4 L 0 F 0 Trg 0 LUN 0 CL 6
usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
usb-storage: Status code 0; transferred 31/31
usb-storage: -- transfer complete
usb-storage: Bulk command transfer result=0
usb-storage: Attempting to get CSW...
usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
usb-storage: Status code 0; transferred 13/13
usb-storage: -- transfer complete
usb-storage: Bulk status result = 0
usb-storage: Bulk Status S 0x53425355 T 0x3fd4 R 0 Stat 0x1
usb-storage: -- transport indicates command failure
usb-storage: Issuing auto-REQUEST_SENSE
usb-storage: Bulk Command S 0x43425355 T 0x80003fd4 L 18 F 128 Trg 0 LUN 0 CL 6
usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
usb-storage: Status code 0; transferred 31/31
usb-storage: -- transfer complete
usb-storage: Bulk command transfer result=0
usb-storage: usb_stor_bulk_transfer_buf: xfer 18 bytes
usb-storage: Status code 0; transferred 18/18
usb-storage: -- transfer complete
usb-storage: Bulk data transfer result 0x0
usb-storage: Attempting to get CSW...
usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
usb-storage: Status code 0; transferred 13/13
usb-storage: -- transfer complete
usb-storage: Bulk status result = 0
usb-storage: Bulk Status S 0x53425355 T 0x80003fd4 R 0 Stat 0x0
usb-storage: -- Result from auto-sense is 0
usb-storage: -- code: 0xf0, key: 0x2, ASC: 0x3a, ASCQ: 0x0
usb-storage: (Unknown Key): (unknown ASC/ASCQ)
usb-storage: scsi cmd done, result=0x2
usb-storage: *** thread sleeping.
usb-storage: queuecommand called
usb-storage: *** thread awakened.
usb-storage: Command TEST_UNIT_READY (6 bytes)
usb-storage:  00 00 00 00 00 00
usb-storage: Bulk Command S 0x43425355 T 0x3fd5 L 0 F 0 Trg 0 LUN 0 CL 6
usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
usb-storage: Status code 0; transferred 31/31
usb-storage: -- transfer complete
usb-storage: Bulk command transfer result=0
usb-storage: Attempting to get CSW...
usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
usb-storage: Status code 0; transferred 13/13
usb-storage: -- transfer complete
usb-storage: Bulk status result = 0
usb-storage: Bulk Status S 0x53425355 T 0x3fd5 R 0 Stat 0x1
usb-storage: -- transport indicates command failure
usb-storage: Issuing auto-REQUEST_SENSE
usb-storage: Bulk Command S 0x43425355 T 0x80003fd5 L 18 F 128 Trg 0 LUN 0 CL 6
usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
usb-storage: Status code 0; transferred 31/31
usb-storage: -- transfer complete
usb-storage: Bulk command transfer result=0
usb-storage: usb_stor_bulk_transfer_buf: xfer 18 bytes
usb-storage: Status code 0; transferred 18/18
usb-storage: -- transfer complete
usb-storage: Bulk data transfer result 0x0
usb-storage: Attempting to get CSW...
usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
usb-storage: Status code 0; transferred 13/13
usb-storage: -- transfer complete
usb-storage: Bulk status result = 0
usb-storage: Bulk Status S 0x53425355 T 0x80003fd5 R 0 Stat 0x0
usb-storage: -- Result from auto-sense is 0
usb-storage: -- code: 0xf0, key: 0x2, ASC: 0x3a, ASCQ: 0x0
usb-storage: (Unknown Key): (unknown ASC/ASCQ)
usb-storage: scsi cmd done, result=0x2
usb-storage: *** thread sleeping.
usb-storage: queuecommand called
usb-storage: *** thread awakened.
usb-storage: Command TEST_UNIT_READY (6 bytes)
usb-storage:  00 00 00 00 00 00
usb-storage: Bulk Command S 0x43425355 T 0x3fd6 L 0 F 0 Trg 0 LUN 0 CL 6
usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
usb-storage: Status code 0; transferred 31/31
usb-storage: -- transfer complete
usb-storage: Bulk command transfer result=0
usb-storage: Attempting to get CSW...
usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
usb-storage: Status code 0; transferred 13/13
usb-storage: -- transfer complete
usb-storage: Bulk status result = 0
usb-storage: Bulk Status S 0x53425355 T 0x3fd6 R 0 Stat 0x1
usb-storage: -- transport indicates command failure
usb-storage: Issuing auto-REQUEST_SENSE
usb-storage: Bulk Command S 0x43425355 T 0x80003fd6 L 18 F 128 Trg 0 LUN 0 CL 6
usb-storage: usb_stor_bulk_transfer_buf: xfer 31 bytes
usb-storage: Status code 0; transferred 31/31
usb-storage: -- transfer complete
usb-storage: Bulk command transfer result=0
usb-storage: usb_stor_bulk_transfer_buf: xfer 18 bytes
usb-storage: Status code 0; transferred 18/18
usb-storage: -- transfer complete
usb-storage: Bulk data transfer result 0x0
usb-storage: Attempting to get CSW...
usb-storage: usb_stor_bulk_transfer_buf: xfer 13 bytes
usb-storage: Status code 0; transferred 13/13
usb-storage: -- transfer complete
usb-storage: Bulk status result = 0
usb-storage: Bulk Status S 0x53425355 T 0x80003fd6 R 0 Stat 0x0
usb-storage: -- Result from auto-sense is 0
usb-storage: -- code: 0xf0, key: 0x2, ASC: 0x3a, ASCQ: 0x0
usb-storage: (Unknown Key): (unknown ASC/ASCQ)
usb-storage: scsi cmd done, result=0x2
usb-storage: *** thread sleeping.
Attached scsi removable disk sda at scsi14, channel 0, id 0, lun 0
bound device '14:0:0:0' to driver 'sd'
CLASS: registering class device: ID = '14:0:0:0'
class_hotplug - name = 14:0:0:0
usb-storage: queuecommand called
usb-storage: *** thread awakened.
usb-storage: Bad target number (1:0)
usb-storage: scsi cmd done, result=0x40000
usb-storage: *** thread sleeping.
usb-storage: queuecommand called
usb-storage: *** thread awakened.
usb-storage: Bad target number (2:0)
usb-storage: scsi cmd done, result=0x40000
usb-storage: *** thread sleeping.
usb-storage: queuecommand called
usb-storage: *** thread awakened.
usb-storage: Bad target number (3:0)
usb-storage: scsi cmd done, result=0x40000
usb-storage: *** thread sleeping.
usb-storage: queuecommand called
usb-storage: *** thread awakened.
usb-storage: Bad target number (4:0)
usb-storage: scsi cmd done, result=0x40000
usb-storage: *** thread sleeping.
usb-storage: queuecommand called
usb-storage: *** thread awakened.
usb-storage: Bad target number (5:0)
usb-storage: scsi cmd done, result=0x40000
usb-storage: *** thread sleeping.
usb-storage: queuecommand called
usb-storage: *** thread awakened.
usb-storage: Bad target number (6:0)
usb-storage: scsi cmd done, result=0x40000
usb-storage: *** thread sleeping.
usb-storage: queuecommand called
usb-storage: *** thread awakened.
usb-storage: Bad target number (7:0)
usb-storage: scsi cmd done, result=0x40000
usb-storage: *** thread sleeping.
usb-storage: device scan complete

---

### Post by jkrolen5500 on 2005-07-20
Since no one answered my question, I will bump it.

---

### Post by sbassett on 2005-07-21
[QUOTE=jkrolen5500]Since no one answered my question, I will bump it.[/QUOTE]
 have you tried fdisk -l /dev/sda1 ?

---

