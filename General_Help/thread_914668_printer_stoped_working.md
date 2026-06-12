---
title: "printer stoped working"
date: 2008-09-09
forum: General Help
---

### Post by Breakar on 2008-09-09
i reinstalled ubuntu and my printer stopped working its a MFC-260C, it picks up my printer with the correct name and driver but when i try print anything it does nothing at all. I'm using hardy 8.04

for device URI it says usb://Brother/MFC-260C, and i remember it being something else last time like 

direct hal:///org/freedesktop/Hal/devices/usb_device_4f9_1d6_BROC8F388199_if0_pr

```
 lpinfo -v
network socket
network beh
direct hal:///org/freedesktop/Hal/devices/usb_device_4f9_1d6_BROC8F388199_if0_printer_noserial
direct usb://Brother/MFC-260C
direct hpfax
direct hp
network http
network ipp
network lpd
direct parallel:/dev/lp0
file cups-pdf:/
direct scsi
network smb

```

I remember it printing really easily last time i had it running.

---

### Post by plucky on 2008-09-09
> i reinstalled ubuntu and my printer stopped working its a MFC-260C,


Have you re-installed the printer drivers,which are now packaged in synaptic.

```
sudo apt-get install brother-lpr-drivers-extra brother-cups-wrapper-extra
```

You might have to remove the printer shown in **System > Administration > Printing**


Good Luck

---

### Post by Breakar on 2008-09-09
i tried reinstall the drivers same thing, this is what i get from running the troubleshoot

```
Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x8eb2160>,
 'cups_instance': None,
 'cups_queue': 'MFC-260C',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Brother/MFC-260C',
                       'printer-info': u'Brother MFC-260C',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Brother MFC-260C CUPS v1.1',
                       'printer-state': 4,
                       'printer-state-message': u'Printer is now on-line.',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 135244,
                       'printer-uri-supported': u'ipp://localhost:631/printers/MFC-260C'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': 'Printer is now on-line.',
 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_job_status': [(42, 'MFC-260C', 'flyer')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': 'Printer is now on-line.',
 'printer-state-reasons': 'none'}

```

I'm not sure of this is related, but i remember i had a virtualbox installed and i had to create a USB group and enable myself, i wonder if i need to do that for the printer because i did at first install virtualbox before this printer and i dont have a virtualbox installed right now. I will try create a USB groups and see if that works i remember reading that 8.04 doesnt use USB groups.


edit - fixed the problem it had no ink.

---

