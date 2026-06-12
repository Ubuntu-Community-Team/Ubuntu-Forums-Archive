---
title: "Hp 4650 (usb)"
date: 2008-07-17
forum: General Help
---

### Post by Dale Lewis on 2008-07-17
Hope I can find some help I am going insane with this printer:confused: I have an HP 4650 Color Laser with the latest HP drivers installed and it is connected via a usb cable. The printer is detected with no problem all the way down to the correct amount of ram installed. When I try to print I am getting a communication error. If I boot into vista no problem..prints with no issues using the same usb cable.

When I first loaded hardy I was able to print one test page but it hasn't printed since. Any ideas or suggestions would be greatly appreciated. Thanks!!!!

---

### Post by jonian_g on 2008-07-17
Check this post:

[http://ubuntuforums.org/showthread.php?t=835872](http://ubuntuforums.org/showthread.php?t=835872)

Try ramjet_1953's tip.

---

### Post by Dale Lewis on 2008-07-17
Saw that thread and tried it. Still no a no go. Thanks for posting!!

---

### Post by ramjet_1953 on 2008-07-18
Here's the official Ubuntu howto on using a network printer via SAMBA.

[https://help.ubuntu.com/8.04/printing/C/printing.html#network](https://help.ubuntu.com/8.04/printing/C/printing.html#network)

Regards,
Roger :cool:

Sorry, I posted this in the wrong place!!!

---

### Post by Cotopaxi on 2008-07-18
Dale,

I will give you intructions to perform one check, but my system is Kubuntu, so you will have to tranlate these instructions to your system.

In Main Menu>System Settings>Printers, click on "Add new Printer/Class".

Now click through, until you reach the window "Backend Selection", where you can choose the way the printer is connected. From the list of clickable items, there is one called "Local printer (parallel, serial, USB). Is this item CLICKABLE, or is it GRAYED OUT?

We will then start from there.

---

### Post by Dale Lewis on 2008-07-18
Cotopaxi,

I'm running Gnome and the menus are a little different. When I try to go into "printers" from the main menu it just hour glasses and stops. I am able to get in under the system admin screen and was able to pull this from a log. Thanks!!!!!

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x9abb100>,
 'cups_instance': None,
 'cups_queue': 'HP_Color_LaserJet_4650',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/HP_Color_LaserJet_4650?serial=00000D925AD0',
                       'printer-info': u'HP_Color_LaserJet_4650',
                       'printer-is-shared': True,
                       'printer-location': u'dale-desktop',
                       'printer-make-and-model': u'HP Color LaserJet 4650 Postscript (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'No %%BoundingBox: comment in header!',
                       'printer-state-reasons': [u'connecting-to-device'],
                       'printer-type': 37084,
                       'printer-uri-supported': u'ipp://localhost:631/printers/HP_Color_LaserJet_4650'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': 'No %%BoundingBox: comment in header!',
 'printer-state-reasons': 'connecting-to-device'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(54, u'Job canceled.')],
 'test_page_job_id': [54],
 'test_page_job_status': [(54, 'HP_Color_LaserJet_4650', 'Test Page')],
 'test_page_jobs_cancelled': True,
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'connecting-to-device'}

---

### Post by Cotopaxi on 2008-07-19
Ok Dale, eventually you will find a help in the following thread:

[http://kubuntuforums.net/forums/index.php?topic=3089184.0](http://kubuntuforums.net/forums/index.php?topic=3089184.0)

In this thread, go to the second of tomstrong and look at how he solved the problem.

Eventually this will solve your problem too.

Good Luck!

---

### Post by Dale Lewis on 2008-07-21
Thanks!!! That took care of it!! O:)

---

