---
title: "Printing a blank page"
date: 2007-01-07
forum: Hardware &amp; Laptops
---

### Post by Celestianpower on 2007-01-07
Hello.

I have a problem with my printer, or at least with printing. When I send a file to print (I've tried both Open Office files and PDFs), the printer starts up, the slider moves back and forth, and the job appears on the printing list. However, what comes out is just a blank page.

I have HP PSC 1410 printer (at least, that's what it says on the top); it has printed fine for about a year. I printed a test page, and that came out perfectly.

What am I to do? 

Thanks in advance for any help you can give. Kind regards,
CP

---

### Post by Celestianpower on 2007-01-07
> **Celestianpower said:**
> Hello.

I have a problem with my printer, or at least with printing. When I send a file to print (I've tried both Open Office files and PDFs), the printer starts up, the slider moves back and forth, and the job appears on the printing list. However, what comes out is just a blank page.

I have HP PSC 1410 printer (at least, that's what it says on the top); it has printed fine for about a year. I printed a test page, and that came out perfectly.

What am I to do? 

Thanks in advance for any help you can give. Kind regards,
CP
Did I post to the right section?

If not, my apologies, but there are an awful lot.

CP

---

### Post by tymek on 2007-03-19
Hello,

I have the same problem under Ubuntu 6.10 with my HP Deskjet 845c (connected via USB), however test print pages come out blank too.

Upon booting into Windows the printer prints normally.

tymek

---

### Post by 11hjpphty76lkjj on 2007-03-23
Please make sure you are using the latest version of HPLIP.

[http://hplip.sf.net](http://hplip.sf.net)

---

### Post by Tumpster on 2007-05-10
I've installed the latest version and I'm still getting blank pages!

---

### Post by 11hjpphty76lkjj on 2007-05-14
Are you able to print anything ever from the printer?  Can you connect it to a windows system and are you able to print?  How old are the ink cartridges and so forth?  The printer should work great, I've verified on another PSC1410 and it works...so i'm thinking there may be a hardware problem perhaps?

A

---

### Post by Tumpster on 2007-05-24
I have plenty of ink, I don't boot into windows but before when I was dual booting it printed fine in windows. Any ideas?

---

### Post by 11hjpphty76lkjj on 2007-05-25
Tumpster:

Really it sounds like a possible hardware issue.  If possible try and reproduce on another system.  I'm able to print to a PSC1410 with no problems on ubuntu--so really I'm leaning towards a hardware consideration with your situation.

A

---

### Post by nkjsat on 2007-05-26
i have hp deskjet 845c and i have the same problem too.Untill yesterday i was using kubuntu 7.04 and i had no problem with it.I think the problem is ubuntu.Any suggestions?

---

### Post by ozzy19 on 2007-11-06
This problem is really bugging me. Printing works fine in windows, everything is recognized properly in ubuntu but it prints blank pages.

---

### Post by 11hjpphty76lkjj on 2007-11-06
It works in windows but NOT ubuntu? That is odd.  Can you run hp-check and post the output?

A

---

### Post by gcrussell1 on 2007-11-11
@ KalosaurusRex (or anyone else who can help) - I'm running into the same problem as the other posters on this page - my printer (Deskjet 3558 ) prints in XP (tested after I first ran into the problem), but not in Gutsy.

I first had the problem under the 2.7.7 version of HPLIP from the repos, so I ran the latest HPLIP installer (2.7.10) and ran into a potential problem - at the end of the GUI phase where I was asked to identify my printer, everything seemed to go well until the end of the setup, when I got an error message along the lines of > Printer queue setup failed
Please restart CUPS and try again....and then it went back to the terminal and the installer was apparently finished.

Since I ran a comprehensive installer, I don't really know what CUPS is or how I should try again, or if that would help anyway. I ran hp-check (which only worked after running 2.7.10, and here are the resultsL```
hp-check[31028]: info: :
Initializing. Please wait...
Distributor ID:	Ubuntu


Release:	7.10


scheduler is running


1.3.2


Linux greg-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux


hp-check[31028]: info: :
hp-check[31028]: info: :---------------
hp-check[31028]: info: :| SYSTEM INFO |
hp-check[31028]: info: :---------------
hp-check[31028]: info: :
hp-check[31028]: info: :[01mBasic system information:[0m
hp-check[31028]: info: :Linux greg-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

hp-check[31028]: info: :
hp-check[31028]: info: :[01mDistribution:[0m
hp-check[31028]: info: :ubuntu 7.10
hp-check[31028]: info: :[01m
HPOJ running?[0m
hp-check[31028]: info: :No, HPOJ is not running (OK).
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking Python version...[0m
hp-check[31028]: info: :OK, version 2.5.1 installed
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking PyQt version...[0m
hp-check[31028]: info: :OK, version 3.17 installed.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking SIP version...[0m
hp-check[31028]: info: :OK, Version 4.7 installed
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for CUPS...[0m
hp-check[31028]: info: :Status: scheduler is running
hp-check[31028]: info: :Version: 1.3.2
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for Reportlab...[0m
hp-check[31028]: info: :OK, version >= 2.0
hp-check[31028]: info: :
hp-check[31028]: info: :----------------
hp-check[31028]: info: :| DEPENDENCIES |
hp-check[31028]: info: :----------------
hp-check[31028]: info: :
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for dependency: cups - Common Unix Printing System...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for dependency: cups-devel- Common Unix Printing System development files...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for dependency: gcc - GNU Project C and C++ Compiler...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for dependency: libcrypto - OpenSSL cryptographic library...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for dependency: libjpeg - JPEG library...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for dependency: libnetsnmp-devel - SNMP networking library development files...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for dependency: libpthread - POSIX threads library...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for dependency: libtool - Library building support services...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for dependency: libusb - USB library...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for dependency: make - GNU make utility to maintain groups of programs...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for dependency: ppdev - Parallel port support kernel module....[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for dependency: PyQt - Qt interface for Python...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for dependency: python-devel - Python development files...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for dependency: Python 2.3 or greater - Required for fax functionality...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for dependency: Python 2.2 or greater - Python programming language...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for dependency: Reportlab - PDF library for Python...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for dependency: SANE - Scanning library...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for dependency: SANE - Scanning library development files...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for dependency: scanimage - Shell scanning program...[0m
warning: NOT FOUND! This is an OPTIONAL dependency. Some HPLIP functionality may not function properly.
hp-check[31028]: info: :To install this dependency, execute this command:
hp-check[31028]: info: :sudo apt-get install --yes --force-yes libsane
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for dependency: xsane - Graphical scanner frontend for SANE...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :
hp-check[31028]: info: :----------------------
hp-check[31028]: info: :| HPLIP INSTALLATION |
hp-check[31028]: info: :----------------------
hp-check[31028]: info: :
hp-check[31028]: info: :
hp-check[31028]: info: :[01mCurrently installed HPLIP version...[0m
hp-check[31028]: info: :HPLIP 2.7.10 currently installed in '/usr/share/hplip'.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mCurrent contents of '/etc/hp/hplip.conf' file:[0m
hp-check[31028]: info: :# hplip.conf.  Generated from hplip.conf.in by configure.

[hpssd]
# Note: hpssd does not support dynamic ports
# Port 2207 is the IANA assigned port for hpssd
port=2207

[hplip]
version=2.7.10

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-2.7.10
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
foomatic=/usr/share/foomatic

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=no
gui-build=yes
scanner-build=yes
fax-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
foomatic-xml-install=yes
foomatic-ppd-install=no
internal-tag=2.7.10.11

hp-check[31028]: info: :
hp-check[31028]: info: :----------------------
hp-check[31028]: info: :| INSTALLED PRINTERS |
hp-check[31028]: info: :----------------------
hp-check[31028]: info: :
hp-check[31028]: info: :
hp-check[31028]: info: :[01mdeskjet_3500[0m
hp-check[31028]: info: :[01m------------[0m
hp-check[31028]: info: :Type: Printer
hp-check[31028]: info: :Installed in HPLIP?: Yes, using the hp: CUPS backend.
hp-check[31028]: info: :Device URI: hp:/usb/deskjet_3500?serial=CN3683F2059D
hp-check[31028]: info: :PPD: /etc/cups/ppd/deskjet_3500.ppd
hp-check[31028]: info: :PPD Description: HP DeskJet 3550 Foomatic/hpijs (recommended)
hp-check[31028]: info: :Printer status: printer deskjet_3500 is idle.  enabled since Mon 12 Nov 2007 10:55:20 AM CST

hp-check[31028]: info: :
hp-check[31028]: info: :----------------------
hp-check[31028]: info: :| SANE CONFIGURATION |
hp-check[31028]: info: :----------------------
hp-check[31028]: info: :
hp-check[31028]: info: :[01m'hpaio' in '/etc/sane.d/dll.conf'...[0m
hp-check[31028]: info: :OK, found. SANE backend 'hpaio' is properly set up.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking output of 'scanimage -L'...[0m
error: scanimage not found.
hp-check[31028]: info: :
hp-check[31028]: info: :---------------------
hp-check[31028]: info: :| PYTHON EXTENSIONS |
hp-check[31028]: info: :---------------------
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking 'cupsext' CUPS extension...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking 'pcardext' Photocard extension...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking 'hpmudext' I/O extension...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking 'scanext' SANE scanning extension...[0m
hp-check[31028]: info: :OK, found.
hp-check[31028]: info: :
hp-check[31028]: info: :
hp-check[31028]: info: :-----------------
hp-check[31028]: info: :| USB I/O SETUP |
hp-check[31028]: info: :-----------------
hp-check[31028]: info: :
hp-check[31028]: info: :
hp-check[31028]: info: :[01mChecking for permissions of USB attached printers...[0m
hp-check[31028]: info: :HP Device 0x7304 at 005:004: 
hp-check[31028]: info: :    Device URI: hp:/usb/deskjet_3500?serial=CN3683F2059D
hp-check[31028]: info: :    Device node: /dev/bus/usb/005/004
hp-check[31028]: info: :    Mode: 0666
hp-check[31028]: info: :
hp-check[31028]: info: :-----------
hp-check[31028]: info: :| SUMMARY |
hp-check[31028]: info: :-----------
hp-check[31028]: info: :
error: 1 error or warning.
hp-check[31028]: info: :
hp-check[31028]: info: :[01mSummary of needed commands to run to satisfy missing dependencies:[0m
hp-check[31028]: info: :sudo apt-get install --yes --force-yes libsane
hp-check[31028]: info: :
hp-check[31028]: info: :Please refer to the installation instructions at:
hp-check[31028]: info: :http://hplip.sourceforge.net/install/index.html
```Anyway, after all of this, I tried to print a page from abiword (OOo's been a bit spastic for me lately), and it remained blank - the printer runs like normal, the print heads print, but the ink doesn't come out. Any ideas?

---

### Post by 11hjpphty76lkjj on 2007-11-12
Try running:

sudo /etc/init.d/cupsys restart

and then printing. Although you said the print head moves..but it doesn't print...

Can you run

sudo tail -f /var/log/messages

and then try printing and post any messages from the /var/log/messages

A

---

### Post by gcrussell1 on 2007-11-12
> **kalosaurusrex said:**
> 
sudo /etc/init.d/cupsys restart
No dice
[QUOTE=kalosaurusrex]Can you run

sudo tail -f /var/log/messages

and then try printing and post any messages from the /var/log/messages

A[/QUOTE]I'm not sure that I understand what you're asking - when I run the above command in Terminal, it comes up with the log and locks up my terminal (probably a way around this, but I'm pretty noobish). I tried printing with gedit (using the GUI) after running the above command with the same results as usual, but the log didn't seem to update - when I ran *less /var/log/messages* the last entry in the log was from before I ran your command above. Did I do something other than what you intended?

---

### Post by 11hjpphty76lkjj on 2007-11-13
If you are looking at the log it shouldn't lock up terminal...I've done it a million times w/o that result.  You may have some sort of system problem going on.  

What happened when you ran

```
sudo /etc/init.d/cupsys restart
```

any errors?  and then try to print? If you goto 

```
http://localhost:631
```

what version of cups does it say you are using?

A

---

### Post by gcrussell1 on 2007-11-14
Sorry, "locks up" wasn't the right way to put it, I just mean that it takes over the terminal and I don't have a command line there anymore - it runs fine, but without a typical command line I'm worthless (though I'm arguably worthless with a typical command line as well), so I couldn't actually print through that terminal unless there's something I don't know (99.95% chance that there is in this case). While I had that terminal running, however, I tried to print out of gedit and had the same problem, and nothing came up on the log in the terminal, and when I *less*ed the log after closing gedit and the terminal containing the log, there were no entries that weren't there before the attempted print job.

Also, I ran the restart cupsys command you gave me, and it restarted just fine, but still had the same printing problem after the cupsys restart. I'm running CUPS 1.3.2.

Incidentally, is there anything REALLY basic that I might be missing, like needing to start up the computer with the printer plugged in and turned on (I don't keep it plugged in for lack of outlets and USB ports normally)? That seems to happen a lot with Linux noobs like myself.

---

### Post by briandu on 2007-11-14
Hi there,

may I suggest the following:
goto [http://localhost:631](http://localhost:631) and manual modify your printer driver to use CUPS and not the hplip.

I had a similar problem with my HP1100 - it would work erratically. Once I changed it from foomatic..etc. to CUPS the probs all disappeared.

try it.

Good luck:guitar:

---

### Post by linuxonbute on 2007-11-14
> **gcrussell1 said:**
> No dice
I'm not sure that I understand what you're asking - when I run the above command in Terminal, it comes up with the log and locks up my terminal (probably a way around this, but I'm pretty noobish). I tried printing with gedit (using the GUI) after running the above command with the same results as usual, but the log didn't seem to update - when I ran *less /var/log/messages* the last entry in the log was from before I ran your command above. Did I do something other than what you intended?

tail  with the -f option keeps tail running and updating it's output. It's purpose is so you can run some other program and then look back at the output of tail to see what has happened.

to get back to your prompt press and keep pressed the Control key  (  marked Ctrl and near bottom left of the keyboard )  and c

---

### Post by 11hjpphty76lkjj on 2007-11-14
If you can run the PrintingBugInfo Script and post the output.

HPLIP should work fine on gutsy..i'm using hplip 2.6.10 on gutsy with no problems. (and i've tested it on a lot of printers) But I'm thinking there may be a problem with the feisty -> gutsy upgrade that is breaking.  did you do a clean install or upgrade?

[https://wiki.ubuntu.com/PrintingBugInfoScript](https://wiki.ubuntu.com/PrintingBugInfoScript)

A

---

### Post by gcrussell1 on 2007-11-14
> **linuxonbute said:**
> tail  with the -f option keeps tail running and updating it's output. It's purpose is so you can run some other program and then look back at the output of tail to see what has happened.

to get back to your prompt press and keep pressed the Control key  (  marked Ctrl and near bottom left of the keyboard )  and cYeah... I ran across that keystroke pair in a tutorial a couple weeks ago, but I totally forgot the keystrokes involved... I thought it had something to do with one of the f- keys. ](*,) I ran gedit through the terminal, typed up abcdefg and hit print, and the terminal got bombarded with errors:```
Model not found, discarding config

(gedit:6062): GnomePrint-WARNING **: Could not create filter from description 'GnomePrintFilterSelect': filter 'GnomePrintFilterSelect' is unknown

(gedit:6062): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:6062): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:6062): GnomePrint-WARNING **: Could not create filter from description 'GnomePrintFilterClip [ GnomePrintFilterMultipage ]': filter 'GnomePrintFilterClip' is unknown

(gedit:6062): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gedit:6062): libgnomeprintui-CRITICAL **: gnome_print_layout_selector_load_filter: assertion `GNOME_IS_PRINT_FILTER (f)' failed

(gedit:6062): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:6062): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:6062): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:6062): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:6062): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:6062): GnomePrint-CRITICAL **: gnome_print_filter_reset: assertion `GNOME_IS_PRINT_FILTER (f)' failed

(gedit:6062): GnomePrint-CRITICAL **: gnome_print_filter_flush: assertion `GNOME_IS_PRINT_FILTER (f)' failed

(gedit:6062): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:6062): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:6062): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:6062): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:6062): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:6062): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:6062): GnomePrint-CRITICAL **: gnome_print_filter_reset: assertion `GNOME_IS_PRINT_FILTER (f)' failed

(gedit:6062): GnomePrint-CRITICAL **: gnome_print_filter_flush: assertion `GNOME_IS_PRINT_FILTER (f)' failed

** (gedit:6062): WARNING **: could not set the value of Settings.Document.Filter, node not found
```
> **kalosaurusrex said:**
> If you can run the PrintingBugInfo Script and post the output.

HPLIP should work fine on gutsy..i'm using hplip 2.6.10 on gutsy with no problems. (and i've tested it on a lot of printers) But I'm thinking there may be a problem with the feisty -> gutsy upgrade that is breaking.  did you do a clean install or upgrade?

[https://wiki.ubuntu.com/PrintingBugInfoScript](https://wiki.ubuntu.com/PrintingBugInfoScript)

ARan it (with the -u switch), and here's the output:```
ProblemType: printingbuginfo v2.0: printingbug+localusb (https://wiki.ubuntu.com/PrintingBugInfoScript)
CupsConfiguredDevices: device for deskjet_3500: hp:/usb/deskjet_3500?serial=CN3683F2059D
CupsConfiguredPPDs: deskjet_3500: HP DeskJet 3550 Foomatic/hpijs (recommended)
Date: Thu Nov 15 10:53:52 2007
DesktopEnvironment: GNOME
DistroRelease: Ubuntu 7.10
EtcPapersize: letter
InstalledPrintingPackages:
 ii  cupsys                   1.3.2-1ubuntu7           Common UNIX Printing System(tm) - server
 ii  cupsys-driver-gutenprint 5.0.1-0ubuntu8           printer drivers for CUPS
 ii  foo2zjs                  20070625-0ubuntu1        Support for printing to ZjStream-based printers
 ii  foomatic-db              20070919-0ubuntu3        OpenPrinting printer support - database
 ii  foomatic-db-engine       3.0.2-20070719-0ubuntu4  OpenPrinting printer support - programs
 ii  foomatic-db-gutenprint   5.0.1-0ubuntu8           OpenPrinting printer support - database for Gutenprint printer d
 ii  foomatic-db-hpijs        20070813-0ubuntu1        OpenPrinting printer support - database for HPIJS driver
 ii  foomatic-filters         3.0.2-20070719-0ubuntu1  OpenPrinting printer support - filters
 ii  ghostscript              8.61.dfsg.1~svn8187-0ubu The GPL Ghostscript PostScript/PDF interpreter
 ii  hpijs                    2.7.7+2.7.7.dfsg.1-0ubun HP Linux Printing and Imaging - gs IJS driver (hpijs)
 ii  hplip                    2.7.7.dfsg.1-0ubuntu5    HP Linux Printing and Imaging System (HPLIP)
 ii  ijsgutenprint            5.0.1-0ubuntu8           inkjet server - Ghostscript driver for Gutenprint
 ii  libgnomeprint2.2-0       2.18.2-0ubuntu1          The GNOME 2.2 print architecture - runtime files
 ii  min12xxw                 0.0.9-1build1            Printer driver for KonicaMinolta PagePro 1[234]xxW
 ii  openprinting-ppds        20070919-0ubuntu3        OpenPrinting printer support - PostScript PPD files
 ii  pnm2ppa                  1.12-16                  PPM to PPA converter
 ii  pxljr                    1.1-0ubuntu1             Driver for HP's Color LaserJet 35xx/36xx color laser printers
 ii  splix                    1.0.1.1-0ubuntu2         Driver for Samsung's SPL2 (bw) and SPLc (color) laser printers
 ii  system-config-printer    0.7.75+svn1653-0ubuntu2  Printer configuration GUI
Locale: LANG=en_US.UTF-8, LC_CTYPE=en_US.UTF-8, LC_PAPER=en_US.UTF-8
Uname: Linux greg-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
UsbPrinterDevices: 
UsbPrinterIEEE1284Id: 
UsbPrinterKernelModules:
 usblp                  15104  0 
 usbcore               138632  7 usblp,snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,ohci_hcd
lsusb:
 Bus 005 Device 005: ID 041e:4045 Creative Technology, Ltd 
 Bus 005 Device 004: ID 041e:4048 Creative Technology, Ltd 
 Bus 005 Device 003: ID 041e:404b Creative Technology, Ltd 
 Bus 005 Device 001: ID 0000:0000  
 Bus 002 Device 001: ID 0000:0000  
 Bus 003 Device 003: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
 Bus 003 Device 001: ID 0000:0000  
 Bus 004 Device 002: ID 03f0:7304 Hewlett-Packard DeskJet 35xx
 Bus 004 Device 001: ID 0000:0000  
 Bus 001 Device 001: ID 0000:0000  
```It's telling me that I'm still using HPLIP 2.7.7 - though I installed 2.7.10 (with a problem - see a previous post). Could that possibly be part of the issue?

EDIT: I forgot to mention - Gutsy has been my first experience with Linux in any form - so no upgrade issues from Feisty. I've got a Feisty Live CD but the only time it's ever been in my computer was when I burned it...

---

### Post by pyman on 2007-11-26
I had the same issue printing a blank page with my HP 1315xi all in one
All I had to do was go into 

[http://localhost:631](http://localhost:631)
set up to use cups then
sudo /etc/init.d/cupsys restart
and everything starte working..
It's magic... I swear....
:guitar:

---

