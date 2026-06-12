---
title: "HP 1020 Laser Printer not printing"
date: 2010-07-22
forum: Hardware
---

### Post by J Bratton on 2010-07-22
Hey folks. I've had a heck of a time getting my HP 1020 printer to print. A few months ago, it was working every once in a while, if I stood on my head and rebooted and reinstalled the printer and the moon was full. And blue. Lately, I haven't gotten it to work at all. 

I'm using HPLip, latest and greatest. When I run hp-setup, it detects the printer OK. Problem is, when I try to print, it never actually prints. I either get "pending" or "processing" and then when I dig into it more, sometimes it tells me the printer isn't found. Yet, it finds it just fine when I run hp-setup.

Here's the output of hp-check:
=========================================================================
john@john-desktop:~$ sudo hp-check

HP Linux Imaging and Printing System (ver. 3.10.2)
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
Linux john-desktop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux

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
[plugin]
eula = 1
installed = 1



Current contents of '~/.hplip/hplip.conf' file:
[last_used]
printer_name=
working_dir=.
device_uri="hp:/usb/HP_LaserJet_1020?serial=FN1E1EX"

[commands]
scan=/usr/bin/simple-scan %SANE_URI%

[installation]
version=3.10.2rc1.9
date_time=07/22/2010 16:21:31

[settings]
systray_messages=0
systray_visible=0

[fax]
email_address=
voice_phone=

[refresh]
rate=30
enable=true
type=1

[polling]
enable=false
device_list=
interval=5


--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                        Model           
  --------------------------------  ----------------
  hp:/usb/HP_LaserJet_1020?serial=  HP LaserJet 1020
  FN1E1EX                                           

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
HP_LaserJet_1020
----------------
Type: Printer
Device URI: hp:/usb/HP_LaserJet_1020?serial=FN1E1EX
PPD: /etc/cups/ppd/HP_LaserJet_1020.ppd
PPD Description: HP LaserJet 1020 hpijs, 3.10.2, requires proprietary plugin
Printer status: printer HP_LaserJet_1020 now printing HP_LaserJet_1020-0.  enabled since Thu 22 Jul 2010 04:58:53 PM MDT
Required plug-in status: Installed
error: Device busy: hp:/usb/HP_LaserJet_1020?serial=FN1E1EX
error: Device not found
error: Communication status: Failed


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


 
-----------------
| USB I/O SETUP |
-----------------

Checking for permissions of USB attached printers...

HP Device 0x2b17 at 001:014: 
    Device URI: hp:/usb/HP_LaserJet_1020?serial=FN1E1EX
    Device node: /dev/bus/usb/001/014
    Mode: 0664

---------------
| USER GROUPS |
---------------

root

error: User needs to be member of group 'lp' to enable print, scan & fax.
error: User needs to be member of group 'lpadmin' to manage printers.

-----------
| SUMMARY |
-----------

error: 1 error or warning.

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.
=====================================================================

So, the only error showing is that the user needs to be a member of groups "lp" and "lpadmin" but as far as I can tell, I (john) am a member of that group, so not sure why I'm getting that error message.

Here's the group info:

john@john-desktop:~$ groups
john adm lp dialout cdrom audio dip plugdev lpadmin admin sambashare

==============

Thanks for any help. It seems like it would be really silly to have to buy a new printer just because I can't get this one to work. Also silly- the number of hours/days I've spent trying to get this to work.

Using Lucid Lynx. Printer is USB connected. Printer itself works.
thanks!

---

### Post by MyR on 2010-07-22
hi there,

[http://ubuntuforums.org/showthread.php?t=1172301](http://ubuntuforums.org/showthread.php?t=1172301)

[http://ubuntuforums.org/showthread.php?t=102372](http://ubuntuforums.org/showthread.php?t=102372)

[http://ubuntuforums.org/showthread.php?t=1376099](http://ubuntuforums.org/showthread.php?t=1376099)

[http://ubuntuforums.org/showthread.php?t=1088348](http://ubuntuforums.org/showthread.php?t=1088348)

looks like a number of people have got it working...

---

### Post by drs305 on 2010-07-22
I've spent time over the years battling with my HP 1000. From time to time it still balks. I've found that having a shortcut to the CUPS control panel on my Internet browser is very handy. I'll state up front that this helps on a printer that *sometimes* acts but but *normally* works properly.

When my printer doesn't print, I check the status via the CUPS link, 'Jobs' tab. Often the problem is that the print job failed to 'release', so printing is only one click away at that point. And this works whether it's the CUPS or hpijs setup. I have both when trouble starts I can try a different driver.

The link address is: [http://localhost:631/](http://localhost:631/)

A better solution would be for the older HP Laserjet's to always work, but that just doesn't seem to be in the cards.

---

### Post by J Bratton on 2010-07-22
Thanks folks. Keeping a link to CUPS close by seems handy. And, following one of the links MyR provided
[http://ubuntuforums.org/showthread.php?t=1172301](http://ubuntuforums.org/showthread.php?t=1172301)
gave me enough information to get printing. Here's what of that worked for me:

sudo apt-get remove hp*

wget [http://prdownloads.sourceforge.net/hplip/hplip-3.9.12.run](http://prdownloads.sourceforge.net/hplip/hplip-3.9.12.run)

sh hplip-3.9.12.run

I didn't need to run hp-setup after that; apparently the problem was elsewhere. I got some conflicting error messages after the last line, some saying things had failed, some saying things have worked, but it printed. I wonder for how long?  ;)

Anyway, thanks much. I should have asked here sooner!

---

### Post by alpha-buntu on 2011-02-12
Same for me, sometimes works, sometimes not.

Reboot, reconnect usb, and giving kisses works, or not. I hate that piece!

---

### Post by J Bratton on 2011-02-15
Update- after much, much tinkering with the HP printer and Lucid, I could get the printer to work, but only if I left it on and didn't reboot. If I did either of those things, I'd have to go into terminal, remove everything HP, then re-install. Definitely a bit of a pain. 

Then moved to a clean install of 10.10 Maverick. The HP printer works now. It found the driver, I loaded it one time, then done. Sometimes I have to turn the printer off and back on again, but that's it.

---

### Post by MyR on 2011-02-15
> **J Bratton said:**
> Update- after much, much tinkering with the HP printer and Lucid, I could get the printer to work, but only if I left it on and didn't reboot. If I did either of those things, I'd have to go into terminal, remove everything HP, then re-install. Definitely a bit of a pain. 

Then moved to a clean install of 10.10 Maverick. The HP printer works now. It found the driver, I loaded it one time, then done. Sometimes I have to turn the printer off and back on again, but that's it.

I am glad it works for you!  I have been working on a solution for Linux users with regard to purchasing new hardware.  Would you be willing to [submit a report]("http://linuxdeal.com/add-printer.php") for the printer?

---

### Post by milos.forman on 2011-08-14
If you ride Lucid make sure that you have **foo2zjs** driver (*support for printing to ZjStream-based printers*) installed. You can install the driver using Synaptic. It works with HP LaserJet 1000/1005/1018/1020/1022; After you install the driver, plug the printer into the usb port and turn in on. You'll get an wizard which will help you configure the printer. You just need to download HP support from their website. (option d). And that's all folks :)

---

