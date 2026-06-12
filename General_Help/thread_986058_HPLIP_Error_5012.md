---
title: "HPLIP Error 5012"
date: 2008-11-18
forum: General Help
---

### Post by rhardie on 2008-11-18
I used the HPLIP HP Linux Imaging and Printing ( [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) ) to detect and set up my HP 4100MFP (Multifunction Printer).

The printer was automatically detected in moments and set up took a few seconds.  I attempted to print a test page and received a "communication error 5012).

Previous attempts to print using the Ubuntu printer set up would also set up the printer with the same results of not being able to print.  Error box kept appearing suggesting the printer was not turned on (form of communication error, I suppose).

Printer does print test page OK.

I did Google search and have found some references to other printers with mention of permissions or setting something up in root.  Not sure that anything like this applies.

System:

OS: Ubuntu 8.10
Processor:  AMD 64 Athlon 3200
Memory:  3 GB
Printer Networking: Ethernet
Printer address:  Mfg default 192.0.0.192 (detected by HPLIP)
PPD/Driver: HP Laserjet 4100 MFP v.3010.107 Postscript (Recommended)

Summary:

Printer self test = OK
Cat5 cable test = OK
HPLIP detects printer = OK
Print job successful = NO

Thanks in advance!  :-)

---

### Post by Tamlynmac on 2008-11-18
Have you rebooted both the printer and the PC? Shut both down and star printer first. I had a similar problem until rebooting both devices. Hope it's that simple for you to.

---

### Post by Rayaz on 2008-11-18
Is it connected by a LAN cable? If yes then try setting up a static IP address. Should work wonders!

---

### Post by Mark Phelps on 2008-11-18
You tried accessing and configuring the printer using localhost:631 in a browser?  I use that to manage a networked HP printer, without using HPLIP, and it works great.

---

### Post by rhardie on 2008-11-21
Thanks for the replies.

Yes, this is on an Ethernet connection.

Yes, I did the Local Host.

Yes, the printer's IP address is static.

I'll attempt to shut down both pretty soon and see if that has an effect.

Thanks, again!

---

### Post by rhardie on 2008-11-21
Did the sequence recommended with same communication error 5012.

Powered down workstation
Powered down HP 4100
Restarted HP 4100
Hp 4100 completes self test and in online status (Green)
Power up workstation
Open HPLIP
Receive Communication error 5012

**************************

rocky@rocky-desktop:~$ **hp-check -t**

HP Linux Imaging and Printing System (ver. 2.8.7)
Dependency/Version Check Utility ver. 14.0

Copyright (c) 2001-8 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies are installed  
to successfully compile HPLIP.                                                                                                                                                   
2. Run-time check mode (-r or --run): Use this mode to determine if a distro supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball has the proper        
dependencies installed to successfully run.                                                                                                                                      
3. Both compile- and run-time check mode (-b or --both) (Default): This mode will check both of the above cases (both compile- and run-time dependencies).                       

Saving output in log file: hp-check.log

Initializing. Please wait...
warning: Invalid ppd_dir value: None

---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux rocky-desktop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux

Distribution:
ubuntu 8.10

HPOJ running?
error: Yes, HPOJ is running. HPLIP is not compatible with HPOJ. To run HPLIP, please remove HPOJ.

Checking Python version...
OK, version 2.5.2 installed

Checking PyQt version...
OK, version 3.17 installed.

Checking SIP version...
error: SIP not installed or version not found.

Checking for CUPS...
Status: scheduler is running
error: Version: (Not available. CUPS may not be installed or not running.)

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.82.4


------------------------------------
| COMPILE AND RUNTIME DEPENDENCIES |
------------------------------------

note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).

Checking for dependency: cups - Common Unix Printing System...
OK, found.

Checking for dependency: cups-ddk - CUPS driver development kit...
OK, found.

Checking for dependency: cups-devel- Common Unix Printing System development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: dbus - Message bus system...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: gcc - GNU Project C and C++ Compiler...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: libjpeg - JPEG library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: libpthread - POSIX threads library...
OK, found.

Checking for dependency: libtool - Library building support services...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: libusb - USB library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: ppdev - Parallel port support kernel module....
OK, found.

Checking for dependency: PyQt - Qt interface for Python...
OK, found.

Checking for dependency: python-ctypes - A foreign function library for Python...
OK, found.

Checking for dependency: python-dbus - Python bindings for dbus...
OK, found.

Checking for dependency: python-devel - Python development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
OK, found.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: SANE - Scanning library development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: scanimage - Shell scanning program...
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 2.8.7 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=2.8.7

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hpijs/HP
ppdbase=/usr/share/ppd/hpijs
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
foomatic-drv-install=yes
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
internal-tag=2.8.7.3
restricted-build=no



-------------------------------
| DISCOVERED PARALLEL DEVICES |
-------------------------------

No devices found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
HP_LaserJet_4100_MFP
--------------------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/net/HP_LaserJet_4100_MFP?ip=192.0.0.192
PPD: /etc/cups/ppd/HP_LaserJet_4100_MFP.ppd
PPD Description: HP LaserJet 4100 MFP v.3010.107 Postscript (recommended)
Printer status: printer HP_LaserJet_4100_MFP is idle.  enabled since Fri 21 Nov 2008 06:05:17 AM CST
error: Unable to communicate with device (code=12): hp:/net/HP_LaserJet_4100_MFP?ip=192.0.0.192


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
error: Not found. SANE backend 'hpaio' NOT properly setup (needs to be added to /etc/sane.d/dll.conf).

Checking output of 'scanimage -L'...
error: scanimage not found.

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
 
-----------
| SUMMARY |
-----------

error: 16 errors and/or warnings.

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.
rocky@rocky-desktop:~$

---

### Post by Rayaz on 2008-11-21
Please set a static IP adress for your wired connection in the network manager.

---

### Post by rhardie on 2009-01-28
got it fixed.  Reset IP address.  It appears the IP address range I assumed we had was not valid.  Moved to a lower IP address and all works OK.  This makes sense when the message says that the printer may not be connected.

I guess the system can detect the printer even if it can not send a print job to that IP address.

The IP address range did not occur to me as I "assumed" (wrongly) that just because the system detected the printer that it would also "print" to the printer.

The HPLIP tool really is a class act in Linux tools!

Thanks for everyone's help!:D

---

### Post by createsean on 2010-01-31
I'm getting the same error with my HPC6180.

I tried to open the network manager like Rayaz suggested, but it's not anywhere.I've checked every single menu and flyout and I can't find it.

Anyhow I'm a novice with linux and would appreciate your help.

---

### Post by Rayaz on 2010-01-31
Hi

Right click on the network manager icon in the system tray. From there  select "Edit Connections".

Hope this helps.

---

### Post by createsean on 2010-02-01
Rayaz,

Now that I've done that I realize I don't know how to find the static ip for my printer

---

### Post by Rayaz on 2010-02-01
Hi

You really shouldn't need to know the ip of the printer. Just add a printer via  "System=>Administration=>Printing. It should detect your networked printer.

---

### Post by createsean on 2010-02-01
Yeah my printer shows up there but when I print to it the printer status gives me a "not connected?" error. I know the printer is connected because I have no problems printing in windows. I've also set this printer to be the system wide default.

Interestingly I also get a black balloon in the corner of my screen that shows printing is complete - though nothing printed.

---

### Post by createsean on 2010-02-01
I just ran the printing troubleshooter and it didn't solve the problem but it did give me this diagnostic output.

> 
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Is local server publishing?):
{'local_server_exporting_printers': False}
Page 3 (Choose printer):
{'cups_dest': <cups.Dest Photosmart_C6100 (default)>,
 'cups_instance': None,
 'cups_queue': 'Photosmart_C6100',
 'cups_queue_listed': True}
Page 4 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/net/Photosmart_C6100_series?zc=HP4A8D1B',
                       'printer-info': u'Photosmart_C6100',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'HP Photosmart c6100 Series hpijs, 3.9.8',
                       'printer-state': 3,
                       'printer-state-message': u'/usr/lib/cups/backend/hp failed',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 8556572,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Photosmart_C6100'},
 'cups_printer_remote': False,
 'hplip_output': (['',
                   '\x1b[01mHP Linux Imaging and Printing System (ver. 3.9.8)\x1b[0m',
                   '\x1b[01mDevice Information Utility ver. 5.2\x1b[0m',
                   '',
                   'Copyright (c) 2001-9 Hewlett-Packard Development Company, LP',
                   'This software comes with ABSOLUTELY NO WARRANTY.',
                   'This is free software, and you are welcome to distribute it',
                   'under certain conditions. See COPYING file for more details.',
                   '',
                   '',
                   '\x1b[01mhp:/net/Photosmart_C6100_series?zc=HP4A8D1B\x1b[0m',
                   '',
                   '\x1b[01mDevice Parameters (dynamic data):\x1b[0m',
                   '\x1b[01m  Parameter                     Value(s)                                                  \x1b[0m',
                   '  ----------------------------  ----------------------------------------------------------',
                   '  back-end                      hp                                                        ',
                   '  cups-printers                 Photosmart_C6100                                          ',
                   '  cups-uri                      hp:/net/Photosmart_C6100_series?zc=HP4A8D1B               ',
                   '  dev-file                                                                                ',
                   '  device-state                  -1                                                        ',
                   '  device-uri                    hp:/net/Photosmart_C6100_series?zc=HP4A8D1B               ',
                   '  deviceid                                                                                ',
                   '  error-state                   101                                                       ',
                   '  fax-uri                       hpfax:/net/Photosmart_C6100_series?zc=HP4A8D1B            ',
                   '  host                          HP4A8D1B                                                  ',
                   '  is-hp                         True                                                      ',
                   '  panel                         0                                                         ',
                   '  panel-line1                                                                             ',
                   '  panel-line2                                                                             ',
                   '  port                          1                                                         ',
                   '  scan-uri                      hpaio:/net/Photosmart_C6100_series?zc=HP4A8D1B            ',
                   '  serial                                                                                  ',
                   '  status-code                   5002                                                      ',
                   '  status-desc                                                                             ',
                   '\x1b[01m',
                   'Model Parameters (static data):\x1b[0m',
                   '\x1b[01m  Parameter                     Value(s)                                                  \x1b[0m',
                   '  ----------------------------  ----------------------------------------------------------',
                   '  align-type                    1                                                         ',
                   '  clean-type                    1                                                         ',
                   '  color-cal-type                4                                                         ',
                   '  copy-type                     0                                                         ',
                   '  embedded-server-type          1                                                         ',
                   '  fax-type                      1                                                         ',
                   '  fw-download                   False                                                     ',
                   '  icon                          Photosmart_C6100.png                                      ',
                   '  io-mfp-mode                   3                                                         ',
                   '  io-mode                       1                                                         ',
                   '  io-support                    6                                                         ',
                   '  job-storage                   0                                                         ',
                   '  linefeed-cal-type             0                                                         ',
                   '  model                         Photosmart_C6100_series                                   ',
                   '  model-ui                      HP Photosmart c6100 Series                                ',
                   '  model1                        HP Photosmart C6150 All-in-One Printer                    ',
                   '  model2                        HP Photosmart C6154 All-in-One Printer                    ',
                   '  model3                        HP Photosmart C6170 All-in-One Printer                    ',
                   '  model4                        HP Photosmart C6175 All-in-One Printer                    ',
                   '  model5                        HP Photosmart C6180 All-in-One Printer                    ',
                   '  model6                        HP Photosmart C6183 All-in-One Printer                    ',
                   '  model7                        HP Photosmart C6185 All-in-One Printer                    ',
                   '  model8                        HP Photosmart C6188 All-in-One Printer                    ',
                   '  model9                        HP Photosmart C6190 All-in-One Printer                    ',
                   '  monitor-type                  0                                                         ',
                   '  panel-check-type              1                                                         ',
                   '  pcard-type                    2                                                         ',
                   '  plugin                        0                                                         ',
                   '  plugin-reason                 0                                                         ',
                   '  power-settings                0                                                         ',
                   '  pq-diag-type                  0                                                         ',
                   '  r-type                        1                                                         ',
                   '  r0-agent1-kind                2                                                         ',
                   '  r0-agent1-sku                 2                                                         ',
                   '  r0-agent1-type                1                                                         ',
                   '  r0-agent2-kind                2                                                         ',
                   '  r0-agent2-sku                 2                                                         ',
                   '  r0-agent2-type                4                                                         ',
                   '  r0-agent3-kind                2                                                         ',
                   '  r0-agent3-sku                 2                                                         ',
                   '  r0-agent3-type                5                                                         ',
                   '  r0-agent4-kind                2                                                         ',
                   '  r0-agent4-sku                 2                                                         ',
                   '  r0-agent4-type                6                                                         ',
                   '  r0-agent5-kind                2                                                         ',
                   '  r0-agent5-sku                 2                                                         ',
                   '  r0-agent5-type                7                                                         ',
                   '  r0-agent6-kind                2                                                         ',
                   '  r0-agent6-sku                 2                                                         ',
                   '  r0-agent6-type                8                                                         ',
                   '  r0-agent7-kind                1                                                         ',
                   '  r0-agent7-type                12                                                        ',
                   '  r1-agent1-kind                2                                                         ',
                   '  r1-agent1-sku                 2                                                         ',
                   '  r1-agent1-type                1                                                         ',
                   '  r1-agent2-kind                2                                                         ',
                   '  r1-agent2-sku                 2                                                         ',
                   '  r1-agent2-type                4                                                         ',
                   '  r1-agent3-kind                2                                                         ',
                   '  r1-agent3-sku                 2                                                         ',
                   '  r1-agent3-type                5                                                         ',
                   '  r1-agent4-kind                2                                                         ',
                   '  r1-agent4-sku                 2                                                         ',
                   '  r1-agent4-type                6                                                         ',
                   '  r1-agent5-kind                2                                                         ',
                   '  r1-agent5-sku                 2                                                         ',
                   '  r1-agent5-type                7                                                         ',
                   '  r1-agent6-kind                2                                                         ',
                   '  r1-agent6-sku                 2                                                         ',
                   '  r1-agent6-type                8                                                         ',
                   '  r1-agent7-kind                1                                                         ',
                   '  r1-agent7-type                12                                                        ',
                   '  r2-agent1-kind                2                                                         ',
                   '  r2-agent1-sku                 363                                                       ',
                   '  r2-agent1-type                1                                                         ',
                   '  r2-agent2-kind                2                                                         ',
                   '  r2-agent2-sku                 363                                                       ',
                   '  r2-agent2-type                4                                                         ',
                   '  r2-agent3-kind                2                                                         ',
                   '  r2-agent3-sku                 363                                                       ',
                   '  r2-agent3-type                5                                                         ',
                   '  r2-agent4-kind                2                                                         ',
                   '  r2-agent4-sku                 363                                                       ',
                   '  r2-agent4-type                6                                                         ',
                   '  r2-agent5-kind                2                                                         ',
                   '  r2-agent5-sku                 363                                                       ',
                   '  r2-agent5-type                7                                                         ',
                   '  r2-agent6-kind                2                                                         ',
                   '  r2-agent6-sku                 363                                                       ',
                   '  r2-agent6-type                8                                                         ',
                   '  r4-agent1-kind                2                                                         ',
                   '  r4-agent1-sku                 177                                                       ',
                   '  r4-agent1-type                1                                                         ',
                   '  r4-agent2-kind                2                                                         ',
                   '  r4-agent2-sku                 177                                                       ',
                   '  r4-agent2-type                4                                                         ',
                   '  r4-agent3-kind                2                                                         ',
                   '  r4-agent3-sku                 177                                                       ',
                   '  r4-agent3-type                5                                                         ',
                   '  r4-agent4-kind                2                                                         ',
                   '  r4-agent4-sku                 177                                                       ',
                   '  r4-agent4-type                6                                                         ',
                   '  r4-agent5-kind                2                                                         ',
                   '  r4-agent5-sku                 177                                                       ',
                   '  r4-agent5-type                7                                                         ',
                   '  r4-agent6-kind                2                                                         ',
                   '  r4-agent6-sku                 177                                                       ',
                   '  r4-agent6-type                8                                                         ',
                   '  r8-agent1-kind                2                                                         ',
                   '  r8-agent1-sku                 801                                                       ',
                   '  r8-agent1-type                1                                                         ',
                   '  r8-agent2-kind                2                                                         ',
                   '  r8-agent2-sku                 801                                                       ',
                   '  r8-agent2-type                4                                                         ',
                   '  r8-agent3-kind                2                                                         ',
                   '  r8-agent3-sku                 801                                                       ',
                   '  r8-agent3-type                5                                                         ',
                   '  r8-agent4-kind                2                                                         ',
                   '  r8-agent4-sku                 801                                                       ',
                   '  r8-agent4-type                6                                                         ',
                   '  r8-agent5-kind                2                                                         ',
                   '  r8-agent5-sku                 801                                                       ',
                   '  r8-agent5-type                7                                                         ',
                   '  r8-agent6-kind                2                                                         ',
                   '  r8-agent6-sku                 801                                                       ',
                   '  r8-agent6-type                8                                                         ',
                   '  scan-style                    1                                                         ',
                   '  scan-type                     1                                                         ',
                   '  status-battery-check          0                                                         ',
                   '  status-dynamic-counters       1                                                         ',
                   '  status-type                   2                                                         ',
                   '  support-released              True                                                      ',
                   '  support-subtype               16101                                                     ',
                   '  support-type                  2                                                         ',
                   '  support-ver                   1.6.9                                                     ',
                   "  tech-class                    ['DJGenericVIP']                                          ",
                   "  tech-subclass                 ['Normal']                                                ",
                   '  tech-type                     2                                                         ',
                   '  usb-pid                       22801                                                     ',
                   '  usb-vid                       1008                                                      ',
                   '  wifi-config                   0                                                         ',
                   '\x1b[01m',
                   'Status History (most recent first):\x1b[0m',
                   '\x1b[01m  Date/Time             Code   Status Description                        User      Job ID  \x1b[0m',
                   '  --------------------  -----  ----------------------------------------  --------  --------',
                   '  02/02/10 12:51:21     5012   Device communication error                sean      0       ',
                   '  02/02/10 12:35:52     501    Print job has completed                   sean      3       ',
                   '  02/02/10 12:35:12     500    Started a print job                       sean      3       ',
                   '  02/02/10 12:33:57     501    Print job has completed                   sean      3       ',
                   '  02/02/10 12:33:15     500    Started a print job                       sean      3       ',
                   '  02/02/10 12:27:50     501    Print job has completed                   sean      3       ',
                   '  02/02/10 12:27:07     500    Started a print job                       sean      3       ',
                   '',
                   '',
                   'Done.',
                   ''],
                  ['\x1b[35;01mwarning: No display found.\x1b[0m',
                   '\x1b[31;01merror: hp-info -u/--gui requires Qt4 GUI support. Entering interactive mode.\x1b[0m',
                   '\x1b[31;01merror: Unable to communicate with device (code=12): hp:/net/Photosmart_C6100_series?zc=HP4A8D1B\x1b[0m',
                   '\x1b[31;01merror: Error opening device (Device not found).\x1b[0m',
                   ''],
                  0),
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'color-supported': True,
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.4.1',
                                 'device-uri': u'hp:/net/Photosmart_C6100_series?zc=HP4A8D1B',
                                 'document-format-default': u'application/octet-stream',
                                 'document-format-supported': [u'application/octet-stream',
                                                               u'application/openofficeps',
                                                               u'application/pdf',
                                                               u'application/postscript',
                                                               u'application/vnd.cups-banner',
                                                               u'application/vnd.cups-command',
                                                               u'application/vnd.cups-pdf',
                                                               u'application/vnd.cups-postscript',
                                                               u'application/vnd.cups-raw',
                                                               u'application/vnd.hp-hpgl',
                                                               u'application/x-cshell',
                                                               u'application/x-csource',
                                                               u'application/x-perl',
                                                               u'application/x-shell',
                                                               u'image/gif',
                                                               u'image/jpeg',
                                                               u'image/png',
                                                               u'image/tiff',
                                                               u'image/x-bitmap',
                                                               u'image/x-photocd',
                                                               u'image/x-portable-anymap',
                                                               u'image/x-portable-bitmap',
                                                               u'image/x-portable-graymap',
                                                               u'image/x-portable-pixmap',
                                                               u'image/x-sgi-rgb',
                                                               u'image/x-sun-raster',
                                                               u'image/x-xbitmap',
                                                               u'image/x-xpixmap',
                                                               u'image/x-xwindowdump',
                                                               u'text/css',
                                                               u'text/html',
                                                               u'text/plain'],
                                 'finishings-default': 3,
                                 'finishings-supported': [3],
                                 'generated-natural-language-supported': [u'en_US'],
                                 'ipp-versions-supported': [u'1.0',
                                                            u'1.1',
                                                            u'2.0',
                                                            u'2.1'],
                                 'job-hold-until-default': u'no-hold',
                                 'job-hold-until-supported': [u'no-hold',
                                                              u'indefinite',
                                                              u'day-time',
                                                              u'evening',
                                                              u'night',
                                                              u'second-shift',
                                                              u'third-shift',
                                                              u'weekend'],
                                 'job-k-limit': 0,
                                 'job-page-limit': 0,
                                 'job-priority-default': 50,
                                 'job-priority-supported': [100],
                                 'job-quota-period': 0,
                                 'job-settable-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'job-hold-until',
                                                                       u'job-priority',
                                                                       u'media',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
                                 'job-sheets-default': (u'none', u'none'),
                                 'job-sheets-supported': [u'none',
                                                          u'classified',
                                                          u'confidential',
                                                          u'secret',
                                                          u'standard',
                                                          u'topsecret',
                                                          u'unclassified'],
                                 'marker-change-time': 0,
                                 'media-col-supported': [u'media-color',
                                                         u'media-key',
                                                         u'media-size',
                                                         u'media-type'],
                                 'media-default': u'na_letter_8.5x11in',
                                 'media-supported': [u'na_letter_8.5x11in',
                                                     u'iso_a4_210x297mm',
                                                     u'na_index-4x6_4x6in',
                                                     u'na_5x7_5x7in',
                                                     u'na_index-4x6_4x6in',
                                                     u'na_index-3x5_3x5in',
                                                     u'na_index-5x8_5x8in',
                                                     u'iso_a5_148x210mm',
                                                     u'iso_a6_105x148mm',
                                                     u'iso_a6_105x148mm',
                                                     u'jis_b5_182x257mm',
                                                     u'adobe_CDDVD80_83.6083x83.6083mm',
                                                     u'adobe_CDDVD120_5x5in',
                                                     u'na_number-10_4.125x9.5in',
                                                     u'iso_c5_162x229mm',
                                                     u'iso_c6_114x162mm',
                                                     u'iso_dl_110x220mm',
                                                     u'iso_b5_176x250mm',
                                                     u'na_monarch_3.875x7.5in',
                                                     u'na_executive_7.25x10.5in',
                                                     u'na_foolscap_8.5x13in',
                                                     u'jpn_hagaki_100x148mm',
                                                     u'na_legal_8.5x14in',
                                                     u'jpn_oufuku_148x200mm',
                                                     u'roc_16k_7.75x10.75in',
                                                     u'na_foolscap_8.5x13in',
                                                     u'custom_min_1x4in',
                                                     u'custom_max_13x19in'],
                                 'multiple-document-handling-supported': [u'separate-documents-uncollated-copies',
                                                                          u'separate-documents-collated-copies'],
                                 'multiple-document-jobs-supported': True,
                                 'multiple-operation-time-out': 300,
                                 'natural-language-configured': u'en_US',
                                 'notify-attributes-supported': [u'printer-state-change-time',
                                                                 u'notify-lease-expiration-time',
                                                                 u'notify-subscriber-user-name'],
                                 'notify-events-default': [u'job-completed'],
                                 'notify-events-supported': [u'job-completed',
                                                             u'job-config-changed',
                                                             u'job-created',
                                                             u'job-progress',
                                                             u'job-state-changed',
                                                             u'job-stopped',
                                                             u'printer-added',
                                                             u'printer-changed',
                                                             u'printer-config-changed',
                                                             u'printer-deleted',
                                                             u'printer-finishings-changed',
                                                             u'printer-media-changed',
                                                             u'printer-modified',
                                                             u'printer-restarted',
                                                             u'printer-shutdown',
                                                             u'printer-state-changed',
                                                             u'printer-stopped',
                                                             u'server-audit',
                                                             u'server-restarted',
                                                             u'server-started',
                                                             u'server-stopped'],
                                 'notify-lease-duration-default': 86400,
                                 'notify-lease-duration-supported': (0,
                                                                     2147483647),
                                 'notify-max-events-supported': [100],
                                 'notify-pull-method-supported': [u'ippget'],
                                 'notify-schemes-supported': [u'mailto',
                                                              u'rss'],
                                 'number-up-default': 1,
                                 'number-up-supported': [1, 2, 4, 6, 9, 16],
                                 'operations-supported': [2,
                                                          4,
                                                          5,
                                                          6,
                                                          8,
                                                          9,
                                                          10,
                                                          11,
                                                          12,
                                                          13,
                                                          16,
                                                          17,
                                                          18,
                                                          19,
                                                          20,
                                                          21,
                                                          22,
                                                          23,
                                                          24,
                                                          25,
                                                          26,
                                                          27,
                                                          28,
                                                          34,
                                                          35,
                                                          37,
                                                          38,
                                                          16385,
                                                          16386,
                                                          16387,
                                                          16388,
                                                          16389,
                                                          16390,
                                                          16391,
                                                          16392,
                                                          16393,
                                                          16394,
                                                          16395,
                                                          16396,
                                                          16397,
                                                          16398,
                                                          16399,
                                                          16423],
                                 'orientation-requested-default': None,
                                 'orientation-requested-supported': [3,
                                                                     4,
                                                                     5,
                                                                     6],
                                 'page-ranges-supported': True,
                                 'pages-per-minute': 1,
                                 'pdl-override-supported': [u'not-attempted'],
                                 'port-monitor': u'none',
                                 'port-monitor-supported': [u'none'],
                                 'printer-commands': [u'AutoConfigure',
                                                      u'Clean',
                                                      u'PrintSelfTestPage'],
                                 'printer-current-time': '(IPP_TAG_DATE)',
                                 'printer-error-policy': u'retry-job',
                                 'printer-error-policy-supported': [u'abort-job',
                                                                    u'retry-current-job',
                                                                    u'retry-job',
                                                                    u'stop-printer'],
                                 'printer-info': u'Photosmart_C6100',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'',
                                 'printer-make-and-model': u'HP Photosmart c6100 Series hpijs, 3.9.8',
                                 'printer-more-info': u'http://localhost:631/printers/Photosmart_C6100',
                                 'printer-name': u'Photosmart_C6100',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1265081769,
                                 'printer-state-message': u'/usr/lib/cups/backend/hp failed',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 8556572,
                                 'printer-up-time': 1265082667,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/Photosmart_C6100'],
                                 'queued-job-count': 0,
                                 'server-is-sharing-printers': False,
                                 'sides-default': u'one-sided',
                                 'sides-supported': [u'one-sided',
                                                     u'two-sided-long-edge',
                                                     u'two-sided-short-edge'],
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 5 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'DryTime': u'Zero',
                                            u'Duplex': u'None',
                                            u'InputSlot': u'Default',
                                            u'PageRegion': u'letter',
                                            u'PageSize': u'letter',
                                            u'PrintoutMode': u'Normal'},
                               u'PrintoutMode': {u'Quality': u'FromPrintoutMode'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 6 (Local or remote?):
{'printer_is_remote': False}
Page 7 (Printer state reasons):
{'printer-state-message': u'/usr/lib/cups/backend/hp failed',
 'printer-state-reasons': [u'none']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
                          'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 29441L,
 'error_log_debug_logging_set': True}
Page 9 (Print test page):
{'test_page_attempted': '02/Feb/2010:12:52:23 +0000',
 'test_page_job_id': [4],
 'test_page_job_status': [(True,
                           4,
                           'Photosmart_C6100',
                           'Test Page',
                           'Processing',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-count': 1,
                            'document-format': u'application/vnd.cups-banner',
                            'job-hold-until': u'3:57:51',
                            'job-id': 4,
                            'job-k-octets': 1,
                            'job-media-progress': 0,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/4',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'sean',
                            'job-printer-state-message': u'/usr/lib/cups/backend/hp failed',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1265082804,
                            'job-printer-uri': u'ipp://sean-desktop:0/printers/Photosmart_C6100',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 4,
                            'job-state-reasons': u'job-hold-until-specified',
                            'job-uri': u'ipp://localhost:631/jobs/4',
                            'job-uuid': u'urn:uuid:d3d0fa5b-5a34-39da-4b80-db6d13321afe',
                            'printer-uri': u'ipp://localhost/printers/Photosmart_C6100',
                            'time-at-completed': None,
                            'time-at-creation': 1265082743,
                            'time-at-processing': 1265082743})],
 'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['D [02/Feb/2010:12:52:15 +0900] cupsdSetBusyState: Not busy',
               'D [02/Feb/2010:12:52:15 +0900] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:15 +0900] cupsdSetBusyState: Active clients',
               'D [02/Feb/2010:12:52:15 +0900] cupsdAuthorize: No authentication data provided.',
               'D [02/Feb/2010:12:52:15 +0900] cupsdReadClient: 11 1.1 Get-Jobs 1',
               'D [02/Feb/2010:12:52:15 +0900] Get-Jobs ipp://localhost/printers/',
               'D [02/Feb/2010:12:52:15 +0900] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [02/Feb/2010:12:52:15 +0900] cupsdSetBusyState: Not busy',
               'D [02/Feb/2010:12:52:15 +0900] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:15 +0900] cupsdSetBusyState: Active clients',
               'D [02/Feb/2010:12:52:15 +0900] cupsdAuthorize: No authentication data provided.',
               'D [02/Feb/2010:12:52:15 +0900] cupsdReadClient: 11 1.1 Get-Jobs 1',
               'D [02/Feb/2010:12:52:15 +0900] Get-Jobs ipp://localhost/printers/',
               'D [02/Feb/2010:12:52:15 +0900] [Job 1] Loading attributes...',
               'D [02/Feb/2010:12:52:15 +0900] [Job 2] Loading attributes...',
               'D [02/Feb/2010:12:52:15 +0900] [Job 3] Loading attributes...',
               'D [02/Feb/2010:12:52:15 +0900] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [02/Feb/2010:12:52:15 +0900] cupsdSetBusyState: Not busy',
               'D [02/Feb/2010:12:52:15 +0900] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:15 +0900] cupsdSetBusyState: Active clients',
               'D [02/Feb/2010:12:52:15 +0900] cupsdAuthorize: No authentication data provided.',
               'D [02/Feb/2010:12:52:15 +0900] cupsdReadClient: 11 1.1 Create-Printer-Subscription 1',
               'D [02/Feb/2010:12:52:15 +0900] Create-Printer-Subscription /',
               'D [02/Feb/2010:12:52:15 +0900] cupsdCreateSubscription(con=0xb8fae218(11), uri="/")',
               'D [02/Feb/2010:12:52:15 +0900] pullmethod="ippget"',
               'D [02/Feb/2010:12:52:15 +0900] notify-lease-duration=86400',
               'D [02/Feb/2010:12:52:15 +0900] notify-time-interval=0',
               'D [02/Feb/2010:12:52:15 +0900] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [02/Feb/2010:12:52:15 +0900] Added subscription 9 for server',
               'D [02/Feb/2010:12:52:15 +0900] cupsdMarkDirty(-----S)',
               'D [02/Feb/2010:12:52:15 +0900] cupsdSetBusyState: Active clients and dirty files',
               'D [02/Feb/2010:12:52:15 +0900] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [02/Feb/2010:12:52:15 +0900] cupsdSetBusyState: Dirty files',
               'D [02/Feb/2010:12:52:16 +0900] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:16 +0900] cupsdSetBusyState: Active clients and dirty files',
               'D [02/Feb/2010:12:52:16 +0900] cupsdAuthorize: No authentication data provided.',
               'D [02/Feb/2010:12:52:16 +0900] cupsdReadClient: 11 1.1 Get-Notifications 1',
               'D [02/Feb/2010:12:52:16 +0900] Get-Notifications /',
               'D [02/Feb/2010:12:52:16 +0900] cupsdIsAuthorized: requesting-user-name="sean"',
               'D [02/Feb/2010:12:52:16 +0900] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [02/Feb/2010:12:52:16 +0900] cupsdSetBusyState: Dirty files',
               'D [02/Feb/2010:12:52:23 +0900] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [02/Feb/2010:12:52:23 +0900] cupsdReadClient: 14 POST /printers/Photosmart_C6100 HTTP/1.1',
               'D [02/Feb/2010:12:52:23 +0900] cupsdSetBusyState: Active clients and dirty files',
               'D [02/Feb/2010:12:52:23 +0900] cupsdAuthorize: No authentication data provided.',
               'D [02/Feb/2010:12:52:23 +0900] cupsdReadClient: 14 1.1 Print-Job 1',
               'D [02/Feb/2010:12:52:23 +0900] Print-Job ipp://localhost/printers/Photosmart_C6100',
               'D [02/Feb/2010:12:52:23 +0900] [Job ???] Auto-typing file...',
               'I [02/Feb/2010:12:52:23 +0900] [Job ???] Request file type is application/vnd.cups-banner.',
               'D [02/Feb/2010:12:52:23 +0900] cupsdMarkDirty(----J-)',
               'D [02/Feb/2010:12:52:23 +0900] add_job: requesting-user-name="sean"',
               'D [02/Feb/2010:12:52:23 +0900] Adding default job-sheets values "none,none"...',
               'I [02/Feb/2010:12:52:23 +0900] [Job 4] Adding start banner page "none".',
               'D [02/Feb/2010:12:52:23 +0900] cupsdMarkDirty(-----S)',
               'D [02/Feb/2010:12:52:23 +0900] cupsdMarkDirty(----J-)',
               'I [02/Feb/2010:12:52:23 +0900] [Job 4] Adding end banner page "none".',
               'I [02/Feb/2010:12:52:23 +0900] [Job 4] File of type application/vnd.cups-banner queued by "sean".',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] hold_until=0',
               'I [02/Feb/2010:12:52:23 +0900] [Job 4] Queued on "Photosmart_C6100" by "sean".',
               'D [02/Feb/2010:12:52:23 +0900] cupsdMarkDirty(----J-)',
               'D [02/Feb/2010:12:52:23 +0900] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [02/Feb/2010:12:52:23 +0900] cupsdMarkDirty(-----S)',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] job-sheets=none,none',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] argv[0]="Photosmart_C6100"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] argv[1]="4"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] argv[2]="sean"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] argv[3]="Test Page"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] argv[4]="1"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] argv[5]="job-uuid=urn:uuid:d3d0fa5b-5a34-39da-4b80-db6d13321afe job-originating-host-name=localhost"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] argv[6]="/var/spool/cups/d00004-001"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[8]="HOME=/var/spool/cups/tmp"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[10]="SERVER_ADMIN=root@sean-desktop"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[11]="SOFTWARE=CUPS/1.4.1"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[12]="TMPDIR=/var/spool/cups/tmp"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[13]="TZ=Asia/Seoul"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[14]="USER=root"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[16]="CUPS_ENCRYPTION=IfRequested"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[17]="IPP_PORT=631"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[18]="CHARSET=utf-8"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[19]="LANG=en_US.UTF-8"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[20]="PPD=/etc/cups/ppd/Photosmart_C6100.ppd"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[21]="RIP_MAX_CACHE=1548046k"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[23]="DEVICE_URI=hp:/net/Photosmart_C6100_series?zc=HP4A8D1B"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[24]="PRINTER_INFO=Photosmart_C6100"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[25]="PRINTER_LOCATION="',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[26]="PRINTER=Photosmart_C6100"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[27]="CUPS_FILETYPE=document"',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] envp[28]="FINAL_CONTENT_TYPE=printer/Photosmart_C6100"',
               'I [02/Feb/2010:12:52:23 +0900] [Job 4] Started filter /usr/lib/cups/filter/bannertops (PID 6761)',
               'I [02/Feb/2010:12:52:23 +0900] [Job 4] Started filter /usr/lib/cups/filter/pstopdf (PID 6762)',
               'I [02/Feb/2010:12:52:23 +0900] [Job 4] Started filter /usr/lib/cups/filter/pdftopdf (PID 6763)',
               'I [02/Feb/2010:12:52:23 +0900] [Job 4] Started filter /usr/lib/cups/filter/foomatic-rip (PID 6764)',
               'I [02/Feb/2010:12:52:23 +0900] [Job 4] Started backend /usr/lib/cups/backend/hp (PID 6765)',
               'D [02/Feb/2010:12:52:23 +0900] cupsdMarkDirty(-----S)',
               'D [02/Feb/2010:12:52:23 +0900] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/Photosmart_C6100) from localhost',
               'D [02/Feb/2010:12:52:23 +0900] cupsdSetBusyState: Printing jobs and dirty files',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Getting input from file',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] foomatic-rip version 4.0.3.215 running...',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Parsing PPD file ...',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Added option Resolution',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Added option PageSize',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Added option Model',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Added option PrintoutMode',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Added option InputSlot',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Added option Duplex',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Added option DryTime',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] pstopdf 5 args: 4 sean Test Page 1 job-uuid=urn:uuid:d3d0fa5b-5a34-39da-4b80-db6d13321afe job-originating-host-name=localhost',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] PPD: /etc/cups/ppd/Photosmart_C6100.ppd',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Added option Quality',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Added option ImageableArea',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Added option PaperDimension',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Added option Font',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4]',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Parameter Summary',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] -----------------',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4]',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Spooler: cups',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Printer: Photosmart_C6100',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Shell: /bin/bash',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] PPD file: /etc/cups/ppd/Photosmart_C6100.ppd',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] ATTR file:',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Printer model: HP Photosmart c6100 Series hpijs, 3.9.8',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Job title: Test Page',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] File(s) to be printed:',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] <STDIN>',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4]',
               "D [02/Feb/2010:12:52:23 +0900] [Job 4] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts",
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Printing system options:',
               "D [02/Feb/2010:12:52:23 +0900] [Job 4] Pondering option 'job-uuid=urn:uuid:d3d0fa5b-5a34-39da-4b80-db6d13321afe'",
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Unknown option job-uuid=urn:uuid:d3d0fa5b-5a34-39da-4b80-db6d13321afe.',
               "D [02/Feb/2010:12:52:23 +0900] [Job 4] Pondering option 'job-originating-host-name=localhost'",
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Unknown option job-originating-host-name=localhost.',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Options from the PPD file:',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4]',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] ================================================',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4]',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] File: <STDIN>',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4]',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] ================================================',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4]',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] load_banner(filename="/var/spool/cups/d00004-001")',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Page = 612x792; 18,36 to 594,783',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] PNG image: 192x128x8, color_type=2 (RGB)',
               'D [02/Feb/2010:12:52:23 +0900] PID 6761 (/usr/lib/cups/filter/bannertops) exited with no errors.',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Resolution: 1200',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Page size: letter',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Width: , height: , absolute margins: 0, 0, ,',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Relative margins: , , ,',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] PPD options: -r1200',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] PostScript to be injected:',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer -dDoNumCopies -r1200 - -',
               'D [02/Feb/2010:12:52:23 +0900] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [02/Feb/2010:12:52:23 +0900] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [02/Feb/2010:12:52:23 +0900] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:23 +0900] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [02/Feb/2010:12:52:23 +0900] cupsdAuthorize: No authentication data provided.',
               'D [02/Feb/2010:12:52:23 +0900] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:23 +0900] cupsdAuthorize: No authentication data provided.',
               'D [02/Feb/2010:12:52:23 +0900] cupsdReadClient: 16 1.1 Get-Jobs 1',
               'D [02/Feb/2010:12:52:23 +0900] Get-Jobs ipp://localhost/printers/',
               'D [02/Feb/2010:12:52:23 +0900] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [02/Feb/2010:12:52:23 +0900] cupsdReadClient: 17 1.1 Get-Notifications 1',
               'D [02/Feb/2010:12:52:23 +0900] Get-Notifications /',
               'D [02/Feb/2010:12:52:23 +0900] cupsdIsAuthorized: requesting-user-name="sean"',
               'D [02/Feb/2010:12:52:23 +0900] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [02/Feb/2010:12:52:23 +0900] cupsdSetBusyState: Printing jobs and dirty files',
               'D [02/Feb/2010:12:52:23 +0900] cupsdReadClient: 17 WAITING Closing on EOF',
               'D [02/Feb/2010:12:52:23 +0900] cupsdCloseClient: 17',
               'D [02/Feb/2010:12:52:23 +0900] cupsdReadClient: 16 WAITING Closing on EOF',
               'D [02/Feb/2010:12:52:23 +0900] cupsdCloseClient: 16',
               'D [02/Feb/2010:12:52:23 +0900] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [02/Feb/2010:12:52:23 +0900] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:23 +0900] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [02/Feb/2010:12:52:23 +0900] cupsdAuthorize: No authentication data provided.',
               'D [02/Feb/2010:12:52:23 +0900] [Job 4] GPL Ghostscript 8.70: Set UseCIEColor for UseDeviceIndependentColor to work properly.',
               'D [02/Feb/2010:12:52:23 +0900] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [02/Feb/2010:12:52:23 +0900] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:23 +0900] cupsdAuthorize: No authentication data provided.',
               'D [02/Feb/2010:12:52:23 +0900] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:23 +0900] cupsdAuthorize: Authorized as sean using PeerCred',
               'D [02/Feb/2010:12:52:23 +0900] cupsdReadClient: 11 1.1 Get-Notifications 1',
               'D [02/Feb/2010:12:52:23 +0900] Get-Notifications /',
               'D [02/Feb/2010:12:52:23 +0900] cupsdIsAuthorized: requesting-user-name="sean"',
               'D [02/Feb/2010:12:52:23 +0900] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [02/Feb/2010:12:52:23 +0900] cupsdReadClient: 16 1.1 Get-Notifications 1',
               'D [02/Feb/2010:12:52:23 +0900] Get-Notifications /',
               'D [02/Feb/2010:12:52:23 +0900] cupsdIsAuthorized: requesting-user-name="sean"',
               'D [02/Feb/2010:12:52:23 +0900] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [02/Feb/2010:12:52:23 +0900] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1',
               'D [02/Feb/2010:12:52:23 +0900] CUPS-Get-Printers',
               'D [02/Feb/2010:12:52:23 +0900] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [02/Feb/2010:12:52:23 +0900] cupsdSetBusyState: Printing jobs and dirty files',
               'D [02/Feb/2010:12:52:23 +0900] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:23 +0900] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [02/Feb/2010:12:52:23 +0900] cupsdAuthorize: No authentication data provided.',
               'D [02/Feb/2010:12:52:23 +0900] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:23 +0900] cupsdAuthorize: Authorized as sean using PeerCred',
               'D [02/Feb/2010:12:52:23 +0900] cupsdReadClient: 16 1.1 Get-Job-Attributes 1',
               'D [02/Feb/2010:12:52:23 +0900] Get-Job-Attributes ipp://localhost/jobs/4',
               'D [02/Feb/2010:12:52:23 +0900] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/4) from localhost',
               'D [02/Feb/2010:12:52:23 +0900] cupsdReadClient: 17 1.1 CUPS-Get-Classes 1',
               'D [02/Feb/2010:12:52:23 +0900] CUPS-Get-Classes',
               'D [02/Feb/2010:12:52:23 +0900] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [02/Feb/2010:12:52:23 +0900] cupsdSetBusyState: Printing jobs and dirty files',
               'D [02/Feb/2010:12:52:23 +0900] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:23 +0900] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [02/Feb/2010:12:52:23 +0900] cupsdAuthorize: Authorized as sean using PeerCred',
               'D [02/Feb/2010:12:52:23 +0900] cupsdReadClient: 17 1.1 CUPS-Get-Default 1',
               'D [02/Feb/2010:12:52:23 +0900] CUPS-Get-Default',
               'D [02/Feb/2010:12:52:23 +0900] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [02/Feb/2010:12:52:23 +0900] cupsdSetBusyState: Printing jobs and dirty files',
               'D [02/Feb/2010:12:52:23 +0900] cupsdReadClient: 16 WAITING Closing on EOF',
               'D [02/Feb/2010:12:52:23 +0900] cupsdCloseClient: 16',
               'D [02/Feb/2010:12:52:24 +0900] PID 6762 (/usr/lib/cups/filter/pstopdf) exited with no errors.',
               'D [02/Feb/2010:12:52:24 +0900] PID 6763 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [02/Feb/2010:12:52:24 +0900] [Job 4] Filetype: PDF',
               'D [02/Feb/2010:12:52:24 +0900] [Job 4] Storing temporary files in /var/spool/cups/tmp',
               'D [02/Feb/2010:12:52:24 +0900] [Job 4] File contains 1 pages',
               'D [02/Feb/2010:12:52:24 +0900] [Job 4] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="deskjet 5600" -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=2,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-jRh6K6',
               'D [02/Feb/2010:12:52:24 +0900] [Job 4] Starting process "kid3" (generation 1)',
               'D [02/Feb/2010:12:52:24 +0900] [Job 4] Starting process "kid4" (generation 2)',
               'D [02/Feb/2010:12:52:24 +0900] [Job 4] Starting process "renderer" (generation 2)',
               'D [02/Feb/2010:12:52:24 +0900] [Job 4] JCL: \x1b%-12345X@PJL',
               'D [02/Feb/2010:12:52:24 +0900] [Job 4] <job data>',
               'D [02/Feb/2010:12:52:24 +0900] [Job 4]',
               'D [02/Feb/2010:12:52:37 +0900] [Job 4] STATE: +connecting-to-device',
               'D [02/Feb/2010:12:52:37 +0900] cupsdMarkDirty(-----S)',
               'D [02/Feb/2010:12:52:38 +0900] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [02/Feb/2010:12:52:38 +0900] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:38 +0900] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [02/Feb/2010:12:52:38 +0900] cupsdAuthorize: No authentication data provided.',
               'D [02/Feb/2010:12:52:38 +0900] cupsdAcceptClient: 18 from localhost (Domain)',
               'D [02/Feb/2010:12:52:38 +0900] cupsdReadClient: 18 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:38 +0900] cupsdAuthorize: No authentication data provided.',
               'D [02/Feb/2010:12:52:38 +0900] cupsdReadClient: 16 1.1 Get-Jobs 1',
               'D [02/Feb/2010:12:52:38 +0900] Get-Jobs ipp://localhost/printers/',
               'D [02/Feb/2010:12:52:38 +0900] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [02/Feb/2010:12:52:38 +0900] cupsdReadClient: 18 1.1 Get-Notifications 1',
               'D [02/Feb/2010:12:52:38 +0900] Get-Notifications /',
               'D [02/Feb/2010:12:52:38 +0900] cupsdIsAuthorized: requesting-user-name="sean"',
               'D [02/Feb/2010:12:52:38 +0900] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [02/Feb/2010:12:52:38 +0900] cupsdSetBusyState: Printing jobs and dirty files',
               'D [02/Feb/2010:12:52:38 +0900] cupsdReadClient: 16 WAITING Closing on EOF',
               'D [02/Feb/2010:12:52:38 +0900] cupsdCloseClient: 16',
               'D [02/Feb/2010:12:52:38 +0900] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [02/Feb/2010:12:52:38 +0900] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:38 +0900] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [02/Feb/2010:12:52:38 +0900] cupsdAuthorize: No authentication data provided.',
               'D [02/Feb/2010:12:52:38 +0900] cupsdReadClient: 18 WAITING Closing on EOF',
               'D [02/Feb/2010:12:52:38 +0900] cupsdCloseClient: 18',
               'D [02/Feb/2010:12:52:38 +0900] cupsdReadClient: 16 1.1 Get-Notifications 1',
               'D [02/Feb/2010:12:52:38 +0900] Get-Notifications /',
               'D [02/Feb/2010:12:52:38 +0900] cupsdIsAuthorized: requesting-user-name="sean"',
               'D [02/Feb/2010:12:52:38 +0900] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [02/Feb/2010:12:52:38 +0900] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:38 +0900] cupsdAuthorize: No authentication data provided.',
               'D [02/Feb/2010:12:52:38 +0900] cupsdReadClient: 11 1.1 Get-Notifications 1',
               'D [02/Feb/2010:12:52:38 +0900] Get-Notifications /',
               'D [02/Feb/2010:12:52:38 +0900] cupsdIsAuthorized: requesting-user-name="sean"',
               'D [02/Feb/2010:12:52:38 +0900] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [02/Feb/2010:12:52:38 +0900] cupsdSetBusyState: Printing jobs and dirty files',
               'D [02/Feb/2010:12:52:38 +0900] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:38 +0900] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [02/Feb/2010:12:52:38 +0900] cupsdAuthorize: Authorized as sean using PeerCred',
               'D [02/Feb/2010:12:52:38 +0900] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1',
               'D [02/Feb/2010:12:52:38 +0900] CUPS-Get-Printers',
               'D [02/Feb/2010:12:52:38 +0900] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [02/Feb/2010:12:52:38 +0900] cupsdSetBusyState: Printing jobs and dirty files',
               'D [02/Feb/2010:12:52:38 +0900] cupsdReadClient: 16 WAITING Closing on EOF',
               'D [02/Feb/2010:12:52:38 +0900] cupsdCloseClient: 16',
               'D [02/Feb/2010:12:52:38 +0900] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:38 +0900] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [02/Feb/2010:12:52:38 +0900] cupsdAuthorize: Authorized as sean using PeerCred',
               'D [02/Feb/2010:12:52:38 +0900] cupsdReadClient: 17 1.1 CUPS-Get-Classes 1',
               'D [02/Feb/2010:12:52:38 +0900] CUPS-Get-Classes',
               'D [02/Feb/2010:12:52:38 +0900] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [02/Feb/2010:12:52:38 +0900] cupsdSetBusyState: Printing jobs and dirty files',
               'D [02/Feb/2010:12:52:38 +0900] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:38 +0900] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [02/Feb/2010:12:52:38 +0900] cupsdAuthorize: Authorized as sean using PeerCred',
               'D [02/Feb/2010:12:52:38 +0900] cupsdReadClient: 17 1.1 CUPS-Get-Default 1',
               'D [02/Feb/2010:12:52:38 +0900] CUPS-Get-Default',
               'D [02/Feb/2010:12:52:38 +0900] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [02/Feb/2010:12:52:38 +0900] cupsdSetBusyState: Printing jobs and dirty files',
               'I [02/Feb/2010:12:52:46 +0900] Saving job cache file "/var/cache/cups/job.cache"...',
               'I [02/Feb/2010:12:52:46 +0900] Saving subscriptions.conf...',
               'D [02/Feb/2010:12:52:46 +0900] cupsdSetBusyState: Printing jobs',
               'D [02/Feb/2010:12:52:46 +0900] Report: clients=3',
               'D [02/Feb/2010:12:52:46 +0900] Report: jobs=4',
               'D [02/Feb/2010:12:52:46 +0900] Report: jobs-active=1',
               'D [02/Feb/2010:12:52:46 +0900] Report: printers=1',
               'D [02/Feb/2010:12:52:46 +0900] Report: printers-implicit=0',
               'D [02/Feb/2010:12:52:46 +0900] Report: stringpool-string-count=1195',
               'D [02/Feb/2010:12:52:46 +0900] Report: stringpool-alloc-bytes=9072',
               'D [02/Feb/2010:12:52:46 +0900] Report: stringpool-total-bytes=26584',
               'D [02/Feb/2010:12:52:51 +0900] [Job 4] prnt/backend/hp.c 720: ERROR: cannot open device stat=12: hp:/net/Photosmart_C6100_series?zc=HP4A8D1B',
               'D [02/Feb/2010:12:52:51 +0900] PID 6765 (/usr/lib/cups/backend/hp) stopped with status 1!',
               'D [02/Feb/2010:12:52:51 +0900] [Job 4] renderer exited with status 0',
               'D [02/Feb/2010:12:52:51 +0900] [Job 4] kid4 exited with status 0',
               'D [02/Feb/2010:12:52:51 +0900] [Job 4] kid3 finished',
               'D [02/Feb/2010:12:52:51 +0900] [Job 4] Kid3 exit status: 0',
               'D [02/Feb/2010:12:52:51 +0900] [Job 4]',
               'D [02/Feb/2010:12:52:51 +0900] [Job 4] Closing foomatic-rip.',
               'D [02/Feb/2010:12:52:51 +0900] PID 6764 (/usr/lib/cups/filter/foomatic-rip) exited with no errors.',
               'I [02/Feb/2010:12:52:51 +0900] [Job 4] Backend returned status 1 (failed)',
               'D [02/Feb/2010:12:52:51 +0900] set_hold_until: hold_until = 1265083071',
               'D [02/Feb/2010:12:52:51 +0900] cupsdMarkDirty(----J-)',
               'D [02/Feb/2010:12:52:51 +0900] cupsdSetBusyState: Printing jobs and dirty files',
               'D [02/Feb/2010:12:52:51 +0900] cupsdMarkDirty(-----S)',
               'D [02/Feb/2010:12:52:52 +0900] cupsdAcceptClient: 15 from localhost (Domain)',
               'D [02/Feb/2010:12:52:52 +0900] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [02/Feb/2010:12:52:52 +0900] cupsdReadClient: 15 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:52 +0900] cupsdSetBusyState: Active clients and dirty files',
               'D [02/Feb/2010:12:52:52 +0900] cupsdAuthorize: No authentication data provided.',
               'D [02/Feb/2010:12:52:52 +0900] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:52 +0900] cupsdAuthorize: No authentication data provided.',
               'D [02/Feb/2010:12:52:52 +0900] cupsdReadClient: 15 1.1 Get-Notifications 1',
               'D [02/Feb/2010:12:52:52 +0900] Get-Notifications /',
               'D [02/Feb/2010:12:52:52 +0900] cupsdIsAuthorized: requesting-user-name="sean"',
               'D [02/Feb/2010:12:52:52 +0900] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [02/Feb/2010:12:52:52 +0900] cupsdReadClient: 16 1.1 Get-Jobs 1',
               'D [02/Feb/2010:12:52:52 +0900] Get-Jobs ipp://localhost/printers/',
               'D [02/Feb/2010:12:52:52 +0900] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [02/Feb/2010:12:52:52 +0900] cupsdSetBusyState: Dirty files',
               'D [02/Feb/2010:12:52:52 +0900] cupsdReadClient: 15 WAITING Closing on EOF',
               'D [02/Feb/2010:12:52:52 +0900] cupsdCloseClient: 15',
               'D [02/Feb/2010:12:52:52 +0900] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:52 +0900] cupsdSetBusyState: Active clients and dirty files',
               'D [02/Feb/2010:12:52:52 +0900] cupsdAuthorize: No authentication data provided.',
               'D [02/Feb/2010:12:52:52 +0900] cupsdReadClient: 16 WAITING Closing on EOF',
               'D [02/Feb/2010:12:52:52 +0900] cupsdCloseClient: 16',
               'D [02/Feb/2010:12:52:52 +0900] cupsdAcceptClient: 15 from localhost (Domain)',
               'D [02/Feb/2010:12:52:52 +0900] cupsdReadClient: 15 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:52 +0900] cupsdAuthorize: No authentication data provided.',
               'D [02/Feb/2010:12:52:52 +0900] cupsdReadClient: 11 1.1 Get-Notifications 1',
               'D [02/Feb/2010:12:52:52 +0900] Get-Notifications /',
               'D [02/Feb/2010:12:52:52 +0900] cupsdIsAuthorized: requesting-user-name="sean"',
               'D [02/Feb/2010:12:52:52 +0900] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [02/Feb/2010:12:52:52 +0900] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:52 +0900] cupsdAuthorize: Authorized as sean using PeerCred',
               'D [02/Feb/2010:12:52:52 +0900] cupsdReadClient: 15 1.1 Get-Notifications 1',
               'D [02/Feb/2010:12:52:52 +0900] Get-Notifications /',
               'D [02/Feb/2010:12:52:52 +0900] cupsdIsAuthorized: requesting-user-name="sean"',
               'D [02/Feb/2010:12:52:52 +0900] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [02/Feb/2010:12:52:52 +0900] cupsdReadClient: 17 1.1 CUPS-Get-Printers 1',
               'D [02/Feb/2010:12:52:52 +0900] CUPS-Get-Printers',
               'D [02/Feb/2010:12:52:52 +0900] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [02/Feb/2010:12:52:52 +0900] cupsdSetBusyState: Dirty files',
               'D [02/Feb/2010:12:52:52 +0900] cupsdReadClient: 15 WAITING Closing on EOF',
               'D [02/Feb/2010:12:52:52 +0900] cupsdCloseClient: 15',
               'D [02/Feb/2010:12:52:52 +0900] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:52 +0900] cupsdSetBusyState: Active clients and dirty files',
               'D [02/Feb/2010:12:52:52 +0900] cupsdAuthorize: Authorized as sean using PeerCred',
               'D [02/Feb/2010:12:52:52 +0900] cupsdReadClient: 17 1.1 CUPS-Get-Classes 1',
               'D [02/Feb/2010:12:52:52 +0900] CUPS-Get-Classes',
               'D [02/Feb/2010:12:52:52 +0900] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [02/Feb/2010:12:52:52 +0900] cupsdSetBusyState: Dirty files',
               'D [02/Feb/2010:12:52:52 +0900] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [02/Feb/2010:12:52:52 +0900] cupsdSetBusyState: Active clients and dirty files',
               'D [02/Feb/2010:12:52:52 +0900] cupsdAuthorize: Authorized as sean using PeerCred',
               'D [02/Feb/2010:12:52:52 +0900] cupsdReadClient: 17 1.1 CUPS-Get-Default 1',
               'D [02/Feb/2010:12:52:52 +0900] CUPS-Get-Default',
               'D [02/Feb/2010:12:52:52 +0900] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [02/Feb/2010:12:52:52 +0900] cupsdSetBusyState: Dirty files',
               'I [02/Feb/2010:12:53:22 +0900] Saving job cache file "/var/cache/cups/job.cache"...',
               'I [02/Feb/2010:12:53:22 +0900] Saving subscriptions.conf...',
               'D [02/Feb/2010:12:53:22 +0900] cupsdSetBusyState: Not busy',
               'D [02/Feb/2010:12:53:22 +0900] [Job 1] Unloading...',
               'D [02/Feb/2010:12:53:22 +0900] [Job 2] Unloading...',
               'D [02/Feb/2010:12:53:22 +0900] [Job 3] Unloading...',
               'D [02/Feb/2010:12:53:24 +0900] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [02/Feb/2010:12:53:24 +0900] cupsdSetBusyState: Active clients',
               'D [02/Feb/2010:12:53:24 +0900] cupsdAuthorize: No authentication data provided.',
               'D [02/Feb/2010:12:53:24 +0900] cupsdReadClient: 11 1.1 Get-Job-Attributes 1',
               'D [02/Feb/2010:12:53:24 +0900] Get-Job-Attributes ipp://localhost/jobs/4',
               'D [02/Feb/2010:12:53:24 +0900] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/4) from localhost',
               'D [02/Feb/2010:12:53:24 +0900] cupsdSetBusyState: Not busy',
               'D [02/Feb/2010:12:53:24 +0900] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [02/Feb/2010:12:53:24 +0900] cupsdSetBusyState: Active clients',
               'D [02/Feb/2010:12:53:24 +0900] cupsdAuthorize: No authentication data provided.',
               'D [02/Feb/2010:12:53:24 +0900] cupsdReadClient: 11 1.1 Cancel-Subscription 1',
               'D [02/Feb/2010:12:53:24 +0900] Cancel-Subscription /',
               'D [02/Feb/2010:12:53:24 +0900] cupsdIsAuthorized: requesting-user-name="sean"',
               'D [02/Feb/2010:12:53:24 +0900] cupsdMarkDirty(-----S)',
               'D [02/Feb/2010:12:53:24 +0900] cupsdSetBusyState: Active clients and dirty files',
               'D [02/Feb/2010:12:53:24 +0900] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [02/Feb/2010:12:53:24 +0900] cupsdSetBusyState: Dirty files',
               'D [02/Feb/2010:12:53:24 +0900] cupsdAcceptClient: 15 from localhost (Domain)',
               'D [02/Feb/2010:12:53:24 +0900] cupsdReadClient: 15 GET /admin/log/error_log HTTP/1.1',
               'D [02/Feb/2010:12:53:24 +0900] cupsdSetBusyState: Active clients and dirty files',
               'D [02/Feb/2010:12:53:24 +0900] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 11 (Locale issues):
{'printer_page_size': u'letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}



---

### Post by createsean on 2010-02-03
Anyone? would really like to print.

---

### Post by dmurphy787 on 2010-08-29
I also have my printer detected but when I print it says that there is a communication error.  I have restarted checked updates but I do not know what else to do.  I am new and would also appreciate any help.   :D

---

### Post by mirchichamu on 2010-09-05
> **dmurphy787 said:**
> I also have my printer detected but when I print it says that there is a communication error.  I have restarted checked updates but I do not know what else to do.  I am new and would also appreciate any help.   :D

Hi,
I was having the same problem of 5012 error. It would print one page and again the same error. I changed my router and everything became alright. If still has any problem, then click on the hp icon and delete all your printers and reinstall again. Make sure you select the correct mode of printer like USB, wired or wireless network printer.

---

### Post by LinuxVictim on 2011-02-06
Hi, I had a similar problem with a very new HP LaserJet P1102.

The driver support for this model has only just been added to Maverick.
I am using lucid, so I had to install it with the HP installer.
This worked, but it had reliability problems, (device communication error...) so I thought I'd update the driver.
I am now running 3.11.1.

Note that I didn't remove the printer from the installed printers.

After following the install procedures, the printer constantly replied with Communication Error 5012.
I did the reboot/reconnect thing: no improvement.

The solution was:
[B]
(Upgrade the HPLIP driver as mentioned.)
Remove the printer in the ubuntu printer settings.[/B]

Then it got detected almost instantaneously.
Maybe throw in another reconnect/reboot.

This now works reliably.

The only problem with it, is that it's id has now changed, so all network printer installations have to be updated. *sigh*

Anyway, maybe this helps someone.

---

### Post by profgus on 2011-06-19
I also had the 5012 communication error, with an HP L7680 all-in-one printer.

The (final) fix was to enable SNMP (Simple Network Management Protocol) on the printer via the printer's web interface. To get to the latter, (one way) is to enter its IP address into a browser. 

[You can get the IP address directly from the printer via its own physical screen. Press the Setup button on the panel, then drill down through network options, and select the display network information option. Can
't access it right now or I'd be more specific.]

Click: Network>SNMP
then select the: "                                          Enable SNMPv1 Read-Write Access" radio button. (It might also work with the read-only option, I didn't try it.)

Good Luck!

---

### Post by ragesh.g on 2011-08-03
I'm using hp laserjet M1132MFP and getting the same error. But This connection is local usb connection. These are the errors I got when I run the following command. Please help guys.

[ragesh@ragesh ~]$ hp-check -t

HP Linux Imaging and Printing System (ver. 3.11.7)
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
Linux ragesh.datstruct.com 2.6.38.8-35.fc15.i686 #1 SMP Wed Jul 6 14:46:26 UTC 2011 i686 i686 i386 GNU/Linux

Distribution:
fedora 15

Checking Python version...
OK, version 2.7.1 installed

Checking PyQt 4.x version...
OK, version 4.8.3 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.4.7
error_log is set to level: debug

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
HPLIP 3.11.7 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.11.7

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/cups/model/HP
ppdbase=/usr/share/cups/model
doc=/usr/share/doc/hplip-3.11.7
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
internal-tag=3.11.7
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=no
hpijs-only-build=no
lite-build=no
udev-acl-rules=no
hpcups-only-build=no
hpijs-only-build=no


Current contents of '/var/lib/hp/hplip.state' file:
[plugin]
installed = 1
eula = 1



Current contents of '~/.hplip/hplip.conf' file:
[installation]
date_time = 08/03/2011 13:49:30
version = 3.11.7

[settings]
systray_visible = 0
systray_messages = 0

[last_used]
device_uri = "hp:/usb/HP_LaserJet_Professional_M1132_MFP?serial=000000000QH41P3BSI1c"
printer_name = HP-LaserJet-Professional-M1132-MFP
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

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
HP-LaserJet-Professional-M1132-MFP
----------------------------------
Type: Printer
Device URI: hp:/usb/HP_LaserJet_Professional_M1132_MFP?serial=000000000QH41P3BSI1c
PPD: /etc/cups/ppd/HP-LaserJet-Professional-M1132-MFP.ppd
PPD Description: HP LaserJet Professional m1132 MFP, hpcups 3.11.7, requires proprietary plugin
Printer status: printer HP-LaserJet-Professional-M1132-MFP disabled since Tue 02 Aug 201Rendering completed
Required plug-in status: Installed
error: Unable to communicate with device (code=12): hp:/usb/HP_LaserJet_Professional_M1132_MFP?serial=000000000QH41P3BSI1c
error: Device not found
error: Communication status: Failed

HP_LaserJet_Professional_M1132_MFP
----------------------------------
Type: Printer
Device URI: hp:/usb/HP_LaserJet_Professional_M1132_MFP?serial=000000000QH41P3BSI1c
PPD: /etc/cups/ppd/HP_LaserJet_Professional_M1132_MFP.ppd
PPD Description: HP LaserJet Professional m1132 MFP, hpcups 3.11.7, requires proprietary plugin
Printer status: printer HP_LaserJet_Professional_M1132_MFP disabled since Wed 03 Aug 201Rendering completed
Required plug-in status: Installed
error: Unable to communicate with device (code=12): hp:/usb/HP_LaserJet_Professional_M1132_MFP?serial=000000000QH41P3BSI1c
error: Device not found
error: Communication status: Failed


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

HP Device 0x42a at 001:003: 
    Device URI: hp:/usb/HP_LaserJet_Professional_M1132_MFP?serial=000000000QH41P3BSI1c
    Device node: /dev/bus/usb/001/003
    Mode: 0660
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/001/003
# owner: root
# group: lp
user::rw-
user:ragesh:rw-
group::rw-
mask::rw-
other::---



---------------
| USER GROUPS |
---------------

ragesh sys lp wheel


-----------
| SUMMARY |
-----------

error: 2 errors and/or warnings.

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.

---

### Post by rabicula on 2011-09-28
Hi,

Had the same problems and every solution I found in the forums didn't work. I think it was related with the way hplip tries to find the printer on the network.
Anyway, I tried this: hp-setup -i <your_printer_ip_address> and it worked! Thought I had to share this. 

> **Rayaz said:**
> Hi

Right click on the network manager icon in the system tray. From there  select "Edit Connections".

Hope this helps.

---

### Post by Ralph L on 2012-06-11
I did what rabicula did.  It also worked for me.  I discovered that the hp-setup (no parameters) GUI and ```
hp-toolbox
``` both set the printer URI to &#8220;hp:/net/Photosmart_C6100_series?zc=HP547597&#8221; rather than to &#8220;hp:/net/Photosmart_C6100_series?ip=192.168.0.31&#8221; as it should be.  On Lucid you can go to Main menu>System>Administration>Printing (system-config-printing if you need to install it with Synaptic) and change this.  Right click on the printer icon, select Properties and edit the URI box.  For the printer (not for a printer/fax) you can also set the URI to "socket://<your printer URL>:9100" and it will work.  However, if you have a printer/fax you need to use &#8220;hp:/net/Photosmart_C6100_series?zc=HP547597&#8221;.  Also the fax device (the icon Properties) must have a Make/Model of &#8220;HP Fax hpcups&#8221;.  This cannot be changed with system-config-printing.  The only way I found to get the fax to work was to use 
```
hp-setup -i 192.168.0.31
```
or to use the hp-toolbox GUI.  The toolbox sets the URI wrong, but it can be corrected in system-config-printing.  The Model/Make parameters are set correctly by toolbox.  Note that my printer URL is 192.168.0.31.  Yours will be different.

I am about to try this same setup on Precise Pangolin 12.04.

Hope this helps somebody.

---

