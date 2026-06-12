---
title: "Undetected parallel printer in Jaunty Jackalope URGENT!"
date: 2009-05-23
forum: Hardware
---

### Post by Cubytus on 2009-05-23
Hi to everyone, 

I wanted to migrate a 8.04 workstation computer to a 9.04, and, as usual with computers, nothing went as planned; I needed to do a clean install from scratch as I got a mysterious "Power manager not properly installed" with the upgrade method.

In **8.04**, I set up an HP LaserJet 1100 that was printing flawlessly; I set it up using the standard Ubuntu GUI, and use it daily. This printer is perfectly functional, so please no "have you tested on another machine" answers.

Now, I basically have a clean 9.04 install, but I cannot find the parallel port in the default GUI? What the heck???

I also tried installing HPLIP's GUI just to make it easier, and it states that it cannot detect anything on the parallel port (HPLIP never worked with that printer anyway, so I didn't consider it much).

I finally tried in CUPS directly, but there again, I don't know how to formulate the URL to represent a parallel-connected printer.

AS I absolutely need this computer to work, before reversing to 8.10 in a hurry, is there a cleaner solution to solve this deal-breaking bug?

Thanks for help!

---

### Post by j0eb0b on 2009-05-23
Is the printer connected to the motherboard using a standard parallel cable or is it connected via a parallel to usb gender changing cable?  

I am having similar issues with an HP Laserjet 5L which worked properly using 8.04 and now semi-works using 9.04.  9.04 does not recognize the printer as a parallel device but does see it as a 5L via usb.  Using CUPS i was able to get the printer to print although I am still having issues printing emails.  Like you, HP LIBS does not detect any HP printers connected to my system using their standard configuration utility.

I,too, should have stayed with 8.04.  While there are some good changes in 9.04 there are serious bugs too and printing to older parallel printers seems to be one of them.

---

### Post by albinootje on 2009-05-23
> **Cubytus said:**
> 
I finally tried in CUPS directly, but there again, I don't know how to formulate the URL to represent a parallel-connected printer. 

You can set it up on the commandline, for example :

```

lpadmin -p LaserJet -m laserjet.ppd -v parallel:/dev/lp0 -E

```
Where the ppd file would be the ppd file (driver) that your printer needs.

[http://www.cups.org/doc-1.1/sam.html#4_2_1](http://www.cups.org/doc-1.1/sam.html#4_2_1)

See also :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/369850](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/369850)
[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

---

### Post by Cubytus on 2009-05-23
It's directly connected to the motherboard. In fact, I didn't move any cable while changing OSes.

However, I cannot rely on a backup USB port, since there are **no USB** on the printer

albinootje> If that matters, I don't see any lpX (X being a digit) in my /dev tree

Some people mentioned to keep the printer on and connected during install, but this has not changed anything for me.

Is it possible to install 8.10, then move to 9.04 using the standard upgrade method without losing printing ability?

I went to the link provided in Launchpad, and tried the solutions posted once again.

I added parport_pc in /etc/modules, and rebooted. 

I then tried to install the printer using the standard Ubuntu GUI, and it detected the correct printer on the parallel port.

I could set it up using CUPS+Gutenprint, as I saw it gave "less bad" results as a color approximation at 600dpi.

Then...on to my other issue, [there]("http://ubuntuforums.org/showthread.php?p=7333030#post7333030").

---

### Post by j0eb0b on 2009-05-23
What I suggested is replacing the existing parallel cable with a parallel to usb cable.  The cable I am talking about has a parallel connection to connect to the printer and a usb at the other end to connect to any available usb port on the computer.  Cables such as these are available at Radioshack ect.  I grant you that you should not have to do this since it appears to be a flaw in Jaunty but in my case it allowed me to continue using my Laserjet.  Since my first post, I have resolved my printing problems and the device now works normally using CUPS.

---

### Post by albinootje on 2009-05-23
> **Cubytus said:**
> 
I could set it up using CUPS+Gutenprint, as I saw it gave "less bad" results as a color approximation at 600dpi.

So.. the printing problem is solved ? or not ?

---

### Post by Cubytus on 2009-05-23
I will never buy any new hardware when the problem is purely software. Jaunty wouldn't let me use my stuff? Fine, so let's dump Jaunty. Changing hardware because the OS imposes it is valid in Microsoft's world, not Ubuntu. If that was not possible to solve it, I would simply have returned to Intrepid Ibex, and I encourage anyone to do so.

And *for now*, the problem seems solved by adding parport_pc to the /etc/modules file. Of course a reboot is necessary. For other readers, I've been told that this solution doesn't work for everyone, which is a sure sign that Jaunty is indeed faulty.

I stress on *for now*, since I don't have the means to extensively test the machine. What an irony..having one of the most stable kernels that is not able to load the proper modules.

---

### Post by j0eb0b on 2009-05-24
If an earlier distro works with your hardware then use it.  I will tell you that if you ever replace your computer or have to change the motherboard in your existing computer you will have to use a gender changing cable to support your parallel printer.  I upgrade rather than discard my hardware and had to face this fact 3 years ago.  To my knowledge no company has makes a motherboard that still includes a parallel port.  

Your comparisons to Microsoft provokes an interesting discussion.  My current machine runs Jaunty, Windows 7 and Windows XP.  As much as I would love to throw Microsoft over the transom, the only OS that supports all of my hardware and all of my programs is XP.  I have a Cannon PIXMA ip1600 attached that is a boat anchor with Unbuntu with no kluge available to get it to do anything.  Microsoft got a bad rap with Vista because of device drivers and program compatibility.  As much as I like Unbuntu and other Linux distros most of them are no better than Vista in supporting the universe of legacy hardware and software out there.  

Hope things return to normal for you when you fall back to 8.10 or 8.04.

---

### Post by 11hjpphty76lkjj on 2009-05-24
Please run:

hp-check -t

and post the entire output.

We're looking for the section that says pp-build= 

Should be yes, if it says no you'll need to reinstall HPLIP, do a custom install and enable parallel.

Aaron

---

### Post by Cubytus on 2009-05-25
**j0eb0b**, I still like to keep up to date with Ubuntu versions, since they usually provide enhancements. I do admit that WinXP has the greatest driver database I ever seen in any OS. Your experience in upgrading your hardware isn't in any way similar as mine, since I haven't upgraded since 8.04. Computer is still the same, say, crap, but functional crap :D I also hate to simply trash functional hardware, the reason why I'm still looking for charities dedicated to promoting Linux to the youth that would come home pick up the 4 functional CRTs and 1 dot-matrix printer I have. So far, none turned out to exist in Montreal. I would also gladly give them all that old computer & slow parallel laser printer if my father and I didn't need them. I would love to keep up-to-date with more powerful and eco-friendly technology, but money isn't there.

I also admit it's similarly very strange for *some* (seems to depend on the CPU you're using) full-size ATX motherboards not to include IEEE1284 capability although they still bear a completely useless and bulkier floppy port. What motherboard is not able to boot from USB or CD, nowadays? But if I was in such a case, I would still buy a IEEE1284 card for the same price as a cable converter (gender changer is an improper term since it implies that the port itself remains the same, which is untrue). Plus, as the 1100 uses a special cable, I'm unsure that it would easily pair with a converter. 

If you still find XP irreplaceable, you must have some custom applications for it. I don't miss any program from Windows except ISOBuster, that I can run in WINE.


**kalosaurusrex**, I solved the problem by adding **parport_pc** to the **/etc/modules** files; however, it is said that this solution doesn't work for everyone (Yes, it was that urgent to have printing capability that I didn't lose time and went straight to the solution). This is the output *after* modification. But remember you told me long ago that you had no way of testing HPLIP with the LaserJet 1100.
```
HP Linux Imaging and Printing System (ver. 3.9.2)
Dependency/Version Check Utility ver. 14.1

Copyright (c) 2001-8 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the HPLIP supplied tarball (.tar.gz or .run) to determine if   
the proper dependencies are installed to successfully compile HPLIP.                                                                        
2. Run-time check mode (-r or --run): Use this mode to determine if a distro supplied package (.deb, .rpm, etc) or an already built HPLIP   
supplied tarball has the proper dependencies installed to successfully run.                                                                 
3. Both compile- and run-time check mode (-b or --both) (Default): This mode will check both of the above cases (both compile- and run-time 
dependencies).                                                                                                                              

Saving output in log file: hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux tarcum-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

Distribution:
ubuntu 9.04

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.6.2 installed

Checking PyQt 4.x version...
error: NOT FOUND OR FAILED TO LOAD!

Checking for CUPS...
Status: l’ordonnanceur tourne
Version: 1.3.9
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
OK, found.

Checking for dependency: CUPS devel- Common Unix Printing System development files...
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
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libjpeg62-dev

Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libsnmp-dev

Checking for dependency: libpthread - POSIX threads library...
OK, found.

Checking for dependency: libtool - Library building support services...
OK, found.

Checking for dependency: libusb - USB library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libusb-dev

Checking for dependency: make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: ppdev - Parallel port support kernel module....
OK, found.

Checking for dependency: PyQt 4- Qt interface for Python (for Qt version 4.x)...
error: NOT FOUND! This is a REQUIRED/RUNTIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes python-qt4

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
error: NOT FOUND! This is a REQUIRED/RUNTIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes python-qt4-dbus

Checking for dependency: Python ctypes - A foreign function library for Python...
OK, found.

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python devel - Python development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes python2.5-dev

Checking for dependency: Python XML libraries...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.
To install this dependency, execute this command:
sudo aptitude install --assume-yes python-reportlab

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: SANE - Scanning library development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libsane-dev

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 3.9.2 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.9.2

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
internal-tag=3.9.2.49
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes




Current contents of '~/.hplip/hplip.conf' file:
[last_used]
printer = 
device_uri = Creates device URIs for local and network connected printers for use with CUPS.
	Usage: hp-makeuri [OPTIONS] [SERIAL NO.|USB ID|IP|DEVNODE]
	[SERIAL NO.|USB ID|IP|DEVNODE]
	USB IDs (usb        "xxx:yyy" where xxx is the USB bus ID and yyy is the
	only):              USB device ID. The ':' and all leading zeroes must be
	present.
	(Use the 'lsusb' command to obtain this information.
	See Note 1.)
	IPs (network        IPv4 address "a.b.c.d" or "hostname"
	only):
	DEVNODE (parallel   "/dev/parportX", X=0,1,2,...
	only):
	SERIAL NO. (usb     "serial no."
	and parallel
	only):
	[OPTIONS]
	To specify the      -p<port> or --port=<port> (Valid values are 1*, 2, and
	port on a           3. *default)
	multi-port
	JetDirect:
	Show the CUPS URI   -c or --cups
	only (quiet mode):
	Show the SANE URI   -s or --sane
	only (quiet mode):
	Show the HP Fax     -f or --fax
	URI only (quiet
	mode):
	Set the logging     -l<level> or --logging=<level>
	level:
	<level>: none, info*, error, warn, debug (*default)
	Run in debug mode:  -g (same as option: -ldebug)
	This help           -h or --help
	information:
	Examples:
	USB:                $ hp-makeuri 001:002
	Network:            $ hp-makeuri 66.35.250.209
	Parallel:           $ hp-makeuri /dev/parport0
	USB or parallel     $ hp-makeuri US123456789
	(using serial
	number):
	Notes:
	1. Example using 'lsusb' to obtain USB bus ID and USB device ID (example only, the values you obtain will differ) :
	$ lsusb
	Bus 003 Device 011: ID 03f0:c202 Hewlett-Packard
	$ hp-makeuri 003:011
	(Note: You may have to run 'lsusb' from /sbin or another location. Use '$ locate lsusb' to determine this.)
	See Also:
	hp-setup
set%20the%20logging%20%20%20%20%20-l%3clevel%3e%20or%20--logging = <level>
to%20specify%20the%20%20%20%20%20%20-p%3cport%3e%20or%20--port = <port> (Valid values are 1*, 2, and
devnode%20%28parallel%20%20%20%22\dev\parportx%22%2c%20x = 0, 1, 2, ...

[commands]
scan = /usr/bin/xsane -V %SANE_URI%

[installation]
date_time = 05/25/09 07:52:38
version = 3.9.2.49

[settings]
systray_visible = 0

[refresh]
rate = 30
enable = true
type = 1

[polling]
enable = false
device_list = 
interval = 5



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

 
warning: No queues found.

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
 
-----------
| SUMMARY |
-----------

error: 9 errors and/or warnings.

Summary of needed commands to run to satisfy missing dependencies:
sudo aptitude install --assume-yes libjpeg62-dev
sudo aptitude install --assume-yes libsnmp-dev
sudo aptitude install --assume-yes libusb-dev
sudo aptitude install --assume-yes python-qt4
sudo aptitude install --assume-yes python-qt4-dbus
sudo aptitude install --assume-yes python2.5-dev
sudo aptitude install --assume-yes python-reportlab
sudo aptitude install --assume-yes libsane-dev

Please refer to the installation instructions at:
http://hplip.sourceforge.net/install/index.html


Done.
```
There is pp-build=yes.

Do you want me to comment out the **parport_pc** line in **/etc/modules** to help you diagnose the issue?

If that helps, it's [this bug]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/369850") from Launchpad

---

### Post by 11hjpphty76lkjj on 2009-05-25
I don't remember sorry..but you are correct we don't have a LaserJet 1100 to test on.

The /etc/modules  **parport_pc **shouldn't be of any concern.  Although be sure that you are using the ppdev module.  You can look over this,

[http://hplipopensource.com/node/217](http://hplipopensource.com/node/217)

Although maybe you already have.

---

### Post by Cubytus on 2009-05-25
There I followed the steps in the link provided at the best of my knowledge:

```
tarcum@tarcum-desktop:~$ lsmod | grep ppdev
ppdev                  15620  0 
parport                42220  3 ppdev,parport_pc,lp

```

I then removed the printer from CUPS, and added it using **sudo hp-setup -i**. I then asked for a test page, but nothing came out, but I got an error message telling that HPLP couldn't communicate with the printer.

Same problem as a year and a half before.

---

### Post by 11hjpphty76lkjj on 2009-05-25
Are you using the same computer?  Can you try a different computer?  Can you check if the printer works with windows?

---

### Post by Cubytus on 2009-05-25
Yes, it's on the same computer. I don't have Windows on hand, but successfuly used that printer for about 3000 pages under Ubuntu 7.10 and 8.04. Not using HPLIP, however, but the built-in capabilities of Ubuntu.

---

### Post by uaskg on 2009-06-05
The suggested solution to add parport_pc to /etc/modules did not work for me. After reboot I got

askg@hp:~$ dmesg | grep parport
[   40.549127] parport: bad specifier `aut'
[   40.666100] parport: bad specifier `aut'
[   40.777822] parport: bad specifier `aut'

Which seems to point to one of the BIOS settings if I am not mistaken (I am connecting to the HP laptop over SSH).

So there must be more to it, for me at least.
/G

---

### Post by uaskg on 2009-06-06
> **uaskg said:**
> The suggested solution to add parport_pc to /etc/modules did not work for me. After reboot I got

askg@hp:~$ dmesg | grep parport
[   40.549127] parport: bad specifier `aut'
[   40.666100] parport: bad specifier `aut'
[   40.777822] parport: bad specifier `aut'

So there must be more to it, for me at least.
/G

Well, problem solved. The solution, it seemed, was elsewhere. I had already edited the file /etc/modprobe.d/alsa-base.conf following the advice in
[https://answers.launchpad.net/ubuntu/+question/69233](https://answers.launchpad.net/ubuntu/+question/69233)

But I had made a typo, writing "irq=aut" instead of "irq=auto" as suggested. This probably accounted for the error message from dmesg.

I quote from the advice:

  hi, i had same problem till today
  i only add that lines to /etc/modprobe.d/alsa-base.conf (maybe   
  yours is /etc/modprobe.conf)
  # parallel_port:
  alias parport_lowlevel parport_pc
  options parport_pc io=0x378 irq=auto

So that is what I should have done. I now did, but with irq=7. It works:

askg@hp:~$ dmesg | grep parport
[   40.712246] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   40.765221] parport0: Printer, Hewlett-Packard HP LaserJet 5L
[   40.767422] lp0: using parport0 (interrupt-driven).

/G

---

