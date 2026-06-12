---
title: "HP deskjet d1660 - &quot;grayscale mode&quot; &amp; black cartridge not working"
date: 2009-11-05
forum: Hardware
---

### Post by eskararriba on 2009-11-05
hi, 

I just bought an HP deskjet d1660 inkjet printer; after installing it using the HPlip-version 3.9.8., which comes with ubuntu 9.10, the printer wouldn't print in grayscale mode - and everything that should be black is printed somewhat brown (and really bad quality); I installed the latest HPlip version (3.9.10), but the printer wouldn't work at all. now I'm back to version 3.9.8., but the problem remains: the printer doesn't use the black cartridge. 

the outcome of the "dpkg -l hplip" command is: 

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  hplip          3.9.8-1ubuntu2 HP Linux Printing and Imaging System (HPLIP)

does anyone have any idea how to fix this? 
thanks

---

### Post by eskararriba on 2009-11-05
and again: here comes the output of the "hp-check"-command - hope it helps:


eskararriba@parker:~$ hp-check

HP Linux Imaging and Printing System (ver. 3.9.10)
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
Linux parker 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

Distribution:
ubuntu 9.10

Checking Python version...
OK, version 2.6.4 installed

Checking PyQt 4.x version...
OK, version 4.6 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.4.1
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

Checking for dependency: CUPS DDK - CUPS driver development kit...
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.
To install this dependency, execute this command:
sudo aptitude install --assume-yes cupsddk cupsddk-drivers

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
HPLIP 3.9.10 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.9.10

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hplip/HP
ppdbase=/usr/share/ppd/hplip
doc=/usr/share/doc/hplip-3.9.10
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
internal-tag=3.9.10.68
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
printer_name = HP-Deskjet-D1600-series
working_dir = .
device_uri = hp:/usb/Deskjet_D1600_series?serial=CN999391CQ05CT

[commands]
scan = /usr/bin/xsane -V %SANE_URI%

[installation]
version = 3.9.10.68
date_time = 11/05/2009 22:19:00

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

  Device URI                        Model                  
  --------------------------------  -----------------------
  hp:/usb/Deskjet_D1600_series?ser  HP Deskjet D1600 series
  ial=CN999391CQ05CT                                       

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
1.1-root-hub
------------
Type: Unknown
Device URI: usb://Linux%20Foundation/1.1%20root%20hub?serial=0000:00:02.0
PPD: /etc/cups/ppd/1.1-root-hub.ppd
PPD Description: Generic text-only printer
Printer status: printer 1.1-root-hub disabled since Tue 26 May 2009 08:36:17 PM CDT -   Unplugged or turned off
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

HP-Deskjet-D1600-series
-----------------------
Type: Printer
Device URI: hp:/usb/Deskjet_D1600_series?serial=CN999391CQ05CT
PPD: /etc/cups/ppd/HP-Deskjet-D1600-series.ppd
PPD Description: HP Deskjet d1600 Series hpijs, 3.9.8
Printer status: printer HP-Deskjet-D1600-series is idle.  enabled since Thu 05 Nov 2009 10:07:43 PM CST
Communication status: Good

Stylus-CX3700
-------------
Type: Unknown
Device URI: usb://EPSON/Stylus%20CX3700
PPD: /etc/cups/ppd/Stylus-CX3700.ppd
PPD Description: Epson Stylus CX3700 - CUPS+Gutenprint v5.2.4
Printer status: printer Stylus-CX3700 disabled since Wed 21 Oct 2009 10:15:14 AM CDT -  Unplugged or turned off
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `v4l:/dev/video0' is a Noname HP Webcam virtual device


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

HP Device 0x7f11 at 001:006: 
    Device URI: hp:/usb/Deskjet_D1600_series?serial=CN999391CQ05CT
    Device node: /dev/bus/usb/001/006
    Mode: 0660

---------------
| USER GROUPS |
---------------

eskararriba adm dialout cdrom plugdev lpadmin admin sambashare


-----------
| SUMMARY |
-----------

error: 3 errors and/or warnings.

Summary of needed commands to run to satisfy missing dependencies:
sudo aptitude install --assume-yes cupsddk cupsddk-drivers

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.
eskararriba@parker:~$

---

### Post by eskararriba on 2009-11-07
update: as you can see, the "dpkg"-command states: 

ii hplip 3.9.8-1ubuntu2 HP Linux Printing and Imaging System (HPLIP)

while the hp-check command says: 

Currently installed HPLIP version...
HPLIP 3.9.10 currently installed in '/usr/share/hplip'.

- I figured that I'd better completely remove HPLIP, and then re-installed the 3.9.10-version from the hp-website. the outcome of the "dpkg -l hplip"-command goes like this now: 

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  hplip          <none>         (no description available)


- the output of the "hp-check" command is:  


HP Linux Imaging and Printing System (ver. 3.9.10)
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
Linux parker 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

Distribution:
ubuntu 9.10

Checking Python version...
OK, version 2.6.4 installed

Checking PyQt 4.x version...
OK, version 4.6 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.4.1
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

Checking for dependency: CUPS DDK - CUPS driver development kit...
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.
To install this dependency, execute this command:
sudo aptitude install --assume-yes cupsddk cupsddk-drivers

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
HPLIP 3.9.10 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.9.10

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.9.10
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
internal-tag=3.9.10.72
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
printer_name = HP-Deskjet-D1600-series
working_dir = .
device_uri = hp:/usb/Deskjet_D1600_series?serial=CN999391CQ05CT

[commands]
scan = /usr/bin/xsane -V %SANE_URI%

[installation]
version = 3.9.10.72
date_time = 11/07/2009 12:13:39

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

  Device URI                        Model                  
  --------------------------------  -----------------------
  hp:/usb/Deskjet_D1600_series?ser  HP Deskjet D1600 series
  ial=CN999391CQ05CT                                       

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
1.1-root-hub
------------
Type: Unknown
Device URI: usb://Linux%20Foundation/1.1%20root%20hub?serial=0000:00:02.0
PPD: /etc/cups/ppd/1.1-root-hub.ppd
PPD Description: Generic text-only printer
Printer status: printer 1.1-root-hub disabled since Tue 26 May 2009 08:36:17 PM CDT -   Unplugged or turned off
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

Deskjet_D1600
-------------
Type: Printer
Device URI: hp:/usb/Deskjet_D1600_series?serial=CN999391CQ05CT
PPD: /etc/cups/ppd/Deskjet_D1600.ppd
PPD Description: HP Deskjet d1500 Series, hpcups 3.9.10
Printer status: printer Deskjet_D1600 is idle.  enabled since Sat 07 Nov 2009 12:01:09 PM CST
Communication status: Good

HP-Deskjet-D1600-series
-----------------------
Type: Printer
Device URI: hp:/usb/Deskjet_D1600_series?serial=CN999391CQ05CT
PPD: /etc/cups/ppd/HP-Deskjet-D1600-series.ppd
PPD Description: HP Deskjet d1600 Series, hpcups 3.9.10
Printer status: printer HP-Deskjet-D1600-series is idle.  enabled since Sat 07 Nov 2009 Processing page 2...
Communication status: Good

Stylus-CX3700
-------------
Type: Unknown
Device URI: usb://EPSON/Stylus%20CX3700
PPD: /etc/cups/ppd/Stylus-CX3700.ppd
PPD Description: Epson Stylus CX3700 - CUPS+Gutenprint v5.2.4
Printer status: printer Stylus-CX3700 disabled since Wed 21 Oct 2009 10:15:14 AM CDT -  Unplugged or turned off
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `v4l:/dev/video0' is a Noname HP Webcam virtual device


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

HP Device 0x7f11 at 001:003: 
    Device URI: hp:/usb/Deskjet_D1600_series?serial=CN999391CQ05CT
    Device node: /dev/bus/usb/001/003
    Mode: 0660

---------------
| USER GROUPS |
---------------

eskararriba adm dialout cdrom plugdev lpadmin admin sambashare


-----------
| SUMMARY |
-----------

error: 3 errors and/or warnings.

Summary of needed commands to run to satisfy missing dependencies:
sudo aptitude install --assume-yes cupsddk cupsddk-drivers

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.
-----------------------------------------------------------------------------------------------------

I tried to run sudo aptitude install --assume-yes cupsddk cupsddk-drivers, but nothing would happen:

eskararriba@parker:~$ sudo aptitude install --assume-yes cupsddk cupsddk-drivers
[sudo] password for eskararriba: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

any ideas?

---

### Post by metalqga on 2009-11-23
Same prob here (in debian lenny). I've been trying to modify the HP_Deskjet_D1600.ppd but no luck. The printer doesn't respond at all when set to print in grayscale!

---

### Post by sefsinalas on 2009-11-25
I have the same problem...i cant print with the black cartridge...someone help me please!

---

### Post by Butthead on 2010-01-30
Anybody had any luck getting the HP DJ D1660 working correctly in Linux yet? :confused:

I wish my DJ 540C still worked. :mad:

---

### Post by eskararriba on 2010-01-30
I'm using CUPS and the DJ 1660 works just fine. I'm far from being a pro, so I can only try to approximately tell you what I did do fix the issue - there's surely some unnecessary steps in here, but anyways...

I first removed HPLIP completely:

su -c "rm -rf /usr/share/hplip"

sudo rm -rf /usr/share/hplip

then I reinstalled:

sh hplip-3.9.10.run

after that, I installed CUPS (before the complete removal, that didn't work - now it did):

sudo aptitude install --assume-yes cupsddk cupsddk-drivers

I did a "hp-check", then "hp-plugin" and finally "hp-setup"; when the setup is running, use CUPS - when you configure the printer via CUPS, things seem to work. I don't really recall what "driver"-option I chose in the config menu, but it's one of the first two or three CUPS will give you (you'll see what I mean when you get there...). 


hope it works, let me know
cheers

---

### Post by Butthead on 2010-01-31
Hi Eskararriba,

Thanks for the help!  I noticed by the "aptitude" line that you must be using Gnome as your Desktop manager.  Since I'm using Kubuntu on a 64 bit x2 based system, I wonder if your "fix" will work for me? :confused:

Anyway, it's worth a shot.  I'm going to see if any of my other queries got me any responses first, and then try what you outlined.

Thanks again for the help! :guitar:

---

### Post by Butthead on 2010-02-01
Hi Eskararriba,

Thanks, you're a lifesaver! :guitar:

Your commands worked perfectly! (should almost be made a sticky). ;)

I am now printing successfully under Kubuntu with the HP D1660 DeskJet printer.

Now how to figure out how replicate this in Mandriva so the printer will work in there too. :confused:

Don't sell yourself short (far from a pro statement).  I would have never figured out how to do this myself in 1,000 years. :P

---

### Post by viaciofano on 2010-02-08
eskararriba
thanks i went to the hplip site. updated as followed and now can see the xsane window whereas before on the original system i could print....thanks. just have to wo0rk out how to scan now...
thanks all for your help

---

### Post by SR_ELPIRATA on 2010-02-22
A friend of mine has this printer as well, so we started your procedure but with the many hp-check stuff that shows up is a bit complicated. I noticed that we had the 3.9.8 version installed (Ubuntu 9.04) and used the check stuff portion to make sure I had all the packages needed.

Then, I noticed the link to the HPLIP site and I went there and.... there was an automatic installer there, with all steps outlined. That automatic installer also checks for dependencies and stuff needed so there's no need to do it separately (like I did).

Just download the file, change directory and execute (as per their instructions). Since we had 9.04 the link there says that we could use the automatic wizard feature. After checking for dependencies (which I had downloaded them before) it tried to run but for 3 times it stopped and always for the same missing file, 'python-devel' which if you try to download yourself doesnt exist, at least not with that name.

All you need to do is to install that file but instead of python-devel is called python-dev. After that, the automatic wizard (which at the start is just a script) progressed as normal and then it made the actual installer, which then, after finishing, adds the HP logo to your printer icon when connected and powered on.

So, its working and we didnt have to do any of the removing stuff, since the installer script did it itself.

BTW I was surprised when 'eska' said in the subject that it didnt work in grayscale mode, I guess because it means that somehow it found a driver for this D1660 whereas we couldnt.

Also, wanted to mention that even though many HP printers work well with Linux... this HPLIP software works for 1597 (or so they said) HP printers, so it might be a good idea to keep it handy.

ELP

PS: Eska you should edit the subject to SOLVED status, so others can benefit from this and not overlook it.

---

### Post by Tommykry on 2010-05-27
Help anyone! having the same problems with Linux Mint 9 and Hp Deskjet D1660. I've tried everything! I got the printer to print a test page only once, the printer works on win xp and Pclos 2010, I've tried the
instructions above with no success any help would be great, the printer just sits there and does nothing when i send it to print, it is recognized by all the hp software and everything works like it should other then it won't print, here is what happens when i try and run the software from the hp site :( :

tommy@tommy-laptop ~ $ cd Desktop
tommy@tommy-laptop ~/Desktop $ sh hplip-3.10.5.run
Creating directory hplip-3.10.5
Verifying archive integrity... All good.
Uncompressing HPLIP 3.10.5 Self Extracting Archive.................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

HP Linux Imaging and Printing System (ver. 3.10.5)
HPLIP Installer ver. 5.1

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Wed-26-May-2010_23:35:46.log

/
note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.


INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to choose installation options to fit specific requirements.

Please choose the installation mode (a=automatic*, c=custom, q=quit) : a

Initializing. Please wait...
 

INTRODUCTION
------------
This installer will install HPLIP version 3.10.5 on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).


DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Linux Mint 9.

Is "Linux Mint 9" your correct distro/OS and version (y=yes*, n=no, q=quit) ? y


ENTER USER PASSWORD
-------------------
Please enter the user (tommy)'s password: 
Password accepted


RUNNING PRE-INSTALL COMMANDS
----------------------------
OK


INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 7 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
warning: This installer cannot install 'gcc' for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.
tommy@tommy-laptop ~/Desktop $

---

### Post by Tommykry on 2010-05-28
Anyone:(

---

