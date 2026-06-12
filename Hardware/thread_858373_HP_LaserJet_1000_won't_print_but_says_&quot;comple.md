---
title: "HP LaserJet 1000 won't print but says &quot;completed&quot;"
date: 2008-07-13
forum: Hardware
---

### Post by sven 22 on 2008-07-13
Hi,

I'm new to Linux and just did a fresh 8.04 install.

Have just locally installed an HP 1000 printer, including driver.
It printed remotely from an XP box.

But it's not printing, even through Document Print Status is "completed." Is it not fully installed, and how should I finish the install?

Thanks! 

Sven

Below is the troubleshoot printout.

Page 1 (Choose printer):

{'cups_dest': <cups.Dest object at 0x870e0c0>,

 'cups_instance': None,

 'cups_queue': 'hp_LaserJet_1000',

 'cups_queue_listed': True}

Page 2 (Check printer sanity):

{'cups_device_uri_scheme': u'hp',

 'cups_printer_dict': {'device-uri': u'hp:/usb/hp_LaserJet_1000?serial=0',

                       'printer-info': u'hp_LaserJet_1000',

                       'printer-is-shared': True,

                       'printer-location': u'heron1',

                       'printer-make-and-model': u'HP LaserJet 1000 Foomatic/foo2zjs (recommended)',

                       'printer-state': 3,

                       'printer-state-message': u'',

                       'printer-state-reasons': [u'none'],

                       'printer-type': 167940,

                       'printer-uri-supported': u'ipp://localhost:631/printers/hp_LaserJet_1000'},

 'is_cups_class': False}

Page 3 (Printer state reasons):

{'printer-state-message': '', 'printer-state-reasons': 'none'}

Page 4 (Print test page):

{'test_page_job_status': [], 'test_page_successful': False}

Page 5 (Printer state reasons):

{'printer-state-message': '', 'printer-state-reasons': 'none'}

---

### Post by retrow on 2008-07-13
You can use the *generic postscript printer* instead of choosing your specific printer from the list. I had the same problem with my Xerox printer and choosing the generic postscript option resolved the problem.

---

### Post by sven 22 on 2008-07-13
Hi,

Well, I tried the generic driver but that's not working either.

The printer DID work from this install of Heron, using the HP driver, when I had the printer connected to a Windows box.

And I've deleted that printer reference to the Windows box to avoid confusion.

And I tried rebooting the computer and rebooting the printer.

---

### Post by sven 22 on 2008-07-13
Hmmm. Well that IS a puzzle.

That's two computers with fresh installs of Heron 8.04 and the printer works with neither, although the foo2zjs driver is installed, and the printer self-test page works.

I've checked off "enabled" and "accepting jobs."

I've tried deleting and re-installing the HP LaserJet 1000 (basic laser) printer, and that's also what the HP manual says to do.

So...evidently there's something more to the install process.

---

### Post by rjbeeth on 2008-09-25
How did your problem resolution work out?

I do have an HP1000 printing locally from an Ubuntu box and it is working fine on Ubuntu 8.04. However I am having serious issues printing across the network to it from an XP laptop.

It is doing exactly the same sort of thing as you were having (hence the question).

I've actually dug a little deeper and captured both spooled documents and have found that the local spool (which works) differs dramatically from the network spool (which doesn't) but so far no one has offered any suggestions.

If you are still having problems printing locally I might be able to help, however be warned that I haven't figured out the network printing issues yet!

---

