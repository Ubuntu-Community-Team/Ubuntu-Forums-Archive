---
title: "Lost printer configuration"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by MacDuff on 2009-05-28
Trying out Kubuntu 9.04 and when I tried to set up a network printer the system stalled.  I re-booted and now when I return to select Printer Configuration the cursor just spins until it times out.  I cannot get into the printer configuration file.

What do I need to do to restore the printer configuration?

---

### Post by Christian_Joe_Linux on 2009-08-13
Yeah, I can't even install a printer in Ubuntu 9.04.  The system can't create a tmp file for the printer

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest psc-1200-series (default)>,
 'cups_instance': None,
 'cups_queue': 'psc-1200-series',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/psc_1200_series?serial=MY39JF216H5H',
                       'printer-info': u'HP psc 1200 series',
                       'printer-is-shared': True,
                       'printer-location': u'rubori',
                       'printer-make-and-model': u'HP PSC 1200 Series hpijs, 3.9.2',
                       'printer-state': 3,
                       'printer-state-message': u"Can't create temporary file",
                       'printer-state-reasons': [u'connecting-to-device'],
                       'printer-type': 167948,
                       'printer-uri-supported': u'ipp://localhost:631/printers/psc-1200-series'},
 'cups_printer_remote': False,
 'hplip_output': (['',
                   '\x1b[01mHP Linux Imaging and Printing System (ver. 3.9.2)\x1b[0m',
                   '\x1b[01mSystem Tray Status Service ver. 2.0\x1b[0m',
                   '',
                   'Copyright (c) 2001-9 Hewlett-Packard Development Company, LP',
                   'This software comes with ABSOLUTELY NO WARRANTY.',
                   'This is free software, and you are welcome to distribute it',
                   'under certain conditions. See COPYING file for more details.',

---

