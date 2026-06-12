---
title: "HP Deskjet 1220C: Unable to communicate with device (code=12)"
date: 2014-03-25
forum: Hardware
---

### Post by corbiauantoine on 2014-03-25
Hi,

I'm new with Ubuntu, got version 13.10 and the latest hplip.
When I type in console hp-check -g I get the following error: Unable to communicate with device (code=12): hp:/usb/DeskJet_1220C?serial=MY22L331P20O

I see that the printer is not found via USB and don't know what to do.
Can anyone help please? I would be grateful.

Below the code from hp-check:
```

hp-check[2862]: debug: Searching for file(s) 'dbus-message.h' in '/usr/include' that contain 'dbus_message_new_signal'...
hp-check[2862]: debug: Checking file '/usr/include/dbus-1.0/dbus/dbus-message.h' for contents 'dbus_message_new_signal'...
hp-check[2862]: debug: 'dbus_message_new_signal' found in file '/usr/include/dbus-1.0/dbus/dbus-message.h'.
hp-check[2862]: debug: /usr/include/dbus-1.0/dbus/dbus-message.h
hp-check[2862]: debug: Found files: ['/usr/include/dbus-1.0/dbus/dbus-message.h']
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 dbus                 DBus                      REQUIRED        -               1.6.12          OK         -
hp-check[2862]: debug: Checking: cups-config --version
hp-check[2862]: debug: 1.7rc1

hp-check[2862]: debug: 1.7rc1
hp-check[2862]: debug: scheduler is running

hp-check[2862]: debug: CUPS is running. scheduler is running
 
hp-check[2862]: debug: Checking: installed ver=1.7  min ver=1.1
hp-check[2862]: debug: Found.
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
hp-check[2862]: debug: Checking: installed ver=1.7  min ver=1.4
hp-check[2862]: debug: Found.
hp-check[2862]: debug: cups -ddk not required as cups version [1.7] is => 1.4 
 cups                 CUPS                      REQUIRED        1.1             1.7             OK         'CUPS Scheduler is running'
hp-check[2862]: debug: Checking: installed ver=0.998  min ver=0.9
hp-check[2862]: debug: Found.
hp-check[2862]: debug: Checking: installed ver=0.998  min ver=0.9
hp-check[2862]: debug: Found.
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 xsane                SANE-GUI                  OPTIONAL        0.9             0.998           OK         -

-------------------------
|  General Dependencies |
-------------------------

hp-check[2862]: debug: Trying to import 'reportlab'...
hp-check[2862]: debug: Trying to import 'reportlab'...
hp-check[2862]: debug: Version: 2.6
hp-check[2862]: debug: Success.
hp-check[2862]: debug: Checking: installed ver=2.6  min ver=2.0
hp-check[2862]: debug: Found.
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 reportlab            Python-PDF-Lib            OPTIONAL        2.0             2.6             OK         -
hp-check[2862]: debug: Checking: openssl version
hp-check[2862]: debug: OpenSSL 1.0.1e 11 Feb 2013

hp-check[2862]: debug: OpenSSL 1.0.1e 11 Feb 2013
hp-check[2862]: debug: Checking for library 'libcrypto'...
hp-check[2862]: debug: Found.
hp-check[2862]: debug: Searching for file 'crypto.h' in '/usr/include'...
hp-check[2862]: debug: File found at '/usr/include/openssl/crypto.h'
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 libcrypto            OpenSSL-Crypto-Lib        REQUIRED        -               1.0.1           OK         -
hp-check[2862]: debug: Checking for PIL...
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 pil                  Python-Image-Lib          OPTIONAL        -               1.1.7           OK         -
hp-check[2862]: debug: Checking PyQt 4.x version...
hp-check[2862]: debug: Checking: installed ver=4.10.3  min ver=4.0
hp-check[2862]: debug: Found.
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 pyqt4-dbus           PyQt4-DBUS                REQUIRED        4.0             4.10.3          OK         -
hp-check[2862]: debug: Checking for library 'libjpeg'...
hp-check[2862]: debug: Found.
hp-check[2862]: debug: Searching for file 'jpeglib.h' in '/usr/include'...
hp-check[2862]: debug: File found at '/usr/include/jpeglib.h'
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 libjpeg              JPEG-Lib                  REQUIRED        -               -               OK         -
hp-check[2862]: debug: Checking for library 'libpthread'...
hp-check[2862]: debug: Found.
hp-check[2862]: debug: Searching for file 'pthread.h' in '/usr/include'...
hp-check[2862]: debug: File found at '/usr/include/pthread.h'
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 libpthread           POSIX-Threads-Lib         REQUIRED        -               2.17            OK         -
hp-check[2862]: debug: Checking for python-dbus (>= 0.80)...
hp-check[2862]: debug: Version: 1.2.0
hp-check[2862]: debug: Checking: installed ver=1.2.0  min ver=0.80.0
hp-check[2862]: debug: Found.
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 python-dbus          Python-DBUS               REQUIRED        0.80.0          1.2.0           OK         -
hp-check[2862]: debug: Checking: python --version
hp-check[2862]: debug: Python 2.7.5+

hp-check[2862]: debug: Python 2.7.5+
hp-check[2862]: debug: Searching for file 'Python.h' in '/usr/include'...
hp-check[2862]: debug: File found at '/usr/include/python2.7/Python.h'
hp-check[2862]: debug: Checking: installed ver=2.7.5  min ver=2.2
hp-check[2862]: debug: Found.
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 python-devel         Python-SDK                REQUIRED        2.2             2.7.5           OK         -
hp-check[2862]: debug: Checking PyQt 4.x version...
hp-check[2862]: debug: Checking: installed ver=4.10.3  min ver=4.0
hp-check[2862]: debug: Found.
hp-check[2862]: debug: Checking: installed ver=4.10.3  min ver=2.3
hp-check[2862]: debug: Found.
hp-check[2862]: debug: Checking: installed ver=4.10.3  min ver=2.2
hp-check[2862]: debug: Found.
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 pyqt4                Python-Qt4                REQUIRED        4.0             4.10.3          OK         -
hp-check[2862]: debug: Checking: cups-config --version
hp-check[2862]: debug: 1.7rc1

hp-check[2862]: debug: 1.7rc1
hp-check[2862]: debug: Searching for file 'cups.h' in '/usr/include'...
hp-check[2862]: debug: File found at '/usr/include/cups/cups.h'
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 cups-devel           CUPS-SDK                  REQUIRED        -               1.7             OK         -
hp-check[2862]: debug: Checking: sane-config --version
hp-check[2862]: debug: 1.0.23

hp-check[2862]: debug: 1.0.23
hp-check[2862]: debug: Searching for file(s) 'sane.h' in '/usr/include' that contain 'extern SANE_Status sane_init'...
hp-check[2862]: debug: Checking file '/usr/include/sane/sane.h' for contents 'extern SANE_Status sane_init'...
hp-check[2862]: debug: 'extern SANE_Status sane_init' found in file '/usr/include/sane/sane.h'.
hp-check[2862]: debug: /usr/include/sane/sane.h
hp-check[2862]: debug: Found files: ['/usr/include/sane/sane.h']
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 sane-devel           SANE-SDK                  REQUIRED        -               1.0.23          OK         -
hp-check[2862]: debug: Checking for library 'libusb-1.0'...
hp-check[2862]: debug: Found.
hp-check[2862]: debug: Searching for file(s) 'libusb.h' in '/usr/include/libusb-1.0' that contain 'libusb_init'...
hp-check[2862]: debug: Checking file '/usr/include/libusb-1.0/libusb.h' for contents 'libusb_init'...
hp-check[2862]: debug: 'libusb_init' found in file '/usr/include/libusb-1.0/libusb.h'.
hp-check[2862]: debug: /usr/include/libusb-1.0/libusb.h
hp-check[2862]: debug: Found files: ['/usr/include/libusb-1.0/libusb.h']
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 libusb               USB-Lib                   REQUIRED        -               1.0             OK         -
hp-check[2862]: debug: Checking: sane-config --version
hp-check[2862]: debug: 1.0.23

hp-check[2862]: debug: 1.0.23
hp-check[2862]: debug: Checking for library 'libsane'...
hp-check[2862]: debug: Found.
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 sane                 Scan-Lib                  REQUIRED        -               1.0.23          OK         -
hp-check[2862]: debug: Checking: cups-config --version
hp-check[2862]: debug: 1.7rc1

hp-check[2862]: debug: 1.7rc1
hp-check[2862]: debug: Searching for file 'raster.h' in '/usr/include/cups'...
hp-check[2862]: debug: File found at '/usr/include/cups/raster.h'
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 cups-image           CUPS-Image-Lib            REQUIRED        -               1.7             OK         -
hp-check[2862]: debug: Checking: net-snmp-config --version
hp-check[2862]: debug: 5.7.2

hp-check[2862]: debug: 5.7.2
hp-check[2862]: debug: Checking for library 'libnetsnmp'...
hp-check[2862]: debug: Found.
hp-check[2862]: debug: Searching for file 'net-snmp-config.h' in '/usr/include'...
hp-check[2862]: debug: File found at '/usr/include/net-snmp/net-snmp-config.h'
hp-check[2862]: debug: Checking: installed ver=5.7.2  min ver=5.0.9
hp-check[2862]: debug: Found.
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 libnetsnmp-devel     SNMP-Networking-SDK       REQUIRED        5.0.9           5.7.2           OK         -
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 python-xml           Python-XML-Lib            REQUIRED        -               2.1.0           OK         -
hp-check[2862]: debug: Checking: python-notify --version
hp-check[2862]: debug: Not found!
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 python-notify        Desktop-notifications     OPTIONAL        -               -               OK         -

------------------------------
|  Compile Time Dependencies |
------------------------------

hp-check[2862]: debug: Checking: gcc --version
hp-check[2862]: debug: gcc (Ubuntu/Linaro 4.8.1-10ubuntu9) 4.8.1
Copyright (C) 2013 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


hp-check[2862]: debug: gcc (Ubuntu/Linaro 4.8.1-10ubuntu9) 4.8.1
hp-check[2862]: debug: Checking: gcc --version (min ver=0.000000)
hp-check[2862]: debug: gcc (Ubuntu/Linaro 4.8.1-10ubuntu9) 4.8.1
Copyright (C) 2013 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


hp-check[2862]: debug: Found.
hp-check[2862]: debug: Checking: g++ --version (min ver=0.000000)
hp-check[2862]: debug: g++ (Ubuntu/Linaro 4.8.1-10ubuntu9) 4.8.1
Copyright (C) 2013 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


hp-check[2862]: debug: Found.
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 gcc                  gcc-Compiler              REQUIRED        -               4.8.1           OK         -
hp-check[2862]: debug: Checking: libtool --version
hp-check[2862]: debug: libtool (GNU libtool) 2.4.2
Written by Gordon Matzigkeit <gord@gnu.ai.mit.edu>, 1996

Copyright (C) 2011 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

hp-check[2862]: debug: libtool (GNU libtool) 2.4.2
hp-check[2862]: debug: Checking for libtool...
hp-check[2862]: debug: Checking: libtool --version (min ver=0.000000)
hp-check[2862]: debug: libtool (GNU libtool) 2.4.2
Written by Gordon Matzigkeit <gord@gnu.ai.mit.edu>, 1996

Copyright (C) 2011 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

hp-check[2862]: debug: Found.
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 libtool              Build-tools               REQUIRED        -               2.4.2           OK         -
hp-check[2862]: debug: Checking: make --version
hp-check[2862]: debug: GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for i686-pc-linux-gnu

hp-check[2862]: debug: GNU Make 3.81
hp-check[2862]: debug: Checking: make --version (min ver=3.000000)
hp-check[2862]: debug: GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for i686-pc-linux-gnu

hp-check[2862]: debug: GNU Make 3.81
hp-check[2862]: debug: Ver=3.810000 Min ver=3.000000
hp-check[2862]: debug: Checking: installed ver=3.81  min ver=3.0
hp-check[2862]: debug: Found.
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 make                 GNU-Build-tools           REQUIRED        3.0             3.81            OK         -

----------------------
|  Python Extentions |
----------------------

hp-check[2862]: debug: Checking 'cupsext' CUPS extension...
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 cupsext              CUPS-Extension            REQUIRED        -               3.14.3          OK         -
hp-check[2862]: debug: Checking 'pcardext' Photocard extension...
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 pcardext             PhotoCard-Extension       REQUIRED        -               3.14.3          OK         -
hp-check[2862]: debug: Checking 'hpmudext' I/O extension...
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 hpmudext             IO-Extension              REQUIRED        -               3.14.3          OK         -

-----------------------
|  Scan Configuration |
-----------------------

hp-check[2862]: debug: 'Checking for hpaio' in '/etc/sane.d/dll.conf'...
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 hpaio                HPLIP-SANE-Backend        REQUIRED        -               3.14.3          OK         'hpaio found in /etc/sane.d/dll.conf'
hp-check[2862]: debug: Checking 'scanext' SANE scanning extension...
hp-check[2862]: debug: Auto installation is supported for Distro =ubuntu version =13.10 
 scanext              Scan-SANE-Extension       REQUIRED        -               3.14.3          OK         -

------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------

hp-check[2862]: debug: 
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

No Scanner found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

hp-check[2862]: debug: Probing bus: usb
No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

hp-check[2862]: debug: device for DESKJET-1220C: hp:/usb/DeskJet_1220C?serial=MY22L331P20O


hp-check[2862]: debug: [('DESKJET-1220C', 'hp:/usb/DeskJet_1220C?serial=MY22L331P20O')]
hp-check[2862]: debug: hp:/usb/DeskJet_1220C?serial=MY22L331P20O: back_end:hp is_hp:True bus:usb model:DeskJet_1220C serial:MY22L331P20O dev_file: host: zc: port:1
DESKJET-1220C
-------------
Type: Printer
Device URI: hp:/usb/DeskJet_1220C?serial=MY22L331P20O
PPD: /etc/cups/ppd/DESKJET-1220C.ppd
PPD Description: HP Deskjet 1220c, hpcups 3.12.6
hp-check[2862]: debug: printer DESKJET-1220C is idle.  enabled since Tue 25 Mar 2014 09:53:59 AM CET

Printer status: printer DESKJET-1220C is idle.  enabled since Tue 25 Mar 2014 09:53:59 AM CET
hp-check[2862]: debug: Device URI: hp:/usb/DeskJet_1220C?serial=MY22L331P20O
hp-check[2862]: debug: Printer: None
hp-check[2862]: debug: hp:/usb/DeskJet_1220C?serial=MY22L331P20O: back_end:hp is_hp:True bus:usb model:DeskJet_1220C serial:MY22L331P20O dev_file: host: zc: port:1
hp-check[2862]: debug: URI: backend=hp, is_hp=True, bus=usb, model=DeskJet_1220C, serial=MY22L331P20O, dev=, host=, port=1
hp-check[2862]: debug: Model/UI model: DeskJet_1220C/HP Deskjet 1220c
hp-check[2862]: debug: hp:/usb/DeskJet_1220C?serial=MY22L331P20O: back_end:hp is_hp:True bus:usb model:DeskJet_1220C serial:MY22L331P20O dev_file: host: zc: port:1
hp-check[2862]: debug: Cache miss: deskjet_1220c
hp-check[2862]: debug: Reading file: /usr/share/hplip/data/models/models.dat
hp-check[2862]: debug: Searching for section [deskjet_1220c] in file /usr/share/hplip/data/models/models.dat
hp-check[2862]: debug: Found section [deskjet_1220c] in file /usr/share/hplip/data/models/models.dat
hp-check[2862]: debug: Re-reading CUPS printer queue information.
hp-check[2862]: debug: Opening device: hp:/usb/DeskJet_1220C?serial=MY22L331P20O (not for printing)
hp-check[2862]: debug: I/O mode=6
error: Unable to communicate with device (code=12): hp:/usb/DeskJet_1220C?serial=MY22L331P20O
hp-check[2862]: debug: Exception: 2 (Device not found)
error: Device not found
error: Communication status: Failed


--------------
| PERMISSION |
--------------

hp-check[2862]: debug: Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


-----------
| SUMMARY |
-----------

Missing Required Dependencies
-----------------------------
None

Missing Optional Dependencies
-----------------------------
None


Total Errors: 1
Total Warnings: 0

```

Best,
Antoine

---

### Post by corbiauantoine on 2014-03-26
I've tried to reinstall a few times with older versions, restarted both  printers and laptop, sort of the things I read in other posts with  similar problems, but I'm not able to find a solution. I would really  appreciate the help of someone please.

---

