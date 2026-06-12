---
title: "hp1000 printer install"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by hatmancan on 2009-02-01
i am having aa problem again with trying to install my hp driver
i went to the linux site for the direct download and entered the following after downloading to my desktop.
here is what i was told to enter...sh hplip-2.8.9.run

when i hit enter i get an error saying bad command./
am i missing auto run and if so where doo i find it?
i am very new to this so be aware
thanks
hat

---

### Post by Mark Phelps on 2009-02-01
Unless you have a very new model HP printer, it's best to use the version of HPLIP listed in Synaptic because that will take care of the dependencies as well.  Is the HP1000 a brand new printer model?

Suggest you check Synaptic (System --> Administration --> Synaptic Package Manager).  The default version in Intrepid is 2.8.7.

---

### Post by hatmancan on 2009-02-01
ok i re-installed
when i go to print a page says printer may not be connected..but is
can you make another suggestion?

i tried the run from terminal as it says to use update but will not let me run
thanks
hat

---

### Post by bpalone on 2009-02-01
If you haven't set up the printer in CUPS, you will not be getting it to work.  To set it up in CUPS enter the following address in your web browser:

[http://localhost:631](http://localhost:631)

I think you can figure it out from there.  If not, someone here will certainly be able to help.

---

### Post by hatmancan on 2009-02-03
i went to this and it shows my printer listed there..
do you know the instructions using sudo to install from the desktop?
i saved the recommended download to here but will not let me use auto-run?
is my auto not set up?
how do i check?
and how do i install
thanks
hat

---

### Post by bpalone on 2009-02-03
Go into your Synaptic Package Manager and do a search for "hplip" (without the quotes).  It should bring up somewhere around nine packages for that search.  Select the "hplip" entry and install it.

That should get you going.  I have a 1220C and it is very similar to the the 1000.  The package and some additional info is available on SourceForge if I remember correctly.  It sticks to my mind that the 1000 is in the list of supported printers.

If after installing, you are still having trouble go back into the CUPS setup and be sure that the printer is configured properly.

Good luck.

---

### Post by hatmancan on 2009-02-03
I reinstall the hplip
when i go to file print>says printing
nothing comes through on printer

how do i uninstall the printer itself and re-install
maybe that will help
i know it will work as it worked before
hat

---

### Post by hatmancan on 2009-02-03
ok i ran a diagnostics from some program
here is what i get back
can someone figure this out for me????
thanks in advance 
hat
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest hp-LaserJet-1000>,
 'cups_instance': None,
 'cups_queue': 'hp-LaserJet-1000',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/hp_LaserJet_1000?serial=0',
                       'printer-info': u'Hewlett-Packard hp LaserJet 1000',
                       'printer-is-shared': True,
                       'printer-location': u'dave-desktop',
                       'printer-make-and-model': u'HP LaserJet 1000 Foomatic/foo2zjs (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 36868,
                       'printer-uri-supported': u'ipp://localhost:631/printers/hp-LaserJet-1000'},
 'cups_printer_remote': False,
 'hplip_output': (['',
                   '\x1b[01mHP Linux Imaging and Printing System (ver. 2.8.7)\x1b[0m',
                   '\x1b[01mDevice Information Utility ver. 4.1\x1b[0m',
                   '',
                   'Copyright (c) 2001-8 Hewlett-Packard Development Company, LP',
                   'This software comes with ABSOLUTELY NO WARRANTY.',
                   'This is free software, and you are welcome to distribute it',
                   'under certain conditions. See COPYING file for more details.',
                   '',
                   '',
                   '\x1b[01mhp:/usb/hp_LaserJet_1000?serial=0\x1b[0m',
                   '',
                   '\x1b[01mDevice Parameters (dynamic data):\x1b[0m',
                   '\x1b[01m  Parameter                     Value(s)                                                  \x1b[0m',
                   '  ----------------------------  ----------------------------------------------------------',
                   '  back-end                      hp                                                        ',
                   '  cups-printer                  hp-LaserJet-1000                                          ',
                   '  cups-uri                      hp:/usb/hp_LaserJet_1000?serial=0                         ',
                   '  dev-file                                                                                ',
                   '  device-state                  1                                                         ',
                   '  device-uri                    hp:/usb/hp_LaserJet_1000?serial=0                         ',
                   '  deviceid                      MFG:Hewlett-Packard;MDL:hp LaserJet                       ',
                   '                                1000;CMD:ZJS;CLS:PRINTER;DES:hp LaserJet 1000;            ',
                   '  duplexer                      0                                                         ',
                   '  error-state                   0                                                         ',
                   '  host                                                                                    ',
                   '  in-tray1                      1                                                         ',
                   '  in-tray2                      1                                                         ',
                   '  is-hp                         True                                                      ',
                   '  media-path                    1                                                         ',
                   '  panel                         0                                                         ',
                   '  panel-line1                                                                             ',
                   '  panel-line2                                                                             ',
                   '  photo-tray                    0                                                         ',
                   '  port                          1                                                         ',
                   '  r                             0                                                         ',
                   '  revision                      254                                                       ',
                   '  rg                            000                                                       ',
                   '  rr                            000000                                                    ',
                   '  rs                            000000000                                                 ',
                   '  serial                        0                                                         ',
                   '  status-code                   1000                                                      ',
                   '  status-desc                   Idle.                                                     ',
                   '  supply-door                   1                                                         ',
                   '  top-door                      1                                                         ',
                   '\x1b[01m',
                   'Model Parameters (static data):\x1b[0m',
                   '\x1b[01m  Parameter                     Value(s)                                                  \x1b[0m',
                   '  ----------------------------  ----------------------------------------------------------',
                   '  align-type                    0                                                         ',
                   '  clean-type                    0                                                         ',
                   '  color-cal-type                0                                                         ',
                   '  copy-type                     0                                                         ',
                   '  embedded-server-type          0                                                         ',
                   '  fax-type                      0                                                         ',
                   '  fw-download                   1                                                         ',
                   '  icon                          default_printer.png                                       ',
                   '  io-mfp-mode                   1                                                         ',
                   '  io-mode                       1                                                         ',
                   '  io-support                    2                                                         ',
                   '  job-storage                   0                                                         ',
                   '  linefeed-cal-type             0                                                         ',
                   '  model                         hp_LaserJet_1000                                          ',
                   '  model-ui                      HP LaserJet 1000                                          ',
                   '  model1                        LaserJet 1000                                             ',
                   '  panel-check-type              0                                                         ',
                   '  pcard-type                    0                                                         ',
                   '  plugin                        1                                                         ',
                   '  power-settings                0                                                         ',
                   '  pq-diag-type                  0                                                         ',
                   '  r-type                        0                                                         ',
                   '  scan-style                    0                                                         ',
                   '  scan-type                     0                                                         ',
                   '  status-battery-check          0                                                         ',
                   '  status-dynamic-counters       0                                                         ',
                   '  status-type                   8                                                         ',
                   '  support-released              1                                                         ',
                   '  support-type                  2                                                         ',
                   '  support-ver                   2.7.12                                                    ',
                   "  tech-class                    ['LJZjsMono']                                             ",
                   "  tech-subclass                 ['Normal']                                                ",
                   '  tech-type                     3                                                         ',
                   '  usb-pid                       0517                                                      ',
                   '  usb-vid                       03f0                                                      ',
                   '\x1b[01m',
                   'Status History (most recent first):\x1b[0m',
                   '\x1b[01m  Date/Time             Code   Status Description                        User      Job ID  \x1b[0m',
                   '  --------------------  -----  ----------------------------------------  --------  --------',
                   '  02/03/09 18:59:19     1000   Idle.                                     dave      0       ',
                   '  02/03/09 18:57:52     501    Print job has completed.                  dave      10      ',
                   '  02/03/09 18:57:23     500    Started a print job.                      dave      10      ',
                   '  02/03/09 18:56:32     1000   Idle.                                     dave      0       ',
                   '  02/03/09 18:55:00     703    Printer is accepting jobs.                dave      0       ',
                   '  02/03/09 18:54:58     702    Printer is rejecting jobs.                dave      0       ',
                   '  02/03/09 18:54:37     501    Print job has completed.                  dave      9       ',
                   '  02/03/09 18:54:29     5021   Device is busy.                           dave      0       ',
                   '  02/03/09 18:53:46     500    Started a print job.                      dave      9       ',
                   '  02/03/09 18:53:46     1000   Idle.                                     dave      0       ',
                   '',
                   '',
                   'Done.',
                   ''],
                  ['']),
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'Copies': u'1',
                                            u'InputSlot': u'Auto',
                                            u'MediaType': u'Standard',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'Quality': u'normal'},
                               u'Miscellaneous': {u'Nup': u'1up',
                                                  u'NupOrient': u'port'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:HP;MDL:hp LaserJet 1000;CLS:PRINTER;DES:hp LaserJet 1000;SN:0;',
                      'device-info': u'HP LaserJet 1000 USB 0 HPLIP',
                      'device-make-and-model': u'HP LaserJet 1000'}}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 388L}
Page 8 (Print test page):
{'test_page_attempted': True,
 'test_page_job_id': [11],
 'test_page_job_status': [(True,
                           11,
                           'hp-LaserJet-1000',
                           'Test Page',
                           'Processing',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-ca',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 11,
                            'job-k-octets': 17,
                            'job-media-sheets-completed': 1,
                            'job-more-info': u'ipp://localhost:631/jobs/11',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'dave',
                            'job-printer-state-message': u'',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1233702000,
                            'job-printer-uri': u'ipp://dave-desktop:631/printers/hp-LaserJet-1000',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 5,
                            'job-state-reasons': u'job-printing',
                            'job-uri': u'ipp://localhost:631/jobs/11',
                            'job-uuid': u'urn:uuid:38ca7ca0-abf8-3db1-5ad9-f1e2d6ec5aa4',
                            'printer-uri': u'ipp://localhost/printers/hp-LaserJet-1000',
                            'time-at-completed': None,
                            'time-at-creation': 1233701973,
                            'time-at-processing': 1233701973})],
 'test_page_successful': False}
Page 9 (Error log fetch):
{'error_log': []}

---

### Post by bpalone on 2009-02-03
It looks like you have everything there, but your printer isn't identified to the system.   Here is what my printer def looked like from the CUPS browser interface:

Description: DeskJet_1220C
Location: bill-desktop
Printer Driver: HP Deskjet 1220c Foomatic/hpijs, hpijs 2.8.2
Printer State: idle, accepting jobs, published.
Device URI: hp:/usb/DeskJet_1220C?serial=SG0BH130ZQOK 

(This was from before I networked everything.)

Notice the serial=XXXXXXXXXXXXXX at the end of the URI:.  That is how it is identified to the system.  I can't remember how to get that info, or if the CUPS interface got it after or while I modified the printer.  Try going through the modify printer and see if that gets it to see the printer properly.  Then do a test page.  You are close, but close only counts in horse shoes and and grenades.  I may have to dig out one of my books and find setting up CUPS to get you there if this doesn't get it.

Don't give up.  I fought quite a while when I moved to network printing, but I got it figured out.

---

### Post by hatmancan on 2009-02-04
tried to modify printer..
still says printing job but nothing comes through on the printer..
any other suggestions?
ty
hat

---

### Post by bpalone on 2009-02-05
Ok, let's be sure that your printer is being seen.  In a terminal type the following:   lsusb     your printer should be listed as one of the usb devices. 

One other question.  Do have your printer plugged in and turned on when you start your computer or boot into Ubuntu?  If not your printer won't be found (according to my reference material). 

If things are working correctly your printer should be listed in /proc/bus/usb/devices (again according to my reference material).

I hope this helps.  If not maybe we can set a time so we are both on the forums at the same time.

---

### Post by hatmancan on 2009-02-05
here is the output i get
dave@dave-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 03f0:0517 Hewlett-Packard LaserJet 1000
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
dave@dave-desktop:~$ 
is this the way it should be?
hat

---

### Post by bpalone on 2009-02-05
It is seeing it.  Did you have it turned on when you booted?

If so, then CUPS should of found it.  If not, reboot with the printer turned on.  Then go to the Browser CUPS page and try a test page again.

If you still have no joy, then I would try adding your printer again via the browser page.  It will step you through several steps that are pretty much self explanatory.  Just, give it a different name than the entry CUPS now shows in the printer list.  You may have to play with some of the options.

Here is what I had used when I had my Deskjet 1220C hooked to the computer via USB:

Device: AppSocket/HP Jetdirect
Device URI: hp:/usb/DeskJet_1220C?serial=SG0BH130ZQOK
Make: HP
Model: HP Deskjet 1220c Foomatic/hpijs(en)

Hope this helps.

---

### Post by hatmancan on 2009-02-06
ok still no luck installing printer
still keeps saying printing but printer does not print
printer is on
does anyone have instructions on how to update the printer drivers?
maybe this is problem
thanks
hat

---

### Post by bpalone on 2009-02-07
OK, just did a quick Google and found that a driver is needed with the Hplib.  Here is the link to where I found that info:

[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1000.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1000.html)

Now, here is where to get the driver and instructions for the install:

[http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)

Sorry for the run around earlier. Had I done the Google earlier we would of had it done and over with.  As they say, "GOOGLE is your friend."

Good luck.

Just found some more info for you about it:

[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1000](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1000)

---

### Post by hatmancan on 2009-02-07
bp
i went back in a thread i had before located here below
[http://ubuntuforums.org/showthread.php?t=957084](http://ubuntuforums.org/showthread.php?t=957084)
i used the instructions there and was able to get printer to work..
when i used the location you said to it would not work..maybe keep this for reference in case someone else comes across this for an hp1000

thanks for all your help
hat

---

