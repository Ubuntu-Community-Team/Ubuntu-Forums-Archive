---
title: "HPLIP 3.9.8 &quot;Communication Error 5012"
date: 2009-08-24
forum: Hardware
---

### Post by colin.p on 2009-08-24
I have an HP Officejet 6500 E709n connected wirelessly to a Trendnet wireless router using a dynamic IP (all computers connect to the router dynamically)  using the newest driver hplip 3.9.8.
It keeps getting a communication error 5012 when I open HP manager. Sometimes it will connect after a reboot of the computer, router and printer and will print a test page, but close HP Manager and the printer loses connection.
When I first installed the printer using CUPS it printed ok, but I admit I was determined to be able to use all functions using the HP gui, and that's when it stopped working.
I have searched extensively on Google and several forums and have found that it is a known issue but doesn't seem to have a definitive answer.
There is a bug report at [https://bugs.launchpad.net/hplip/+bug/309833](https://bugs.launchpad.net/hplip/+bug/309833).

This computer is a dual boot of jaunty and XP SP3. We have two other computers connected to the router, a wireless laptop (Vista) and a desktop rj45 (XP SP3) and of course all print fine in windows. Now I know that sooner or later this problem will be solved (evidently this is a new model of printer), so I will check in regularly to see if there is a solution, and if I ever find a solution, I will post back here.
Until then, it still is faster to boot into windows to print, than running upstairs and restarting everything.

info is below

colin@colin-desktop:~$ hp-info

HP Linux Imaging and Printing System (ver. 3.9.8)
Device Information Utility ver. 5.2

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Using device: hp:/net/Officejet_6500_E709n?zc=HPD323A9

error: Unable to communicate with device (code=12): hp:/net/Officejet_6500_E709n?zc=HPD323A9
error:  Unable to open device hp:/net/Officejet_6500_E709n?zc=HPD323A9. 

Done.


colin@colin-desktop:~$ hp-check

HP Linux Imaging and Printing System (ver. 3.9.8)
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
Linux colin-desktop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

Distribution:
ubuntu 9.04

Checking Python version...
OK, version 2.6.2 installed

Checking PyQt 4.x version...
OK, version 4.4.4 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.3.9
error_log is set to level: info

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
HPLIP 3.9.8 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.9.8

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.9.8
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
internal-tag=3.9.8.36
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=yes
hpijs-only-build=no
lite-build=no
udev-acl-rules=no


Current contents of '/var/lib/hp/hplip.state' file:
# hplip.state - HPLIP runtime persistent variables. 

[plugin]
installed=0
eula=0



Current contents of '~/.hplip/hplip.conf' file:
[last_used]
printer_name = 
printer = 
working_dir = .
device_uri = "hp:/net/Officejet_6500_E709n?zc=HPD323A9"

[commands]
scan = /usr/bin/xsane -V %SANE_URI%

[installation]
version = 3.9.8.36
date_time = 09-08-24 19:29:43

[settings]
systray_messages = 0
systray_visible = 1

[fax]
email_address = 
voice_phone = 

[refresh]
rate = 30
enable = true
type = 2

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

 
Officejet_6500_E709n
--------------------
Type: Printer
Device URI: hp:/net/Officejet_6500_E709n?zc=HPD323A9
PPD: /etc/cups/ppd/Officejet_6500_E709n.ppd
PPD Description: HP Officejet 6500 e709n, hpcups 3.9.8
Printer status: printer Officejet_6500_E709n is idle.  enabled since Sun 16 Aug 2009 05:46:05 PM EDT
error: Unable to communicate with device (code=12): hp:/net/Officejet_6500_E709n?zc=HPD323A9
error: unable to open channel
error: Communication status: Failed

Officejet_6500_E709n_fax
------------------------
Type: Fax
Device URI: hpfax:/net/Officejet_6500_E709n?zc=HPD323A9
PPD: /etc/cups/ppd/Officejet_6500_E709n_fax.ppd
PPD Description: HP Fax hpcups
Printer status: printer Officejet_6500_E709n_fax is idle.  enabled since Sun 16 Aug 2009 05:46:05 PM EDT
error: Unable to communicate with device (code=12): hpfax:/net/Officejet_6500_E709n?zc=HPD323A9
error: unable to open channel
error: Communication status: Failed


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/net/Officejet_6500_E709n?zc=HPD323A9' is a Hewlett-Packard Officejet_6500_E709n all-in-one


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

colin adm dialout cdrom dip plugdev lpadmin admin sambashare


-----------
| SUMMARY |
-----------

error: 2 errors and/or warnings.

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.
colin@colin-desktop:~$

---

### Post by colin.p on 2009-08-28
I got an answer and so far, 15 minutes and the printer hasn't lost communication.

Thanks Aaron.

Colin


Your question #81249 on HPLIP changed:
[https://answers.launchpad.net/hplip/+question/81249](https://answers.launchpad.net/hplip/+question/81249)

    Status: Open => Needs information

Aaron Albright requested for more information:
It looks like the printer queue is using the hostname.  Is it possible
to try using the IP address instead?

sudo hp-setup

Select manually discovery, then enter the IP address, etc.

If that fixes it I'll need to do some testing using the hostname rather
than the IP and see if there might be some issue.

Thanks.

Aaron

---

### Post by slowlap on 2009-08-29
I had the same problem when i upgraded hp2.8.12.run to 3.9.8.run,
I tried re-installing several times and re-booting printer and pc, but every time It installed fine, but when I rebooted the pc I got the same error (Device communication error 5012).
I did the same I ran hp-setup in a terminal and selected wireless setup, but instead of letting hp find the printer, I clicked on advanced and put in the ip address manually which in my case was 192.168.0.2
Now it works fine, Its a shame hp don't have a fix already for this though!!

---

### Post by colin.p on 2009-08-29
Aaron from launchpad indicated that there might be an issue with using the host name instead of the IP. Since you have confirmed with the same issue and resolution, it would seem that this is a fairly common problem.
In either case they are aware of it and hopefully the next version of hplip will not have this problem.

Colin

---

### Post by landersohn on 2009-12-27
I just wanted to know whether I am alone still having this problem in HPLIP 3.9.12? I am using a Deskjet F4280 and get exactly this error. Printing works but the status functions do not

---

### Post by colin.p on 2009-12-27
I have since given up on using my 6500 as a wireless printer and have moved it beside my (cheap) router and hooked it by rj45.
I no longer have flakey connectivity issues in karmic and even my wife's Vista wireless laptop sees the printer alot better (believe it or not, Vista had a much harder time connecting to the printer).
I realize that it might not be a practical solution for some, but it works better for me.

---

### Post by Xanko on 2010-08-18
I have been having the same problem. Error 5012 in HPLIP GUI and Error 12 in the hp-check -t. CUPS works fine however I cannot get status from HPLIP GUI (also I would like to be able to scan from computers not directly hooked to the scanner??) I tried to manually add the printer using it's IP address however I get the following error "Printer Queue Setup Failed. Please restart CUPS and try again. Restarted and it still does not work....

---

### Post by Xanko on 2010-08-20
I believe I have solved my problem for anyone having similar issues I will post my fix. I initially setup the printer as a USB printer however after removing the printer from HPLIP GUI and re-adding it as a Wireless Printer I now have connectivity from all my computers on the network. The printer address is now listed as 'hp:/net/PhotosmartXXX' as opposed to 'hp:/usb/PhotosmartXXX'.

---

### Post by h0bbe on 2010-10-29
I solved my problems by reinstalling the printer not usinf the HPLIP interface, like a post in this thread: [http://ubuntuforums.org/showthread.php?t=1384560](http://ubuntuforums.org/showthread.php?t=1384560)

I went to the display on the printer and connected it to my wifi network. After that i went to the Ubuntu menu System-Administration-Printer and found the printer!

---

### Post by carchaias on 2011-09-16
I had the same Problem  with an OfficeJet Pro 8500. Inserting the IP in setup manually solved it . hplip is 3.11.7 . with Ubuntu Maveric

---

### Post by SaintDanBert on 2012-01-16
> **carchaias said:**
> I had the same Problem  with an OfficeJet Pro 8500. Inserting the IP in setup manually solved it . hplip is 3.11.7 . with Ubuntu Maveric

1. I set my HP-8500 from its panel using the Wifi tools. I named an IP
address of my choice rather than rely on DHCP.
2. In HPLIP, I said "network connection" (no wifi) -- after all, if wifi is really working, it is just another IP address on the LAN.
3. HPLIP found the printer all was well.
...
4. Upgrade to Mint-12, now I get "Comm Error 5012".
5. Moved printer (unrelated to this issue) and connect by wire
6. Configured wire net at the printer panel using the same fixed IP
as I used before under wifi.
7. Still get the "Error 5012"

SUMMARY:
** Somewhere between Ubuntu 10.04 and 11.10 (Mint-12) something changed in HPLIP-land because I didn't use to have any troubles
** I have yet to try to re-install naming the printer IP address
** Neither 10.04 nor 11.04 (Mint-11) have or had any troubles.

~~~ 8d;-/ Dan

---

### Post by colin.p on 2012-01-16
I am seeing more and more people with HP printer issues, and of course, they are using a more current version of ubuntu. I seem to remember in one of the threads, that HPLIP wasn't working properly in natty and for certain in oneiric. It seems that printing seemed to work, but scanning, copying, and faxing didn't. 
Of course, I am not seeing any of this, as my 6500 has worked flawlessly in karmic and now lucid. I may wait quite awhile after 12.04 comes out, to see if HP printer problems had been fixed and then I would upgrade.
But in either case, thanks for updating this thread. It may keep people like me on lucid for quite some time yet.

---

### Post by Blempis on 2012-07-30
> **colin.p said:**
> I am seeing more and more people with HP printer issues

Here is one more. The problem child is HP deskjet 6500 with "communication error 5012". 

That same printer works flawlessly with an ancient 600 Mhz Windows 98 (stand alone) machine like it used to work with Ubuntu 10.04.

---

### Post by colin.p on 2012-07-30
This is an old thread, so it may get locked, but if you follow the above suggestions, especially about specifying an IP, it should work.
I now use 12.04 and the two wireless printers I have (the 6500 and a cheap Canon) both needed very little threatening to work. As a matter of fact, all functions work just fine.

Since this has been solved for quite awhile, as far as I'm concerned....solved.

---

