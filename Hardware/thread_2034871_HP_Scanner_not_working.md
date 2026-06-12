---
title: "HP Scanner not working"
date: 2012-07-29
forum: Hardware
---

### Post by paulemony on 2012-07-29
Ubuntu 11.10
HP Deskjet 2050 J510 3in1
HPLIP 3.11.7-1ubuntu3.1

Seems to be a common problem but I can't find the answer, printer & copier work but scanner has stopped working (although it does on different laptop running Ubuntu 12.04). HPLIP toolbox says "No installed HP devices found", Simple Scan has "No scanners available" and XSane "No devices available". **hp-check-t** has these errors:

[B]Checking for dependency: DBus - Message bus system...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.

| DISCOVERED USB DEVICES |
No devices found.

INSTALLED CUPS PRINTER QUEUES
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

USB I/O SETUP
HP Device 0x8711 at 001:006: 
    Device URI: hp:/usb/Deskjet_2050_J510_series?serial=CN18112RG905QV
error: Unsupported model: Deskjet_2050_J510_series
[/B]

So it does know it's there, but why it says "unsupported" when it is I don't know. Anybody know what's needed?

---

### Post by paulemony on 2012-07-29
P.S. dbus 1.4.14-1ubuntu1 *is* installed

---

### Post by CinemaFoto on 2013-04-26
Hi!
Suddenly got the same problem. Cannot say exactly when and what was a trigger for that, but one day HPLIP stopped to 'see' my [HP Deskjet 2050 j510 All-in-one Printer]("http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_2050_j510_series.html") ("The device"). As I remember, I scanned something, and I was going to scan another page, but suddenly XSane (through GIMP) didn't 'feel' any connected device. Turning on - off the device didn't help. So I tried to disconnect - reconnect USB cable of the device. It caused my PC to hang up with CapsLock and ScrollLock blinking LEDs (Kernel panic?). Restart didn't help. [FONT=Courier New]lsusb[/FONT] sees Hewlett-Packard Device: [[FONT=Courier New]Bus 001 Device 004: ID 03f0:8711 Hewlett-Packard[/FONT]]. I was thinking already to buy a new All-in-One device... But decided to check it in Windows (XP) too. What a miracle - some kind of reincarnation - the device is working perfect in WinXP!
HPLIP was completely removed and reinstalled by Synaptic. Didn't help.
The situation for now. Reconnection of USB cable don't cause hanging up anymore. The device is able to print (didn't see any problem in printing!), but HPLIP don't 'see' any connected device. HPLIP prints out the message:
> HP Device 0x8711 at 001:004: 
    Device URI: hp:/usb/Deskjet_2050_J510_series?serial=CN15512HQ805QV
error: Unsupported model: Deskjet_2050_J510_series
As You can see in the link above, the device was listed in HPLIP as almost fully supported and was purchased by me just because I knew that this model has support in Linux.
How can I bring back the scanning abilities of the device under Ubuntu?
If this is not the correct place to ask that question, please, make me know where it is correct to publish it.
I'm running 10.04 LTS - the Lucid Lynx (Still! Don't like Unity on Desktop, have no time to tune it to GNOME).
Here output of [FONT=Courier New]hp-check -t[/FONT]:
> ---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux core2duo 2.6.32-43-generic #97-Ubuntu SMP Wed Sep 5 16:42:26 UTC 2012 x86_64 GNU/Linux

Distribution:
ubuntu 10.04

Checking Python version...
OK, version 2.6.5 installed

Checking PyQt 4.x version...
OK, version 4.7.2 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.4.3
error_log is set to level: warn

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.83.0


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
HPLIP 3.10.2 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.10.2

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hplip/HP
ppdbase=/usr/share/ppd/hplip
doc=/usr/share/doc/hplip-doc/HTML
icon=no
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=yes
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
hpijs-install=yes
foomatic-drv-install=yes
foomatic-ppd-install=yes
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.10.2rc1.9
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=yes
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
[last_used]
printer_name = Deskjet-2050-J510-series
working_dir = .
device_uri = "hp:/usb/Deskjet_2050_J510_series?serial=CN15512HQ805QV"

[commands]
scan = /usr/bin/xsane -V %SANE_URI%

[installation]
version = 3.10.2rc1.9
date_time = 04/26/2013 09:47:45

[settings]
systray_messages = 0
systray_visible = 1

[fax]
email_address = 
voice_phone = 

[refresh]
rate = 30
enable = false
type = 1

[polling]
enable = false
device_list = 
interval = 5



--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Deskjet-2050-J510-series
------------------------
Type: Unknown
Device URI: usb://HP/Deskjet%202050%20J510%20series?serial=CN15512HQ805QV
PPD: /etc/cups/ppd/Deskjet-2050-J510-series.ppd
PPD Description: HP Deskjet 2050 j510 Series, hpcups 3.11.10
Printer status: printer Deskjet-2050-J510-series is idle.  enabled since Fri 26 Apr 2013 07:35:26 AM IDT
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

HP Device 0x8711 at 001:004: 
    Device URI: hp:/usb/Deskjet_2050_J510_series?serial=CN15512HQ805QV
error: Unsupported model: Deskjet_2050_J510_series

---------------
| USER GROUPS |
---------------

c********o adm lp dialout cdrom plugdev lpadmin admin sambashare

User member of group 'lp'. Enables print/ scan/ fax.
User member of group 'lpadmin'.

-----------
| SUMMARY |
-----------

error: 1 error or warning.

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.
Thank You in advance.

---

### Post by CinemaFoto on 2013-04-27
OK. Downloading and reinstalling of HPLIP from the Project's Web Site resolved the problem. First of all I marked for Complete Uninstall all HPLIP rows in Synaptic and applied the changes. After that I've got the newest package from [HPLIP website]("http://hplipopensource.com/hplip-web/gethplip.html"). Then I followed the [Installation Instruction]("http://hplipopensource.com/hplip-web/install/install/index.html") of the .run installer. When the installation started, it discovered, that there is some missing library - [FONT=Courier New]libusb[/FONT]. May it be the problem? As for now, [FONT=Courier New]hp-setup[/FONT] found the device, Sane can scan and everything is looking good for now.
Maybe it can be useful for somebody else.

---

