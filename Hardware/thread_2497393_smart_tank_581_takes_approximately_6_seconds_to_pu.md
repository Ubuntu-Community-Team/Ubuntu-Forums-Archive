---
title: "smart tank 581 takes approximately 6 seconds to pull and print the next page"
date: 2024-05-03
forum: Hardware
---

### Post by FzDAsFc on 2024-05-03
Kubuntu 22.04
HP Smart Tank 581
Driver: Current - HP Smart Tank 580-590 Series, hpcups 3.23.12
Problem: when printing any document with more than 2 pages, when you finish printing a page, it takes approximately 6 seconds to pull the next page to be printed, and so on page after page. As I have dual boot, when I print the same document in Windows 10 it pulls the page immediately after the previous one has been printed.
On the same Kubuntu 22.04, when printing the same document on another printer, be it the Canon G3010 or the Epson T25, the next page is pulled immediately.
Below the comand:
[COLOR=#000000][FONT=&amp]gomide@gomide-desktop:~$ hp-check -t
/usr/bin/hp-check:685: SyntaxWarning: "is not" with a literal. Did you mean "!="?
  if 'getfacl' not in g and '' is not g and 'file' not in g:
Saving output in log file: /home/gomide/hp-check.log[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]HP Linux Imaging and Printing System (ver. 3.23.12)
Dependency/Version Check Utility ver. 15.1[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the HPLIP supplied tarball (.tar.gz or .run) to
determine if the proper dependencies are installed to successfully compile HPLIP.
2. Run-time check mode (-r or --run): Use this mode to determine if a distro supplied package (.deb, .rpm, etc) or an already built
HPLIP supplied tarball has the proper dependencies installed to successfully run.
3. Both compile- and run-time check mode (-b or --both) (Default): This mode will check both of the above cases (both compile- and
run-time dependencies).[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Check types:
a. EXTERNALDEP - External Dependencies
b. GENERALDEP - General Dependencies (required both at compile and run time)
c. COMPILEDEP - Compile time Dependencies
d. [All are run-time checks]
PYEXT SCANCONF QUEUES PERMISSION[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Status Types:
    OK
    MISSING - Missing Dependency or Permission or Plug-in
    INCOMPAT - Incompatible dependency-version or Plugin-version[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]---------------
| SYSTEM INFO |
---------------[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp] Kernel: 6.5.0-28-generic #29~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Thu Apr 4 14:39:20 UTC 2 GNU/Linux
 Host: gomide-desktop
 Proc: 6.5.0-28-generic #29~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Thu Apr 4 14:39:20 UTC 2 GNU/Linux
 Distribution: 12 22.04
 Bitness: 64 bit[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]-----------------------
| HPLIP CONFIGURATION |
-----------------------[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]HPLIP-Version: HPLIP 3.23.12
HPLIP-Home: /usr/share/hplip
HPLIP-Installation: Auto installation is supported for ubuntu distro 22.04 version[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf. Generated from hplip.conf.in by configure.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][hplip]
version=3.23.12[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.23.12
html=/usr/share/doc/hplip-3.23.12
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp
bin=/usr/bin
apparmor=/etc/apparmor.d
# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
libusb01-build=no
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
internal-tag=3.23.12
restricted-build=no
ui-toolkit=qt5
qt3=no
qt4=no
qt5=yes
policy-kit=no
lite-build=no
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no
apparmor_build=yes
class-driver=no[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Current contents of '/var/lib/hp/hplip.state' file:
[plugin]
installed = 1
eula = 1
version = 3.23.12[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Current contents of '~/.hplip/hplip.conf' file:
[upgrade]
notify_upgrade = true
last_upgraded_time = 1711188772
pending_upgrade_time = 0
latest_available_version = 3.23.1[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][installation]
date_time = 04/30/24 05:39:48
version = 3.23.12[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp] <Package-name> <Package-Desc> <Required/Optional> <Min-Version> <Installed-Version> <Status> <Comment>[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]-------------------------
| External Dependencies |
-------------------------[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp] cups CUPS - Common Unix Printing System REQUIRED 1.1 2.4.1 OK 'CUPS Scheduler is running'
 gs GhostScript - PostScript and PDF language interpreter and previewer REQUIRED 7.05 9.55.0 OK -
 xsane xsane - Graphical scanner frontend for SANE OPTIONAL 0.9 0.999 OK -
 scanimage scanimage - Shell scanning program OPTIONAL 1.0 1.1.1 OK -
 dbus DBus - Message bus system REQUIRED - 1.12.20 OK -
 policykit PolicyKit - Administrative policy framework OPTIONAL - 0.105 OK -
 network network -wget OPTIONAL - 1.21.2 OK -
 avahi-utils avahi-utils OPTIONAL - 0.8 OK -[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]------------------------
| General Dependencies |
------------------------[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp] libjpeg libjpeg - JPEG library REQUIRED - - OK -
 cups-devel CUPS devel- Common Unix Printing System development files REQUIRED - 2.4.1 OK -
 cups-image CUPS image - CUPS image development files REQUIRED - 2.4.1 OK -
 libpthread libpthread - POSIX threads library REQUIRED - b'2.36' OK -
 libusb libusb - USB library REQUIRED - 1.0 OK -
 sane SANE - Scanning library REQUIRED - - OK -
 sane-devel SANE - Scanning library development files REQUIRED - - OK -
 libavahi-dev libavahi-dev REQUIRED - - OK -
 libnetsnmp-devel libnetsnmp-devel - SNMP networking library development files REQUIRED 5.0.9 5.9.1 OK -
 libcrypto libcrypto - OpenSSL cryptographic library REQUIRED - 3.0.2 OK -
 python3X Python 2.2 or greater - Python programming language REQUIRED 2.2 3.10.12 OK -
 python3-notify2 Python libnotify - Python bindings for the libnotify Desktop notifications OPTIONAL - - OK -
 python3-pyqt5-dbus PyQt 5 DBus - DBus Support for PyQt5 OPTIONAL 5.0 5.15.6 OK -
 python3-pyqt5 PyQt 5- Qt interface for Python (for Qt version 4.x) REQUIRED 5.0 5.15.6 OK -
 python3-dbus Python DBus - Python bindings for DBus REQUIRED 0.80.0 1.2.18 OK -
 python3-xml Python XML libraries REQUIRED - 2.4.7 OK -
 python3-devel Python devel - Python development files REQUIRED 2.2 3.10.12 OK -
 python3-pil PIL - Python Imaging Library (required for commandline scanning with hp-scan) OPTIONAL - 10.2.0 OK -
 python3-reportlab Reportlab - PDF library for Python OPTIONAL 2.0 3.6.8 OK -[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]--------------
| COMPILEDEP |
--------------[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp] libtool libtool - Library building support services REQUIRED - 2.4.6 OK -
 gcc gcc - GNU Project C and C++ Compiler REQUIRED - 11.4.0 OK -
 make make - GNU make utility to maintain groups of programs REQUIRED 3.0 4.3 OK -[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]---------------------
| Python Extentions |
---------------------[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp] cupsext CUPS-Extension REQUIRED - 3.23.12 OK -
 hpmudext IO-Extension REQUIRED - 3.23.12 OK -[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]----------------------
| Scan Configuration |
----------------------[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp] hpaio HPLIP-SANE-Backend REQUIRED - 3.23.12 OK 'hpaio found in /etc/sane.d/dll.conf'
 scanext Scan-SANE-Extension REQUIRED - 3.23.12 OK -[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]device `hpaio:/net/Smart_Tank_580-590_series?ip=192.168.0.134' is a Hewlett-Packard Smart_Tank_580-590_series all-in-one
device `escl:[https://192.168.0.134:443]("https://192.168.0.134/")' is a HP Smart Tank 580-590 series [E2A044] platen scanner
device `airscan:w2:Canon G3010 series' is a WSD Canon G3010 series ip=192.168.0.183
device `airscan:e0:HP Smart Tank 580-590 series [E2A044]' is a eSCL HP Smart Tank 580-590 series [E2A044] ip=192.168.0.134
device `hpaio:/net/Smart_Tank_580-590_series?ip=192.168.0.134' is a Hewlett-Packard Smart_Tank_580-590_series all-in-one
device `escl:[https://192.168.0.134:443]("https://192.168.0.134/")' is a HP Smart Tank 580-590 series [E2A044] platen scanner
device `airscan:w2:Canon G3010 series' is a WSD Canon G3010 series ip=192.168.0.183
device `airscan:e0:HP Smart Tank 580-590 series [E2A044]' is a eSCL HP Smart Tank 580-590 series [E2A044] ip=192.168.0.134[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]--------------------------
| DISCOVERED USB DEVICES |
--------------------------[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]No devices found.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Canon_G3010_series
------------------
Type: Unknown
Device URI: dnssd://Canon%20G3010%20series._ipp._tcp.local/?uuid=00000000-0000-1000-8000-00183b0a407c
PPD: /etc/cups/ppd/Canon_G3010_series.ppd
warning: Failed to read /etc/cups/ppd/Canon_G3010_series.ppd ppd file
PPD Description:
Printer status: impressora Canon_G3010_series está inativa; habilitada desde seg 29 abr 2024 11:44:04
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend for HP-Devices.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Canon_G3010_series@7FE1D6000000.local
-------------------------------------
Type: Unknown
Device URI: dnssd://Canon%20G3010%20series._ipp._tcp.local/?uuid=00000000-0000-1000-8000-00183b0a407c
PPD: /etc/cups/ppd/Canon_G3010_series@7FE1D6000000.local.ppd
warning: Failed to read /etc/cups/ppd/Canon_G3010_series@7FE1D6000000.local.ppd ppd file
PPD Description:
Printer status: impressora [EMAIL="Canon_G3010_series@7FE1D6000000.local"]Canon_G3010_series@7FE1D6000000.local[/EMAIL] está inativa; habilitada desde sáb 27 abr 2024 08:27:39
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend for HP-Devices.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Epson_Stylus_T25_Melhor_Cor_Lenta
---------------------------------
Type: Unknown
Device URI: usb://EPSON/Stylus%20T25?serial=ME4Z105791%20%20%20%20%20%20%20%20
PPD: /etc/cups/ppd/Epson_Stylus_T25_Melhor_Cor_Lenta.ppd
warning: Failed to read /etc/cups/ppd/Epson_Stylus_T25_Melhor_Cor_Lenta.ppd ppd file
PPD Description:
Printer Unplugged or turned offn_Stylus_T25_Melhor_Cor_Lenta desabilitada desde seg 29 abr 2024 11:43:20 -
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend for HP-Devices.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Epson_Stylus_T25_Rapida
-----------------------
Type: Unknown
Device URI: usb://EPSON/Stylus%20T25?serial=ME4Z105791%20%20%20%20%20%20%20%20
PPD: /etc/cups/ppd/Epson_Stylus_T25_Rapida.ppd
warning: Failed to read /etc/cups/ppd/Epson_Stylus_T25_Rapida.ppd ppd file
PPD Description:
Printer Unplugged or turned offn_Stylus_T25_Rapida desabilitada desde seg 29 abr 2024 11:43:20 -
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend for HP-Devices.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]HP_Smart_Tank_580-590_series
----------------------------
Type: Unknown
Device URI: dnssd://HP%20Smart%20Tank%20580-590%20series%20%5BE2A044%5D._ipp._tcp.local/?uuid=1efe314f-16ea-4deb-8fef-b742a1a75133
PPD: /etc/cups/ppd/HP_Smart_Tank_580-590_series.ppd
warning: Failed to read /etc/cups/ppd/HP_Smart_Tank_580-590_series.ppd ppd file
PPD Description:
Printer status: impressora HP_Smart_Tank_580-590_series está inativa; habilitada desde sáb 27 abr 2024 09:20:41
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend for HP-Devices.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Smart_Tank_580-590
------------------
Type: Printer
Device URI: hp:/net/Smart_Tank_580-590_series?ip=192.168.0.134
PPD: /etc/cups/ppd/Smart_Tank_580-590.ppd
warning: Failed to read /etc/cups/ppd/Smart_Tank_580-590.ppd ppd file
PPD Description:
Printer status: impressora Smart_Tank_580-590 está inativa; habilitada desde seg 29 abr 2024 11:43:49
Communication status: Good[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]--------------
| PERMISSION |
--------------[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]-----------
| SUMMARY |
-----------[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Missing Required Dependencies
-----------------------------
None[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Missing Optional Dependencies
-----------------------------
None[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Total Errors: 0
Total Warnings: 5[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Done.[/FONT][/COLOR]

---

### Post by him610 on 2024-05-04
I know nothing about HP 581 tank printers, but could you show the contents of */home/gomide/hp-check.log*

---

### Post by yancek on 2024-05-05
Check the file in question (/usr/bin/hp-check) particularly for the error line mentioned in your output:

>  [COLOR=#000000][FONT=&amp]/usr/bin/hp-check:685: SyntaxWarning: "is not" with a literal. Did you mean "!="?
  if 'getfacl' not in g and '' is not g and 'file' not in g:[/FONT][/COLOR]

The line referenced above is shown in my file as:  for g in getfacl_out_list:  if 'getfacl' not in g and '' != g and 'file' not in g:

and your output would indicate you do not have the != there.  Have you modified this file?  This line beings at line 575 in my hp-check file but may not be the same on yours.  You can get the file numbered by line by going to the /usr/bin directory and doing:  nl hp-check

---

### Post by FzDAsFc on 2024-05-05
[FONT=monospace][COLOR=#000000]573                                          out =''[/COLOR]
   574                                          for g in getfacl_out_list:
   575                                              if 'getfacl' not in g and '' is not g and 'file' not in g:
   576                                                  pat = re.compile('''.*:(.*)''')
   577                                                  if pat.search(g):
   578                                                      out = out +' '+ pat.search(g).group(1)
   579                                          log.info("%-15s %-30s %-15s %-8s %-8s %-8s %s"%("USB", printer_name, "Required", "-", "-", "OK", "Node:'%s' Perm:'%s'"%(devnode,out)))
   580                                      else:
   581                                          log.info("%-15s %-30s %-15s %-8s %-8s %-8s %s"%("USB", printer_name, "Required","-","-","OK", "Node:'%s' Mode:'%s'"%(devnode,st_mode&0o777)))
       

[/FONT]

---

### Post by FzDAsFc on 2024-05-05
The hp-check output is in the question right after "gomide@gomide-desktop:~$ hp-check -t"

---

### Post by FzDAsFc on 2024-05-05
[COLOR=#000000]The hp-check output is in the question right after "gomide@gomide-desktop:~$ hp-check -t"[/COLOR]

---

