---
title: "Brother printer package needs reinstalling, but no archive ??"
date: 2022-02-03
forum: Hardware
---

### Post by oygle on 2022-02-03
Installed the Brother printer drivers for a MFCJ1300DW about a month ago, printed a test page and all okay. Went to use it yesterday and kept getting a 'waiting' message, even though the printer was powered on and USB cable connected. Lots of searching and it seemed to be a driver problem, most advised to re-install. So, did that and now some errors, in fact now even an old HP printer that I used for scanning isn't recognised.

I think I may have removed one package, and now possibly CUPS is messed up ??

The drivers are at [https://support.brother.com/g/b/downloadtop.aspx?c=au&lang=en&prod=mfcj1300dw_eu_as](https://support.brother.com/g/b/downloadtop.aspx?c=au&lang=en&prod=mfcj1300dw_eu_as)

This was the package that was installed ```
sudo apt install lprng
```

Had some sort of errors, so tried unistalling, and that compounded the package problems. Can't even get into Synaptic, it gives this error message

> E: The package mfcj1300dwpdrv:i386 needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

then exits. Have tried uninstalling the drivers and re-installing, and the first hint of any errors are at

> E: The package mfcj1300dwpdrv:i386 needs to be reinstalled, but I can't find an archive for it.

Log attached, more info there.

I don't know _where_ the package installer is searching, but it is in the path where the commands are issued

```
$ ls mfc*
```

> mfcj1300dwpdrv-1.0.5-0a.i386.deb  mfcj1300dwpdrv-1.0.5-0.i386.deb

---

### Post by oygle on 2022-02-03
Just tried this ..

```
sudo dpkg --remove --force-all mfcj1300dwpdrv
```

> dpkg: warning: overriding problem because --force enabled:
dpkg: warning: package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
(Reading database ... 295319 files and directories currently installed.)
Removing mfcj1300dwpdrv:i386 (1.0.5-0) ...
Restarting cups (via systemctl): cups.service.
dpkg: error processing package mfcj1300dwpdrv:i386 (--remove):
 installed mfcj1300dwpdrv:i386 package post-removal script subprocess returned error exit status 5
Errors were encountered while processing:
 mfcj1300dwpdrv:i386

---

### Post by wildmanne39 on 2022-02-03
Thread moved to the hardware sub-forum.

---

### Post by oygle on 2022-02-03
Thank you

---

### Post by oygle on 2022-02-03
Some searching suggested deleting all the files in /var/lib/apt/lists/. See [https://askubuntu.com/questions/147178/e-the-package-needs-to-be-reinstalled-but-i-cant-find-an-archive-for-it#152693](https://askubuntu.com/questions/147178/e-the-package-needs-to-be-reinstalled-but-i-cant-find-an-archive-for-it#152693)

> sudo rm /var/lib/apt/lists/* -vf

Is that **SAFE** to do so ??

I tried this

```
sudo dpkg -i mfcj1300dwpdrv-1.0.5-0.i386.deb
```

> (Reading database ... 295290 files and directories currently installed.)
Preparing to unpack mfcj1300dwpdrv-1.0.5-0.i386.deb ...
Unpacking mfcj1300dwpdrv:i386 (1.0.5-0) over (1.0.5-0) ...
Restarting cups (via systemctl): cups.service.
dpkg: warning: old mfcj1300dwpdrv:i386 package post-removal script subprocess returned error exit status 5
dpkg: trying script from the new package instead ...
Restarting cups (via systemctl): cups.service.
dpkg: error processing archive mfcj1300dwpdrv-1.0.5-0.i386.deb (--install):
 new mfcj1300dwpdrv:i386 package post-removal script subprocess returned error exit status 5
Restarting cups (via systemctl): cups.service.
dpkg: error while cleaning up:
 new mfcj1300dwpdrv:i386 package post-removal script subprocess returned error exit status 5
Errors were encountered while processing:
 mfcj1300dwpdrv-1.0.5-0.i386.deb

Using the post at [https://unix.stackexchange.com/questions/599158/unable-to-install-or-uninstall-broken-half-installed-package-installed-via-dpkg](https://unix.stackexchange.com/questions/599158/unable-to-install-or-uninstall-broken-half-installed-package-installed-via-dpkg) as a reference, the file /var/lib/dpkg/info/mfcj1300dwpdrv.postrm is

> 
#!/bin/sh
# ESP Package Manager v4.1
rm -f /tmp/mfcj1300dw_latest_print_info
if [ "$(which semanage 2> /dev/null)" != '' ];then
semanage fcontext -d -t cupsd_rw_etc_t '/opt/brother/Printers/mfcj1300dw/inf(/.*)?'
semanage fcontext -d -t bin_t          '/opt/brother/Printers/mfcj1300dw/lpd(/.*)?'
semanage fcontext -d -t bin_t          '/opt/brother/Printers/mfcj1300dw/cupswrapper(/.*)?'
if [ "$(which restorecon 2> /dev/null)" != '' ];then
restorecon -R /opt/brother/Printers/mfcj1300dw
fi
fi
if [ -e /etc/init.d/cups ]; then
/etc/init.d/cups restart
fi
if [ -e /etc/init.d/lprng ]; then
/etc/init.d/lprng restart
elif [ -e /etc/init.d/lpd ]; then
/etc/init.d/lpd restart
fi


but what line is in error ??

I did install this driver one month ago, no errors at all. Yet somehow the package or package info is corrupted ??

---

### Post by oygle on 2022-02-04
From the file /var/lib/dpkg/status

> 
Package: mfcj1300dwpdrv
Status: install ok half-configured
Maintainer: Brother Industries, Ltd.
Architecture: i386
Version: 1.0.5-0
Conflicts: conflict_package
Description: Brother Inkjet Printer Driver 
 Copyright: 2003-2017 Brother Industries, Ltd. All Rights Reserved 
 Brother Inkjet Printer (LPR/CUPS) Driver


one 'fix' suggested > Just open /var/lib/dpkg/status file as root and remove the corresponding entry from it.

**SAFE** or not ???

---

### Post by oygle on 2022-02-04
I just ran "chkrootkit" and it found the following ...

================
Searching for Linux.Xor.DDoS ...                            INFECTED:
Possible Malicious Linux.Xor.DDoS installed
/tmp/qapt-deb-installer/opt/brother/Printers/mfcj1300dw/lpd/filter_mfcj1300dw
/tmp/qapt-deb-installer/opt/brother/Printers/mfcj1300dw/lpd/brmfcj1300dwfilter
/tmp/qapt-deb-installer/opt/brother/Printers/mfcj1300dw/cupswrapper/cupswrappermfcj1300dw
/tmp/qapt-deb-installer/opt/brother/Printers/mfcj1300dw/cupswrapper/brother_mfcj1300dw_printer_en.ppd
/tmp/qapt-deb-installer/opt/brother/Printers/mfcj1300dw/cupswrapper/brother_lpdwrapper_mfcj1300dw
/tmp/qapt-deb-installer/opt/brother/Printers/mfcj1300dw/inf/setupPrintcapij
/tmp/qapt-deb-installer/usr/bin/brprintconf_mfcj1300dw

==================

so the Brother website **MAY** be infected ?? Or does chkrootkit report incorrectly ??

---

### Post by oygle on 2022-02-04
Brother support got back to me and stated to issue these commands

```
sudo rm /var/lib/dpkg/info/mfcj1300dwpdrv*
sudo dpkg --configure -D 777 mfcj1300dwpdrv
sudo apt -f install
```

but there were errors still. I had tried a few different suggestions from forums, and for some reason, again gained access to Synaptic. So, things were starting to look good. Well, at least better. Tried those 3 commands again and no errors.

Tried printing a page, and a message

> 
File "usr/lib/cups/backend/usb" not available. No such file or directory

Two posts at [https://unix.stackexchange.com/questions/350714/how-to-add-a-usb-printer-using-lpadmin](https://unix.stackexchange.com/questions/350714/how-to-add-a-usb-printer-using-lpadmin) and [https://unix.stackexchange.com/questions/24468/mount-printers-at-dev-usb-and-still-use-cups#25027](https://unix.stackexchange.com/questions/24468/mount-printers-at-dev-usb-and-still-use-cups#25027) , both talk about using **lpadmin** , which isn't installed and seems to be some kind of cups client.

```
sudo cat /etc/cups/printers.conf
```

> 
# Printer configuration file for CUPS v2.3.1
# Written by cupsd
# DO NOT EDIT THIS FILE WHEN CUPSD IS RUNNING
NextPrinterId 5
<DefaultPrinter MFCJ1300DW>
PrinterId 4
UUID urn:uuid:39989226-f50f-340a-54bd-0a27ff980fdc
Info MFCJ1300DW
Location Dell-Inspiron-3542
MakeModel Brother MFC-J1300DW CUPS
DeviceURI usb://dev/usb/lp0
State Idle
StateTime 1643960667
ConfigTime 1643960661
Type 8392732
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
AllowUser ********
OpPolicy default
ErrorPolicy retry-job
</DefaultPrinter>

```
lsusb
```

> Bus 001 Device 007: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 008: ID 0cf3:0036 Qualcomm Atheros Communications 
Bus 001 Device 005: ID 0c45:670b Microdia 
Bus 001 Device 004: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 001 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

From [https://www.openprinting.org/download/kpfeifle/LinuxKongress2002/Tutorial/VI.CUPS-Connections/VI.tutorial-handout-cups-connections.html](https://www.openprinting.org/download/kpfeifle/LinuxKongress2002/Tutorial/VI.CUPS-Connections/VI.tutorial-handout-cups-connections.html)

> **Local printers: Parallel, USB, serial, FireWire, SCSI**

The important part here is the "**device-URI**". This way you tell CUPS which backend it shall use with the printer "printername". The backends for most types of local printers are already part of the CUPS package. CUPS 1.1.x contains backends for parallel, serial, and USB printers, CUPS 1.2.x will also support FireWire (IEEE 1394) and SCSI printers.

The backends do not only send data to the appropriate devices. They are also called when CUPS is started. They auto-detect which printer models are connected to which ports. So you should set up your BIOS for the parallel ports to allow bi-directional communication. Then your printer(s) can answer to the auto-detection requests.

To see which devices the CUPS backends auto-detect currently, execute them without command line options:

   $ /usr/lib/cups/backend/usb
   direct usb:/dev/usb/lp0 "HP PSC 950xi" "USB Printer #1"
   direct usb:/dev/usb/lp1 "EPSON USB Printer" "USB Printer #2"
   direct usb:/dev/usb/lp2 "EPSON USB Printer" "USB Printer #3"
   direct usb:/dev/usb/lp3 "Unknown" "USB Printer #4"
   $

I don't have a file called  /usr/lib/cups/backend/usb , and the instructions for the Brother printer driver install stated if using a USB connection to reply **N** to "device-URI" in the install.

---

### Post by oygle on 2022-02-04
I installed CUPS and CUPS client, at least could view the web interface and see a bit more. After sorting the driver/package side of things, it got down to "waiting" messages. The USB port on the printer I had been using was not shown in Brother manuals (on the front left hand side). Read the quick setup guide and it had a picture of using either CAT6 or USB, but it was **INSIDE**. Fortunately had the right type, and it printed okay.

So the port at the front doesn't work. Also I never had **lsusb** show the Brother printer, hence the cable issue. But it showed when the usb cable was plugged into the top of the printer.

---

### Post by oygle on 2022-02-06
.. and now the scanner works, all "driverless" - see [https://pastebin.com/gU5f01Ky](https://pastebin.com/gU5f01Ky)

---

