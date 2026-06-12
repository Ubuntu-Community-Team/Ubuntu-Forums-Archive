---
title: "Fujitsu 6130-z Scanner Not Detected"
date: 2014-09-03
forum: Hardware
---

### Post by richard86 on 2014-09-03
It seems that none of the USB scanners that I am attaching to my Ubuntu box are being detected by sane using the command sane-find-scanner, however lsusb shows the scanner as attached.  
```
lsusb -s 003:002
Bus 003 Device 002: ID 04c5:11f3 Fujitsu, Ltd 
```
The device is listed on the SANE supported devices list and is correctly listed with the device ID I have.  
[TABLE]
[TR]
[TD="align: center"]fi-6130Z[/TD]
[TD="align: center"]USB[/TD]
[TD="align: center"]0x04c5/0x11f3[/TD]
[TD="align: center"][COLOR=#007000]Complete[/COLOR][/TD]
[TD]small, current[/TD]
[TD="align: center"][fujitsu]("http://www.thebility.com/fujitsu/") 
(117)[/TD]
[TD="align: center"][sane-fujitsu]("http://www.sane-project.org/man/sane-fujitsu.5.html")[/TD]
[/TR]
[/TABLE]

The backend is "fujitsu" and I have the file /etc/sane.d/fujitsu.conf with the device listed, and I've tried with both the usb lines commented and uncommmented below.
```
# For Fujitsu scanners connected via USB on a known device (kernel driver):
usb /dev/usb/scanner0


# For Fujitsu scanners connected via USB using vendor and device ids (libusb):
usb VENDORID PRODUCTID

#fi-6130Z
usb 0x04c5 0x11f3

```

My udev rules at /lib/udev/rules.d/40-libsane.rules also appear to have the correct device ID listed.
```
# Fujitsu fi-6130ZATTRS{idVendor}=="04c5", ATTRS{idProduct}=="11f3", ENV{libsane_matched}="yes"



```

However, whenever I run sane-find-scanner, it comes back with no devices found.
```
sudo sane-find-scanner 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.


  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.


could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.


  # Not checking for parallel port scanners.


  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.



```


Interestingly, if I fire up a CentOS 6 guest machine in VirtualBox, running on this Ubuntu host, it actually finds the scanner when you run sane-find-scanner
```
found USB scanner (vendor=0x04c5, product=0x11f3) at libusb:001:002
```

uname -a output on my Ubuntu box is 
```
Linux ub-desktop 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

Any help in getting this resolved would be greatly appreciated.

Thanks, Rich.

---

### Post by richard86 on 2014-09-12
Bump.

---

