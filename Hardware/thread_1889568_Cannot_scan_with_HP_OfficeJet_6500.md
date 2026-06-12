---
title: "Cannot scan with HP OfficeJet 6500"
date: 2011-12-01
forum: Hardware
---

### Post by wrknight on 2011-12-01
:( Cannot scan with HP OfficeJet 6500 all-in-one printer.

I cannot use the scan function on my HP OJ 6500 all-in-one printer using xsane or simple-scan on ubuntu 11.04 running on an intel i5 2320 cpu.  HPLIP version is 3.11.10.  The printer works fine on Ubuntu and Windows 7, and the scannoer works on Windows 7 but not on Ubuntu.  

Using xsane, I get the following error messages: "failed to open device 'hpaio:/usb/OfficeJet_6500 - Device Busy"   and   "HPLIP Device Status - OfficeJet 6500 - Scan Job Failed (2002)"

Using simple-scan I get the following messages:  "Failed to Scan - Unable to connect to Scanner"  and
"HPLIP Device Status - OfficeJet 6500 - Scan Job Failed (2002)"

On a couple of occasions after turning both the computer and printer off and back on, simple-scan activated the scanner and diplayed a couple of lines of image prior to freezing up and displaying error message.  After that, I continued to get the “unable to connect to scanner” or “device busy” message.

Other messages are:
$ scanimage -L

device `hpaio:/usb/Officejet_6500_E709n?serial=TH06B2216X05G2' is a Hewlett-Packard Officejet_6500_E709n all-in-one


$ scanimage

scanimage: open of device hpaio:/usb/Officejet_6500_E709n?serial=TH06B2216X05G2 failed: Error during device I/O


$ hp-setup


HP Linux Imaging and Printing System (ver. 3.11.10)

Printer/Fax Setup Utility ver. 9.0



Copyright (c) 2001-9 Hewlett-Packard Development Company, LP

This software comes with ABSOLUTELY NO WARRANTY.

This is free software, and you are welcome to distribute it

under certain conditions. See COPYING file for more details.



Searching on USB bus...

[COLOR="Red"]error: Channel write error

error:  An I/O error occurred.  Please check the USB connection to your printer and try again. (Device I/O error)[/COLOR]

Searching... (bus=usb, search=(None), desc=0)

/

Done.


hp-check finds no errors or warnings

Output from hp-check -t is:

$ hp-check -t



HP Linux Imaging and Printing System (ver. 3.11.10)

Dependency/Version Check Utility ver. 14.3



Copyright (c) 2001-9 Hewlett-Packard Development Company, LP

This software comes with ABSOLUTELY NO WARRANTY.

This is free software, and you are welcome to distribute it

under certain conditions. See COPYING file for more details.



Note: hp-check can be run in three modes:

1. Compile-time check mode (-c or --compile): Use this mode before compiling the HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies are       

installed to successfully compile HPLIP.                                                                                                                                    

2. Run-time check mode (-r or --run): Use this mode to determine if a distro supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball has the proper   

dependencies installed to successfully run.                                                                                                                                 

3. Both compile- and run-time check mode (-b or --both) (Default): This mode will check both of the above cases (both compile- and run-time dependencies).                  



Saving output in log file: hp-check.log



Initializing. Please wait...

 

---------------

| SYSTEM INFO |

---------------



Basic system information:

Linux I-5 2.6.38-13-generic #52-Ubuntu SMP Tue Nov 8 16:53:51 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux



Distribution:

ubuntu 11.04



Checking Python version...

OK, version 2.7.1 installed



Checking PyQt 4.x version...

OK, version 4.8.3 installed.



Checking for CUPS...

Status: scheduler is running

Version: 1.4.6

error_log is set to level: warn



Checking for dbus/python-dbus...

dbus daemon is running.

python-dbus version: 0.83.1





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

HPLIP 3.11.10 currently installed in '/usr/share/hplip'.



Current contents of '/etc/hp/hplip.conf' file:

# hplip.conf.  Generated from hplip.conf.in by configure.



[hplip]

version=3.11.10



[dirs]

home=/usr/share/hplip

run=/var/run

ppd=/usr/share/ppd/HP

ppdbase=/usr/share/ppd

doc=/usr/share/doc/hplip-3.11.10

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

internal-tag=3.11.10

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

[last_used]

device_uri = "hpfax:/usb/Officejet_6500_E709n?serial=TH06B2216X05G2"

printer_name = HP-Fax

working_dir = .



[settings]

systray_visible = 0

systray_messages = 0



[commands]

scan = /usr/bin/simple-scan %SANE_URI%



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



[installation]

date_time = 12/01/2011 12:35:37

version = 3.11.10







--------------------------

| DISCOVERED USB DEVICES |

--------------------------



  Device URI                                          Model                             

  --------------------------------------------------  ----------------------------------

  hp:/usb/Officejet_6500_E709n?serial=TH06B2216X05G2  HP Officejet 6500 E709n           



---------------------------------

| INSTALLED CUPS PRINTER QUEUES |

---------------------------------



 

Officejet-6500-E709n

--------------------

Type: Printer

Device URI: hp:/usb/Officejet_6500_E709n?serial=TH06B2216X05G2

PPD: /etc/cups/ppd/Officejet-6500-E709n.ppd

PPD Description: HP Officejet 6500 e709n, hpcups 3.11.1

Printer status: printer Officejet-6500-E709n is idle.  enabled since Wed 30 Nov 2011 08:31:19 PM EST

Communication status: Good



Officejet-6500-E709n-Fax

------------------------

Type: Fax

Device URI: hpfax:/usb/Officejet_6500_E709n?serial=TH06B2216X05G2

PPD: /etc/cups/ppd/Officejet-6500-E709n-Fax.ppd

PPD Description: HP Fax hpcups

Printer status: printer Officejet-6500-E709n-Fax is idle.  enabled since Wed 30 Nov 2011 08:31:19 PM EST

Communication status: Good



Officejet_6500_E709n

--------------------

Type: Printer

Device URI: hp:/usb/Officejet_6500_E709n?serial=TH06B2216X05G2

PPD: /etc/cups/ppd/Officejet_6500_E709n.ppd

PPD Description: HP Officejet 6500 e709n, hpcups 3.11.10

Printer status: printer Officejet_6500_E709n is idle.  enabled since Wed 30 Nov 2011 08:31:19 PM EST

Communication status: Good



Officejet_6500_E709n_2

----------------------

Type: Printer

Device URI: hp:/usb/Officejet_6500_E709n?serial=TH06B2216X05G2

PPD: /etc/cups/ppd/Officejet_6500_E709n_2.ppd

PPD Description: HP Officejet 6500 e709n, hpcups 3.11.10

Printer status: printer Officejet_6500_E709n_2 is idle.  enabled since Thu 01 Dec 2011 12:24:16 PM EST

Communication status: Good



Officejet_6500_E709n_fax

------------------------

Type: Fax

Device URI: hpfax:/usb/Officejet_6500_E709n?serial=TH06B2216X05G2

PPD: /etc/cups/ppd/Officejet_6500_E709n_fax.ppd

PPD Description: HP Fax hpcups

Printer status: printer Officejet_6500_E709n_fax is idle.  enabled since Wed 30 Nov 2011 08:31:19 PM EST

Communication status: Good



Officejet_6500_E709n_fax_2

--------------------------

Type: Fax

Device URI: hpfax:/usb/Officejet_6500_E709n?serial=TH06B2216X05G2

PPD: /etc/cups/ppd/Officejet_6500_E709n_fax_2.ppd

PPD Description: HP Fax hpcups

Printer status: printer Officejet_6500_E709n_fax_2 is idle.  enabled since Thu 01 Dec 2011 12:24:16 PM EST

Communication status: Good





----------------------

| SANE CONFIGURATION |

----------------------



'hpaio' in '/etc/sane.d/dll.conf'...

OK, found. SANE backend 'hpaio' is properly set up.



Checking output of 'scanimage -L'...

device `hpaio:/usb/Officejet_6500_E709n?serial=TH06B2216X05G2' is a Hewlett-Packard Officejet_6500_E709n all-in-one





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



HP Device 0x4512 at 001:005: 

    Device URI: hp:/usb/Officejet_6500_E709n?serial=TH06B2216X05G2

    Device node: /dev/bus/usb/001/005

    Mode: 0664



---------------

| USER GROUPS |

---------------



wayne root daemon bin sys adm disk lp mail news uucp man proxy kmem dialout fax cdrom floppy tape sudo audio dip backup operator list irc src gnats shadow utmp video sasl plugdev staff games users libuuid crontab syslog fuse messagebus mlocate ssh avahi-autoipd avahi netdev bluetooth lpadmin ssl-cert gdm pulse pulse-access utempter rtkit admin saned sambashare vboxusers project





-----------

| SUMMARY |

-----------



No errors or warnings.



Done.

---

