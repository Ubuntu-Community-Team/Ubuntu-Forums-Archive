---
title: "Epson SX200 installation problems"
date: 2009-08-08
forum: Hardware
---

### Post by davesmith on 2009-08-08
Hello

I have just got a new Epson Stylus SX200 USB scanner/printer/copier and i'm having trouble getting it to work. I'm running Hardy 8.04.. The stand-alone copier works, but not the scanner (sane can't detect it) or the printer

The system detected it when connected to my USB port, the wizard popped up and it found a driver set, and installed. But nothing happens when I try and print....the document is queued and the system reports that the print job is complete, but nothing prints!

The printing troubleshooter gave the following report:-

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x9ce68a0>,
 'cups_instance': None,
 'cups_queue': 'Stylus_SX200',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://EPSON/Stylus%20SX200',
                       'printer-info': u'EPSON Stylus SX200',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Epson Stylus Scan 2500 - CUPS+Gutenprint v5.0.2',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 8425484,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Stylus_SX200'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_job_status': [], 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}

Can anyone help me here plz? Ive searched the forums without much success

thanks

Davesmith

---

### Post by davesmith on 2009-08-09
Bump!

---

### Post by davesmith on 2009-08-09
Dogmeat posted an excellent howto on epson printers/scanners/copiers at:-

[http://ubuntuforums.org/showthread.php?t=908443&highlight=epson+stylus](http://ubuntuforums.org/showthread.php?t=908443&highlight=epson+stylus)

I can confirm that the howto works to get the scanner working with sane :guitar: 

and my epson stylus sx200 scanner and the copier are now functional on this hardy 8.04 system. THANKS DOGMEAT, nice code!!

However, lots of folks are having problems getting the epson printer to work. There are any number of unanswered posts from ppl having probs with epson printers. Is there anyone out there with enough beans to post a terminal howto? Maybe Dogmeat retired....

DaveS

---

### Post by davesmith on 2009-08-10
bump!  have to ask the question, ar*e* epson supported by the ubuntu community?

---

### Post by x86-64-Scotland on 2009-08-14
I followed this guide on a friends 9.04 installation, everything looked good till I got to the scanimage -L, which said no scanner found.

Could someone please post a step by step for the epson sx200 on 9.04?

Cheers

---

### Post by zenade on 2009-08-14
This is a slight modification of the instructions given by Kaho on [http://ubuntuforums.org/showthread.php?t=932547&highlight=sx200&page=2](http://ubuntuforums.org/showthread.php?t=932547&highlight=sx200&page=2) to get the Epson Stylus SX200 scanner working on Ubuntu 9.04 using Xsane.

Open epson.conf
```
sudo gedit /etc/sane.d/epson.conf
```And add the following 3 lines:
```
usb 0x4b8 0x849
usb /dev/usbscanner0
usb /dev/usb/scanner0
```Create 45-libsane.rules
```
sudo gedit /etc/udev/rules.d/45-libsane.rules
```And add the following 2 lines:
```
# Epson Stylus SX200
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0849", MODE="664", GROUP="saned"
```Open System > Administration > Users and Groups

Select your user account.
Click unlock.
Enter password.
Click Manage Groups.
Select saned.
Click Properties.
Tick your username in Group Members.
Click OK.
Click Close.
Click Close.
Reboot.

Select Applications > Graphics > Xsane Image scanning program.

---

### Post by davesmith on 2009-08-16
Dogmeats howto on Epson Stylus scanners at  

[http://ubuntuforums.org/showthread.php?t=908443&highlight=epson+sx200](http://ubuntuforums.org/showthread.php?t=908443&highlight=epson+sx200)

works well, I got the sccanner to work just fine by following it

To get the printer to work, go to Epson's website and find the drivers section. Epson support the Linux community, they have drivers for most distros. Mine was in a deb package for 8.04 Hardy:-

pipslite_1.4.0-3_i386.deb

I installed it, re-booted, then connected the printer and switched it on. A printer icon appeared on the taskbar panel :) and a wizard takes you through the set-up, I choose the Epson Printers #1 driver, not the one for Epson Stylus. The test print had the Ubuntu icon and colour scales :guitar:


Good Luck!

---

### Post by x86-64-Scotland on 2009-08-18
> **zenade said:**
> This is a slight modification of the instructions given by Kaho on [http://ubuntuforums.org/showthread.php?t=932547&highlight=sx200&page=2](http://ubuntuforums.org/showthread.php?t=932547&highlight=sx200&page=2) to get the Epson Stylus SX200 scanner working on Ubuntu 9.04 using Xsane.
......

This advice worked perfectly, after removing sane/xsane and its previous configuration files. I could see in the logs the system kept looking for a scanner which was no longer connected to the system. An old HP P/S/C which broke, hence the Epson replacement.

Cheers

---

### Post by zenade on 2009-11-02
For Ubuntu 9.10, you must edit the epson2.conf file instead of the epson.conf file as described in my previous post.  Just insert a "2" when following the instructions.

---

