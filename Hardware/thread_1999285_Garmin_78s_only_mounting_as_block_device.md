---
title: "Garmin 78s only mounting as block device"
date: 2012-06-07
forum: Hardware
---

### Post by talikarng on 2012-06-07
Hello,

I have had a quick read through various threads with no luck.
Whenever I connect my gps (Garmin GPSMap 78s) via usb it is only recognised as a block device.

Regardless of whether the gps was turned on or not, when I plug it in all I see is a screen saying "Saving <blah blah>..." and then the GARMIN logo with a USB logo below it. I can not go back to the satellite screen etc. When I remove the usb cable the GPS turns off.

I have checked dmesg output which only refers to it being a block device. I have installed gpsd and set it up using dpkg-reconfigure. I can not get any live gps output on xgps, gpsmon etc.

Any suggestions?

---

### Post by Cheesehead on 2012-06-07
The most likely problem is a gpsd.hotpplug event hasn't been enabled in udev, so it's not listening on that particular block device...but let's make sure that everything else works first before we bark up that tree.

Your first step is to figure out which block device the gps is plugged into.

Your second step is to point gpsd to that block device.For example, the following two commands will kill the currently-running gpsd, and then restart it looking for input on a specific block device. 
```
$ pkill gpsd
$ gpsd /dev/my-device-name
```

Your third step is to use xgps or gpsmon to check correct connectivity,

Okay, once all that works then you're ready for the fourth step.

The fourth step is to fix the gpsd.hotplug event to do all this automatically. The excellent [gpsd Troubleshooting Guide]("gpsd.berlios.de/troubleshooting.html") covers the possible problems and fixes very well.

---

### Post by talikarng on 2012-06-08
Thankyou Cheesehead,

I am having trouble working out where the device is connected <I should add that the interface is set to "NMEA In/Out" with NMEA Sentences set to "on">

From sudo tail -f /var/log/syslog
```


Jun  8 23:58:58 jolly-roger kernel: [ 2541.513766] usb 2-1.2: new full-speed USB device number 24 using ehci_hcd
Jun  8 23:58:58 jolly-roger kernel: [ 2541.585419] usb 2-1.2: device descriptor read/64, error -32
Jun  8 23:58:58 jolly-roger kernel: [ 2541.705314] hub 2-1:1.0: unable to enumerate USB device on port 2
Jun  8 23:59:10 jolly-roger kernel: [ 2553.511362] usb 2-1.2: new high-speed USB device number 25 using ehci_hcd
Jun  8 23:59:10 jolly-roger mtp-probe: checking bus 2, device 25: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2"
Jun  8 23:59:10 jolly-roger kernel: [ 2553.604252] scsi12 : usb-storage 2-1.2:1.0
Jun  8 23:59:10 jolly-roger mtp-probe: bus: 2, device: 25 was not an MTP device
Jun  8 23:59:11 jolly-roger kernel: [ 2554.601009] scsi 12:0:0:0: Direct-Access     Garmin   GARMIN Flash     1.00 PQ: 0 ANSI: 5
Jun  8 23:59:11 jolly-roger kernel: [ 2554.601500] scsi 12:0:0:1: Direct-Access     Garmin   GARMIN SD Card   1.00 PQ: 0 ANSI: 5
Jun  8 23:59:11 jolly-roger kernel: [ 2554.602269] sd 12:0:0:0: Attached scsi generic sg2 type 0
Jun  8 23:59:11 jolly-roger kernel: [ 2554.602478] sd 12:0:0:1: Attached scsi generic sg3 type 0
Jun  8 23:59:11 jolly-roger kernel: [ 2554.604840] sd 12:0:0:0: [sdb] 3973120 512-byte logical blocks: (2.03 GB/1.89 GiB)
Jun  8 23:59:11 jolly-roger kernel: [ 2554.605307] sd 12:0:0:0: [sdb] Write Protect is off
Jun  8 23:59:11 jolly-roger kernel: [ 2554.605313] sd 12:0:0:0: [sdb] Mode Sense: 23 00 00 00
Jun  8 23:59:11 jolly-roger kernel: [ 2554.606804] sd 12:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  8 23:59:11 jolly-roger kernel: [ 2554.607424] sd 12:0:0:1: [sdc] Attached SCSI removable disk
Jun  8 23:59:11 jolly-roger kernel: [ 2554.612708]  sdb:
Jun  8 23:59:11 jolly-roger kernel: [ 2554.615545] sd 12:0:0:0: [sdb] Attached SCSI removable disk


```

I tried to run gpsd on sdb and sdc but they didn't work. Is that because they are storage devices?

From sudo lsusb -v

```
Bus 002 Device 025: ID 091e:2459 Garmin International 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x091e Garmin International
  idProduct          0x2459 
  bcdDevice            5.09
  iManufacturer           0 
  iProduct                0 
  iSerial                 5 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0

```

Is the location of the device here or how I can find it?

---

### Post by talikarng on 2012-06-09
On a fresh install (onto a laptop I want to use when geocaching) I get the following results:

```
gpsmon
localhost:2947:               Unknown device>
(79) {"class":"VERSION","release":"3.4","rev":"3.4","proto_major":3,"proto_minor":6,


```
No changes after several minutes.

```

sudo gpsd -N -D4 usb:
gpsd:INFO: launching (Version 3.4)
gpsd:INFO: listening on port gpsd
gpsd:PROG: NTPD shmat(2916368,0,0) succeeded, segment 0
gpsd:PROG: NTPD shmat(2949137,0,0) succeeded, segment 1
gpsd:PROG: NTPD shmat(2818061,0,0) succeeded, segment 2
gpsd:PROG: NTPD shmat(2850830,0,0) succeeded, segment 3
gpsd:PROG: successfully connected to the DBUS system bus
gpsd:PROG: shmat() succeeded, segment 2883599
gpsd:PROG: shared-segment creation succeeded,
gpsd:INFO: NTPD ntpd_link_activate: 1
gpsd:INFO: stashing device usb: at slot 0
gpsd:PROG: changing to group 20
gpsd:INFO: running with effective group ID 20
gpsd:INFO: running with effective user ID 65534
gpsd:INFO: startup at 2012-06-09T12:21:23.000Z (1339244483)
gpsd:PROG: checking client(0)
gpsd:PROG: no etc/gpsd/device-hook present, skipped running ACTIVATE hook
gpsd:INFO: opening read-only GPS data source type 0 and at 'usb:'
gpsd:ERROR: device open failed: No such file or directory - retrying read-only
gpsd:ERROR: read-only device open failed: No such file or directory
gpsd:ERROR: usb:: device activation failed.
gpsd:INFO: reconnection attempt on device 0
gpsd:PROG: no etc/gpsd/device-hook present, skipped running ACTIVATE hook
gpsd:INFO: opening read-only GPS data source type 0 and at 'usb:'
gpsd:ERROR: device open failed: No such file or directory - retrying read-only
gpsd:ERROR: read-only device open failed: No such file or directory
gpsd:ERROR: usb:: device activation failed.
gpsd:INFO: reconnection attempt on device 0

```

dmesg output
```
[ 5294.860437] usb 1-2: new high-speed USB device number 5 using ehci_hcd
[ 5294.994723] scsi4 : usb-storage 1-2:1.0
[ 5295.994227] scsi 4:0:0:0: Direct-Access     Garmin   GARMIN Flash     1.00 PQ: 0 ANSI: 5
[ 5295.994896] scsi 4:0:0:1: Direct-Access     Garmin   GARMIN SD Card   1.00 PQ: 0 ANSI: 5
[ 5295.997099] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 5295.997851] sd 4:0:0:1: Attached scsi generic sg3 type 0
[ 5296.005493] sd 4:0:0:0: [sdb] 3973120 512-byte logical blocks: (2.03 GB/1.89 GiB)
[ 5296.014379] sd 4:0:0:0: [sdb] Write Protect is off
[ 5296.014389] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 5296.015368] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[ 5296.015731] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 5296.020497]  sdb:
[ 5296.032228] sd 4:0:0:0: [sdb] Attached SCSI removable disk

```

sudo udevadm monitor
```

KERNEL[5294.993656] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2 (usb)
KERNEL[5294.994431] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0 (usb)
KERNEL[5294.995055] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4 (scsi)
KERNEL[5294.995095] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/scsi_host/host4 (scsi_host)
UDEV  [5295.002414] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2 (usb)
UDEV  [5295.005586] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0 (usb)
UDEV  [5295.006330] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4 (scsi)
UDEV  [5295.009213] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/scsi_host/host4 (scsi_host)
KERNEL[5295.998073] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0 (scsi)
UDEV  [5295.998133] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0 (scsi)
KERNEL[5295.998171] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:0 (scsi)
KERNEL[5295.998200] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:0/scsi_disk/4:0:0:0 (scsi_disk)
KERNEL[5295.998228] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:0/scsi_device/4:0:0:0 (scsi_device)
KERNEL[5295.998265] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:0/scsi_generic/sg2 (scsi_generic)
KERNEL[5295.998300] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:0/bsg/4:0:0:0 (bsg)
KERNEL[5295.998331] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:1 (scsi)
KERNEL[5295.998357] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:1/scsi_disk/4:0:0:1 (scsi_disk)
KERNEL[5295.998384] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:1/scsi_device/4:0:0:1 (scsi_device)
KERNEL[5295.998417] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:1/scsi_generic/sg3 (scsi_generic)
KERNEL[5295.998450] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:1/bsg/4:0:0:1 (bsg)
UDEV  [5295.999309] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:0 (scsi)
UDEV  [5296.001839] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:0/scsi_disk/4:0:0:0 (scsi_disk)
UDEV  [5296.002926] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:0/scsi_device/4:0:0:0 (scsi_device)
KERNEL[5296.005210] add      /devices/virtual/bdi/8:32 (bdi)
KERNEL[5296.005267] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:1/block/sdc (block)
UDEV  [5296.005656] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:0/bsg/4:0:0:0 (bsg)
UDEV  [5296.005883] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:1 (scsi)
UDEV  [5296.006182] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:0/scsi_generic/sg2 (scsi_generic)
KERNEL[5296.007320] change   /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:1/block/sdc (block)
UDEV  [5296.009225] add      /devices/virtual/bdi/8:32 (bdi)
UDEV  [5296.011207] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:1/bsg/4:0:0:1 (bsg)
UDEV  [5296.012762] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:1/scsi_device/4:0:0:1 (scsi_device)
UDEV  [5296.014178] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:1/scsi_generic/sg3 (scsi_generic)
UDEV  [5296.014665] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:1/scsi_disk/4:0:0:1 (scsi_disk)
KERNEL[5296.015865] add      /devices/virtual/bdi/8:16 (bdi)
UDEV  [5296.016204] add      /devices/virtual/bdi/8:16 (bdi)
KERNEL[5296.020924] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:0/block/sdb (block)
KERNEL[5296.029826] change   /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:1/block/sdc (block)
UDEV  [5296.045344] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:1/block/sdc (block)
UDEV  [5296.070420] change   /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:1/block/sdc (block)
UDEV  [5296.090649] change   /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:1/block/sdc (block)
UDEV  [5296.200604] add      /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/host4/target4:0:0/4:0:0:0/block/sdb (block)
KERNEL[5296.356265] add      /module/fat (module)
UDEV  [5296.356975] add      /module/fat (module)
KERNEL[5296.357731] add      /kernel/slab/fat_cache (slab)
KERNEL[5296.357806] add      /kernel/slab/fat_inode_cache (slab)
UDEV  [5296.358426] add      /kernel/slab/fat_inode_cache (slab)
UDEV  [5296.358469] add      /kernel/slab/fat_cache (slab)
KERNEL[5296.376448] add      /module/vfat (module)
UDEV  [5296.376507] add      /module/vfat (module)
KERNEL[5296.394465] add      /module/nls_cp437 (module)
UDEV  [5296.394523] add      /module/nls_cp437 (module)
KERNEL[5296.400957] add      /module/nls_iso8859_1 (module)
UDEV  [5296.401717] add      /module/nls_iso8859_1 (module)

```

Still no joy. When I run xgps I don't see any GPS data at all.

I tried to copy /lib/udev/rules.d/40-gpsd.rules to /etc/rules.d/, rebooted the computer and then plugged in the GPS. I didn't manually start gpsd because I thought that the udev script would do that automatically. When I tried to run xpgs all I got was an error message saying "gpsd is not running"

So I went back and ran dpkg-reconfigure gpsd. See below:
```
# Default settings for gpsd.
# Please do not edit this file directly - use `dpkg-reconfigure gpsd' to
# change the options.
START_DAEMON="true"
GPSD_OPTIONS=""
DEVICES=""
USBAUTO="true"
GPSD_SOCKET="/var/run/gpsd.sock"
```

Now when I plug in the GPS and run xgps or gpsmon I don't get an error message saying that gpsd is not running. But I still can't get any GPS data.

Any ideas?

---

### Post by Cheesehead on 2012-06-09
The logs show that it's mounting as a removable drive (sdb and/or sdc) instead of a serial device. That's handy for uploading and downloading routes/points/maps...but not so much for NMEA stream.

Try [http://wiki.openstreetmap.org/wiki/USB_Garmin_on_GNU/Linux](http://wiki.openstreetmap.org/wiki/USB_Garmin_on_GNU/Linux).

Admittedly, my much older Garmin connects using a serial port, so I'm unable to reproduce the issue.

---

### Post by talikarng on 2012-06-09
Thankyou for mentioning the serial port Cheesehead.

I went away and did a bit of reading and found that the garmin_gps module provides serial port emulation when a USB connection is made. I removed this module from the balcklist.

In order to get this to work I had to set the GPS interface to "None" and when I plugged in the USB cable, tell the GPS to not enter "USB Mass Storage Mode".

When I checked dmesg I saw that /dev/ttyUSB0 had been created and I was able to get GPS data using xgps!

Is there somewhere I can write all of this up so that if someone else comes along next year wanting to do the same thing there is some reference at hand?

---

### Post by Cheesehead on 2012-06-11
The Ubuntu Wiki, the Garmin Wiki, the OpenStreetMap wiki, your blog, etc.
Or just the tail end of this thread. Any search will take a confused user here.

Glad you thought of the module. Most instructions are about how it messes them up and how to disable it!

---

