---
title: "HPLIP crashes during scanner setup process"
date: 2011-05-04
forum: Hardware
---

### Post by FuriousGeorge on 2011-05-04
When attempting to configure my HP MF2727 Multifunction device for network scanning through HPLIP the device is detected but the program crashes when I click "Next".

When running the software from the console the following error appears in Kubuntu 8.04:

$ sudo hp-setup

HP Linux Imaging and Printing System (ver. 2.8.2)
Printer/Fax Setup Utility ver. 7.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Traceback (most recent call last):
  File "/usr/share/hplip/ui/setupform.py", line 275, in showPage
    self.readwriteFaxInformation(True)
  File "/usr/share/hplip/ui/setupform.py", line 814, in readwriteFaxInformation
    self.fax_number = unicode(d.getPhoneNum())
  File "/usr/share/hplip/fax/soapfax.py", line 129, in getPhoneNum
    return fax_setup['faxsetupwizard-faxvoicenumber-faxnumber']
KeyError: 'faxsetupwizard-faxvoicenumber-faxnumber'


I've tried Google searching for a solution, but no luck thus far.

Any help is much appreciated.

---

### Post by FuriousGeorge on 2011-05-18
Bump?

---

