---
title: "Problem installing HP OfficeJet as wireless network printer on ubuntu 10.04"
date: 2011-11-16
forum: Hardware
---

### Post by tjoff on 2011-11-16
I have bought a HP OfficeJet 6500A plus All-In-One printer, which I want to use with ubuntu 10.04 as a wireless network printer.
Before i bought i checked compatibility and functionality on [www.hplipopensource.org](www.hplipopensource.org) and [www.openprinting.org](www.openprinting.org), and all seemde to be  in order.

The machine is autodetected and fully functional when connected with a usb cable, but i have not managed to get it to work as a wireless printer.
This is what I did:

I configured the printer on the wireless network (through the printer interface), and it connects. It prints out a "Wireless Network Test Report", and everything works.  I can ping to its local ip adress.

I installed hplip 3.11.10 and dependencies manually. I did this because the default hplip in ubuntu 10.04 did not recognise the device.

I ran 'hp-check', which gave no errors or warnings:

```
tjoff@mek-403-jakbo-01:~$ hp-check 

HP Linux Imaging and Printing System (ver. 3.11.10)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
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
Linux mek-403-jakbo-01 2.6.32-35-generic #78-Ubuntu SMP Tue Oct 11 16:11:24 UTC 2011 x86_64 GNU/Linux

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
printer_name = 
working_dir = .
device_uri = "hp:/usb/Officejet_6500_E710n-z?serial=CN16F2402Q05JW"

[commands]
scan = /usr/bin/xsane -V %SANE_URI%

[installation]
version = 3.11.10
date_time = 2011-11-16 14:30:35

[settings]
systray_messages = 0
systray_visible = 0

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

  Device URI                        Model                    
  --------------------------------  -------------------------
  hp:/usb/Officejet_6500_E710n-z?s  HP Officejet 6500 E710n-z
  erial=CN16F2402Q05JW                                       

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
B-403-271-A4-COLOR2
-------------------
Type: Unknown
Device URI: smb://mek-ps1.win.dtu.dk/403-271-A4-Color

B403-271-A4-BW
--------------
Type: Unknown
Device URI: smb://mek-ps1.win.dtu.dk/403-271-A4-BW

HP-Officejet-6500-E710n-z-FAX
-----------------------------
Type: Printer
Device URI: hp:/usb/Officejet_6500_E710n-z?serial=CN16F2402Q05JW
PPD: /etc/cups/ppd/HP-Officejet-6500-E710n-z-FAX.ppd
PPD Description: HP Officejet 6500 e710n-z, hpcups 3.11.10
Printer status: printer HP-Officejet-6500-E710n-z-FAX is idle.  enabled since 2011-11-16T01:00:45 CET
Communication status: Good


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/usb/Officejet_6500_E710n-z?serial=CN16F2402Q05JW' is a Hewlett-Packard Officejet_6500_E710n-z all-in-one


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

HP Device 0x5412 at 002:005: 
    Device URI: hp:/usb/Officejet_6500_E710n-z?serial=CN16F2402Q05JW
    Device node: /dev/bus/usb/002/005
    Mode: 0664

---------------
| USER GROUPS |
---------------

lp adm dialout cdrom plugdev lpadmin admin sambashare vboxusers


-----------
| SUMMARY |
-----------

No errors or warnings.

Done.
```


I then ran 'sudo hp-setup', chose the device (which was detected), chose my wireless network, entered the wireless security key. On the configuration results dialog I get two messages:
"Your printer has been succesfully configured on the wireless network. You may now unplug the USB cable"
and
"The Ethernet cable is plugged in which will prevent you from connecting to a wireless network. To connect wirelessly, remove the cable and try again. (VSA000)"
There is no ethernet cable plugged in, so i can't remove it. I unplug the USB cable and click 'finish'. This makes the 'hp-setup'-dialog start over again, and the printer has not been installed.
In the terminal i have the following:

```
tjoff@mek-403-jakbo-01:~$ sudo hp-setup
[sudo] password for tjoff: 

HP Linux Imaging and Printing System (ver. 3.11.10)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching on USB bus...
GET /IoMgmt/Adapters HTTP/1.1
Host: localhost
User-Agent: hplip/3.0
Content-Type: text/xml; charset=utf-8
Content-Length: 0


GET /IoMgmt/Adapters/Wifi0/WifiNetworks HTTP/1.1
Host: localhost
User-Agent: hplip/3.0
Content-Type: text/xml; charset=utf-8
Content-Length: 0


GET /IoMgmt/Adapters/Wifi0/Profiles/Active HTTP/1.1
Host: localhost
User-Agent: hplip/3.0
Content-Type: text/xml; charset=utf-8
Content-Length: 0


GET /IoMgmt/Adapters/Wifi0/Protocols HTTP/1.1
Host: localhost
User-Agent: hplip/3.0
Content-Type: text/xml; charset=utf-8
Content-Length: 0


error: Missing response key: 'io:protocols-io:protocol-dd:dnsserveripaddress-0'
GET /IoMgmt/Adapters/Wifi0/VsaCodes.xml HTTP/1.1
Host: localhost
User-Agent: hplip/3.0
Content-Type: text/xml; charset=utf-8
Content-Length: 0


GET /IoMgmt/Adapters/Wifi0/WifiNetworks/SSID=mVnmXfsu HTTP/1.1
Host: localhost
User-Agent: hplip/3.0
Content-Type: text/xml; charset=utf-8
Content-Length: 0


GET /IoMgmt/IoConfig.xml HTTP/1.1
Host: localhost
User-Agent: hplip/3.0
Content-Type: text/xml; charset=utf-8
Content-Length: 0

```

I then tried to reconnect the printer usb cable and run 'hp-toolbox' and click "Wireless/wifi setup using USB". Now i get the error:

```
tjoff@mek-403-jakbo-01:~$ hp-toolbox 

HP Linux Imaging and Printing System (ver. 3.11.10)
HP Device Manager ver. 15.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


HP Linux Imaging and Printing System (ver. 3.11.10)
Wifi Configuration Utility ver. 1.1

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: Channel write error
error:  An I/O error occurred.  Please check the USB connection to your printer and try again. (Device I/O error)
Done.

```
Output of 'lsusb':
```
tjoff@mek-403-jakbo-01:~$ lsusb
Bus 007 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 1113:3163 Medion AG 
Bus 005 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:8140 Dell Computer Corp. Wireless 360 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 03f0:5412 Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
I do not have a clue know how to proceed from here, and any help is most welcome.

---

### Post by efflandt on 2011-11-16
I imagine the wireless printer setup is only for a wireless printer that is NOT connected to a wireless network (ad-hoc instead of infrastructure?).

If both the computer and printer are associated with and connected to wireless access point or router, the fact that it is wireless should not matter at all.  Have you tried simply setting it up as a network printer (AppSocket/HP JetDirect)?  That is all I do for a Lexmark color laser printer which is actually hard wired, but my computer is wireless connected to the LAN.

---

### Post by tjoff on 2011-11-16
Well, efflandt, you are absolutely right.  I did what you said and it worked right away. Apparantly I did not really understand what I was doing. Thanks for giving me, not the answer I asked for, but the answer I needed :-) Kudos!

---

