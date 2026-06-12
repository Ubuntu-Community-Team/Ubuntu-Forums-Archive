---
title: "Trouble Installing a CS-10 internet stick"
date: 2010-03-15
forum: Hardware
---

### Post by kengele on 2010-03-15
Hi .... 

I have a Lenovo T61 laptop running on Ubuntu 9.10 (Karmic) Kernel Linux 2.6.31-20 generic and Gnome 2.28.1

I tried to install a Nokia CS-10 internet stick by downloading the software for linux on the Nokia website [http://europe.nokia.com/support/product-support/cs-10/software](http://europe.nokia.com/support/product-support/cs-10/software)

I followed the instructions in the readme file than came with the download (basically I unzipped the archive and followed instructions as I would any download using Synaptic Package Manager).

While installing the package I received the following message -

Installation finished

Failed to install package "nokia-zerocd_0.2-10_all.deb" with a terminal window below that indicated

Selecting previously deselected package nokia-zerocd
(Reading database ... 181058 files and directories currently installed.)
Unpacking nokia-zerocd  (from nokia-zerocd_0.2-10_all.deb) ...
Setting up nokia-zerocd (0-2.10) ...
Unrecognized command
dpkg: error processing nokia-zerocd (--install):
subprocess installed post installation script returned error exit status 1
Errors were encountered while processing


Then later while I tried to update because ...

there is a big "no-entry" icon on the toolbar where the update manager icon normally is...when I hover over it ... it has a pop up saying 
An error occurred Please run Package Manager from the right-click menu or 
apt-get in a terminal to see what is wrong.  ...

...the Update Manager says 
Package in Inconsistant State
The package "nokia-zerocd" is in an inconsistant state and needs to be reinstalled, but no archive can be found for it. Please re-install the package manually or remove it from the system.

I have tried to re-install it and the Package Installer says
Could not open "nokia-zerocd"

I have tried to remove it from the system and the Package Manager cannot and says 
An error occurred. The following details are provided:
E: The package nokia-zerocd needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.


Can anyone guide me from here?  
How can I unistall the "nokia-zerocd" package so that everything was as it was previously?  and / or
How can I install the package properly so that the CS-10 internet stick works properly?

Many thanks and hopeful.

---

### Post by kengele on 2010-03-15
No replies!!  Did I post too much information?  

I searched for a file called nokia-zerocd and found nothing.... All I have noticed is that /etc/udev/rules.d/70-persistent-cd.rules  includes instructions about the new datacard.  Could that be why everything is jammed?  Is it safe to alter this file, with a backup copy on standby, or will that create a huge mess?

Any ideas anyone?


the contents of
/etc/udev/rules.d/70-persistent-cd.rules  

# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
#  (pci-0000:00:1f.1-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
# Datacard_CD-ROM (pci-0000:00:1d.7-usb-0:2.3:1.0-scsi-0:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="Nokia_Datacard_CD-ROM_0.0.1-0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"

---

