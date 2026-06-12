---
title: "Samsung ML-4500 print setup problems"
date: 2005-12-12
forum: Hardware &amp; Laptops
---

### Post by bazcor on 2005-12-12
Hello and thanks for reading this. The problem I have is tha my printer (samsung ML-4500) will not print it just sits there, although the printer is shown as 'ready'.

When I go to a terminal and type 'sudo gedit /etc/X11/xorg.conf' and then  attempt to print the document, the following text is produced in the terminal window:-
-----------------------------------------------------------------------
barry@ubuntu:~$ sudo gedit /etc/X11/xorg.conf
Password:
Model not found, discarding config

(gedit:10261): GnomePrint-WARNING **: Could not create filter from description 'frgba': filter 'frgba' is unknown

(gedit:10261): GnomePrintCupsPlugin-WARNING **: iconv does not support ppd character encoding: ISOLatin1, trying CSISOLatin1
---------------------------------------------------------------------------

I have both cups and foomatic packages installed. What am I missing here?

TIA Barry.

Edit .. all ok now by a system of pure guess work I have found the solution!!!

---

### Post by garethppls on 2006-03-30
would be very nice if you told us how because I'm having problems with it now :(

---

