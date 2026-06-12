---
title: "usb transfer speed, not usb2"
date: 2007-09-01
forum: Hardware &amp; Laptops
---

### Post by PetePete on 2007-09-01
been backing up data onto an external hard drive through a usb2 hard disk caddy.

my laptop has usb2 but rsync tells me the transfer is avg 6.1mb a second which seems more usb1 speed than usb2.

any ideas how I can force it to recognise the caddy as usb2?

The disk is a 80gb 7200rpm drive ext3 formatted.

heres my /var/log/syslog output

```

Sep  1 14:51:11 pete-laptop kernel: [16773.644000] usb 3-3: new high speed USB device using ehci_hcd and address 5
Sep  1 14:51:12 pete-laptop kernel: [16773.780000] usb 3-3: configuration #1 chosen from 1 choice
Sep  1 14:51:12 pete-laptop kernel: [16773.780000] scsi3 : SCSI emulation for USB Mass Storage devices
Sep  1 14:51:12 pete-laptop kernel: [16773.780000] usb-storage: device found at 5
Sep  1 14:51:12 pete-laptop kernel: [16773.780000] usb-storage: waiting for device to settle before scanning
Sep  1 14:51:12 pete-laptop NetworkManager: <debug info>^I[1188654672.247640] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10DB5E293').
Sep  1 14:51:12 pete-laptop NetworkManager: <debug info>^I[1188654672.516580] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10DB5E293_if0').
Sep  1 14:51:12 pete-laptop NetworkManager: <debug info>^I[1188654672.517724] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10DB5E293_if0_scsi_host').
Sep  1 14:51:12 pete-laptop NetworkManager: <debug info>^I[1188654672.518729] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10DB5E293_usbraw').
Sep  1 14:51:17 pete-laptop kernel: [16778.780000] usb-storage: device scan complete
Sep  1 14:51:18 pete-laptop kernel: [16779.848000] scsi 3:0:0:0: Direct-Access     Hitachi  HDS721680PLAT80  0000 PQ: 0 ANSI: 0
Sep  1 14:51:18 pete-laptop kernel: [16779.852000] SCSI device sdb: 160836480 512-byte hdwr sectors (82348 MB)
Sep  1 14:51:18 pete-laptop kernel: [16779.856000] sdb: Write Protect is off
Sep  1 14:51:18 pete-laptop kernel: [16779.856000] sdb: Mode Sense: 27 00 00 00
Sep  1 14:51:18 pete-laptop kernel: [16779.856000] sdb: assuming drive cache: write through
Sep  1 14:51:18 pete-laptop kernel: [16779.856000] SCSI device sdb: 160836480 512-byte hdwr sectors (82348 MB)
Sep  1 14:51:18 pete-laptop kernel: [16779.856000] sdb: Write Protect is off
Sep  1 14:51:18 pete-laptop kernel: [16779.856000] sdb: Mode Sense: 27 00 00 00
Sep  1 14:51:18 pete-laptop kernel: [16779.856000] sdb: assuming drive cache: write through
Sep  1 14:51:18 pete-laptop kernel: [16779.856000]  sdb: sdb1
Sep  1 14:51:18 pete-laptop kernel: [16779.872000] sd 3:0:0:0: Attached scsi disk sdb
Sep  1 14:51:18 pete-laptop kernel: [16779.872000] sd 3:0:0:0: Attached scsi generic sg2 type 0
Sep  1 14:51:18 pete-laptop NetworkManager: <debug info>^I[1188654678.260899] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10DB5E293_if0_scsi_host_scsi_device_lun0').
Sep  1 14:51:18 pete-laptop NetworkManager: <debug info>^I[1188654678.348458] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10DB5E293_if0_scsi_host_scsi_device_lun0_scsi_generic').
Sep  1 14:51:18 pete-laptop NetworkManager: <debug info>^I[1188654678.484998] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Hitachi_HDS721680PLAT80_DEF10DB5E293_0_0').
Sep  1 14:51:18 pete-laptop NetworkManager: <debug info>^I[1188654678.622600] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_51ce6146_893e_4c20_887d_6d85edad0dd1').
Sep  1 14:51:19 pete-laptop kernel: [16780.744000] kjournald starting.  Commit interval 5 seconds
Sep  1 14:51:19 pete-laptop kernel: [16780.748000] EXT3 FS on sdb1, internal journal
Sep  1 14:51:19 pete-laptop kernel: [16780.748000] EXT3-fs: mounted filesystem with ordered data mode.
Sep  1 14:51:19 pete-laptop hald: mounted /dev/sdb1 on behalf of uid 1000

```

---

### Post by PetePete on 2007-09-01
ps this is the output of lshw when its plugged in..

as (i think!?) you can see it recognises everything as usb2.0
```

*-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
              *-usb
                   description: Mass storage device
                   product: Cypress AT2LP
                   physical id: 3
                   bus info: usb@3:3
                   logical name: scsi10
                   version: 2.40
                   serial: DEF10DB5E293
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=2mA speed=480.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: HDS721680PLAT80
                      vendor: Hitachi
                      physical id: 0.0.0
                      bus info: scsi@10:0.0.0
                      logical name: /dev/sdb
                      version: 0000
                      serial: VP
                      size: 76GB
                      capabilities: partitioned partitioned:dos
                    *-volume
                         description: Linux filesystem partition
                         physical id: 1
                         bus info: scsi@10:0.0.0,1
                         logical name: /dev/sdb1
                         capacity: 76GB
                         capabilities: primary bootable

```

and ive tried rsync and dolphin to transfer files, both are slow, around 5mb second in dolphin.

---

### Post by PetePete on 2007-09-01
update:
removed synchronous and then it got up to speeds of 7.5mb second, but still nowhere near what usb2.0 should be.

edit:
just found out the read is about 25mbs but still the write is 7.5
someone must have an idea?!

---

### Post by klep on 2007-09-05
I have the exact (almost to the letter) problem.

I am using rsync to transfer files are varying size to a usb2.0 harddrive caddy housing a 80gig ide hdd. I only achieve speeds of ~15mb/s max. I have no idea why this might be. I havent tried anything to fix it yet though - i found this post when i started to look for a solution,

---

### Post by PetePete on 2007-09-06
let me know if you find a solution!

removing sync sped things up a little bit for me, i'm wondering if its just hardware related, need to test on windows machine i suppose.

---

