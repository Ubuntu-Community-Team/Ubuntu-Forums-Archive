---
title: "firewire &amp; icy box &amp; acer tm 803"
date: 2005-04-11
forum: Hardware &amp; Laptops
---

### Post by noble on 2005-04-11
hello!

i searched now for hours and was not able to geht my external hdd running.
i bought myself a 3,5" IcyBox whicht should work perfectly under linux - this said some guys whos statements i found with google.

but this wont work for me.

i plug my device on an this will be give as response

> sudo tail -f /var/log/syslog

Apr 12 00:37:04 localhost kernel: ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
Apr 12 00:37:05 localhost kernel: ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[0050770e00071002]
Apr 12 00:37:05 localhost kernel: ieee1394: Node changed: 0-00:1023 -> 0-01:1023Apr 12 00:37:05 localhost kernel: ieee1394: unsolicited response packet received - no tlabel match
Apr 12 00:37:05 localhost kernel: scsi4 : SCSI emulation for IEEE-1394 SBP-2 Devices
Apr 12 00:37:06 localhost kernel: ieee1394: sbp2: Logged into SBP-2 device
Apr 12 00:37:06 localhost kernel: ieee1394: Node 0-00:1023: Max speed [S400] - Max payload [2048]
Apr 12 00:37:06 localhost kernel:   Vendor: SAMSUNG   Model: SP1614N           Rev:
Apr 12 00:37:06 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 06
Apr 12 00:37:06 localhost kernel: SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
Apr 12 00:37:06 localhost kernel: sda: asking for cache data failed
Apr 12 00:37:06 localhost kernel: sda: assuming drive cache: write through
Apr 12 00:37:21 localhost hal.hotplug[14681]: timout(10000 ms) waiting for /devices/pci0000:00/0000:00:1e.0/0000:02:07.0/fw-host0/0050770e00071002/0050770e00071002-0/host4/target4:0:0/4:0:0:0
Apr 12 00:37:31 localhost scsi.agent[14684]: Attribute /sys/devices/pci0000:00/0000:00:1e.0/0000:02:07.0/fw-host0/0050770e00071002/0050770e00071002-0/host4/target4:0:0/4:0:0:0/type does not exist
Apr 12 00:37:36 localhost kernel: ieee1394: sbp2: aborting sbp2 command
Apr 12 00:37:36 localhost kernel: Test Unit Ready 00 00 00 00 00
Apr 12 00:37:36 localhost udev[14708]: creating device node '/dev/sda'
Apr 12 00:37:46 localhost kernel: ieee1394: sbp2: aborting sbp2 command
Apr 12 00:37:46 localhost kernel: Test Unit Ready 00 00 00 00 00
Apr 12 00:37:46 localhost kernel: ieee1394: sbp2: reset requested
Apr 12 00:37:46 localhost kernel: ieee1394: sbp2: Generating sbp2 fetch agent reset
Apr 12 00:37:56 localhost kernel: ieee1394: sbp2: aborting sbp2 command
Apr 12 00:37:56 localhost kernel: Test Unit Ready 00 00 00 00 00
Apr 12 00:37:56 localhost kernel: ieee1394: sbp2: reset requested
Apr 12 00:37:56 localhost kernel: ieee1394: sbp2: Generating sbp2 fetch agent reset
Apr 12 00:38:16 localhost kernel: ieee1394: sbp2: aborting sbp2 command
Apr 12 00:38:16 localhost kernel: Test Unit Ready 00 00 00 00 00
Apr 12 00:38:16 localhost kernel: ieee1394: sbp2: reset requested
Apr 12 00:38:16 localhost kernel: ieee1394: sbp2: Generating sbp2 fetch agent reset

> dmesg

ieee1394: sbp2: hpsb_node_write failed.

ieee1394: sbp2: reset requested
ieee1394: sbp2: Generating sbp2 fetch agent reset
ieee1394: sbp2: hpsb_node_write failed.

ieee1394: sbp2: Bus reset in progress - rejecting command
ieee1394: sbp2: reset requested
ieee1394: sbp2: Generating sbp2 fetch agent reset
ieee1394: sbp2: hpsb_node_write failed.

ieee1394: sbp2: Bus reset in progress - rejecting command
ieee1394: sbp2: reset requested
ieee1394: sbp2: Generating sbp2 fetch agent reset
ieee1394: sbp2: hpsb_node_write failed.

ieee1394: sbp2: Bus reset in progress - rejecting command
scsi: Device offlined - not ready after error recovery: host 5 channel 0 id 0 lun 0
scsi5 (0:0): rejecting I/O to offline device
scsi5 (0:0): rejecting I/O to offline device
scsi5 (0:0): rejecting I/O to offline device
sda : READ CAPACITY failed.
sda : status=0, message=00, host=2, driver=04
sda : sense not available.
scsi5 (0:0): rejecting I/O to offline device
sda: asking for cache data failed
sda: assuming drive cache: write through
 /dev/scsi/host5/bus0/target0/lun0:<3>scsi5 (0:0): rejecting I/O to offline device
Buffer I/O error on device sda, logical block 0
scsi5 (0:0): rejecting I/O to offline device
Buffer I/O error on device sda, logical block 0
 unable to read partition table
Attached scsi disk sda at scsi5, channel 0, id 0, lun 0
ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
ieee1394: unsolicited response packet received - no tlabel match
ieee1394: sbp2: Error reconnecting to SBP-2 device - reconnect failed
ieee1394: sbp2: Logged out of SBP-2 device
ieee1394: sbp2: Logged into SBP-2 device
ieee1394: Node 0-00:1023: Max speed [S400] - Max payload [2048]

I really need your help

thank you

---

