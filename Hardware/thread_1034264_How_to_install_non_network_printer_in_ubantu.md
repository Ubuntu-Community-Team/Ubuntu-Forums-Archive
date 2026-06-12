---
title: "How to install non network printer in ubantu?"
date: 2009-01-08
forum: Hardware
---

### Post by ubantuwannabe on 2009-01-08
Hi,

I'm a linux newbie.

currently I'm installing ubantu on my laptop inspiron 6000. My printer is not attached to any server. My printer is RICOH Aficio MP C2500 PCL 6.

I try all ways of configuring but to no avail.

Here's what I do:

I choose AppSocket/HPDirect

Enter Host 192.168.aa.bb
Port Number 9100 default
click next

next select printer from database

I choose Ricoh.

I choose Aficio MP 2500
I choose the recommended drivers

end of set up.

when I print and view document status there's no error but in the end it din printout, why is this so?

I have 

sudo tail -80 /var/log/cups/error_log


E [08/Jan/2009:18:35:44 +0800] CUPS-Add-Modify-Printer: Unauthorized
E [08/Jan/2009:18:35:44 +0800] cupsdAuthorize: Local authentication certificate not found!
E [08/Jan/2009:18:35:44 +0800] cupsdAuthorize: Local authentication certificate not found!
E [08/Jan/2009:18:35:44 +0800] cupsdAuthorize: Local authentication certificate

I dun get it how come on one hand it is saying u have printed on the other hand it is saying that's an error and worse of all it is not printed yet I have the message that it is printed!

thanks for any assistance rendered!:P

---

### Post by dmizer on 2009-01-09
Moved this to hardware, since this is not a networking question.

Check here: [http://openprinting.org/show_printer.cgi?recnum=Ricoh-Aficio_MP_C2500](http://openprinting.org/show_printer.cgi?recnum=Ricoh-Aficio_MP_C2500)

Looks like the drive you should be using is: pxlcolor-Ricoh?

---

