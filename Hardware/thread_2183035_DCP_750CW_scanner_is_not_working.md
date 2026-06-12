---
title: "DCP 750CW scanner is not working"
date: 2013-10-23
forum: Hardware
---

### Post by arnoldijzermans-b on 2013-10-23
All

Installed 13.10 64 bit early this week

Problem is with the scanner of the Brother DCP-750CW.
the device is connected to my PC using USB
Printing is working fine, but XSANE cannot find the device.

Tried a number of things several times (accoring to installation instructions from Brother) but I am lost.
Also tried to use the scanner using WIFI with no succes

Not sure if it is 
- A wrongly installed kernel dependency
- rights on the device
- 64 bit issue?

Wanted to check with you guys before I start changing things around. Have the feeling I am overlooking something.

Little more background. Using Ubuntu since 8.XX and always managed to get the scanner working.
Thanks for you suggestions in advance
Arnold
-----
Posted some screendumps. If more needed let me know

**lsusb** 
Bus 002 Device 003: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[COLOR=red]Bus 001 Device 003: ID 04f9:01ae Brother Industries, Ltd DCP-750CW RemovableDisk[/COLOR]
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**Sane-find-scanner** 
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x0bda/0x0151 at 002:003: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0003 at 004:001: Access denied (insufficient permissions)
could not open USB device 0x046d/0xc00c at 003:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 003:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
[COLOR=red]  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.[/COLOR]

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

DKPG  (driver installed)
ii   brother-cups-wrapper-common               1.0.0-10-0ubuntu6                        amd64        Common files for Brother cups wrapper packages
ii  brother-udev-rule-type1                   1.0.0-1                                 all          Brother udev rule type 1
ii [COLOR=red] brscan2                                   0.2.5-1                                 amd64        Brother Scanner Driver[/COLOR]
ii   dcp750cwcupswrapper                       1.0.1-1                                  i386         Brother CUPS Inkjet Printer Definitions
ii   dcp750cwlpr                               1.0.1-1                                  i386         Brother lpr Inkjet Printer Definitions
ii   printer-driver-ptouch                     1.3-6                                    amd64        printer driver Brother P-touch label printers

---

### Post by arnoldijzermans-b on 2013-10-27
Apparently no-one knows new directions to point me to. 
Afraid Brother is again giving headaches, annoyingly all worked well within the previous version. 

Will do some diggin. If I find something will let you know.
cheers

---

### Post by leclerc65 on 2013-10-27
Did you try

    sudo gedit /lib/udev/rules.d/40-libsane.rules

    Add the following 2 lines before "LABEL="libsane_rules_end"".

    # Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

Save then reboot.

---

