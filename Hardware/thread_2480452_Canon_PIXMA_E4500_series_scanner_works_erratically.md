---
title: "Canon PIXMA E4500 series scanner works erratically"
date: 2022-10-30
forum: Hardware
---

### Post by arvindp3 on 2022-10-30
I have installed a Canon PIXMA E4570 printer/scanner under my Ubuntu 20.04 using a USB connection.  Ubuntu printer and scanner drivers were downloaded and installed from the Canon website for both printer and scanner.   Canon has supplied a program called scangearmp2 with the scanner drivers that does the scanning.

The printer works fine with all options. But the Scanner behaves erratically with the program scangearmp2.  Sometimes it works, sometimes it doesn't.  For example, if I print a page then the scanner works, but not without the printing. It's difficult to detect a pattern in when it does not work.

The Document Scanner(Simple scan) that was working with my earlier HP printer/scanner doesn't sense this scanner.

I feel there is some configuration/setting within the system or sane backend that is either incorrect or missing.

How do I verify that the system/sane configuration/settings for using this USB scanner are such that the scanner works persistently and properly using the Canon program scangearmp2?

==================================
(1) Output of lsusb | grep Canon is below:
Bus 001 Device 009: ID 04a9:18db Canon, Inc. 

(2) The output of scanimage -L is below:

device `escl:[http://127.0.0.1:60000](http://127.0.0.1:60000)' is a ESCL E4500 series flatbed scanner

(3) The output of sane-find-scanner is below:

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x0bda/0x8153 at 002:003: Access denied (insufficient permissions)
could not open USB device 0x2109/0x0813 at 002:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0003 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x174f/0x2426 at 001:004: Access denied (insufficient permissions)
found USB scanner (vendor=0x04a9 [Canon], product=0x18db [E4500 series]) at libusb:001:009
could not open USB device 0x2109/0x2813 at 001:003: Access denied (insufficient permissions)
could not open USB device 0x8087/0x0aaa at 001:006: Access denied (insufficient permissions)
could not open USB device 0x248a/0x8367 at 001:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

---

