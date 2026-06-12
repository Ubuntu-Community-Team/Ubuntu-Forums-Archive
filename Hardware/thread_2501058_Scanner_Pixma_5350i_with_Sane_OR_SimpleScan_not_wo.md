---
title: "Scanner Pixma_5350i with Sane OR SimpleScan not working"
date: 2024-09-21
forum: Hardware
---

### Post by vexxtech on 2024-09-21
Hello everyone,

I purchased a new printer PIXMA5350i ([https://www.canon.at/support/consumer/products/printers/pixma/ts-series/pixma-ts5350i.html?type=drivers&os=Linux%20(64-bit)](https://www.canon.at/support/consumer/products/printers/pixma/ts-series/pixma-ts5350i.html?type=drivers&os=Linux%20(64-bit))) and installed both drivers for printing and scanning. The printer worked out of the box (with USB and over the network). As usual the integrated scanner needs more attention. 

The scanner is recognised and I am able to scan with ```
scangearmp2
```. Its my parents PC, which is quite old and therefore runs with Ubuntu 16.04 LTS. For their daily usage it is more than enough. I also build an .desktop application to conveniently start the tool using the dashboard and open the scan directory. 

A more practical tool would be the SimpleScan or XSane, but both do not recognise the Scanner. With following threads ([https://askubuntu.com/questions/1508446/ubuntu-22-04-cannot-scan-with-canon-pixma](https://askubuntu.com/questions/1508446/ubuntu-22-04-cannot-scan-with-canon-pixma), [https://superuser.com/questions/1516987/how-to-use-to-a-canon-pixma-scanner-in-gnu-linux-using-sane-and-over-a-local-ne](https://superuser.com/questions/1516987/how-to-use-to-a-canon-pixma-scanner-in-gnu-linux-using-sane-and-over-a-local-ne)). I was unable to get the scanner running

Here is a outline of my progress 
```

pc@pc:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0461:3f41 Primax Electronics, Ltd 
Bus 003 Device 002: ID 1bcf:0005 Sunplus Innovation Technology Inc. Optical Mouse
Bus 003 Device 004: ID 04a9:18d9 Canon, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Installing sane and dependencies with [https://help.ubuntu.com/community/sane](https://help.ubuntu.com/community/sane)

Try to find using xsane
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294272&stc=1[/IMG]

Using the commandline
```

pc@pc:~$ sudo sane-find-scanner -q
could not open USB device 0x8087/0x8000 at 002:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x8087/0x8008 at 001:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0003 at 004:001: Access denied (insufficient permissions)
could not open USB device 0x0461/0x3f41 at 003:003: Access denied (insufficient permissions)
could not open USB device 0x1bcf/0x0005 at 003:002: Access denied (insufficient permissions)
found USB scanner (vendor=0x04a9 [Canon], product=0x18d9 [TS5350i series]) at libusb:003:004
could not open USB device 0x1d6b/0x0002 at 003:001: Access denied (insufficient permissions)

```

and

```

pc@pc:~$ sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

Another approach was to configure dconf file and adding the IP of the printer. Adding the device address to "[B]/etc/sane.d/pixma.conf"
[/B][PHP]
# pixma.conf configuration for the sane pixma backend
#
# define URI's of scanners (one per line)
# This is only used for network scanners.
# normally scanners will be detected by sending a broadcast
# if this does not work under your OS, or if the scanners
# are on a different subnet, configure your scanners URI here
#
# method must be bjnp
# port number can normally be left out, port 8612 is used as default
# Example:
# bjnp://myscanner.my.domain:8612
# bjnp://printer-1.pheasant.org
#

bjnp:://Canon%20TS5350i%20series._ipp._tcp.local/?uuid=00000000-0000-1000-8000-0018d90f4bfc

[/PHP]

This of course does nothing after running "scanimage -L" and  seems only to affect the printer/scanner when connected to a network. Since the printer is connected via USB, I would like to focus on the serial connection. 

There is also mentions about "sane-pixma.5 backend" ([http://www.sane-project.org/man/sane-pixma.5.html](http://www.sane-project.org/man/sane-pixma.5.html)), but I am completly lost what to do with that.

My questions:
[LIST=1]
[*]How can I configure the PIXMA using serial connection (change permissions)? 
[*]Am I missing another library dependend on sane? 
[*](Bonus) Add the scanner also to the home network using its IP or MAC 
[/LIST]

Thanks in advance

---

### Post by vexxtech on 2024-09-21
Following up on the permissions I found [https://askubuntu.com/questions/1508446/ubuntu-22-04-cannot-scan-with-canon-pixma](https://askubuntu.com/questions/1508446/ubuntu-22-04-cannot-scan-with-canon-pixma). I added an udev rule and after relogin this file appeared in /etc/udev/rules.d

# 80-canon_mfp2.rules

ACTION!="add", GOTO="canon_mfp_end"
SUBSYSTEM=="usb_device", GOTO="canon_mfp_start"
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GOTO="canon_mfp_start"
GOTO="canon_mfp_end"

LABEL="canon_mfp_start"

```

#TS5350i series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18d9", MODE="666"
#G600 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18d5", MODE="666"
#TS3500 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18d4", MODE="666"
#TR4600 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18da", MODE="666"
#E4500 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18db", MODE="666"
#TR4700 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18dc", MODE="666"
#XK500 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18df", MODE="666"
#TS8530 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18e0", MODE="666"
#XK100 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18e2", MODE="666"
#TS7530 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18e1", MODE="666"
#TS7450i series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18f7", MODE="666"

#GX6000 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18a6", MODE="666"
#GX7000 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18a8", MODE="666"
#TS5400 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18d8", MODE="666"

#TS3400 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18b7", MODE="666"
#E3400 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18b8", MODE="666"
#TR7000 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18b9", MODE="666"
#G2020 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18bd", MODE="666"
#G3060 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18c3", MODE="666"
#G2060 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18c1", MODE="666"
#G3020 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18bf", MODE="666"
#TS7430 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18b2", MODE="666"
#XK90 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18b6", MODE="666"
#TS8430 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18b5", MODE="666"
#TR7600 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18aa", MODE="666"
#TR8600 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18ad", MODE="666"
#TR8630 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18af", MODE="666"
#TS6400 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18d3", MODE="666"
#TS7400 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18d7", MODE="666"

#G7000 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1863", MODE="666"
#G7080 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1864", MODE="666"
#GM4000 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1869", MODE="666"
#GM4080 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="186a", MODE="666"
#G6000 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1865", MODE="666"
#G6080 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1866", MODE="666"
#TS5300 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="188b", MODE="666"
#TS5380 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="188c", MODE="666"
#TS6300 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="188d", MODE="666"
#TS6380 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="188e", MODE="666"
#TS7330 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="188f", MODE="666"
#TS8300 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1890", MODE="666"
#TS8380 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1891", MODE="666"
#TS8330 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1892", MODE="666"
#XK60 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1893", MODE="666"
#TS6330 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1894", MODE="666"
#TS3300 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18a2", MODE="666"
#E3300 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="18a3", MODE="666"

#MG7500 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="177c", MODE="666"
#MG6600 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="177e", MODE="666"
#MG5600 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="177f", MODE="666"
#MG2900 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1780", MODE="666"
#MB2000 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1778", MODE="666"
#MB2300 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1779", MODE="666"
#MB5000 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1776", MODE="666"
#MB5300 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1777", MODE="666"
#E460 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1788", MODE="666"

#MX490 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1787", MODE="666"
#E480 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1789", MODE="666"

#MG7700 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="178b", MODE="666"
#MG6900 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="178c", MODE="666"
#MG6800 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="178d", MODE="666"
#MG5700 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="178e", MODE="666"
#MG3600 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="178a", MODE="666"

#G3000 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1794", MODE="666"

#TS9000 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="179f", MODE="666"
#TS8000 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1800", MODE="666"
#TS6000 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1801", MODE="666"
#TS5000 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1802", MODE="666"
#MG3000 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="180b", MODE="666"
#E470 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="180c", MODE="666"
#G4000 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="181d", MODE="666"

#MB2100 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1793", MODE="666"
#MB2700 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1792", MODE="666"
#MB5100 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1790", MODE="666"
#MB5400 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="178f", MODE="666"

#TS9100 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1820", MODE="666"
#TS8100 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1821", MODE="666"
#TS6100 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1822", MODE="666"
#TR8500 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1823", MODE="666"
#TR7500 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1824", MODE="666"
#TS5100 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1825", MODE="666"
#TS3100 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1827", MODE="666"
#E3100 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1828", MODE="666"
#TS9180 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="183e", MODE="666"
#TS8180 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="183f", MODE="666"
#TS6180 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1840", MODE="666"
#TR8580 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1841", MODE="666"
#TS8130 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1842", MODE="666"
#TS6130 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1843", MODE="666"
#TR8530 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1844", MODE="666"
#TR7530 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1845", MODE="666"
#XK50 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1846", MODE="666"
#XK70 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1847", MODE="666"

#G3010 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="183b", MODE="666"
#G4010 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="183d", MODE="666"

#TS8200 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1859", MODE="666"
#XK80 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1873", MODE="666"
#TS8230 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="185b", MODE="666"
#TS8280 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="185a", MODE="666"
#TS6200 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1856", MODE="666"
#TS6230 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1858", MODE="666"
#TS6280 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1857", MODE="666"
#TS9500 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="185c", MODE="666"
#TR9530 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="185e", MODE="666"
#TS9580 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="185d", MODE="666"
#TR4500 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1854", MODE="666"
#E4200 series
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1855", MODE="666"
#LiDE 400
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1912", MODE="666"
#LiDE 300
ATTR{idVendor}=="04a9", ATTR{idProduct}=="1913", MODE="666"


LABEL="canon_mfp_end"


```

Running 

```

familypc@familypc:~$ sudo sane-find-scanner 
[sudo] Passwort für familypc: 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9 [Canon], product=0x18d9 [TS5350i series]) at libusb:003:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```

but 

```

familypc@familypc:~$ sudo scanimage -L
[sudo] Passwort für familypc: 

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
familypc@familypc:~$ 

```

still does not detect the scanner. Neither over the network or serial

---

