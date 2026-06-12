---
title: "Epson K300 Scanner cannot run on Ubuntu"
date: 2014-05-03
forum: Hardware
---

### Post by Rainshoots on 2014-05-03
Hi, 

The scanner in my Epson K300 all-in-one printer doesn't seem to work on Ubuntu even after installing all the drivers. 

iScan keeps giving the error msg: 

'Could not send command to scanner. Check the scanner's status.' 

Xsane doesn't work either. The message, originally in Chinese, can be roughly translated as: 

Failed to initiate device 'epkowa:usb:001:014': Device busy. 

May I know how can I get the scanner to work on Ubuntu? 

Thanks you. 

Regards, 
Sati

---

### Post by sammiev on 2014-05-03
> **Rainshoots said:**
> Hi, 

The scanner in my Epson K300 all-in-one printer doesn't seem to work on Ubuntu even after installing all the drivers. 

iScan keeps giving the error msg: 

'Could not send command to scanner. Check the scanner's status.' 

Xsane doesn't work either. The message, originally in Chinese, can be roughly translated as: 

Failed to initiate device 'epkowa:usb:001:014': Device busy. 

May I know how can I get the scanner to work on Ubuntu? 

Thanks you. 

Regards, 
Sati

Use this [addie]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX") and enter in K300 in the search.

---

### Post by Rainshoots on 2014-05-04
> **sammiev said:**
> Use this [addie]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX") and enter in K300 in the search.

Yes, that's exactly what I did. 

As I said, I have installed all the required drivers from the above website. 

And it didn't work.

---

### Post by pdc on 2014-05-04
> As I said, I have installed all the required drivers from the above website.

I am sure you got it all right but if we just check: one needs the data package installed first; 

so that would be[COLOR="#008000"] iscan-data_1.28.0-2_all.deb[/COLOR]

and then [COLOR="#008000"]iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb[/COLOR] (for 64bit) or [COLOR="#008000"]iscan_2.29.3-1~usb0.1.ltdl7_i386.deb[/COLOR] for 32bit

can you paste this command > [COLOR="#FF0000"]dpkg -l | grep iscan[/COLOR] into a terminal, and paste back what you get please

---

### Post by Rainshoots on 2014-05-04
Here are the results: 

ii  iscan                                      2.29.3-1~usb0.1.ltdl7                               simple, easy to use scanner utility for EPSON scanners
ii  iscan-data                                 1.27.0-1                                            Image Scan! for Linux data files
ii  iscan-network-nt                           1.1.1-1                                             Image Scan! Network Plugin

---

### Post by pdc on 2014-05-04
you have certainly got all the right iscan files in place; well done;

Brother recommend when installing the drivers for its range of multi-function devices; to edit the file 40-libsane.rules that lives inside the directory /etc/lib/udev/rules.d

So that might be just what will help you; 

When I look at the file on our computer, there are many Epson entries; but none for yours

______________

If I recommend you add an entry to this file; to tell your system about your device; 

__________ 

perhaps if you first just **read the file; with read-only powers**; so you can see what it is about; 

the command for that is > [COLOR="#FF0000"]gedit /etc/lib/udev/rules.d/40-libsane.rules[/COLOR]

and the idea is to paste into that the ID of your device; any **practice changes** you make here **cannot be saved **

here is an example from my 40-libsane.rules file for an Epson Stylux TX210 device

> # Epson Stylus TX210 Series
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="084f", ENV{libsane_matched}="yes"

_______________________

so we need the ID of your device: if you type > [COLOR="#FF0000"]lsusb[/COLOR] in a terminal, it will LIST all your USB devices; somewhere it should say ID 04b8:0872 Epson K300  ?????    

From here [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids) I guessed it is 0872 (Epson K300 series)

so your entry will look something like

> # Epson K300
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0872", ENV{libsane_matched}="yes"

*if I guessed the correct values in the idProduct field*

__________________

to actually save any changes to the above file, you need sudo powers....................so having looked at the file in gedit; if you ***close gedit*** and then paste the command below


> [COLOR="#FF0000"]gksudo gedit /etc/lib/udev/rules.d/40-libsane.rules[/COLOR]

so you can now WRITE to this file and save the changes .........because of sudo powers..................

if you make room anywhere in the file; by pushing existing entries down; paste your entry that I suggested above, into the file; SAVE; close; reboot

_____________________

any joy?

---

### Post by Rainshoots on 2014-05-04
Thanks for the quick reply! 

> perhaps if you first just **read the file; with read-only powers**; so you can see what it is about; 
the command for that is  	 		 			 			 				[COLOR=#FF0000]gedit /etc/lib/udev/rules.d/40-libsane.rules[/COLOR] 			 		

 	
 


I got the following feedback on terminal followed by an empty file with no text on it. 

> (gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:90:23: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:147:23: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:149:24: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:177:23: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:186:23: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:205:23: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:212:23: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:289:24: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:297:24: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:321:24: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:405:23: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:412:24: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:418:23: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:424:23: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:430:24: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:436:23: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:543:24: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:546:23: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:556:24: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:744:23: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:781:23: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:799:23: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:817:23: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:835:23: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:869:28: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:888:24: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:926:24: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:931:24: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:948:24: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:990:23: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:996:24: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1026:24: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1034:23: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1089:24: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1457:23: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1470:23: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1593:23: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1652:0: unknown @ rule

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1737:97: 'currentColor' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1745:32: Junk at end of value

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1757:13: 'animation' is not a valid property name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1781:23: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1790:23: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1801:23: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1856:24: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1858:28: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1873:24: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1886:24: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1892:24: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1927:24: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1995:23: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: unity.css:11:24: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: unity.css:22:24: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: unity.css:37:24: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: nautilus.css:14:18: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: nautilus.css:51:24: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: nautilus.css:67:24: Horizontal and vertical offsets are required

(gedit:2671): Gtk-WARNING **: Theme parsing error: nautilus.css:78:23: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: nautilus.css:83:23: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: nautilus.css:112:23: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: nautilus.css:125:23: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: nautilus.css:130:23: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: nautilus.css:140:23: 'px' is not a valid color name

(gedit:2671): Gtk-WARNING **: Theme parsing error: gnome-panel.css:94:24: 'px' is not a valid color name

It seems like there is no [COLOR=#FF0000]/lib[/COLOR] folder under my [COLOR=#FF0000]/etc directory. [/COLOR]

---

### Post by pdc on 2014-05-05
my apologies;

it should be

>  [COLOR="#FF0000"]gedit /lib/udev/rules.d/40-libsane.rules[/COLOR]     .that is just to read it and adding gksudo will convert it to read/write

---

### Post by Rainshoots on 2014-05-05
Thanks, but it didn't work. I got the same error msgs after rebooting.

---

### Post by Rainshoots on 2014-05-05
Just for your information, here are the results of the following commands on Terminal: 

*sane-find-scanner*: 

 > # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x0bda, product=0x0129) at libusb:001:009
found USB scanner (vendor=0x04b8, product=0x0872) at libusb:001:007
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

*scanimage -L*: 

> device `epkowa:usb:001:007' is a Epson WorkForce K301/K300 Series flatbed scanner. 

---

### Post by Rainshoots on 2014-05-05
According to the results of '*lsusb*': 

> Bus 001 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 003: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 001 Device 004: ID 0c45:760b Microdia 
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 05e3:0512 Genesys Logic, Inc. 
Bus 001 Device 007: ID 04b8:0872 Seiko Epson Corp. 
Bus 001 Device 008: ID 04ca:3006 Lite-On Technology Corp. 
Bus 001 Device 009: ID 0bda:0129 Realtek Semiconductor Corp.

The device at 001:009 is a Realtek Cardreader Controller. (As indicated by the [Linux-usb]("http://www.linux-usb.org/usb.ids") website: 0bda  Realtek Semiconductor Corp.; 0129  RTS5129 Card Reader Controller.) 

Apparently, Ubuntu has mistaken the card reader for a scanner. 

Any solutions?

---

### Post by pdc on 2014-05-05
I think this is your device as seen in lsusb

> Bus 001 Device 007: ID 04b8:0872 Seiko Epson Corp. 

and it showed up on sane-find-scanner and scanimage -L

____________________________________________________

if we just check you are a member of the scanner group: I think you will be

if you paste this command

> [COLOR="#FF0000"]grep -e scanner /etc/group[/COLOR]

for me, I get scanner: pdc


If your username is not there, you add it with > sudo adduser <username> scanner    where you add your username .........     as described here [https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

_____________________________________________________________________

can we load a file to look at it; if you open with read/write powers:

> [COLOR="#FF0000"]gksudo gedit /etc/sane.d/dll.conf[/COLOR]

can you paste in > [COLOR="#008000"]epkowa[/COLOR] if it is not already there; SAVE; close; reboot; any joy?

__________________________________________

and from this post [http://forums.linuxmint.com/viewtopic.php?f=49&t=5945&start=40](http://forums.linuxmint.com/viewtopic.php?f=49&t=5945&start=40) Postby cupofcalculus on Fri Oct 22, 2010 9:07 am

.............commands to do in red in a terminal .............

> [COLOR="#FF0000"]sudo apt-get install libsane-dev[/COLOR]

> [COLOR="#FF0000"]gksudo etc/udev/rules.d/45-libsane.rules[/COLOR]

and paste into it 

> # This file was automatically created based on description files (*.desc)
# by sane-desc 3.2 from sane-backends 1.0.18-cvs on Fri Oct  5 15:26:21 2007
#
# udev rules file for supported USB devices
#
# To add a USB device, add a rule to the list below between the SUBSYSTEM...
# and LABEL... lines.
#
# To run a script when your device is plugged in, add RUN+="/path/to/script"
# to the appropriate rule.
#
# The following list already contains a lot of scanners. If your scanner
# isn't mentioned there, add it as explained above and mail the entry to
# the sane-devel mailing list (sane-devel@lists.alioth.debian.org).
#

ACTION!="add", GOTO="libsane_rules_end"
SUBSYSTEM!="usb_device", GOTO="libsane_rules_end"

# Epson Stylus K300
SYSFS(idVendor)=="0x04b8", SYSFS(idProduct)=="0x0872", MODE="664", GROUP="scanner"

LABEL="libsane_rules_end"


and where did I get it from? .............this thread [http://launchpadlibrarian.net/14664165/45-libsane.rules](http://launchpadlibrarian.net/14664165/45-libsane.rules) has the list of a huge number of scanners: I deleted all of them; pasted in what I think is the ID and correct details of your scanner; so you can check it looks good

__________________

you will be creating a new file; called 45-libsane.rules so after the pasting; SAVE; CLOSE and try a reboot; any joy?

I offer you these points of advice in good faith; to aim to get your scanner going; I always say: linux is for adults; it is your system and we might upset your system doing the above: but you should be able to delete any pastings above as needed

best wishes

---

### Post by Rainshoots on 2014-05-06
It didn't work. 

After adding my username and editing dll.config, the same errors came up. 

[COLOR=#FF0000]Installing libsane-dev g[COLOR=#FF0000]ave the [COLOR=#FF0000]following results: 

> Get:1 [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) precise-updates/main libtiffxx0c2 amd64 3.9.5-2ubuntu1.5 [6,546 B]
Get:2 [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) precise-updates/main libavahi-common-dev amd64 0.6.30-5ubuntu2.1 [44.5 kB]
Get:3 [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) precise-updates/main libdbus-1-dev amd64 1.4.18-1ubuntu1.4 [212 kB]
Get:4 [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) precise-updates/main libavahi-client-dev amd64 0.6.30-5ubuntu2.1 [38.7 kB]
Get:5 [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) precise-updates/main libexif-dev amd64 0.6.20-2ubuntu0.1 [349 kB]
Get:6 [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) precise/main libusb-dev amd64 2:0.1.12-20 [35.0 kB]
Get:7 [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) precise-updates/main libgphoto2-2-dev amd64 2.4.13-1ubuntu1.2 [2,819 kB]
Get:8 [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) precise/main libieee1284-3-dev amd64 0.2.11-10build1 [50.2 kB]
Get:9 [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) precise-updates/main libjpeg-turbo8-dev amd64 1.1.90+svn733-0ubuntu4.3 [391 kB]
Get:10 [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) precise/main libjpeg8-dev amd64 8c-2ubuntu7 [1,544 B]
Get:11 [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) precise/main libjpeg-dev all 8c-2ubuntu7 [1,536 B]
Get:12 [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) precise-updates/main libtiff4-dev amd64 3.9.5-2ubuntu1.5 [279 kB]
Get:13 [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) precise-updates/main libv4l-dev amd64 0.8.6-1ubuntu2 [7,928 B]
Get:14 [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) precise/main libsane-dev amd64 1.0.22-7ubuntu1 [4,374 kB]
Fetched 8,610 kB in 11s (732 kB/s)                                             
Selecting previously unselected package libtiffxx0c2.
(Reading database ... 212287 files and directories currently installed.)
Unpacking libtiffxx0c2 (from .../libtiffxx0c2_3.9.5-2ubuntu1.5_amd64.deb) ...
Selecting previously unselected package libavahi-common-dev.
Unpacking libavahi-common-dev (from .../libavahi-common-dev_0.6.30-5ubuntu2.1_amd64.deb) ...
Selecting previously unselected package libdbus-1-dev.
Unpacking libdbus-1-dev (from .../libdbus-1-dev_1.4.18-1ubuntu1.4_amd64.deb) ...
Selecting previously unselected package libavahi-client-dev.
Unpacking libavahi-client-dev (from .../libavahi-client-dev_0.6.30-5ubuntu2.1_amd64.deb) ...
Selecting previously unselected package libexif-dev.
Unpacking libexif-dev (from .../libexif-dev_0.6.20-2ubuntu0.1_amd64.deb) ...
Selecting previously unselected package libusb-dev.
Unpacking libusb-dev (from .../libusb-dev_2%3a0.1.12-20_amd64.deb) ...
Selecting previously unselected package libgphoto2-2-dev.
Unpacking libgphoto2-2-dev (from .../libgphoto2-2-dev_2.4.13-1ubuntu1.2_amd64.deb) ...
Selecting previously unselected package libieee1284-3-dev.
Unpacking libieee1284-3-dev (from .../libieee1284-3-dev_0.2.11-10build1_amd64.deb) ...
Selecting previously unselected package libjpeg-turbo8-dev.
Unpacking libjpeg-turbo8-dev (from .../libjpeg-turbo8-dev_1.1.90+svn733-0ubuntu4.3_amd64.deb) ...
Selecting previously unselected package libjpeg8-dev.
Unpacking libjpeg8-dev (from .../libjpeg8-dev_8c-2ubuntu7_amd64.deb) ...
Selecting previously unselected package libjpeg-dev.
Unpacking libjpeg-dev (from .../libjpeg-dev_8c-2ubuntu7_all.deb) ...
Selecting previously unselected package libtiff4-dev.
Unpacking libtiff4-dev (from .../libtiff4-dev_3.9.5-2ubuntu1.5_amd64.deb) ...
Selecting previously unselected package libv4l-dev.
Unpacking libv4l-dev (from .../libv4l-dev_0.8.6-1ubuntu2_amd64.deb) ...
Selecting previously unselected package libsane-dev.
Unpacking libsane-dev (from .../libsane-dev_1.0.22-7ubuntu1_amd64.deb) ...
Processing triggers for doc-base ...
Processing 3 added doc-base files...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up libtiffxx0c2 (3.9.5-2ubuntu1.5) ...
Setting up libavahi-common-dev (0.6.30-5ubuntu2.1) ...
Setting up libdbus-1-dev (1.4.18-1ubuntu1.4) ...
Setting up libavahi-client-dev (0.6.30-5ubuntu2.1) ...
Setting up libexif-dev (0.6.20-2ubuntu0.1) ...
Setting up libusb-dev (2:0.1.12-20) ...
Setting up libgphoto2-2-dev (2.4.13-1ubuntu1.2) ...
Setting up libieee1284-3-dev (0.2.11-10build1) ...
Setting up libjpeg-turbo8-dev (1.1.90+svn733-0ubuntu4.3) ...
Setting up libjpeg8-dev (8c-2ubuntu7) ...
Setting up libjpeg-dev (8c-2ubuntu7) ...
Setting up libtiff4-dev (3.9.5-2ubuntu1.5) ...
Setting up libv4l-dev (0.8.6-1ubuntu2) ...
Setting up libsane-dev (1.0.22-7ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
sati@zephyr:~$ gksudo etc/udev/rules.d/45-libsane.rules[/COLOR][/COLOR][/COLOR]

Nothing came up after that.

---

### Post by Rainshoots on 2014-05-08
I am using ubuntu version 12.04. Would upgrading to a newer version help solve the problem?

---

### Post by pdc on 2014-05-08
> Would upgrading to a newer version help solve the problem? 

............who could say...................??

sometimes folks have enough room on their hard drive for a second distro: so it might be possible to create a small install of ............say.............14.04 and keep the existing till one could evaluate.............but it is your computer to make those calls on .................

---

### Post by Rainshoots on 2014-05-13
After upgrading to Saucy, this is what I get: 

> scanimage -L
device `epkowa:usb:001:010' is a Epson (unknown model) flatbed scanner

> sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x1d6b/0x0003 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x0bda/0x0129 at 001:008: Access denied (insufficient permissions)
could not open USB device 0x04ca/0x3006 at 001:009: Access denied (insufficient permissions)
could not open USB device 0x05e3/0x0608 at 001:005: Access denied (insufficient permissions)
could not open USB device 0x0c45/0x760b at 001:004: Access denied (insufficient permissions)
could not open USB device 0x0458/0x003a at 001:003: Access denied (insufficient permissions)
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
could not open USB device 0x05e3/0x0512 at 001:006: Access denied (insufficient permissions)
could not open USB device 0x05e3/0x0610 at 001:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

---

### Post by Rainshoots on 2014-05-13
sudo sane-find-scanner returned this: 

> sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x0bda [Generic], product=0x0129 [USB2.0-CRW]) at libusb:001:008
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

Again, my card reader is listed as a scanner. 

I highly suspect that this is what's causing my scanner to be unusable under ubuntu. 

Is there a way to tell the computer that the card reader is not a scanner?

---

### Post by pdc on 2014-05-13
> Again, my card reader is listed as a scanner. I highly suspect that this is what's causing my scanner to be unusable under ubuntu.

but I see all this ....................as well................ (I don't get anything like that on our system)

> could not open USB device 0x1d6b/0x0003 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x0bda/0x0129 at 001:008: Access denied (insufficient permissions)
could not open USB device 0x04ca/0x3006 at 001:009: Access denied (insufficient permissions)
could not open USB device 0x05e3/0x0608 at 001:005: Access denied (insufficient permissions)
could not open USB device 0x0c45/0x760b at 001:004: Access denied (insufficient permissions)
could not open USB device 0x0458/0x003a at 001:003: Access denied (insufficient permissions)
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
could not open USB device 0x05e3/0x0512 at 001:006: Access denied (insufficient permissions)
could not open USB device 0x05e3/0x0610 at 001:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)

...................all very strange .............. 

.........so you have a laptop computer...................desktop computer.............and you ................wiped everything on the hard drive...........and started again................ or you have ....................done.............

and you put on 14.04 as a 32bit version ........................  or it's all running inside a virtual install ........................

---

### Post by Rainshoots on 2014-05-15
It's a desktop. I have just upgraded to 13.10 (saucy). 
I did not format the whole disk. Just upgraded using do-release-upgrade. 

I started off with precise (12.04) 64-bit version. The system should be smart enough to upgrade to a 64-bit system rather than a 34-bit one.

---

### Post by pdc on 2014-05-15
>  I have just upgraded to 13.10 (saucy). 

...........oh dear.................... you will only be supported for another 2 months; (support finishes in July 2014)

the current release (14.04) is a long-term support version and will thus continue for up to five years;

Many folks would think you are much better off with a fresh install of 14.04: .......... there are some strange things about your current system ; (When I say fresh install, I mean install as opposed to some sort of what is called an upgrade...)

---

### Post by Rainshoots on 2014-05-16
I am working on it.

---

### Post by Rainshoots on 2014-05-16
Is it possible to preserve my programs and settings with a fresh install? 

I don't want to do them all over again.

---

### Post by pdc on 2014-05-16
yes; if there is enough room on your device to create a new partition; for a clean install of 14.04  

your data should thus be safe on the older install; and you should be able to read it; all a series of "should" ..................

---

### Post by Rainshoots on 2014-05-25
I just did a clean install of Trusty and this is what I have: 

sane-find-scanner
>   # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x1d6b/0x0003 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x0bda/0x0129 at 001:008: Access denied (insufficient permissions)
could not open USB device 0x04ca/0x3006 at 001:009: Access denied (insufficient permissions)
could not open USB device 0x05e3/0x0608 at 001:005: Access denied (insufficient permissions)
could not open USB device 0x0c45/0x760b at 001:004: Access denied (insufficient permissions)
could not open USB device 0x0458/0x003a at 001:003: Access denied (insufficient permissions)
could not open USB device 0x04b8/0x0872 at 001:010: Access denied (insufficient permissions)
could not open USB device 0x05e3/0x0512 at 001:006: Access denied (insufficient permissions)
could not open USB device 0x05e3/0x0610 at 001:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

sudo sane-find-scanner
>   # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x0bda [Generic], product=0x0129 [USB2.0-CRW]) at libusb:001:008
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

scanimage-l
> scanimage: open of device epkowa:usb:001:010 failed: Access to resource has been denied

---

### Post by pdc on 2014-05-25
so you have installed the Epson drivers?

what does 

> [COLOR="#FF0000"]dpkg -l | grep iscan[/COLOR]

give please: if you copy and paste

and what does

> [COLOR="#FF0000"]groups[/COLOR] give please?

---

### Post by Rainshoots on 2014-05-28
[COLOR=#FF0000]dpkg -l | grep iscan[/COLOR]

> ii  iscan                                                 2.29.3-1~usb0.1.ltdl7                               amd64        simple, easy to use scanner utility for EPSON scanners
ii  iscan-data                                            1.28.0-2                                            all          Image Scan! for Linux data files
ii  iscan-network-nt                                      1.1.1-1                                             amd64        Image Scan! Network Plugin


---

### Post by Rainshoots on 2014-05-28
[COLOR=#FF0000]groups
[/COLOR]
> sati adm cdrom sudo dip plugdev lpadmin sambashare

---

### Post by pdc on 2014-05-28
your device is a multi-function so you don't have to be in the scanner group;

however if you want to add yourself the command I understand is

> sudo usermod -a -G [group-name] [user-name]

so it would be > sudo usermod -a -G scanner [user-name]             .............you add your username as indicated

---

### Post by Rainshoots on 2014-05-28
So how do I get my scanner to work from here?

---

### Post by pdc on 2014-05-28
If you type > groups again to see you are now a member of the scanner group

if you are, what does 

> [COLOR="#FF0000"]sane-find-scanner[/COLOR]

> [COLOR="#FF0000"]scanimage -L[/COLOR] give?

and what does 

> [COLOR="#FF0000"]sudo sane-find-scanner[/COLOR]

> [COLOR="#FF0000"]sudo scanimage -L[/COLOR]

give?

and lastly 

> [COLOR="#FF0000"]sudo iscan[/COLOR]

---

