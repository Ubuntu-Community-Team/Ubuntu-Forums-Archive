---
title: "Printer.. Dosnt work MFC-7420"
date: 2008-05-05
forum: Hardware
---

### Post by r1pcurl on 2008-05-05
I couldn't install this printer... 

when im trying to install... im getting this error

sudo dpkg -i cupswrapperMFC7420-2.0.1-2.i386.deb
Selecting previously deselected package cupswrappermfc7420.
(Reading database ... 126488 files and directories currently installed.)
Unpacking cupswrappermfc7420 (from cupswrapperMFC7420-2.0.1-2.i386.deb) ...
Setting up cupswrappermfc7420 (2.0.1-2) ...
/usr/local/Brother/cupswrapper/cupswrapperMFC7420-2.0.1: 64: cannot create /usr/share/cups/model/MFC7420.ppd: Directory nonexistent
 * Restarting Common Unix Printing System: cupsd                                                         [ OK ]
 * Restarting Common Unix Printing System: cupsd                                                         [ OK ]
cp: cannot stat `/usr/share/cups/model/MFC7420.ppd': No such file or directory
dpkg: error processing cupswrappermfc7420 (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupswrappermfc7420
No such file or directory

---

### Post by kattman on 2008-05-05
Here is the fix

# Ubuntu 8.04 does not have /usr/share/cups/model directory where our driver create a ppd file.
Please follow the instruction below when the installation failed with the message about it.

1. Uninstall the cupswrapper driver.
Command : sudo dpkg -P (driver name)

2. Create /usr/share/cups/model directory
Command : sudo mkdir /usr/share/cups/model

3. Install the cupswrapper driver
Command : sudo dpkg -i --force-all --force-architecture (driver file name)

---

### Post by r1pcurl on 2008-05-05
ok, thank you for the quick answer but.. now thats my printer is set-up she dosnt work.. she dosnt print anything... this is the output for the command:lpinfo -v:
network socket
network beh
direct hal:///org/freedesktop/Hal/devices/usb_device_4f9_180_000J5J751770_if0_printer_noserial
direct parallel:/dev/lp0
direct hpfax
direct hp
network http
network ipp
network lpd
file cups-pdf:/
direct scsi
network smb

Thats are Screen Picture from CUPS Manage Printers :

[http://i32.tinypic.com/35craxe.png](http://i32.tinypic.com/35craxe.png)

(oZairis its my pc name)

and ... if you need anything that can help you to help me plz say.

---

### Post by dburnett77 on 2008-05-12
> **kattman said:**
> Here is the fix

# Ubuntu 8.04 does not have /usr/share/cups/model directory where our driver create a ppd file.
Please follow the instruction below when the installation failed with the message about it.

1. Uninstall the cupswrapper driver.
Command : sudo dpkg -P (driver name)

2. Create /usr/share/cups/model directory
Command : sudo mkdir /usr/share/cups/model

3. Install the cupswrapper driver
Command : sudo dpkg -i --force-all --force-architecture (driver file name)

Helped me a bunch, just knowing I needed to make the directory.  Been trying to install Brother MFC465CN since last evening.  Ran the mkdir command and now I can print.  Thanks.

---

### Post by KD6TZF on 2008-05-13
```
stephen@Moneyworkn:~$ sudo dpkg -P mfc6800lpr
[sudo] password for stephen: 
dpkg: error processing mfc6800lpr (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 mfc6800lpr
```I tried to reinstall it but that doesn't work either.

My printer MFC6800 shows as installed, but won't print anything.  I tried to install the driver for it above but got the error message as shown.  Any help anyone can provide will be appreciated.  I've tried following the instructions from Brother web site but may be not doing things correctly.  Something is not right.  Help please.

Thanks,:confused:

---

### Post by tmera on 2008-05-15
Looks like you need the LPR driver.  I had a similar error with my MFC-7420.  I installed brmfc7420lpr-2.0.1-1.i386.deb in addition to following the instruction above and all worked fine.

[Todd Mera]("http://www.AwardWallet.com")

---

### Post by abgame on 2008-09-11
> **kattman said:**
> Here is the fix

# Ubuntu 8.04 does not have /usr/share/cups/model directory where our driver create a ppd file.
Please follow the instruction below when the installation failed with the message about it.

1. Uninstall the cupswrapper driver.
Command : sudo dpkg -P (driver name)

2. Create /usr/share/cups/model directory
Command : sudo mkdir /usr/share/cups/model

3. Install the cupswrapper driver
Command : sudo dpkg -i --force-all --force-architecture (driver file name)

I am using Ubuntu 8.04, printer is Fuji-Xerox Docuprint 203A (same as Brother HL2030). Thanks for your post - your steps didn't work for me as is, but did it a slightly different way, so thought I'd flesh it out the way it worked for me:

1. Uninstall cupswrapper driver as above (have inserted my driver name here, cause I didn't know exactly what that was from your post, initially I was trying to use the full deb package name)
Command: sudo dpkg -P cupswrapperHL2030

2. Create /usr/share/cups/model directory (this worked fine)
Command: sudo mkdir /usr/share/cups/model 

3. Install the cupswrapper driver
Couldn't make your command work - didn't know how - was getting error (sorry closed the terminal before thinking, otherwise I would have posted the error). Anyway I just went back to my original deb package on my desktop and double-clicked it - this time the install completed successfully without errors.

4. Added new printer (I had already previously deleted the non-working printer drivers installed if that makes any difference to anything):
Using menu: System>Administration>Printing>New Printer>FX Docuprint 203A USB #1>Select printer from database: Brother>HL2030 for CUPS [en](recommended) and so on

Printed test page (looks fine), printed page 1 of this page (looks fine) and posted here. Cheers. Thanks for the help.

BTW I had previously already downloaded to desktop and installed (by double-clicking)from Brother website brhl2030lpr-2.0.1-1.i386.deb and cupswrapperHL2030-2.0.1-2.i386.deb(installed with errors and printer didn't work) - yes I am a windows user - hey I'm trying to come to the light side. The printer has been the only major issue. Everything else was easy so far - great job Ubuntu people.

---

### Post by tmorgan9 on 2012-05-13
i cant successfully install my mfc-7420.
I am using ubuntu 64 bit
I installed the deb driver from brother. but it must not find it.
printer says receiving data but no print.
I had some other installation pkg installer to do it last time, but when i had fresh install lost it.

---

