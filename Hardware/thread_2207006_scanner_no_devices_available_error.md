---
title: "scanner: no devices available error"
date: 2014-02-21
forum: Hardware
---

### Post by DeepBlunder on 2014-02-21
Greetings. 
I'm running Ubuntu 12.04 (precise), 32 bit, AMD Athlon(tm) II X3 450 Processor × 3,    8 GB memory, 

My prior HP printer/scanner -- which had been functioning well with my system -- recently died.  I purchased a new HP OfficeJet 6700 printer/scanner.  For reasons I don't understand, my system would not detect the new OfficeJet when connected with USB cable but is now connected and printing via a wireless connection. While printing is now working fine, I unfortunately cannot scan.  When I try to run Xsane or some other scan app, no scanner is detected.  Not sure what to do next and suggestions would be appreciated. 

I have tried installing HPLIP ToolBox through the software center and get the following error: "The following packages have unmet dependencies:

hplip-gui: Depends: hplip (>= 3.12.2-1ubuntu3.4) but 3.12.2-1ubuntu3.4 is to be installed"

Below is the output when I run hp-check -r 


__________________________________

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
 Linux DeskTop1 3.5.0-45-generic #68~precise1-Ubuntu SMP Wed Dec 4 16:19:28 UTC 2013 i686 athlon i386 GNU/Linux  
 

 Distribution:  
 ubuntu 12.04  
 

 Checking Python version...  
 OK, version 2.7.3 installed  
 

 Checking PyQt 4.x version...  
 error: NOT FOUND OR FAILED TO LOAD!  
 

 Checking for CUPS...  
 Status: scheduler is running  
 warning: Version: (cups-config) Not available. Unable to determine installed version of CUPS.)  
 error_log is set to level: warn  
 

 Checking for dbus/python-dbus...  
 dbus daemon is running.  
 python-dbus version: 1.0.0  
   
 

 ------------------------  
 | RUNTIME DEPENDENCIES |  
 ------------------------  
 

 

 Checking for dependency: CUPS - Common Unix Printing System...  
 OK, found.  
 

 Checking for dependency: CUPS DDK - CUPS driver development kit...  
 warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.  
 

 Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...  
 OK, found.  
 

 Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...  
 OK, found.  
 

 Checking for dependency: PolicyKit - Administrative policy framework...  
 OK, found.  
 

 Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...  
 error: NOT FOUND! This is a REQUIRED/RUNTIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.  
 

 Checking for dependency: Python DBus - Python bindings for DBus...  
 OK, found.  
 

 Checking for dependency: Python libnotify - Python bindings for the libnotify Desktop notifications...  
 OK, found.  
 

 Checking for dependency: Python XML libraries...  
 OK, found.  
 

 Checking for dependency: Python 2.3 or greater - Required for fax functionality...  
 OK, found.  
 

 Checking for dependency: Reportlab - PDF library for Python...  
 OK, found.  
 

 Checking for dependency: SANE - Scanning library...  
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
 # hplip.conf.  Generated from hplip.conf.in by configure.  
 

 [hplip]  
 version=3.12.2  
 

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
 internal-tag=3.12.2  
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
 

 

 --------------------------  
 | DISCOVERED USB DEVICES |  
 --------------------------  
 

 No devices found.  
 

 ---------------------------------  
 | INSTALLED CUPS PRINTER QUEUES |  
 ---------------------------------  
 

   
 HP-Officejet-6700  
 -----------------  
 Type: Unknown  
 Device URI: dnssd://Officejet%206700%20%5B41EDFC%5D._pdl-datastream._tcp.local/  
 PPD: /etc/cups/ppd/HP-Officejet-6700.ppd  
 PPD Description: HP Officejet 6500 e709n, hpcups 3.12.2  
 Printer status: printer HP-Officejet-6700 is idle.  enabled since Mon 17 Feb 2014 09:01:10 PM MST  
 warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.  
 

 

 ----------------------  
 | SANE CONFIGURATION |  
 ----------------------  
 

 'hpaio' in '/etc/sane.d/dll.conf'...  
 'hpaio' in '/etc/sane.d/dll.d/hplip'... 
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
 

 

   
 ---------------  
 | USER GROUPS |  
 ---------------  
 

 root  
 

 error: User needs to be member of group 'lp' to enable print, scan & fax.  
 error: User needs to be member of group 'lpadmin' to manage printers.  
 

 -----------  
 | SUMMARY |  
 -----------  
 

 error: 4 errors and/or warnings.  
 

 Please refer to the installation instructions at:  
 [http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

---

### Post by DeepBlunder on 2014-02-22
Embarrased to admit but  I had a cable connection issue that is now fixed. I can connect the printer wirelessly or via the USB. That said, while I able to print, the  desktop still is not detecting the scanner. 

When I run  sane-find-scanner the terminal output reads:

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [HP], product=0x5c12 [Officejet 6700]) at libusb:003:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

I have tried scanimag -L and it says no sane devices found.

---

