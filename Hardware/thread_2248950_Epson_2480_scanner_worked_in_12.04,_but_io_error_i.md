---
title: "Epson 2480 scanner worked in 12.04, but i/o error in 14.04"
date: 2014-10-18
forum: Hardware
---

### Post by jon.ti on 2014-10-18
For years I've been using my "Epson Perfection 2480 Photo" scanner with various iterations of Ubuntu, and I've always been able to get it working by following the instructions in the solved thread "[How do I set up an Epson 2480 scanner?]("http://ubuntuforums.org/showthread.php?t=975051")" 

But these instructions don't work in Ubuntu 14.04 32 bit, at least not on my kit. 

The device is identified correctly ...
```
$ scanimage -L
device `snapscan:libusb:001:004' is a EPSON EPSON Scanner flatbed scanner
```
```
$ lsusb | grep -i epson
Bus 001 Device 004: ID 04b8:0121 Seiko Epson Corp. GT-F500/GT-F550 [Perfection 2480/2580 PHOTO]
```

and found by sane ok
```
$ sane-find-scanner | grep -i epson
found USB scanner (vendor=0x04b8 [EPSON], product=0x0121 [EPSON Scanner]) at libusb:001:004
```

but
```
$ scanimage > image.pnm
scanimage: open of device snapscan:libusb:001:004 failed: Error during device I/O
```

Please, has anyone any ideas as to what might be amiss?

---

### Post by oceola2 on 2014-10-18
Try installing xsane; xsane-common and making sure you have libsane and libsane-common.
It may be you also need the backend drivers in libsane-extras and libsane-xtras-common but try without first.

---

### Post by jon.ti on 2014-10-19
Thanks for the suggestion, but all of those packages are already installed.

I'm thinking it might be a libsane issue. This from /etc/var/syslog from first thing this morning when I tried to use  the scanner with simple scan. Third line from the bottom is where things appear to go wrong.```
Oct 19 07:50:11 odin anacron[899]: Job `cron.daily' terminated
Oct 19 07:50:11 odin anacron[899]: Normal exit (1 job run)
Oct 19 07:56:29 odin dbus[568]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Oct 19 07:56:32 odin dbus[568]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Oct 19 07:56:33 odin kernel: [ 1340.688057] usb 1-2: new high-speed USB device number 4 using ehci-pci
Oct 19 07:56:33 odin kernel: [ 1340.823944] usb 1-2: New USB device found, idVendor=04b8, idProduct=0121
Oct 19 07:56:33 odin kernel: [ 1340.823950] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Oct 19 07:56:33 odin kernel: [ 1340.823954] usb 1-2: Product: EPSON Scanner
Oct 19 07:56:33 odin kernel: [ 1340.823957] usb 1-2: Manufacturer: EPSON
Oct 19 07:56:36 odin kernel: [ 1343.293547] WARNING! power/level is deprecated; use power/control instead
Oct 19 07:56:36 odin colord: Device added: sysfs-EPSON-EPSON_Scanner
Oct 19 07:57:22 odin simple-scan: io/hpmud/pp.c 627: unable to read device-id ret=-1
Oct 19 07:57:50 odin kernel: [ 1417.787444] usb 1-2: USB disconnect, device number 4
Oct 19 07:57:50 odin colord: device removed: sysfs-EPSON-EPSON_Scanner
```What is hpmud, I wonder?

---

### Post by oceola2 on 2014-10-19
OK, I didn't think the HP packages could interfere with the Epson.
One of the issues with the newer HP driver packages are the libsane-hpaio pretty much interferes with older scanners and Xsane.
The older drivers are not present.
Try un-installing that package (libsane-hpaio) and see if your scanner works.
You might not need the hpmud package either unless you have an HP printer.
If so there are ways around that to make the HP printers work.

---

### Post by jon.ti on 2014-10-19
OK, I've uninstalled libsane-hpaio and things have changed. Previously the scanner crashed, it lurched into action (well, briefly made its usual starting noise), then flashed its red led light. Now it doesn't, but syslog reports
```
Oct 19 22:53:19 odin colord: Device added: sysfs-EPSON-EPSON_Scanner
Oct 19 22:55:55 odin kernel: [22037.722769] usb 1-2: usbfs: interface 0 claimed by usbfs while 'xsane' sets config #1
```Thanks, this looks like progress.

---

### Post by jon.ti on 2014-10-20
I've now had time to have a good look at the changed situation. The output from the commands is the same
```
$ sane-find-scanner | grep -i epson
found USB scanner (vendor=0x04b8 [EPSON], product=0x0121 [EPSON Scanner]) at libusb:001:008
$ lsusb | grep -i epson
Bus 001 Device 008: ID 04b8:0121 Seiko Epson Corp. GT-F500/GT-F550 [Perfection 2480/2580 PHOTO]
$ scanimage -L
device `snapscan:libusb:001:008' is a EPSON EPSON Scanner flatbed scanner
$ scanimage > image.pnm
scanimage: open of device snapscan:libusb:001:008 failed: Error during device I/O
```

and syslog reports 
```
Oct 20 08:09:32 odin kernel: [25998.744043] usb 1-2: new high-speed USB device number 8 using ehci-pci
Oct 20 08:09:32 odin kernel: [25998.879869] usb 1-2: New USB device found, idVendor=04b8, idProduct=0121
Oct 20 08:09:32 odin kernel: [25998.879876] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Oct 20 08:09:32 odin kernel: [25998.879879] usb 1-2: Product: EPSON Scanner
Oct 20 08:09:32 odin kernel: [25998.879882] usb 1-2: Manufacturer: EPSON
Oct 20 08:09:33 odin colord: Device added: sysfs-EPSON-EPSON_Scanner
```

but a second attempt with scanimage crashes the scanner and reports no devices 
```
$ scanimage > image.pnm
scanimage: no SANE devices found
```

and now syslog says
```
Oct 20 08:09:33 odin colord: Device added: sysfs-EPSON-EPSON_Scanner
Oct 20 08:13:34 odin cracklib: no dictionary update necessary.
Oct 20 08:13:45 odin colord: Automatic remove of HP-LaserJet-1100-Gray.. from cups-HP-LaserJet-1100
Oct 20 08:13:45 odin colord: Profile removed: HP-LaserJet-1100-Gray..
Oct 20 08:13:45 odin colord: device removed: cups-HP-LaserJet-1100
Oct 20 08:13:47 odin kernel: [26252.974293] type=1400 audit(1413789227.057:76): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=15267 comm="apparmor_parser"
Oct 20 08:13:47 odin kernel: [26252.974310] type=1400 audit(1413789227.057:77): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=15267 comm="apparmor_parser"
Oct 20 08:13:47 odin kernel: [26252.975011] type=1400 audit(1413789227.057:78): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=15267 comm="apparmor_parser"
Oct 20 08:13:48 odin colord: Profile added: HP-LaserJet-1100-Gray..
Oct 20 08:13:48 odin colord: Device added: cups-HP-LaserJet-1100
```

I do have an HP Laser Jet 1100 attached via parallel port to the PC (the PC is my office machine) but it wasn't switched on when I ran the above tests. It seems it's somehow being mistaken for a scanner?

---

### Post by oceola2 on 2014-10-20
Ok, it could be one of the other HP packages.
This is a bit lengthy and you might not need to add all the packages listed but what is important are the HP packages not listed. Took a little time this morning and made the list out of Synaptic with a couple of notes, maybe help with some ideas if nothing else, will check back again.

I debated as to whether this list would be helpful to anyone but it is what I had to do to by-pass the omission of my scanner and printer from the current HP package group. Even though my printer, LaserJetPro 400 (m401n wired), is still being sold along with cartridges at $100+, in large tech related or office retail outlets in the US, HP does not support my printer. The scanner (HP3400c) is so old you can hear the chipmunks working away with hammer and chisel but it still functions under 14.04 LTS Ubuntu as long as the libsane-hpaio is not installed.
    Much of this may be redundant or duns'al but things working is the most important thing. Someone smarter than me may point out the redundancies or overlaps but as it sits this is working.

a2ps 1:4.14-1.3 ; apsfilter 7.2.6-1.3 ; cups 1.7.2-0ubuntu1.2 ; cups-browsed 1.0.52-0ubuntu1.2 ; cups-bsd 1.7.2-0ubuntu1.2 ; cups-client 1.7.2-0ubuntu1.2 ; cups-common 1.7.2-0ubuntu1.2 ; cups-core-drivers 1.7.2-0ubuntu1.2 ; cups-daemon 1.7.2-0ubuntu1.2 ; cups-driver-gutenprint 5.2.10~pre2-0ubuntu2 ; cups-filters 1.0.52-0ubuntu1.2; cups-filters-core-drivers 1.0.52-0ubuntu1.2 ; cups-ppdc 1.7.2-0ubuntu1.2 ; cups-server-common 1.7.2-0ubuntu1.2 ; foomatic-db 20140410-0ubuntu1 ; foomatic-db-engine 4.0.11-0ubuntu1 ; foomatic-db-gutenprint 5.2.10~pre2-oubuntu2 ; ghostscript 9.10~dfsg-0ubuntu10.2 ; ghostscript-x 9.10~dfsg-0ubuntu10.2 ; gimp-gutenprint 5.2.10~pre2-0ubuntu2 ;
hp-ppd 0.9ubuntu2+really-0.2 ; hplip-data 3.14.3-0ubuntu3.2 ; ijsgutenprint 5.2.10~pre2-oubuntu2 ; ijsgutenprint-ppds 5.2.10~pre2-oubuntu2 ; libcups2 1.7.2-0ubuntu1.2 ; libcupscgi1 1.7.2-0ubuntu1.2 ; libcupsfilters1 1.0.52-0ubuntu1.2 ; libcupsimage2 1.7.2-0ubuntu1.2 ; libcupsmime1 1.7.2-0ubuntu1.2 ; libcupsppdc1 1.7.2-0ubuntu1.2 ; libfontembed1 1.0.52-0ubuntu1.2 ; libgs9 9.10~dfsg-0ubuntu10.2 ; libgs9-common 9.10~dfsg-0ubuntu10.2 ; libgutenprint2 5.2.10~pre2-oubuntu2 ; libgutenprintui2-1 5.2.10~pre2-oubuntu2 ; libhpmud0 3.14.3-0ubuntu3.2 ; libqt5printsupport5 5.2.1_dfsg-1ubuntu14.2 ; libxp6 1:1.0.2-1ubuntu1 ; openprinting-ppds 20140410-0ubuntu1 ; printer-driver-foo2zjs 2014209dfsg0-1ubuntu1 ; printer-driver-gutenprint 5.2.10~pre2-oubuntu2 ; printer-driver-hpcups 3.14.3-0ubuntu3.2 ; printer-driver-hpijs 3.14.3-0ubuntu3.2 ; psutils 1.17.dfsg-1 

Note: Sane is not installed but sane-utils are along with xsane and xsane-common.

---

### Post by jon.ti on 2014-10-20
Thanks for that list. I've worked through it and everything on it was or is now installed. I've left sane installed on my system. Is that right?

The usual commands find the scanner ok as before but snapscan > image gives an i/o error```
$ lsusb | grep -i epson
Bus 001 Device 017: ID 04b8:0121 Seiko Epson Corp. GT-F500/GT-F550 [Perfection 2480/2580 PHOTO]
$ sane-find-scanner | grep -i epson
found USB scanner (vendor=0x04b8 [EPSON], product=0x0121 [EPSON Scanner]) at libusb:001:017
$ scanimage -L
device `snapscan:libusb:001:017' is a EPSON EPSON Scanner flatbed scanner
device `hpaio:/par/HP_LaserJet_1100?device=/dev/parport0' is a Hewlett-Packard HP_LaserJet_1100 all-in-one
$ scanimage > image.pnm
[snapscan] Scanner warming up - waiting 8 seconds.
scanimage: sane_start: Error during device I/O
```The scanimage attempt crashed the scanner as before, but it gets as far as attempting to warm it up now. And this interesting line appears in syslog```
Oct 20 21:15:00 odin scanimage: io/hpmud/pp.c 627: unable to read device-id ret=-1
```

---

### Post by oceola2 on 2014-10-21
Sane should not be installed but the sane-utils package should.

---

### Post by jon.ti on 2014-10-21
Apologies, I made a mistake above. Turns out that sane is not and was not installed, but sane-utils is installed ok.

---

### Post by oceola2 on 2014-10-22
Install libsane-extra and libsane-extra common - could be the needed driver is in there?
Which HP files are currently installed on your system and which driver did you select for your printer?

---

### Post by jon.ti on 2014-10-23
Thanks for sticking with this. I've checked that libsane-extras and libsane-extras-common are both installed ok.

the following are the packages from the HP Linux Printing and Imaging System that are installed
```
hplip
hplip-data
libhpmud0
linsane-hpaio
printer-driver-hpcups
printer-driver-hpijs
printer-driver-postscript-hp
```
and for the printer ppd I'm using "HP LaserJet 1100, hpcups 3.14.3 (recommended)".

I'm beginning to wonder whether it might be an idea to revert something - the scanner used to work under linux, so presumably will work again with the right versions of the relevant software? On running *scanimage > image.pnm* syslog reports *scanimage: io/hpmud/pp.c 627: unable to read device-id ret=-1* This seems to point the finger at the libhpmud0 library as a candidate for reversion, or to be replaced by other software that does the same job.

---

### Post by oceola2 on 2014-10-23
The scanner worked in 12.04 because the older driver set did not essentially commandeer the usb system controlling scanning.
The list of files you have installed is what is normal but to make an older scanner and printer work you have to remove some of the new HP packages.
Where the problem occurs is in the multifunction condition of your HP 1100 all-in-one - which looking at the specs, is multi-function printer with a scanner.
In order to enable the Epson you would have to remove the files in **bold** in the list below (There may be one of the other printer-driver-* files which would be removed automatically as well.) and possibly  use a generic postscript driver in foomatic for the HP 1100 printer scanner and use Xsane for the Epson scanner. This would be accomplished with an install of the printer and selecting the generic driver. As a preliminary you could re-install the HP 1100 printer using the printer GUI in "System Settings" to look at the available printer drivers and un-install it if there is no support showing for the generic. Most of the HP gui printer installs support the newer HP packages and won't necessarily show the drivers, use the Ubuntu OS install instead of the HP version.

At this point it's a guess as to whether this will help because you may may need the libsane-hpaio to function the 1100, this package is where most of the problem lies.
Make sure you have the foomatic and other files I listed before and revue the files plus mark down on paper any changes you make so you can restore your HP1100 if this does not work.
It could be it won't because the HP 1100 scanner side is controlling the scanner system completely. I looked at the preferences for Xsane and it does not indicate the ability for two scanners at one time. I believe Simple Scan allows for the use of two scanners in the system which can be selected under preferences/source.
**hplip**
hplip-data
libhpmud0
**libsane-hpaio**<---corrected spelling
printer-driver-hpcups
printer-driver-hpijs
printer-driver-postscript-hp

---

### Post by jon.ti on 2014-10-23
> the multifunction condition of your HP 1100 all-in-one - which looking at the specs, is multi-function printer with a scannerI should've made it clearer earlier that the HP 1100 Laser Jet that I have is a plain old office laser jet printer, it has no scanning ability at all. But it's somehow mistaken for a combo printer/scanner by the software. When this has happened, xsane has given me a choice via a drop down menu as whether to use the Laser Jet "scanner" or the Epson.

Neither hplip nor libsane-hpaio are installed now```
$ dpkg -s hplip | grep Status
Status: deinstall ok config-files
$ dpkg -s libsane-hpaio | grep Status
Status: deinstall ok config-files
```
but no change with scanimage```
$ scanimage > image.pnm
scanimage: open of device snapscan:libusb:001:011 failed: Error during device I/O
```

---

### Post by oceola2 on 2014-10-23
Sorry for the error on the all-in-one.
Did the package printer-driver-postscript-hp get removed with the hplip and libsane-hpai0?
Have you installed the libsane-extras and libsane-extras-common?
Is the open-ppds package installed?

---

### Post by jon.ti on 2014-10-24
I hadn't realised that the parallel port printer might not play nice with the usb scanner. But the printer seems to just need the right ppd file in place and so might be less of a problem.

Presently, 
printer-driver-postscript-hp is **not** installed 
libsane-extras is installed 
libsane-extras-common  is installed
open-ppds is **not** installed

---

### Post by oceola2 on 2014-10-24
The open-ppds may or may not help but it could help in selection of a generic driver under the system printer install, does with older non-supported printers
One of the issues could be your scanner is not supported as are others.
One thing I was wondering is have you tried the scanner with the printer unplugged and have you shut down and restarted your system since the changes?
**Caution**
Do not open any html files in Nautilus while root. If using Firefox it will reset Firefox to the root defaults and will hold under user and you'll have to redo any settings.
You won't lose any bookmarks but it affects the Unity Tool Bar and File, Edit, View History, Bookmarks, Tools and Help will be invisible.
This could be related to the Classic theme restorer.

That stated; You need to open /usr/share/doc/libsane and read the "supported.html" file.
Scroll down to the epson scanners, there are two 2480s listed one seems to work the other has some form of backdoor non-free work around.

---

### Post by jon.ti on 2014-10-24
I've rebooted the computer with the printer disconnected, with no change. But as oceola2 points out, the Epson Perfection 2480 Photo scanner is listed in *file:///usr/share/doc/libsane/html/sane-mfgs.html* as unsupported.  It's a blow. It's hard to understand when working kit gets left stranded by the upgrade process.

But there seems to be hope. The sane-mfgs.html document says my scanner is "supported by the epkowa backend plus non-free interpreter". When I google on that the top link leads to
[http://www.sane-project.org/lists/sane-backends-external.html#S-EPKOWA](http://www.sane-project.org/lists/sane-backends-external.html#S-EPKOWA)
where I read that the epkowa requires the DFSG non-free iscan-plugin-gt-f500 (which is installed on my system), and that the scanner is also supported by the snapscan backend (which I think we've shown not to be the case, in accordance with sane-mfgs.html).

The epkowa backend seems to be called iscan, and this is installed (although iscan-data is not installed and does not appear in the repositories) but when I call iscan I get the error "Could not send command to scanner. Check the scanner's status."

---

### Post by oceola2 on 2014-10-25
Look in your Home directory for the folder .Sane and see if your Epson 2480 is listed under xsane.
Also look for the HP1100. If the 1100 printer is in the list delete it.
There should be only three files Epson 2480, xsane.mdf and xsane.rc

**Additional afterthought:** it might not be the HP1100 in the xsane folder under sane in the home directory, it might be the insidious libsane-hpaio.
Delete it and if it is in the file/.hplip /hplip.conf in your home directory, delete any comment of the libsane-hpaio  and the HP1100.
Use the generic drivers for your printer. re-install xsane and xsane common and re-boot.

You may also be having an issue if you have the HP help center or whatever they call it now  in the Menu bar when you installed 14.04 and may also be listed in the directory tree which allows the updating directly of the HP drivers, by-passing the update manger.
Somehow this may also be interfering as it is connected to the usb device controls.
Look at the address for the printer under the printer icon properties and see if it is using the usb address, just a wild thought at this point.

---

### Post by jon.ti on 2014-10-27
I think the scanner chose a misleading moment to die. 

It's attached to a dual-boot machine, so I found out the Windows installation CD for the scanner, booted into XP and installed Epson's software.  But the scanner crashed in Windows, even on the login screen, which was strange.

I can hardly believe it, it's certainly not died from overuse, but two different Linux backends, plus a Windows attempt certainly point to a fault in the scanner.

Thanks for your help oceola2, and I'm sorry to have led you on something of a wild goose chase.

---

### Post by oceola2 on 2014-10-28
That's disappointing but before throwing in the towel completely I'd see if there was a diagnostic you could run on the scanner.
I'd look on the disk or see if there is something online.

---

