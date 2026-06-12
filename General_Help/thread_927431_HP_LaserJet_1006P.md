---
title: "HP LaserJet 1006P"
date: 2008-09-23
forum: General Help
---

### Post by Bynw on 2008-09-23
I have an HP Laserjet 1006P printer.

I connected to my Ubuntu box and it automatically installed and worked just fine. Then it stopped working. It does not give any errors. It shows the job going to the printer. It shows the job completed. But nothing prints.

I removed the printer completely and put it back 2-3 times before it would print normally again. Moving the printer to another computer (Windows Vista, Mac OS X (Leopard) and it works fine.

Moving the printer back to the Ubuntu machine and it stops working again. Even after restarting the printer. Removing the printer and readding it again. I've done this 3 times so far and it still is not printing out anything.

I need help to get this issue resolved so I stop loosing my printer.

Thanks.


Here is the troubleshooter's bug report when trying to print a test page that said it completed but never printed.

```


Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x8709120>,
 'cups_instance': None,
 'cups_queue': 'HP_LaserJet_P1006',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/HP_LaserJet_P1006?serial=AA09928',
                       'printer-info': u'Hewlett-Packard HP LaserJet P1006',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'HP LaserJet P1006 Foomatic/foo2xqx (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167956,
                       'printer-uri-supported': u'ipp://localhost:631/printers/HP_LaserJet_P1006'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(58, u'Job completed.')],
 'test_page_job_id': [58],
 'test_page_job_status': [(58, 'HP_LaserJet_P1006', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}


```

---

### Post by Muffe on 2008-10-09
I have the same printer. I have tried it on both 8.04 and 8.10, with the same result. The printer is automatically detected and installed, but no paper is coming out of the printer, even tough everything looks good on the PC....

Edit 2008-10-10: Problem solved. I followed the instructions on [http://foo2xqx.rkkda.com/](http://foo2xqx.rkkda.com/) , and then everything worked nicely. I am using Intrepid Ibex at the moment.

---

### Post by hubiedo on 2009-09-02
Thanks- it really works for hp lj p1006 - just like a charm.

this is the second thing i did after it worked. i immediately made a donation to those guys. wow did they save my rear end along with this post.

thanks again

---

### Post by iv2101 on 2010-05-27
I'm glad someone (most people) got their printers working using the instructions on [http://foo2xqx.rkkda.com/](http://foo2xqx.rkkda.com/) but I just can't get any paper to come out of it. I have the hp laserjet p1006. I followed the instructions on the website (fetch, compile, etc) and then I tried (many times) to add the printer in system-config-printer. How do I make it use the new driver?

Thanks!

---

### Post by hubiedo on 2010-05-27
have you tried their forums that they refer to in the directions?

---

### Post by iv2101 on 2010-05-31
Got it working! instructions for adding a printer are not in the ubuntu section but in the cups section. I read it somewhere on their forum. So the thing to do was to add a generic usb printer and this URI: 

CUPS USB NOTES
--------------
    If you are using the USB port, then the URI should be:
	usb:/dev/usb/lp0
	usb:/dev/usb/lp1
    OR
	usb://Samsung/CLP-310%20Series
	usb://Samsung/CLP-310%20Series
	usb://HP/Color%20LaserJet%20CP1215
	usb://HP/Color%20LaserJet%202600n
	usb://HP/LaserJet%201000
	usb://HP/LaserJet%201005
	usb://HP/LaserJet%201018
	usb://HP/LaserJet%201020
	usb://HP/LaserJet%20P1005
	usb://HP/LaserJet%20P1006
	usb://HP/LaserJet%20P1007
	usb://HP/LaserJet%20P1008
	usb://HP/LaserJet%20P1505

    Don't use hp://<whatever> because that is for hplip (a closed source,
    proprietary driver).

---

