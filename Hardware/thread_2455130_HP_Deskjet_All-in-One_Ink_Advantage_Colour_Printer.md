---
title: "HP Deskjet All-in-One Ink Advantage Colour Printer Compatibility"
date: 2020-12-13
forum: Hardware
---

### Post by 3dmatrix on 2020-12-13
My old printer was **_HP DeskJet 2135 All-in-One Ink Advantage Colour Printer_** which worked very well with several versions of Linux and HPLIP 3.16.3
Now I need to buy a new printer which I wish is of similar class.
I am thinking of :
**HP DeskJet 2335 All-in-One Ink Advantage Colour Printer** OR
**HP DeskJet 2778 All-in-One Ink Advantage Wireless Colour Printer**

Can any one tell me about the compatibility of these two printers (especially the first one '2335') with Linux.
On the following website :
[https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index](https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index)
I found

[ATTACH=CONFIG]287542[/ATTACH]

I am not sure what does the term "*_**HP DeskJet Ink Advantage 2300 All-in-One**_*" means.
Does it includes all printer in that series that start with 23XX, which should include HP DeskJet 2335 All-in-One Ink Advantage Colour Printer also ?

**EDIT**
I finally bought **HP DeskJet 2778 All-in-One Ink Advantage Wireless Colour Printer** and it is giving some trouble as mentioned in later posts. Would also like to mention that though this printer has wireless capability, I am not interested in using that feature. So _if anyone can_ kindly help me with its USB cable connectivity only. Help with wireless connectivity is not needed.


.

---

### Post by CelticWarrior on 2020-12-13
> **3dmatrix said:**
> I am not sure what does the term "*_**HP DeskJet Ink Advantage 2300 All-in-One**_*" means.
Does it includes all printer in that series that start with 23XX, which should include HP DeskJet 2335 All-in-One Ink Advantage Colour Printer also ?

Yes, that's exactly what it means.
Ubuntu 20.04 has hplip 3.20.3,
Ubuntu 20.10 has hplip 3.20.5, the minimum version that supports both of those printers.

---

### Post by 3dmatrix on 2020-12-13
Thank you. 
Regarding a printer say **_Canon Pixma E477_**, here ( [https://www.openprinting.org/printer/Canon/Canon-Pixma_E400_Series](https://www.openprinting.org/printer/Canon/Canon-Pixma_E400_Series) ) it mentions 

**Canon Pixma E400 Series**	Color inkjet printer, works *_Mostly_*		
User-contributed Printer Entry
This printer entry was contributed by a user but was not yet verified or proofread by the site administrators. Therefore it is not included in the **_Foomatic_** packages.

But I have noticed many places users have mentioned that they face a lot of problem with Canon printers. Does any one has any experience with Canon Pixma E477 printer ?

---

### Post by CelticWarrior on 2020-12-13
I have some experience.
Most of times most of the models work fine when drivers are installed. Some newer models likely work driverless as well.

---

### Post by 3dmatrix on 2020-12-14
Actually my use of printer is very limited. Average, barely one BW print a day. Rather scanning is still more important.
So for that I do not wish to spend too much money. Just need a basic printer which works for sure.
Do not wish to waste money buying something that will finally be used as a paperweight  :)

---

### Post by 3dmatrix on 2020-12-14
I apologise for my ignorance, but can any one tell me in short how can a wifi enabled Printer / scanner help me to overcome the driver / hardware incompatibility with Linux.
If I have a wifi enabled printer can I straight off print from my computer using wifi ? Without the need of any extra driver or software ?

---

### Post by tokyobadger on 2020-12-15
I recently bought a Canon Pixus TS8430 (printer/scanner), connected it to the router over wifi by selecting it on the printers control panel. My desktop which is hardwired to the same router then picked it up immediately no additional drivers installed.

Both printing and scanning worked fine. Only thing I had to do was select A4 over default Letter.

---

### Post by 3dmatrix on 2020-12-15
> **tokyobadger said:**
> I recently bought a Canon Pixus TS8430 (printer/scanner), connected it to the router over wifi by selecting it on the printers control panel. My desktop which is hardwired to the same router then picked it up immediately no additional drivers installed.

Both printing and scanning worked fine. Only thing I had to do was select A4 over default Letter.

Thanks. 
Unfortunately Canon Pixus series is not available in my area.

---

### Post by tokyobadger on 2020-12-21
The Pixus is sold in other markets as Pixma, for example the Pixma TS8320 sold in the US looks identical to my printer. More relevantly the LCD display is showing the same info as my printer. In 2020, it is highly unlikely that a printer/scanner manufacturer would develop market-specific software so I'd hazard guess that hooking this model up in the same way I did mine would result in the same functionality.

I would also guess that other manufacturers (eg HP) are using same/similar protocol(s); second guess would be that if the device supports Apple AirPrint you'd be able to print over wifi on an up-to-date Ubuntu install (if connected to the same router)

---

### Post by 3dmatrix on 2020-12-22
Finally I bought **HP DeskJet 2778 All-in-One Ink Advantage Wireless Colour Printer** and unfortunately it is not working well with Lubuntu.
I have installed HPLIP 3.20.X printer is not being recognised well, at least through the HPLIP interface. But somehow can manage to print if I ask Lubuntu to recognise it as some other model but Scanning is just not possible. Can any one please help me to install this printer properly. 

I used **hp-plugin** and **hp-doctor** commands but nothing worked.

**hp-plugin** : It tried looking for plugin and then looked for some authintication KEY. Said could not download the KEY. I asked it to proceed without it. Then it asked for root password. After entering that it gave an error :
[COLOR="#FF0000"][B]error : Python gobject/dbus may be not installed
error : Plug-in install failed[/B][/COLOR]
I tried installing what ever I could find relevant but nothing worked.

---

### Post by CelticWarrior on 2020-12-22
A week ago I told you:
> [COLOR=#000000]Ubuntu 20.10 has hplip 3.20.5, the minimum version that supports both of those printers.[/COLOR]

Are you running 20.10?

---

### Post by 3dmatrix on 2020-12-23
I know that, that is why I downloaded and installed HPLIP 3.20.11 on my Lubuntu.
But it is not working.

---

### Post by brian_p on 2020-12-23
> **3dmatrix said:**
> I know that, that is why I downloaded and installed HPLIP 3.20.11 on my Lubuntu.
But it is not working.

Whyever are you using HPLIP?

The device is wireless capable. You are advised to read

 [https://wiki.debian.org/CUPSQuickPrintQueues](https://wiki.debian.org/CUPSQuickPrintQueues)

---

### Post by brian_p on 2020-12-23
> **brian_p said:**
> Whyever are you using HPLIP?

To make this most pointed: your device will operate perfectly well without going near HPLIP. I expect you see it as important because its name begins with "HP".

> The device is wireless capable. You are advised to read

 [https://wiki.debian.org/CUPSQuickPrintQueues](https://wiki.debian.org/CUPSQuickPrintQueues)

My crystal ball tells me that, for reasons you are unwilling to reveal, you wish to avoid a wireless connection. It would be interesting to learn the rationale.

So be it. You will be forever trying to get HPLIP 3.20.11 working and, into the bargain, have other users doing your legwork for you.

---

### Post by 3dmatrix on 2020-12-24
> **brian_p said:**
> Whyever are you using HPLIP?
My crystal ball tells me that, for reasons you are unwilling to reveal, you wish to avoid a wireless connection. It would be interesting to learn the rationale.

I did not buy this printer for its wifi capability. I bought it because it was mentioned on HP's website that it is **FULLY** supported by HPLIP. I anyway neither like nor find wireless connection very secure. If I have to use it I do not need to do much I can simply scan documents using HP smart app on android but I do not want to involve wireless connection or any android device. I wish to simply connect my computer with the printer using USB cable and that is very simple and secure. Moreover many routers create problem as some wireless printer connections need static IP and with Dynamic IP every time the router is restarted IP changes.

**EDIT**
*_Made the following change in the first post._*
I finally bought **HP DeskJet 2778 All-in-One Ink Advantage Wireless Colour Printer** and it is giving some trouble as mentioned in later posts. Would also like to mention that though this printer has wireless capability, I am not interested in using that feature. So _if any one can_, kindly help me with its USB cable connectivity _only_. _Help with wireless connectivity is not needed_.

---

### Post by brian_p on 2020-12-24
It is highly that the DeskJet 2778 supports **IPP-over-USB**. See the relevant sections at

[https://wiki.debian.org/CUPSDriverlessPrinting](https://wiki.debian.org/CUPSDriverlessPrinting)

Purge **ippusbxd**, install **ipp-usb** and **sane-airscan**, and read

[https://forums.linuxmint.com/viewtopic.php?f=51&t=329760](https://forums.linuxmint.com/viewtopic.php?f=51&t=329760)

---

### Post by kurt18947 on 2020-12-25
If your distro doesn't include it, I'd recommend installing system-config-printer, it's found in the repositories. Then start it from a terminal or command window (alt+f2). I find this more informative than the default printer app. HP has had an excellent reputation for working with Linux, I wonder if that's changing.

---

### Post by 3dmatrix on 2020-12-25
> **kurt18947 said:**
> If your distro doesn't include it, I'd recommend installing system-config-printer, it's found in the repositories. Then start it from a terminal or command window (alt+f2). I find this more informative than the default printer app. HP has had an excellent reputation for working with Linux, I wonder if that's changing.

I was also under that kind of impression about HP so I was not looking for any option other than HP. May be I was wrong.

.

---

### Post by 3dmatrix on 2020-12-25
> **brian_p said:**
> It is highly that the DeskJet 2778 supports **IPP-over-USB**. See the relevant sections at

[https://wiki.debian.org/CUPSDriverlessPrinting](https://wiki.debian.org/CUPSDriverlessPrinting)

Purge **ippusbxd**, install **ipp-usb** and **sane-airscan**, and read

[https://forums.linuxmint.com/viewtopic.php?f=51&t=329760](https://forums.linuxmint.com/viewtopic.php?f=51&t=329760)

Thanks Brian.
Will go through those links and get back.
But is _sane-airscan_ not about wireless connection ?

---

### Post by brian_p on 2020-12-26
> But is sane-airscan not about wireless connection ?

The Debian wiki deals with this. IPP-over-USB effectively makes the device a networked one.

---

### Post by 3dmatrix on 2021-01-04
> **CelticWarrior said:**
> Yes, that's exactly what it means.
Ubuntu 20.04 has hplip 3.20.3,
Ubuntu 20.10 has hplip 3.20.5, the minimum version that supports both of those printers.

For my **_HP DeskJet 2778 All-in-One Ink Advantage Wireless Colour Printer_**

I installed **_3.20.11_** but still it does not works.
Tried 

[I]hp-plugin
sudo hp-plugin
hp-doctor
hp-setup[/I]

nothing worked. Each one of them finally ended with some error or the other.
Some how I identify one other model of printer in hp-toolbox, as my printer, and that is how I am able to some how take prints.
But scanning is just not possible.
Simple Scan says "**No Scanner found**"
I use an android app on mobile to do the scanning.
Do you have any suggestion ?

.

---

### Post by fabio1959 on 2021-01-05
[FONT=verdana]Ciao
I wasted hours and hours installing HPLIP ... desperation.:(
[/FONT]
[FONT=verdana]I encountered all the errors mentioned in all forums around the world about HPLIP. 

[/FONT]
[FONT=verdana]The result is that I installed 3.20.11 without any particular commands or as a super user. 

[/FONT]
[FONT=verdana]State of the art: 
1) 2 pc with Ubuntu 18.04 and HPLIP versions 3.18 and 3.17 to print and scan on HP 2600.
[/FONT]
[FONT=verdana]2) I bought a new HP Plus 4110 all in one
[/FONT]
[FONT=verdana]To print no problem but for the scanner ... the black death. [/FONT]
[FONT=verdana]3) everything is in wifi 

[/FONT]
[FONT=verdana]So:[/FONT]
[FONT=verdana]1) Beginning download hplip-x.xx.xx and put in wherever  you want (for me Download/hp ) and remove the previous version if the case
#hp-uninstall 

[/FONT]
[FONT=verdana]2 ) to be sure 
#sudo apt-get purge hplip hplip-data hplip-doc hplip-gui hpijs-ppds \ libsane-hpaio printer-driver-hpcups printer-driver-hpijs 
[/FONT]
[FONT=verdana]#sudo rm -rf / usr / share / hplip /
[/FONT]
[FONT=verdana]#sudo apt-get autoremove

[/FONT]
[FONT=verdana]3) Restart SYS (to avoid Murphy's law) 

4) Finally install it
#sh hplip-3.20.11.run
[/FONT]
[FONT=verdana]4a) always answer with the default and, if necessary, with the GUI version.
4b) will probably go to stop (no system try detected )(4bb) or you will arrive at configuration (4cc) of the printer in both if (4aa) you have to launch #hp-setup manually

[/FONT]
[FONT=verdana]5) Configuration
#hp-setup 

[/FONT]
[FONT=verdana]a) choose NETWORK, manual setting and give the printer's IP address ... if it doesn't find it, do everything again from the beginning . 
If printer will be found select it from the list (click on) and go ahead. 
[/FONT]
[FONT=verdana]If it says that the queue already exists ... install anyway

[/FONT]
[FONT=verdana]6) Driver for the scanner (I think so)
#hp-plugin (you could be here from the beginning but, if not the case run manually the command)
[/FONT]
[FONT=verdana]Wait, wait ... based on, I don't know what, (trying again it finds) it should get ok but if it doesn't find, install it anyway....64 files will be installed. 

[/FONT]
[FONT=verdana]7) Restart SYS (to avoid Murphy's law) 

[/FONT]
[FONT=verdana]8) Test scanner and printer

[/FONT]
[FONT=verdana]9) Restart SYS (to avoid Murphy's law) 

[/FONT]
[FONT=verdana]10) It should be the end the battle ... not the war ;-)


[/FONT]

---

### Post by 3dmatrix on 2021-01-10
I have wasted weeks with this printer and it does not works. Not astonished why people moving from another platform find so difficult to adjust to Linux.

I tried what is mentioned in the previous post but did not help much.

Output of hp-doctor command is pasted here.

```
$ hp-doctor

HP Linux Imaging and Printing System (ver. 3.20.11)
Self Diagnse Utility and Healing Utility ver. 1.0

Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


HP Linux Imaging and Printing System (ver. 3.20.11)
Self Diagnse Utility and Healing Utility ver. 1.0

Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Checking for Deprecated items....
No Deprecated items are found

Checking for HPLIP updates....

HP Linux Imaging and Printing System (ver. 3.20.11)
HPLIP upgrade latest version ver. 1.0

Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: Either Internet is not working or Wget is not installed.
error: Failed to upgrade latest HPLIP. Is hp-upgrade already running (i.e. foreground or background)?

Checking for Dependencies....

---------------
| SYSTEM INFO |
---------------

 Kernel: 5.4.0-53-generic #59~18.04.1-Ubuntu SMP Wed Oct 21 12:14:56 UTC 2020 GNU/Linux
 Host: hontra
 Proc: 5.4.0-53-generic #59~18.04.1-Ubuntu SMP Wed Oct 21 12:14:56 UTC 2020 GNU/Linux
 Distribution: 12 18.04
 Bitness: 64 bit

-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.20.11
HPLIP-Home: /usr/share/hplip
HPLIP-Installation: Auto installation is supported for ubuntu distro  18.04 version 

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.20.11

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.20.11
html=/usr/share/doc/hplip-3.20.11
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
internal-tag=3.20.11
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
qt5=no
policy-kit=no
lite-build=no
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no
apparmor_build=yes
class-driver=no

Current contents of '/var/lib/hp/hplip.state' file:
[plugin]
installed = 1
eula = 1
version = 3.20.11

Current contents of '~/.hplip/hplip.conf' file:
[upgrade]
notify_upgrade = true
last_upgraded_time = 1610261524
pending_upgrade_time = 0
latest_available_version = 3.17.10

[settings]
systray_visible = 0
systray_messages = 0

[last_used]
device_uri = "hp:/usb/DeskJet_2700_series?serial=CN07D3F5W4"
printer_name = 
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

[installation]
date_time = 01/10/21 14:13:08
version = 3.20.11

 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>

--------------
| COMPILEDEP |
--------------

 gcc                  gcc - GNU Project C and C++ Compiler                         REQUIRED        -               7.5.0           OK         -
 make                 make - GNU make utility to maintain groups of programs       REQUIRED        3.0             4.1             OK         -
 libtool              libtool - Library building support services                  REQUIRED        -               2.4.6           OK         -

------------------------
| General Dependencies |
------------------------

 libcrypto            libcrypto - OpenSSL cryptographic library                    REQUIRED        -               1.1.1           OK         -
 python-xml           Python XML libraries                                         REQUIRED        -               2.2.5           OK         -
 libnetsnmp-devel     libnetsnmp-devel - SNMP networking library development files REQUIRED        5.0.9           5.7.3           OK         -
 sane-devel           SANE - Scanning library development files                    REQUIRED        -               -               OK         -
 pil                  PIL - Python Imaging Library (required for commandline scanning with hp-scan) OPTIONAL        -               5.1.0           OK         -
 pyqt4-dbus           PyQt 4 DBus - DBus Support for PyQt4                         REQUIRED        4.0             4.12.1          OK         -
 libpthread           libpthread - POSIX threads library                           REQUIRED        -               2.27            OK         -
 python-devel         Python devel - Python development files                      REQUIRED        2.2             2.7.17          OK         -
 cups-devel           CUPS devel- Common Unix Printing System development files    REQUIRED        -               2.2.7           OK         -
 libavahi-dev         libavahi-dev                                                 REQUIRED        -               -               OK         -
 python-dbus          Python DBus - Python bindings for DBus                       REQUIRED        0.80.0          1.2.6           OK         -
 cups-ddk             CUPS DDK - CUPS driver development kit                       OPTIONAL        -               -               OK         -
 reportlab            Reportlab - PDF library for Python                           OPTIONAL        2.0             3.4.0           OK         -
 pyqt4                PyQt 4- Qt interface for Python (for Qt version 4.x)         REQUIRED        4.0             4.12.1          OK         -
 libusb               libusb - USB library                                         REQUIRED        -               1.0             OK         -
 cups-image           CUPS image - CUPS image development files                    REQUIRED        -               2.2.7           OK         -
 python2X             Python 2.2 or greater - Python programming language          REQUIRED        2.2             2.7.17          OK         -
 python-notify        Python libnotify - Python bindings for the libnotify Desktop notifications OPTIONAL        -               -               OK         -
 libjpeg              libjpeg - JPEG library                                       REQUIRED        -               -               OK         -
 sane                 SANE - Scanning library                                      REQUIRED        -               -               OK         -

----------------------
| Scan Configuration |
----------------------

 scanext              Scan-SANE-Extension                                          REQUIRED        -               3.20.11         OK         -
 hpaio                HPLIP-SANE-Backend                                           REQUIRED        -               3.20.11         OK         'hpaio found in /etc/sane.d/dll.conf'

-------------------------
| External Dependencies |
-------------------------

 gs                   GhostScript - PostScript and PDF language interpreter and previewer REQUIRED  7.05   9.26            OK         -
 scanimage            scanimage - Shell scanning program                   OPTIONAL        1.0             1.0.27          OK         -
 cups                 CUPS - Common Unix Printing System                   REQUIRED        1.1             2.2.7           OK         'CUPS Scheduler is running'
 network              network -wget                                        OPTIONAL        -               1.19.4          OK         -
 policykit            PolicyKit - Administrative policy framework          OPTIONAL        -               0.105           OK         -
 xsane                xsane - Graphical scanner frontend for SANE          OPTIONAL        0.9             0.999           OK         -
 dbus                 DBus - Message bus system                            REQUIRED        -               1.12.2          OK         -
 avahi-utils          avahi-utils                                          OPTIONAL        -               0.7             OK         -

---------------------
| Python Extentions |
---------------------

 hpmudext             IO-Extension                         REQUIRED        -               3.20.11         OK         -
 cupsext              CUPS-Extension                       REQUIRED        -               3.20.11         OK         -

------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------

device `hpaio:/usb/DeskJet_2700_series?serial=CN07D3F5W4' is a Hewlett-Packard DeskJet_2700_series all-in-one
device `hpaio:/net/deskjet_2700_series?ip=192.168.223.1&queue=false' is a Hewlett-Packard deskjet_2700_series all-in-one
device `hpaio:/usb/DeskJet_2700_series?serial=CN07D3F5W4' is a Hewlett-Packard DeskJet_2700_series all-in-one
device `hpaio:/net/deskjet_2700_series?ip=192.168.223.1&queue=false' is a Hewlett-Packard deskjet_2700_series all-in-one

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI               Model                 
  -----------------------  ----------------------
  hp:/usb/DeskJet_2700_se  HP DeskJet 2700 series
  ries?serial=CN07D3F5W4                         

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

DeskJet_2778
------------
Type: Printer
Device URI: hp:/usb/DeskJet_2700_series?serial=CN07D3F5W4
PPD: /etc/cups/ppd/DeskJet_2778.ppd
warning: Failed to read /etc/cups/ppd/DeskJet_2778.ppd ppd file
PPD Description: 
Printer status: printer DeskJet_2778 is idle.  enabled since Sunday 10 January 2021 12:27:36 PM IST
Communication status: Good

HP-DeskJet-2700-series
----------------------
Type: Unknown
Device URI: usb://HP/DeskJet%202700%20series?serial=CN07D3F5W4&interface=1
PPD: /etc/cups/ppd/HP-DeskJet-2700-series.ppd
warning: Failed to read /etc/cups/ppd/HP-DeskJet-2700-series.ppd ppd file
PPD Description: 
Printer status: printer HP-DeskJet-2700-series is idle.  enabled since Wednesday 30 December 2020 05:06:47 PM IST
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend for HP-Devices.

HP_DeskJet_2700_series_23B41A_
------------------------------
Type: Unknown
Device URI: ipps://HP842AFD23B41A.local:631/ipp/print
PPD: /etc/cups/ppd/HP_DeskJet_2700_series_23B41A_.ppd
warning: Failed to read /etc/cups/ppd/HP_DeskJet_2700_series_23B41A_.ppd ppd file
PPD Description: 
Printer status: printer HP_DeskJet_2700_series_23B41A_ is idle.  enabled since Sunday 10 January 2021 02:11:44 PM IST
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend for HP-Devices.

--------------
| PERMISSION |
--------------

USB    DeskJet_2778   Required    -    -   OK     Node:'/dev/bus/usb/002/005' Perm:'  root  saned rw- rw- rw- rw- r--'
 
Checking Permissions....

Checking for Configured Queues....
warning: Fail to read ppd=/etc/cups/ppd/DeskJet_2778.ppd file
warning: Insufficient permission to access file /etc/cups/ppd/DeskJet_2778.ppd
warning: Could not complete Queue(s) configuration check

Checking for HP Properitery Plugin's....
No plug-in printers are configured.
 
Diagnose completed...

More information on Troubleshooting,How-To's and Support is available on [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
```

---

### Post by brian_p on 2021-01-10
> **3dmatrix said:**
> I have wasted weeks with this printer and it does not works. Not astonished why people moving from another platform find so difficult to adjust to Linux.

You have been very unfortunate and met a problem with a package that Ubuntu has provided for printing with a USB connection. You are are just one among many who have encountered the issue. They too were completely mystified.
But I do not intend to go into that here.

In Message #14 I gave some advice. I am now going to lead you step by step through it. In that message I said
> 
...your device will operate perfectly well without going near HPLIP

so it may not surprise you I do not intend using HPLIP. If that does not suit you, stop reading.

[LIST]Switch the 2700 off and disconnect from USB.
[/LIST]
[LIST]Remove ippusbxd ```
apt purge ippusbxd 
```
[/LIST]
[LIST]Download and install **ipp-usb** from [https://download.opensuse.org/repositories/home:/pzz/xUbuntu_20.04/amd64/]("https://download.opensuse.org/repositories/home:/pzz/xUbuntu_20.04/amd64/")
[/LIST]
[LIST]Switch the 2700 on and re-connect to USB.
[/LIST]
[LIST]Provide what you get for ```
systemctl list-units "ipp-usb*" | grep service
```
[/LIST]
More to come!

---

### Post by 3dmatrix on 2021-01-10
> **brian_p said:**
> 
More to come!

```
systemctl list-units "ipp-usb*" | grep service
ipp-usb.service loaded active running Daemon for IPP over USB printer support
```

Is it safe to use this file as it is from an _unknown source_ ?

.

---

### Post by brian_p on 2021-01-11
> **3dmatrix said:**
> ```
systemctl list-units "ipp-usb*" | grep service
ipp-usb.service loaded active running Daemon for IPP over USB printer support
```

Is it safe to use this file as it is from an _unknown source_ ?

.

IMO, yes. ipp-usb from the same source is part of Ubuntu 20.10.

Now give what you get for ```
driverless
```

---

### Post by 3dmatrix on 2021-01-11
> **brian_p said:**
> IMO, yes. ipp-usb from the same source is part of Ubuntu 20.10.

Now give what you get for ```
driverless
```

```
driverless
ipp://localhost:60000/ipp/print
```

---

### Post by brian_p on 2021-01-11
> **3dmatrix said:**
> ```
driverless
ipp://localhost:60000/ipp/print
```

Now set up this print queue: ```
lpadmin -p 2700test -v "ipp://localhost:60000/ipp/print" -E -m everywhere 
```

Test printing with ```
lp -d 2700test /etc/nsswitch.conf
```

---

### Post by 3dmatrix on 2021-01-11
> **brian_p said:**
> Now set up this print queue: ```
lpadmin -p 2700test -v "ipp://localhost:60000/ipp/print" -E -m everywhere 
```

Test printing with ```
lp -d 2700test /etc/nsswitch.conf
```

It printed the content of the file **_nsswitch.conf_**

What next ?

---

### Post by brian_p on 2021-01-11
> It printed the content of the file nsswitch.conf

What next ? 

Nothing really. You now have printing sorted out.

---

### Post by 3dmatrix on 2021-01-12
> **brian_p said:**
> Nothing really. 
You now have printing sorted out.

(1) But printing was anyway never a big problem. It was Scanning that was not working at all.

(2) For printing also, how do I print from (say) Libre Office etc ? We have to kind of (install / register) a printer in the list of Printers.

---

### Post by brian_p on 2021-01-12
> **3dmatrix said:**
> (1) But printing was anyway never a big problem. It was Scanning that was not working at all.

Follow the advice you have already been given. Install sane-airscan from the same place you got ipp-usb and use simple-scan or xsane.
> 
(2) For printing also, how do I print from (say) Libre Office etc ? We have to kind of (install / register) a printer in the list of Printers.

Sorry, I do not sort out issues involving printing from an application's print dialog.

---

### Post by 3dmatrix on 2021-01-12
> **brian_p said:**
> Follow the advice you have already been given. Install sane-airscan from the same place you got ipp-usb and use simple-scan or xsane.
Sorry, I do not sort out issues involving printing from an application's print dialog.

So did all that you asked me to do, helped me in any way ?
I was anyway getting prints and now even for that I have to break my head.
I might have to altogether reinstall that OS.

---

### Post by brian_p on 2021-01-12
> **3dmatrix said:**
> So did all that you asked me to do, helped me in any way ?
I was anyway getting prints and now even for that I have to break my head.
I might have to altogether reinstall that OS.

We take it you are disinclined to install sane-airscan, which is known to work with your device and which is distributed with Ubuntu 20.10?

---

### Post by 3dmatrix on 2021-01-12
> **brian_p said:**
> We take it you are disinclined to install sane-airscan, which is known to work with your device and which is distributed with Ubuntu 20.10?

There is no WE. It is all your own imagination.
Acceptance of sane-airscan comes later.
First you mentioned : "[I][U]...your device will operate perfectly well without going near HPLIP
so it may not surprise you I do not intend using HPLIP. If that does not suit you, stop reading.[/U][/I]"
You are not telling that my printer, which was working fine as a printer with HPLIP, how will it work if it is used with ipp-usb.
You help a blind man to reach the middle of the road and then run away saying you cannot help him.
First my printer has to start working through ipp-usb then comes the solution for scanner.

---

### Post by brian_p on 2021-01-12
> You help a blind man to reach the middle of the road and then run away saying you cannot help him.

It's more like the blind man got a wee bit grumpy and irrationally spurned the offer of help. :(

---

### Post by 3dmatrix on 2021-01-12
> **brian_p said:**
> It's more like the blind man got a wee bit grumpy and irrationally spurned the offer of help. :(

Anyway, thanks for what ever you did.

---

