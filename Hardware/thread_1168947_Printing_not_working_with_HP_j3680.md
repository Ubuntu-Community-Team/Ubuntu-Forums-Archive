---
title: "Printing not working with HP j3680"
date: 2009-05-24
forum: Hardware
---

### Post by larini on 2009-05-24
Hi, just install 8.04.2 and it recognizes my printer, but nothing happens when says to print.

So I install lastest HPLIP drivers and now the printer pull the paper but does not print. It displays "printing"... in panel.

My epson never get problems.

Any help ?

---

### Post by 11hjpphty76lkjj on 2009-05-24
Run:

hp-check -t 

and post the entire output.

Thanks.

Aaron

---

### Post by larini on 2009-05-25
Sorry about delay. Follows the output:


HP Linux Imaging and Printing System (ver. 3.9.4b)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the HPLIP supplied tarball (.tar.gz or .run) to determine if the proper         
dependencies are installed to successfully compile HPLIP.                                                                                                    
2. Run-time check mode (-r or --run): Use this mode to determine if a distro supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball   
has the proper dependencies installed to successfully run.                                                                                                   
3. Both compile- and run-time check mode (-b or --both) (Default): This mode will check both of the above cases (both compile- and run-time dependencies).   

Saving output in log file: hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux servidor 2.6.24-24-generic #1 SMP Wed Apr 15 15:54:25 UTC 2009 i686 GNU/Linux

Distribution:
ubuntu 8.04

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.5.2 installed

Checking PyQt 4.x version...
OK, version 4.3.3 installed.

Checking for CUPS...
Status: o programador está executando
Version: 1.3.7
error_log is set to level: warn

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.82.4


------------------------------------
| COMPILE AND RUNTIME DEPENDENCIES |
------------------------------------

note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).

Checking for dependency: CUPS - Common Unix Printing System...
OK, found.

Checking for dependency: CUPS DDK - CUPS driver development kit...
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

Checking for dependency: ppdev - Parallel port support kernel module....
OK, found.

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
OK, found.

Checking for dependency: Python ctypes - A foreign function library for Python...
OK, found.

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python devel - Python development files...
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
HPLIP 3.9.4b currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.9.4b

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hpijs/HP
ppdbase=/usr/share/ppd/hpijs
doc=/usr/share/doc/hplip-3.9.4b
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp/

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
foomatic-drv-install=yes
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
cups-ppd-install=no
cups-drv-install=no
internal-tag=3.9.4b.10
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=yes


Current contents of '/var/lib/hp/hplip.state' file:
# hplip.state - HPLIP runtime persistent variables. 

[plugin]
installed=0
eula=0



Current contents of '~/.hplip/hplip.conf' file:
[last_used]
printer_name = Officejet_J3600_series
working_dir = .
device_uri = "hp:/usb/Officejet_J3600_series?serial=CN8BA5P7NP053D"

[commands]
scan = /usr/bin/xsane -V %SANE_URI%

[installation]
version = 3.9.4b.10
date_time = 05/25/09 07:54:11

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

  Device URI                                            Model                          
  ----------------------------------------------------  -------------------------------
  hp:/usb/Officejet_J3600_series?serial=CN8BA5P7NP053D  HP Officejet J3600 series      

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
warning: No queues found.

----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/usb/Officejet_J3600_series?serial=CN8BA5P7NP053D' is a Hewlett-Packard Officejet_J3600_series all-in-one


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

HP Device 0x3112 at 003:002: 
    Device URI: hp:/usb/Officejet_J3600_series?serial=CN8BA5P7NP053D
    Device node: /dev/bus/usb/003/002
    Mode: 0660
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/003/002
# owner: lp
# group: lp
user::rw-
user:administrador:rw-
group::rw-
mask::rw-
other::---



---------------
| USER GROUPS |
---------------

administrador adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin sambashare


-----------
| SUMMARY |
-----------

No errors or warnings.

Done.

---

### Post by 11hjpphty76lkjj on 2009-05-25
From this:

```
--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                                            Model                          
  ----------------------------------------------------  -------------------------------
  hp:/usb/Officejet_J3600_series?serial=CN8BA5P7NP053D  HP Officejet J3600 series      

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
warning: No queues found.
```

It appears that HPLIP can detect the printer, however there are no printer queues configured.

Try running:

```
sudo hp-setup
```

Any better?

---

### Post by larini on 2009-05-25
Hi Aaron, hp-setup show me the same printer that already instaled on system. I followed the wizard and it install another copies. Now I have 4 printers, two j3680 and two j3680 fax.

But sill not work, and hp-check prints the same result.

---

### Post by 11hjpphty76lkjj on 2009-05-25
Run:

```
sudo tail -f /var/log/syslog
```

Then try and print and post the output in the syslog.

---

### Post by larini on 2009-05-25
I will try this later, because this machine is far from 
me.
Thanks.

---

### Post by larini on 2009-05-25
sudo tail -f /var/log/syslog
May 25 18:20:15 servidor NetworkManager: <debug> [1243286415.858920] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_3112_CN8BA5P7NP053D_if1'). 
May 25 18:20:15 servidor NetworkManager: <debug> [1243286415.913196] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_3112_CN8BA5P7NP053D_if0'). 
May 25 18:20:16 servidor hal_lpadmin: add
May 25 18:20:17 servidor hal_lpadmin: URIs: ['hp:/usb/Officejet_J3600_series?serial=CN8BA5P7NP053D', 'usb://HP/Officejet%20J3600%20series?serial=CN8BA5P7NP053D', 'hal:///org/freedesktop/Hal/devices/usb_device_3f0_3112_CN8BA5P7NP053D_if1_printer_CN8BA5P7NP053D']
May 25 18:20:17 servidor hal_lpadmin: HPLIP Fax URIs: ['hpfax:/usb/Officejet_J3600_series?serial=CN8BA5P7NP053D']
May 25 18:20:17 servidor hal_lpadmin: Not adding fax printer: Officejet_J3600_series_fax already exists
May 25 18:20:17 servidor hal_lpadmin: Not adding fax printer: Officejet_J3600_fax already exists
May 25 18:20:17 servidor hal_lpadmin: Not adding printer: Officejet_J3600 already exists
May 25 18:20:17 servidor hal_lpadmin: Not adding printer: Officejet_J3600_series already exists
May 25 18:20:17 servidor NetworkManager: <debug> [1243286417.585072] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_3112_CN8BA5P7NP053D_if1_printer_CN8BA5P7NP053D'). 
May 25 18:20:46 servidor kernel: [  585.857770] audit(1243286446.085:6): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=7443 profile="/usr/sbin/cupsd" namespace="default"
May 25 18:20:46 servidor kernel: [  586.406980] usblp0: removed
May 25 18:20:47 servidor kernel: [  587.051760] hub 3-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
May 25 18:20:47 servidor kernel: [  587.051770] usb 3-2: USB disconnect, address 10
May 25 18:20:47 servidor Officejet_J3600_series?serial=CN8BA5P7NP053D: io/hpmud/musb.c 1022: bulk_write failed buf=0xbf968aac size=2272 len=-19: No data available 
May 25 18:20:47 servidor Officejet_J3600_series?serial=CN8BA5P7NP053D: io/hpmud/musb.c 1389: unable to write data hp:/usb/Officejet_J3600_series?serial=CN8BA5P7NP053D: No data available 
May 25 18:20:47 servidor Officejet_J3600_series?serial=CN8BA5P7NP053D: io/hpmud/musb.c 725: invalid deviceid wIndex=1, retrying wIndex=100: No such device 
May 25 18:20:47 servidor Officejet_J3600_series?serial=CN8BA5P7NP053D: io/hpmud/musb.c 734: invalid deviceid retry ret=-19: No such device 
May 25 18:20:47 servidor Officejet_J3600_series?serial=CN8BA5P7NP053D: prnt/backend/hp.c 601: ERROR: 5021 device communication error! 
May 25 18:20:47 servidor kernel: [  587.163703] usb 3-2: new full speed USB device using uhci_hcd and address 11
May 25 18:20:47 servidor kernel: [  587.362905] usb 3-2: configuration #1 chosen from 1 choice
May 25 18:20:47 servidor kernel: [  587.369823] usblp0: USB Bidirectional printer dev 11 if 1 alt 0 proto 2 vid 0x03F0 pid 0x3112
May 25 18:20:47 servidor hal_lpadmin: remove
May 25 18:20:47 servidor hal_lpadmin: Found configured printer: Officejet_J3600_series_fax
May 25 18:20:47 servidor hal_lpadmin: Found configured printer: Officejet_J3600_fax
May 25 18:20:47 servidor hal_lpadmin: Found configured printer: Officejet_J3600
May 25 18:20:47 servidor hal_lpadmin: Found configured printer: Officejet_J3600_series
May 25 18:20:47 servidor NetworkManager: <debug> [1243286447.702254] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_3112_CN8BA5P7NP053D_if1_printer_CN8BA5P7NP053D'). 
May 25 18:20:47 servidor NetworkManager: <debug> [1243286447.705998] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_3112_CN8BA5P7NP053D_if0'). 
May 25 18:20:47 servidor NetworkManager: <debug> [1243286447.709983] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_3112_CN8BA5P7NP053D_if1'). 
May 25 18:20:47 servidor NetworkManager: <debug> [1243286447.712998] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_3112_CN8BA5P7NP053D_if2'). 
May 25 18:20:47 servidor NetworkManager: <debug> [1243286447.722739] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_3112_CN8BA5P7NP053D'). 
May 25 18:20:47 servidor NetworkManager: <debug> [1243286447.722851] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_3112_CN8BA5P7NP053D'). 
May 25 18:20:47 servidor NetworkManager: <debug> [1243286447.744575] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_3112_CN8BA5P7NP053D_if0'). 
May 25 18:20:47 servidor NetworkManager: <debug> [1243286447.767700] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_3112_CN8BA5P7NP053D_if1'). 
May 25 18:20:47 servidor NetworkManager: <debug> [1243286447.820978] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_3112_CN8BA5P7NP053D_if2'). 
May 25 18:20:48 servidor hal_lpadmin: add
May 25 18:20:49 servidor hal_lpadmin: URIs: ['hp:/usb/Officejet_J3600_series?serial=CN8BA5P7NP053D', 'usb://HP/Officejet%20J3600%20series?serial=CN8BA5P7NP053D', 'hal:///org/freedesktop/Hal/devices/usb_device_3f0_3112_CN8BA5P7NP053D_if1_printer_CN8BA5P7NP053D']
May 25 18:20:49 servidor hal_lpadmin: HPLIP Fax URIs: ['hpfax:/usb/Officejet_J3600_series?serial=CN8BA5P7NP053D']
May 25 18:20:49 servidor hal_lpadmin: Not adding fax printer: Officejet_J3600_series_fax already exists
May 25 18:20:49 servidor hal_lpadmin: Not adding fax printer: Officejet_J3600_fax already exists
May 25 18:20:49 servidor hal_lpadmin: Not adding printer: Officejet_J3600 already exists
May 25 18:20:49 servidor hal_lpadmin: Not adding printer: Officejet_J3600_series already exists
May 25 18:20:49 servidor NetworkManager: <debug> [1243286449.455619] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_3112_CN8BA5P7NP053D_if1_printer_CN8BA5P7NP053D'). 

>>> after this the printer stop and I need to turn off printer to exit paper.
Some times prints one line and stop.

The printer test page works ok. windows ok.




after

---

### Post by larini on 2009-05-26
bump!

---

### Post by larini on 2009-05-27
Hi Aaron, any clue ?

---

### Post by larini on 2009-05-28
bump!

---

### Post by cecilieaux on 2010-02-20
> Try running:

```
sudo hp-setup
```

Any better?
Maybe you can help both of us along ...

I tried hp-setup, as you suggested to Larini. (I have the same problem, same printer, with Ubuntu gnome 8.04 LTS. Scans fine, just doesn't print.)

The hp-setup could not come up with a PPD file that matched, so I quit.

Where does one get PPD files?

---

