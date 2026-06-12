---
title: "CUPS Printing From  Vista"
date: 2006-11-26
forum: Hardware &amp; Laptops
---

### Post by tufkal on 2006-11-26
I recently updated my laptop to Windows Vista to try it out, and I have been unable to get it to connect to my printer on my Edgy Eft box.  In the past, I just ran the Adobe Postscript drivers and pointed it to my printer on my EE box, but that program will not work in Vista.  Is there another generic post script driver out there for Vista and/or is there a way I can configure my CUPS differently to make this work with less effort?  Here is my smb.conf.

[global]
	netbios name = TUX
	workgroup = WORKGROUP
        server string = File Server
        security = SHARE
        domain master = Yes
        printing = cups


[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        guest ok = Yes
        printable = Yes
        browseable = No

---

