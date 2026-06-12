---
title: "USB autodetect takes 5 minutes to recognize device"
date: 2005-12-07
forum: Hardware &amp; Laptops
---

### Post by bananana on 2005-12-07
I originally posted this in the GNOME thread (accidentally, of course). After a few days of no replies, I'm moving it here. 

I have a usb flash drive that uses the USB mass storage driver. For some reason, it always takes ~5 minutes to autodetect and mount the drive. It seems that scsi.agent expects it to be /dev/sda when in fact it is /dev/sdb. So it tries to use sda and fails a few times before it tries sdb. This is why it's taking so long. Once it tries sdb, it goes real quick (as you can see from the timestamps below). This is the output from syslog:

[FONT="Fixedsys"]Dec  4 23:27:16 localhost kernel: [4296201.947000] usb 1-3: new full speed USB device using ohci_hcd and address 2
Dec  4 23:27:16 localhost kernel: [4296202.570000] Initializing USB Mass Storage driver...
Dec  4 23:27:16 localhost kernel: [4296202.594000] scsi0 : SCSI emulation for USB Mass Storage devices
Dec  4 23:27:16 localhost kernel: [4296202.598000] usb-storage: device found at 2
Dec  4 23:27:16 localhost kernel: [4296202.598000] usb-storage: waiting for device to settle before scanning
Dec  4 23:27:16 localhost kernel: [4296202.599000] usbcore: registered new driver usb-storage
Dec  4 23:27:16 localhost kernel: [4296202.599000] USB Mass Storage support registered.
Dec  4 23:27:16 localhost usb.agent[8695]:      usb-storage: loaded successfully
Dec  4 23:27:21 localhost kernel: [4296207.598000]   Vendor: ScanLogi  Model: SL11R-IDE         Rev: 0074
Dec  4 23:27:21 localhost kernel: [4296207.598000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Dec  4 23:27:21 localhost kernel: [4296207.605000]   Vendor: ScanLogi  Model: SL11R-IDE         Rev: 0074
Dec  4 23:27:21 localhost kernel: [4296207.605000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Dec  4 23:27:21 localhost kernel: [4296207.618000] usb-storage: device scan complete
Dec  4 23:27:22 localhost scsi.agent[8766]:      sd_mod: loaded sucessfully (for disk)
Dec  4 23:29:02 localhost kernel: [4296207.946000] sda: Spinning up disk....................................................................................................not responding...
Dec  4 23:29:02 localhost kernel: [4296308.145000] sda : READ CAPACITY failed.
Dec  4 23:29:02 localhost kernel: [4296308.145000] sda : status=1, message=00, host=0, driver=08
Dec  4 23:29:02 localhost kernel: [4296308.145000] sd: Current: sense key: Not Ready
Dec  4 23:29:02 localhost kernel: [4296308.145000]     Additional sense: No additional sense information
Dec  4 23:29:02 localhost kernel: [4296308.152000] sda: Write Protect is off
Dec  4 23:29:02 localhost kernel: [4296308.152000] sda: Mode Sense: 00 00 00 00
Dec  4 23:29:02 localhost kernel: [4296308.152000] sda: assuming drive cache: write through
Dec  4 23:29:02 localhost usbmount[8864]: cannnot execute /sbin/udev_volume_id
Dec  4 23:30:42 localhost kernel: [4296308.200000] sda: Spinning up disk....................................................................................................not responding...
Dec  4 23:30:42 localhost kernel: [4296408.507000] sda : READ CAPACITY failed.
Dec  4 23:30:42 localhost kernel: [4296408.507000] sda : status=1, message=00, host=0, driver=08
Dec  4 23:30:42 localhost kernel: [4296408.507000] sd: Current: sense key: Not Ready
Dec  4 23:30:42 localhost kernel: [4296408.507000]     Additional sense: No additional sense information
Dec  4 23:30:42 localhost kernel: [4296408.514000] sda: Write Protect is off
Dec  4 23:30:42 localhost kernel: [4296408.514000] sda: Mode Sense: 00 00 00 00
Dec  4 23:30:42 localhost kernel: [4296408.514000] sda: assuming drive cache: write through
Dec  4 23:32:23 localhost kernel: [4296408.551000] sda: Spinning up disk....................................................................................................not responding...
Dec  4 23:32:23 localhost kernel: [4296508.768000] sda : READ CAPACITY failed.
Dec  4 23:32:23 localhost kernel: [4296508.768000] sda : status=1, message=00, host=0, driver=08
Dec  4 23:32:23 localhost kernel: [4296508.768000] sd: Current: sense key: Not Ready
Dec  4 23:32:23 localhost kernel: [4296508.768000]     Additional sense: No additional sense information
Dec  4 23:32:23 localhost kernel: [4296508.775000] sda: Write Protect is off
Dec  4 23:32:23 localhost kernel: [4296508.775000] sda: Mode Sense: 00 00 00 00
Dec  4 23:32:23 localhost kernel: [4296508.775000] sda: assuming drive cache: write through
Dec  4 23:32:23 localhost kernel: [4296508.775000]  /dev/scsi/host0/bus0/target0/lun0:<3>Buffer I/O error on device sda, logical block 0
Dec  4 23:32:23 localhost kernel: [4296508.775000] Buffer I/O error on device sda, logical block 0
Dec  4 23:32:23 localhost kernel: [4296508.775000]  unable to read partition table
Dec  4 23:32:23 localhost kernel: [4296508.779000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
Dec  4 23:32:23 localhost kernel: [4296508.834000] sdb: Unit Not Ready, sense:
Dec  4 23:32:23 localhost kernel: [4296508.834000] : Current: sense key: No Sense
Dec  4 23:32:23 localhost kernel: [4296508.834000]     Additional sense: No additional sense information
Dec  4 23:32:23 localhost kernel: [4296509.417000] SCSI device sdb: 2104705 512-byte hdwr sectors (1078 MB)
Dec  4 23:32:23 localhost kernel: [4296509.428000] sda: Spinning up disk...<5>sdb: Write Protect is off
Dec  4 23:32:23 localhost kernel: [4296509.435000] sdb: Mode Sense: 00 00 00 00
Dec  4 23:32:23 localhost kernel: [4296509.435000] sdb: assuming drive cache: write through
Dec  4 23:32:23 localhost usbmount[8950]: cannnot execute /sbin/udev_volume_id
Dec  4 23:32:24 localhost kernel: [4296510.118000] SCSI device sdb: 2104705 512-byte hdwr sectors (1078 MB)
Dec  4 23:32:24 localhost kernel: [4296510.125000] sdb: Write Protect is off
Dec  4 23:32:24 localhost kernel: [4296510.125000] sdb: Mode Sense: 00 00 00 00
Dec  4 23:32:24 localhost kernel: [4296510.125000] sdb: assuming drive cache: write through
Dec  4 23:32:25 localhost kernel: [4296510.548000] .<5>SCSI device sdb: 2104705 512-byte hdwr sectors (1078 MB)
Dec  4 23:32:25 localhost kernel: [4296510.751000] sdb: Write Protect is off
Dec  4 23:32:25 localhost kernel: [4296510.751000] sdb: Mode Sense: 00 00 00 00
Dec  4 23:32:25 localhost kernel: [4296510.751000] sdb: assuming drive cache: write through
Dec  4 23:32:25 localhost kernel: [4296510.751000]  /dev/scsi/host0/bus0/target0/lun1:<3>Buffer I/O error on device sdb, logical block 0
Dec  4 23:32:25 localhost kernel: [4296510.751000] Buffer I/O error on device sdb, logical block 1
Dec  4 23:32:25 localhost kernel: [4296510.751000] Buffer I/O error on device sdb, logical block 2
Dec  4 23:32:25 localhost kernel: [4296510.751000] Buffer I/O error on device sdb, logical block 3
Dec  4 23:32:25 localhost kernel: [4296510.751000] Buffer I/O error on device sdb, logical block 4
Dec  4 23:32:25 localhost kernel: [4296510.751000] Buffer I/O error on device sdb, logical block 5
Dec  4 23:32:25 localhost kernel: [4296510.751000] Buffer I/O error on device sdb, logical block 6
Dec  4 23:32:25 localhost kernel: [4296510.751000] Buffer I/O error on device sdb, logical block 7
Dec  4 23:32:25 localhost kernel: [4296510.756000]  unable to read partition table
Dec  4 23:32:25 localhost kernel: [4296510.767000] Attached scsi removable disk sdb at scsi0, channel 0, id 0, lun 1
Dec  4 23:32:25 localhost scsi.agent[8764]:      sd_mod: loaded sucessfully (for disk)
Dec  4 23:32:25 localhost kernel: [4296511.363000] SCSI device sdb: 2104705 512-byte hdwr sectors (1078 MB)
Dec  4 23:32:25 localhost kernel: [4296511.370000] sdb: Write Protect is off
Dec  4 23:32:25 localhost kernel: [4296511.370000] sdb: Mode Sense: 00 00 00 00
Dec  4 23:32:25 localhost kernel: [4296511.370000] sdb: assuming drive cache: write through
Dec  4 23:32:26 localhost kernel: [4296511.785000] .<5>SCSI device sdb: 2104705 512-byte hdwr sectors (1078 MB)
Dec  4 23:32:26 localhost kernel: [4296511.967000] sdb: Write Protect is off
Dec  4 23:32:26 localhost kernel: [4296511.967000] sdb: Mode Sense: 00 00 00 00
Dec  4 23:32:26 localhost kernel: [4296511.967000] sdb: assuming drive cache: write through
Dec  4 23:32:27 localhost kernel: [4296511.967000]  /dev/scsi/host0/bus0/target0/lun1: p1
Dec  4 23:32:28 localhost usbmount[8974]: cannnot execute /sbin/udev_volume_id
Dec  4 23:32:28 localhost kernel: [4296514.455000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

[/FONT]

---

