---
title: "Scanner not working in 16.04"
date: 2016-08-29
forum: Hardware
---

### Post by WimiBuntu on 2016-08-29
Dear all

I have a Canon Canoscan Lide 110. It worked perfectly under 14.04. Now I upgraded to 16.04 LTS and it stopped working.

When I use gscan2pdf it just makes an odd sound and later an I/O error appears.

Searching the net I found that many people have this and similar issues, but I found no solution for that problem.

Here is what I get from the shell:
```

lsusb                                         < ~
Bus 002 Device 004: ID 17ef:1003 Lenovo Integrated Smart Card Reader
Bus 002 Device 003: ID 04a9:1909 Canon, Inc. CanoScan LiDE 110
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f2:b221 Chicony Electronics Co., Ltd integrated camera
Bus 001 Device 004: ID 0a5c:217f Broadcom Corp. BCM2045B (BDC-2.1)
Bus 001 Device 003: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```

sane-find-scanner                             < ~

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x17ef/0x1003 at 002:004: Access denied (insufficient permissions)
could not open USB device 0x8087/0x0024 at 002:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x04f2/0xb221 at 001:005: Access denied (insufficient permissions)
could not open USB device 0x0a5c/0x217f at 001:004: Access denied (insufficient permissions)
could not open USB device 0x147e/0x2016 at 001:003: Access denied (insufficient permissions)
found USB scanner (vendor=0x04a9 [Canon], product=0x1909 [CanoScan], chip=GL124) at libusb:001:006
could not open USB device 0x8087/0x0024 at 001:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```

```

scanimage -L                                  < ~
device `genesys:libusb:001:006' is a Canon LiDE 110 flatbed scanner
```

Could you please point me in the right direction, what I should do/check next?

Thanks!

---

### Post by slickymaster on 2016-08-29
*Thread moved to **Hardware**.*

---

