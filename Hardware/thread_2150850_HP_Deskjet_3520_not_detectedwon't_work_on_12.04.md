---
title: "HP Deskjet 3520 not detected/won't work on 12.04"
date: 2013-06-02
forum: Hardware
---

### Post by dzorug on 2013-06-02
Really new to linux. Using Ubuntu 12.04 64-bit, just got an HP Deskjet 3520 e-All-in-One printer. Trying to print it, but can't. hplib 3.12.1 won't detect the printer, even though the model is supposedly supported. Help please?

Here's the log for hp-check -t:

```
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

hp-check[4536]: info: :
hp-check[4536]: info: :Current contents of '/var/lib/hp/hplip.state' file:
hp-check[4536]: info: :# hplip.state - HPLIP runtime persistent variables. 

[plugin]
installed=0
eula=0


hp-check[4536]: info: :
hp-check[4536]: info: :Current contents of '~/.hplip/hplip.conf' file:
hp-check[4536]: info: :[settings]
systray_visible = 0
systray_messages = 0

[last_used]
device_uri = 
printer_name = 
working_dir = .

[commands]
scan = /usr/bin/simple-scan %SANE_URI%

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

[installation]
date_time = 03/06/2013 00:47:44
version = 3.12.2


hp-check[4536]: info: :
hp-check[4536]: info: :--------------------------
hp-check[4536]: info:  DISCOVERED USB DEVICES |
hp-check[4536]: info: :--------------------------
hp-check[4536]: info: :
hp-check[4536]: info: :No devices found.
hp-check[4536]: info: :
hp-check[4536]: info: :---------------------------------
hp-check[4536]: info:  INSTALLED CUPS PRINTER QUEUES |
hp-check[4536]: info: :---------------------------------
hp-check[4536]: info: :
hp-check[4536]: info: :
hp-check[4536]: info: :HP-Deskjet-3520
hp-check[4536]: info: :---------------
hp-check[4536]: info: :Type: Unknown
hp-check[4536]: info: Device URI: usb://HP/Deskjet%203520%20series?serial=CN2BR1G1DM05SY&interface=1
hp-check[4536]: info: PPD: /etc/cups/ppd/HP-Deskjet-3520.ppd
hp-check[4536]: info: PPD Description: HP Deskjet 3500, hpcups 3.12.2
hp-check[4536]: info: Printer status: printer HP-Deskjet-3520 is idle.  enabled since Sun 02 Jun 2013 10:21:39 PM
    Rendering completed
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.
hp-check[4536]: info: :
hp-check[4536]: info: :
hp-check[4536]: info: :----------------------
hp-check[4536]: info:  SANE CONFIGURATION |
hp-check[4536]: info: :----------------------
hp-check[4536]: info: :
hp-check[4536]: info: :'hpaio' in '/etc/sane.d/dll.conf'...
hp-check[4536]: info: :'hpaio' in '/etc/sane.d/dll.d/hplip'...
hp-check[4536]: info: :OK, found. SANE backend 'hpaio' is properly set up.
hp-check[4536]: info: :
hp-check[4536]: info: :Checking output of 'scanimage -L'...
hp-check[4536]: info: :
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

hp-check[4536]: info: :
hp-check[4536]: info: :---------------------
hp-check[4536]: info:  PYTHON EXTENSIONS |
hp-check[4536]: info: :---------------------
hp-check[4536]: info: :
hp-check[4536]: info: :Checking 'cupsext' CUPS extension...
hp-check[4536]: info: :OK, found.
hp-check[4536]: info: :
hp-check[4536]: info: :Checking 'pcardext' Photocard extension...
hp-check[4536]: info: :OK, found.
hp-check[4536]: info: :
hp-check[4536]: info: :Checking 'hpmudext' I/O extension...
hp-check[4536]: info: :OK, found.
hp-check[4536]: info: :
hp-check[4536]: info: :Checking 'scanext' SANE scanning extension...
hp-check[4536]: info: :OK, found.
hp-check[4536]: info: :
hp-check[4536]: info: :
hp-check[4536]: info: :
hp-check[4536]: info: :-----------------
hp-check[4536]: info:  USB I/O SETUP |
hp-check[4536]: info: :-----------------
hp-check[4536]: info: :
hp-check[4536]: info: :Checking for permissions of USB attached printers...
hp-check[4536]: info: :
HP Device 0xb011 at 002:005: 
hp-check[4536]: info: :    Device URI: hp:/usb/Deskjet_3520_series?serial=CN2BR1G1DM05SY
error: Unsupported model: Deskjet_3520_series
hp-check[4536]: info: :
hp-check[4536]: info: :---------------
hp-check[4536]: info:  USER GROUPS |
hp-check[4536]: info: :---------------
hp-check[4536]: info: :
hp-check[4536]: info: :sparrow adm cdrom sudo dip plugdev lpadmin sambashare

error: User needs to be member of group 'lp' to enable print, scan & fax.
hp-check[4536]: info: :User member of group 'lpadmin'.
hp-check[4536]: info: :
hp-check[4536]: info: :-----------
hp-check[4536]: info:  SUMMARY |
hp-check[4536]: info: :-----------
hp-check[4536]: info: :
error: 14 errors and/or warnings.
hp-check[4536]: info: :
hp-check[4536]: info: Please refer to the installation instructions at:
hp-check[4536]: info: :[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

hp-check[4536]: info: :
hp-check[4536]: info: Done.
```

---

### Post by gordintoronto on 2013-06-02
Is the printer plugged in on the computer you are using, or is it a network printer?

I would run Printing, click on "Add" then "network printer" if appropriate. Select the printer, assuming it shows up, then "forward" and "apply." For my Brother laser, that's it, the drivers are automatically installed.

Don't be in a rush. A couple of those steps take a few seconds to complete.

---

### Post by Yellow Pasque on 2013-06-03
> hplip 3.12.1 won't detect the printer
...
> Minimum HPLIP version	3.12.6
[http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_3520_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_3520_series.html)

---

### Post by Mark Phelps on 2013-06-03
As an alternative, consider using CUPS.  I have used HP all-in-ones over the years and CUPS has always been able to find them and allow me to install the right drivers.  To get to CUPS, open a browser and enter "localhost:631".  Then, go to the page to add a printer.  CUPS will do a search and should find your printer.  If it does, just continue through the setup to install the drivers.

---

### Post by kurt18947 on 2013-06-03
> **Mark Phelps said:**
> As an alternative, consider using CUPS.  I have used HP all-in-ones over the years and CUPS has always been able to find them and allow me to install the right drivers.  To get to CUPS, open a browser and enter "**localhost:731**".  Then, go to the page to add a printer.  CUPS will do a search and should find your printer.  If it does, just continue through the setup to install the drivers.

Should that be localhost:631? :D

---

### Post by Mark Phelps on 2013-06-04
> **kurt18947 said:**
> Should that be localhost:631? :D

YES -- thanks for catching my typo (fixed it).

---

### Post by lammergeir on 2014-01-10
Mark Phelps, thank you for your help.  I've been unsuccessfully trying to instal Epson L300 printer in 13.10 x64. For some reason, the printer install wizard takes me to the download from Epson, and then selects dot matrix printer.   I followed your advicew usings CUPS, and now have a functioning printer!  You've saved what little hair this 65-yr old has left!!!

---

### Post by jim-n-lyne on 2014-03-27
> **Mark Phelps said:**
> As an alternative, consider using CUPS.  I have used HP all-in-ones over the years and CUPS has always been able to find them and allow me to install the right drivers.  To get to CUPS, open a browser and enter "localhost:631".  Then, go to the page to add a printer.  CUPS will do a search and should find your printer.  If it does, just continue through the setup to install the drivers.

I have an hp 3520 on a wireless netwok and used your directions. When I try to print to the printer, the printer wakes up (the panel lights up) but nothing prints. I seems like something is being sent to the printer but nothing prints. Any thoughts? I am a rookie.

thanks

---

### Post by oldfred on 2014-03-27
Did you install latest HPlip version. I found with 12.04 it installed a version that was too old and had to download the latest directly from HP.

HP Deskjet 3520
[http://ubuntuforums.org/showthread.php?t=2109050](http://ubuntuforums.org/showthread.php?t=2109050)
HP's newest On this website you can download the HPLIP software which supports 2,211 HP printers on nearly any Linux distribution available today.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
Ubuntu's older version
sudo apt-get install hplip-gui
gksudo hp-setup
# new version
hp-upgrade

No system tray error:
open up the "startup applications" editor from the admin menu.
add a new program, for the command put:
sleep 10;/usr/bin/hp-systray

---

### Post by jim-n-lyne on 2014-03-27
i'll give it a try, thanks

---

