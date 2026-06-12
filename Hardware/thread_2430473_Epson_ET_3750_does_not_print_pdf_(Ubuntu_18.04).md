---
title: "Epson ET 3750 does not print pdf (Ubuntu 18.04)"
date: 2019-11-02
forum: Hardware
---

### Post by menschmarcus on 2019-11-02
Hello Ubuntu-Fans,

I just got my new printer Epson ET-3750 and - SURPRISE - I can not print pdfs.

I use Ubuntu 18.04.3 LTS (64-bit).
I followed exactly (hopefully) these instructions:
[https://tutorialforlinux.com/2018/03/15/driver-epson-et-3750-ubuntu-18-04-how-to-download-install/](https://tutorialforlinux.com/2018/03/15/driver-epson-et-3750-ubuntu-18-04-how-to-download-install/)

Result:
1. I have "ET-3750" in my list of printers (Settings > Devices > Printers).
2. I can successfully print a test page (Settings > Devices > Printers > "ET-3750" > Printing Options > Test Page).
3. If I open a pdf in evince I can choose the printer, set my preferences and send the printing job. In Ubuntu it says "Printing Canceled". However, the print job seems to successfully reach the printer because on the screen of the Printer it says "Druck abgeschlossen" ("Printing complete"). But it does not print. The same happens if I try to print through the Web Browser, other PDF Viewers etc.

Do you have any ideas how I can fix this issue?

```

$ dpkg -l *cups* lpr* | grep ii
ii  bluez-cups                5.48-0ubuntu3.2   amd64        Bluetooth printer driver for CUPS
ii  cups                      2.2.7-1ubuntu2.7  amd64        Common UNIX Printing System(tm) - PPD/driver support, web interface
ii  cups-browsed              1.20.2-0ubuntu3.1 amd64        OpenPrinting CUPS Filters - cups-browsed
ii  cups-bsd                  2.2.7-1ubuntu2.7  amd64        Common UNIX Printing System(tm) - BSD commands
ii  cups-client               2.2.7-1ubuntu2.7  amd64        Common UNIX Printing System(tm) - client programs (SysV)
ii  cups-common               2.2.7-1ubuntu2.7  all          Common UNIX Printing System(tm) - common files
ii  cups-core-drivers         2.2.7-1ubuntu2.7  amd64        Common UNIX Printing System(tm) - driverless printing
ii  cups-daemon               2.2.7-1ubuntu2.7  amd64        Common UNIX Printing System(tm) - daemon
ii  cups-filters              1.20.2-0ubuntu3.1 amd64        OpenPrinting CUPS Filters - Main Package
ii  cups-filters-core-drivers 1.20.2-0ubuntu3.1 amd64        OpenPrinting CUPS Filters - Driverless printing
ii  cups-ipp-utils            2.2.7-1ubuntu2.7  amd64        Common UNIX Printing System(tm) - IPP developer/admin utilities
ii  cups-pk-helper            0.2.6-1ubuntu1.2  amd64        PolicyKit helper to configure cups with fine-grained privileges
ii  cups-ppdc                 2.2.7-1ubuntu2.7  amd64        Common UNIX Printing System(tm) - PPD manipulation utilities
ii  cups-server-common        2.2.7-1ubuntu2.7  all          Common UNIX Printing System(tm) - server common files
ii  libcups2:amd64            2.2.7-1ubuntu2.7  amd64        Common UNIX Printing System(tm) - Core library
ii  libcups2:i386             2.2.7-1ubuntu2.7  i386         Common UNIX Printing System(tm) - Core library
ii  libcupscgi1:amd64         2.2.7-1ubuntu2.7  amd64        Common UNIX Printing System(tm) - CGI library
ii  libcupsfilters1:amd64     1.20.2-0ubuntu3.1 amd64        OpenPrinting CUPS Filters - Shared library
ii  libcupsimage2:amd64       2.2.7-1ubuntu2.7  amd64        Common UNIX Printing System(tm) - Raster image library
ii  libcupsmime1:amd64        2.2.7-1ubuntu2.7  amd64        Common UNIX Printing System(tm) - MIME library
ii  libcupsppdc1:amd64        2.2.7-1ubuntu2.7  amd64        Common UNIX Printing System(tm) - PPD manipulation library
ii  printer-driver-hpcups     3.17.10+repack0-5 amd64        HP Linux Printing and Imaging - CUPS Raster driver (hpcups)
ii  python3-cups              1.9.73-2          amd64        Python3 bindings for CUPS
ii  python3-cupshelpers       1.5.11-1ubuntu2   all          Python utility modules around the CUPS printing system

```

```

$ dpkg -l libusb* | grep ii
ii  libusb-1.0-0:amd64 2:1.0.21-2                     amd64        userspace USB programming library
ii  libusb-1.0-0:i386  2:1.0.21-2                     i386         userspace USB programming library
ii  libusbmuxd4:amd64  1.1.0~git20171206.c724e70f-0.1 amd64        USB multiplexor daemon for iPhone and iPod Touch devices - library

```

```

$ dpkg -l | egrep Epson
ii  epson-inkjet-printer-escpr                 1.7.5-1lsb3.2                                amd64        Epson Inkjet Printer Driver (ESC/P-R) for Linux
ii  epson-printer-utility                      1.1.0-1lsb3.2                                amd64        Epson Printer Utility for Linux

```

```

$ systemctl --no-pager status cups*
&#9679; cups.path - CUPS Scheduler
   Loaded: loaded (/lib/systemd/system/cups.path; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2019-11-02 11:45:16 CET; 55min ago

Nov 02 11:45:16 theaterplatz-T470 systemd[1]: Started CUPS Scheduler.

&#9679; cups.socket - CUPS Scheduler
   Loaded: loaded (/lib/systemd/system/cups.socket; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2019-11-02 11:45:16 CET; 55min ago
   Listen: /run/cups/cups.sock (Stream)
   CGroup: /system.slice/cups.socket
Failed to dump process list, ignoring: No such file or directory

Nov 02 11:45:16 theaterplatz-T470 systemd[1]: Stopping CUPS Scheduler.
Nov 02 11:45:16 theaterplatz-T470 systemd[1]: Listening on CUPS Scheduler.

&#9679; cups.service - CUPS Scheduler
   Loaded: loaded (/lib/systemd/system/cups.service; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2019-11-02 11:45:16 CET; 55min ago
     Docs: man:cupsd(8)
 Main PID: 3696 (cupsd)
    Tasks: 2 (limit: 4915)
   CGroup: /system.slice/cups.service
           &#9500;&#9472;3696 /usr/sbin/cupsd -l
           &#9492;&#9472;3898 /usr/lib/cups/notifier/dbus dbus://

Nov 02 11:45:16 theaterplatz-T470 systemd[1]: Started CUPS Scheduler.
Nov 02 11:54:55 theaterplatz-T470 /hpfax[8697]: [8697]: error: Failed to create /var/spool/cups/tmp/.hplip

```

```

$ lpstat -t
scheduler is running
no system default destination
device for Epson_ET-3750: dnssd://EPSON%20ET-3750%20Series._ipp._tcp.local/?uuid=cfe92100-67c4-11d4-a45f-381a524798de
Epson_ET-3750 accepting requests since Sa 02 Nov 2019 12:33:05 CET
LaserJet-CM1415fn accepting requests since Do 10 Okt 2019 14:44:00 CEST
printer Epson_ET-3750 is idle.  enabled since Sa 02 Nov 2019 12:33:05 CET
    '''Print job canceled at printer.'''

```

```

$ lpinfo -v
serial serial:/dev/ttyS0?baud=115200
network beh
network ipps
network http
direct ecblp:/var/run/ecblp0
network socket
file cups-brf:/
network lpd
network https
network ipp
direct hp
direct hpfax
network dnssd://EPSON%20ET-3750%20Series._ipp._tcp.local/?uuid=cfe92100-67c4-11d4-a45f-381a524798de
network lpd://192.168.0.30:515/PASSTHRU
network ipp://EPSON4798DE.local:631/ipp/print

```

```

$ uname -rm
4.15.0-66-generic x86_64

```

```

$ ls -l /etc/cups/ppd/* 
'''-rw-r----- 1 root lp 12084 Nov  2 12:19 /etc/cups/ppd/Epson_ET-3750.ppd'''
-rw-r----- 1 root lp  9009 Nov 15  2018 /etc/cups/ppd/LaserJet-CM1415fn.ppd

```

---

### Post by brian_p on 2019-11-02
The printing related outputs are very useful. Good initiative.

What do you get for these commands?

```
sudo grep PCFileName /etc/cups/ppd/Epson_ET-3750.ppd
```

```
sudo grep cupsFilter /etc/cups/ppd/Epson_ET-3750.ppd
```

---

### Post by menschmarcus on 2019-11-07
Hi Brian,
Thank you SO much for your answer. For some reason Ubuntuforums did not notify me that I received your answer. I was just lucky to have a look in here.

```

$ sudo grep PCFileName EPSON_ET-3750_Series.ppd
*PCFileName: "EPET-3750 Series.PPD"
$ sudo grep cupsFilter EPSON_ET-3750_Series.ppd
*cupsFilter: "application/vnd.cups-raster 0 /opt/epson-inkjet-printer-escpr2/cups/lib/filter/epson-escpr-wrapper2"

```

However, I already received help in another forum and I found the solution: The driver was not the right one. I had to install this one and it worked:
[B][URL="https://download3.ebz.epson.net/dsc/f/03/00/10/19/86/f49703bf53d36288fff400f00f702a67959b4660/epson-inkjet-printer-escpr2_1.1.2-1lsb3.2_amd64.deb"]https://download3.ebz.epson.net/dsc/b3.2_amd64.deb

[/URL][/B] So I guess  am happy now tht things have worked out! Thank you anyway for your time.[URL="https://download3.ebz.epson.net/dsc/f/03/00/10/19/86/f49703bf53d36288fff400f00f702a67959b4660/epson-inkjet-printer-escpr2_1.1.2-1lsb3.2_amd64.deb"]
[/URL]

---

### Post by brian_p on 2019-11-07
> So I guess am happy now tht things have worked out! Thank you anyway for your time.


And thank you for taking the trouble to respond with your solution. Glad you got it sorted.

---

