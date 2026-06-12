---
title: "HP All-in-one Scanner not detected. Printer works fine."
date: 2012-02-12
forum: Hardware
---

### Post by Acknud on 2012-02-12
I have a HP DeskJet 3050 J610 series All-in-one printer/scanner. The printer works fine and sets up easily. I can't seem to get the scanner to work. I have trolled these forums and searched for days and I can't figure it out. It is supposted to work. I an running Oneiric. Here are my logs:. I hope someone can figure this out.

 # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [HP], product=0x9311 [Deskjet 3050 J610 series]) at libusb:002:007

# Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

HP Linux Imaging and Printing System (ver. 3.12.2)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2011-14 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the
HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies
are installed to successfully compile HPLIP.
2. Run-time check mode (-r or --run): Use this mode to determine if a distro
supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball
has the proper dependencies installed to successfully run.
3. Both compile- and run-time check mode (-b or --both) (Default): This mode
will check both of the above cases (both compile- and run-time dependencies).

Saving output in log file: hp-check.log

Initializing. Please wait...

---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux Mancave 3.0.0-15-generic-pae #26-Ubuntu SMP Fri Jan 20 17:07:31 UTC 2012 i686 i686 i386 GNU/Linux

Distribution:
ubuntu 11.10

Checking Python version...
OK, version 2.7.2 installed

Checking PyQt 4.x version...
OK, version 4.8.5 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.5.0
error_log is set to level: warn

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.84.0

------------------------------------
| COMPILE AND RUNTIME DEPENDENCIES |
------------------------------------

note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).

Checking for dependency: CUPS - Common Unix Printing System...
OK, found.

Checking for dependency: CUPS devel- Common Unix Printing System development files...
OK, found.

Checking for dependency: CUPS image - CUPS image development files...
OK, found.

Checking for dependency: DBus - Message bus system...
OK, found.

Checking for dependency: gcc - GNU Project C and C++ Compiler...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
OK, found.

Checking for dependency: libjpeg - JPEG library...
OK, found.

Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
OK, found.

Checking for dependency: libpthread - POSIX threads library...
OK, found.

Checking for dependency: libtool - Library building support services...
OK, found.

Checking for dependency: libusb - USB library...
OK, found.

Checking for dependency: make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: PolicyKit - Administrative policy framework...
OK, found.

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
OK, found.

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python devel - Python development files...
OK, found.

Checking for dependency: Python libnotify - Python bindings for the libnotify Desktop notifications...
OK, found.

Checking for dependency: Python XML libraries...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
OK, found.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: SANE - Scanning library development files...
OK, found.

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.

----------------------
| HPLIP INSTALLATION |
----------------------

Currently installed HPLIP version...
HPLIP 3.12.2 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf. Generated from hplip.conf.in by configure.

[hplip]
version=3.12.2

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.12.2
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=no
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
hpijs-install=no
foomatic-drv-install=no
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.12.2
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=no
hpijs-only-build=no
lite-build=no
udev-acl-rules=yes
hpcups-only-build=no
hpijs-only-build=no

Current contents of '/var/lib/hp/hplip.state' file:
# hplip.state - HPLIP runtime persistent variables.

[plugin]
installed=0
eula=0

Current contents of '~/.hplip/hplip.conf' file:
[installation]
date_time = 02/11/2012 15:59:31
version = 3.12.2

[settings]
systray_visible = 0
systray_messages = 0

[last_used]
device_uri = "hp:/usb/Deskjet_3050_J610_series?serial=CN1C7480WR05HX"
printer_name = Deskjet_3050_J610
working_dir = .

[commands]
scan = /usr/bin/xsane -V %SANE_URI%

[refresh]
rate = 30
enable = false
type = 1

[polling]
enable = false
interval = 5
device_list =

[fax]
voice_phone =
email_address =

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI Model
  -------------------------------- ---------------------------
  hp:/usb/Deskjet_3050_J610_series HP Deskjet 3050 J610 series
  ?serial=CN1C7480WR05HX

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

Deskjet-3050-J610-series
------------------------
Type: Unknown
Device URI: usb://HP/Deskjet%203050%20J610%20series?serial=CN1C7480WR05HX&interface=1
PPD: /etc/cups/ppd/Deskjet-3050-J610-series.ppd
PPD Description: HP Deskjet 3050 j610 Series, hpcups 3.11.7
Printer status: printer Deskjet-3050-J610-series is idle. enabled since Sat 11 Feb 2012 03:53:54 PM CST
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

Deskjet_3050_J610
-----------------
Type: Printer
Device URI: hp:/usb/Deskjet_3050_J610_series?serial=CN1C7480WR05HX
PPD: /etc/cups/ppd/Deskjet_3050_J610.ppd
PPD Description: HP Deskjet 3050 j610 Series, hpcups 3.12.2
Printer status: printer Deskjet_3050_J610 is idle. enabled since Sat 11 Feb 2012 03:54:26 PM CST
Communication status: Good

Mancave
-------
Type: Unknown
Device URI: cnijusb:/dev/usb/lp0
PPD: /etc/cups/ppd/Mancave.ppd
PPD Description: Canon MP495 series Ver.3.40
Printer status: printer Mancave is idle. enabled since Sun 27 Nov 2011 07:37:09 AM CST
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

MP495-series
------------
Type: Unknown
Device URI: usb://Canon/MP495%20series?serial=A0FFEE&interface=1
PPD: /etc/cups/ppd/MP495-series.ppd
PPD Description: Canon MP495 series Ver.3.40
Printer status: printer MP495-series is idle. enabled since Tue 27 Dec 2011 09:41:38 PM CST
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
OK, found.

Checking 'scanext' SANE scanning extension...
OK, found.

-----------------
| USB I/O SETUP |
-----------------

Checking for permissions of USB attached printers...

HP Device 0x9311 at 002:007:
    Device URI: hp:/usb/Deskjet_3050_J610_series?serial=CN1C7480WR05HX
    Device node: /dev/bus/usb/002/007
    Mode: 0664

---------------
| USER GROUPS |
---------------

acknud adm lp dialout fax cdrom video plugdev netdev lpadmin admin sambashare scanner

-----------
| SUMMARY |
-----------

error: 3 errors and/or warnings.

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

Done.

hpscan -g

HP Linux Imaging and Printing System (ver. 3.12.2)
Scan Utility ver. 2.2

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

hp-scan[13400]: debug: getDeviceUri(None, None, ['hpaio'], {'scan-type':
(<built-in function gt>, 0)}, , True)
hp-scan[13400]: debug: Mode=0
hp-scan[13400]: debug: Device URI
usb://HP/Deskjet%203050%20J610%20series?serial=CN1C7480WR05HX&interface=1 is
invalid/unknown
hp-scan[13400]: debug: Exception: 4 (Unknown/invalid device-uri field)
hp-scan[13400]: debug:
hp:/usb/Deskjet_3050_J610_series?serial=CN1C7480WR05HX: back_end:hp
is_hp:True bus:usb model:Deskjet_3050_J610_series serial:CN1C7480WR05HX
dev_file: host: zc: port:1
hp-scan[13400]: debug: Cache miss: deskjet_3050_j610_series
hp-scan[13400]: debug: Reading file: /usr/share/hplip/data/models/models.dat
hp-scan[13400]: debug: Searching for section [deskjet_3050_j610_series]
in file /usr/share/hplip/data/models/models.dat
hp-scan[13400]: debug: Found section [deskjet_3050_j610_series] in file
/usr/share/hplip/data/models/models.dat
hp-scan[13400]: debug:
hp:/usb/Deskjet_3050_J610_series?serial=CN1C7480WR05HX: back_end:hp
is_hp:True bus:usb model:Deskjet_3050_J610_series serial:CN1C7480WR05HX
dev_file: host: zc: port:1
hp-scan[13400]: debug: Device URI cnijusb:/dev/usb/lp0 is invalid/unknown
hp-scan[13400]: debug: Exception: 4 (Unknown/invalid device-uri field)
hp-scan[13400]: debug: Device URI
usb://Canon/MP495%20series?serial=A0FFEE&interface=1 is invalid/unknown
hp-scan[13400]: debug: Exception: 4 (Unknown/invalid device-uri field)
hp-scan[13400]: debug:
{'hpaio:/usb/Deskjet_3050_J610_series?serial=CN1C7480WR05HX':
['Deskjet_3050_J610', 'Deskjet_3050_J610_2']}
Using device: hpaio:/usb/Deskjet_3050_J610_series?serial=CN1C7480WR05HX

warning: No destinations specified. Adding 'file' destination by default.
error: Unable to locate device
hpaio:/usb/Deskjet_3050_J610_series?serial=CN1C7480WR05HX using SANE
backend hpaio:. Please check HPLIP installation.

---

### Post by pqwoerituytrueiwoq on 2012-02-13
post output of these commands please use code tags 
[FONT=Courier New]scanimage -L[/FONT][FONT=Courier New][/FONT]

[FONT=Courier New]scanimage --help -d "hpaio:/usb/Deskjet_3050_J610_series?serial=CN1C7480WR05HX"[/FONT]

also it is easier to add hp drivers like this:
[FONT=Courier New]sudo add-apt-repository ppa:hplip-isv/ppa;sudo apt-get update;sudo apt-get install hplip[/FONT]

---

### Post by Acknud on 2012-02-13
I get the same thing.  I have uninstalled and reinstalled several times and I get the same result.  Do I need to take this one back and try another type?  I really need the scanner.  What about a stand alone scanner?  They are more expensive.


```
scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
```

```
scanimage -d "hpaio:/usb/Deskjet_3050_J610_series?serial=CN1C7480WR05HX"
scanimage: open of device hpaio:/usb/Deskjet_3050_J610_series?serial=CN1C7480WR05HX failed: Invalid argument

```

---

### Post by pqwoerituytrueiwoq on 2012-02-13
if you take it back i know my Deskjet F4480 (up to 1200dpi) can scan if you need network scanning that can be handled by ubuntu :) 
[http://ubuntuforums.org/showthread.php?t=1519201&page=12](http://ubuntuforums.org/showthread.php?t=1519201&page=12)

my moms Officejet 4500 G510g-m  also works wich also tops out at 1200 dpi but it can fax unlike mine

also make check for updates wit the update manager

---

### Post by Acknud on 2012-02-13
I would much rather get this working but it appears to be a flop.  This is the second MFP that I have purchased only to not be able to scan with either.  The first was a Canon Pixma 495.

---

### Post by pqwoerituytrueiwoq on 2012-02-13
[FONT=Courier New]sudo add-apt-repository ppa:hplip-isv/ppa;sudo apt-get update;sudo apt-get install hplip[/FONT]
if you ran that command earlier run [FONT=Courier New]sudo apt-get upgrade[/FONT]
if that does not get it working apparently hp has a bug to fix

---

### Post by ahughes on 2012-07-30
Hi everyone,
This is my first post:)
I'm running ubuntu 11.10 with AMD64.
After a couple of days of searching and finding no solution I stumbled across a suggestion. I tried it and it worked! Simply copy(rsync) /usr/lib64 to /usr/lib.

rsync -av /usr/lib64/ /usr/lib/

I hope this helps someone.

---

### Post by lindsay7 on 2012-07-30
I had the same problem, I needed the latest hplip-3.12.6.

Look here

[http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)

---

### Post by markenaix on 2013-03-09
> **ahughes said:**
> Hi everyone,
This is my first post:)
I'm running ubuntu 11.10 with AMD64.
After a couple of days of searching and finding no solution I stumbled across a suggestion. I tried it and it worked! Simply copy(rsync) /usr/lib64 to /usr/lib.

rsync -av /usr/lib64/ /usr/lib/

I hope this helps someone.

It works also for me, ubuntu 12.10, 64 bits, hplip-3.13.3, OfficeJet G55.
Thanks a lot, same behavior before copying lib64 onto lib: printer functional but no scanner.
Great first post!=D>
Made a diff before copying though, interesting part below:
```
diff /usr/lib64/libhpmud.la /usr/lib/libhpmud.la
20c20
< dependency_libs=' -lpthread -ldl -lnetsnmp -lusb -lcrypto'
---
> dependency_libs=' -lpthread -ldl -lnetsnmp -lusb-1.0 -lcrypto'
41c41
< libdir='/usr/lib64'
---
> libdir='/usr/lib'
 diff /usr/lib64/sane/libsane-hpaio.la /usr/lib/sane/libsane-hpaio.la
20c20
< dependency_libs=' /usr/lib64/libhpip.la -lm /usr/lib64/libhpmud.la -lpthread -lnetsnmp -lusb -ldbus-1 -lcups -ldl -lcrypto'
---
> dependency_libs=' /usr/lib/libhpip.la -lm /usr/lib/libhpmud.la -lpthread -lnetsnmp -lusb-1.0 -ldbus-1 -lcups -ldl -lcrypto'
41c41
< libdir='/usr/lib64/sane'
---
> libdir='/usr/lib/sane'
```

I read elsewhere (sorry I lost the link, but was in launchpad.net) to configure hplip to use libusb-0.1 instead of the libusb-1.0 (default) to avoid the communication failure with the device.
The latter could explain the former:-k

---

### Post by CT Husky on 2013-06-15
Just to add in my experience with a similar (now solved) for future users (speaking here as a VERY unsophisticated Ubuntu'er to other noobs):

Basic problem: printer worked fine, but scanner would not find the device.

Basic diagnostics: lsusb showed the device was there; but hp-setup (and the HPLIP GUI) did not find the device; and no scanning program could find a device.
  
Was running Ubuntu 10.04 for years just fine with my HP OfficeJet 4500 Wireless printer.  Wound up having problems trying a direct upgrade from 10.04 to the new 12.04 LongTerm Service Release.  Upgrade f ailed.  Managed to save things by doing a clean install of 10.04, but it did create a couple of glitches, notably that although the printing function worked fine, no scanner program could detect a scanner.  Errors such as "Device  not detected."  Which was weird, because printing worked fine.  Also, HPLIP (The Hewlett Packard Linux driver for HP printers) would not find the device.  But, on the other hand, going to a terminal and running the command "lsusb" -- which as I understand it basically asks what hardware is attached to your computer, such as screens, keyboards, printers, etc. -- would find a Hewlett-Packard device (presumably my printer).

But then even though "lsusb" showed my printer, commands such as "hp-setup" did not work; and when I opened the HPLIP GUI (Graphical User Interface, which is the name for the way to run commands through icons on your task bar and pull-down menus instead of using terminal commands), it would likewise fail to detect any devices. I reinstalled HPLIP multiple times, and deleted the printer via the System > Administration > Printing route several times.


I noticed that even after HPLIP complete removal and reinstallation, etc. the Synaptic Package Manager was reporting that the HPLIP latest version was 3.10.2.  Someone knowledgeable discussing a similar HP scanner-not-found problem (the second Launchpad link below) recommended updating HPLIP to 3.13.2.  I had to do this manually, because Synaptic is apparently hung up on HPLIP 3.10.2 as the "latest version".

What finally worked for me was manually installing the latest version of hplip that I could.

Finally ran into two Launchpad bug discussions, and this discussion here, that solved my problem.

See "Scanner not found since update" [https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/1057601 ]("https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/1057601")

and:

[https://answers.launchpad.net/hplip/+question/223591]("https://answers.launchpad.net/hplip/+question/223591")

Hope this helps someone!

Not clear why Synaptic doesn't have the true latest version of hplip available via the GUI.  Probably lots of good reasons.  But for this particular bug, hplip 3.10.2 or probably any 3.10.X version is just not good enough.

---

