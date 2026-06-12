---
title: "Canon MX320 - Ubuntu 12.04"
date: 2013-03-24
forum: Hardware
---

### Post by gerardc on 2013-03-24
Hi I am trying to get a Canon MX320 working, I have been trying to get this right a couple of times.
The last effort, I deleted all the printer definitions defined , made sure the software is up to date, when I connect the printer syslog shows:

                    usblp1: USB Bidirectional printer dev 4 if 2 alt 0 proto 2 vid 0x04A9 pid 0x1736
Mar 24 21:15:52 PC1 udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.2/usb/lp1
Mar 24 21:15:54 PC1 udev-configure-printer: URI contains USB serial number
Mar 24 21:15:54 PC1 udev-configure-printer: URI match: usb://Canon/MX320%20series?serial=142DFA&interface=1
Mar 24 21:15:54 PC1 udev-configure-printer: device devpath is /devices/pci0000:00/0000:00:1d.7/usb1/1-2
Mar 24 21:15:54 PC1 udev-configure-printer: Device already handled
Mar 24 21:15:54 PC1 udev-configure-printer: device devpath is /devices/pci0000:00/0000:00:1d.7/usb1/1-2
Mar 24 21:15:54 PC1 udev-configure-printer: Device already handled
Mar 24 21:15:54 PC1 udev-configure-printer: About to add queue for usb://Canon/MX320%20series?serial=142DFA&interface=1
Mar 24 21:15:54 PC1 udev-configure-printer: device devpath is /devices/pci0000:00/0000:00:1d.7/usb1/1-2
Mar 24 21:15:54 PC1 udev-configure-printer: Device already handled
Mar 24 21:15:54 PC1 udev-configure-printer: device devpath is /devices/pci0000:00/0000:00:1d.7/usb1/1-2
Mar 24 21:15:54 PC1 udev-configure-printer: Device already handled
Mar 24 21:15:54 PC1 udev-add-printer: add_queue: URIs=['usb://Canon/MX320%20series?serial=142DFA&interface=1']
Mar 24 21:15:54 PC1 udev-add-printer: D-Bus method call failed: org.freedesktop.DBus.Error.ServiceUnknown: The name com.redhat.NewPrinterNotification was not provided by any .service files
Mar 24 21:15:58 PC1 udev-add-printer: PPD: gutenprint.5.2://bjc-MULTIPASS-MX300/expert; Status: 1 

Are the 2 lines above an error ?.

---

### Post by pdc on 2013-03-24
I would suggest you install the drivers that Canon supply; 

you don't tell us if you have 32bit or 64bit; can you tell us that please: perhaps you also help us understand your system; one assumes most folks posting may have a standalone computer with a printer connected by USB cable?

if you go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100187502.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100187502.html)

Canon provide the [COLOR="#008000"]**cnijfilter-mx320series-3.10-1-i386-deb.tar.gz**[/COLOR] which they call MX320series IJ Printer Driver Ver. 3.10 for Linux (debian Packagearchive)

for a 32bit system, commands would be 

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf cnijfilter-mx320series-3.10-1-i386-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd cnijfilter-mx320series-3.10-1-i386-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]./install.sh[/COLOR]

______________________________________________________________________________________________

Canon also provide ScanGearMP to run the scanner [COLOR="#008000"][B]scangearmp-mx320series-1.30-1-i386-deb.tar.gz
[/B][/COLOR]
[http://support-asia.canon-asia.com/contents/ASIA/EN/0100186801.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100186801.html)

it installs as above

to run it, type

> [COLOR="#FF0000"]scangearmp[/COLOR]

and create a launcher for repeated use

---

### Post by gerardc on 2013-03-25
Hi PDC

Apologies , I forgot the details. Yes 32-bit , stand alone PC with printer connected via USB. I will go thru your steps during this week, the pc is in another location to myself and I need to arrange access.

---

### Post by pdc on 2013-03-25
well gerard, it should all go very straightforward-ly........... let us know how you get along

---

