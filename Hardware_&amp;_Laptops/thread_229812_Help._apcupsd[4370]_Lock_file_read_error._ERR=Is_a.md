---
title: "Help. apcupsd[4370]: Lock file read error. ERR=Is a directory"
date: 2006-08-05
forum: Hardware &amp; Laptops
---

### Post by fubadubrub on 2006-08-05
I have solved the mystery with the help of the people from the apcupsd mailing list.

My (# UPSNAME xxx) was in the wrong format I had set it to simply (xxx).

Wrong
** Back-UPS**

Right
**UPSNAME Back-UPS**

Also my usb       <BLANK> was wrong as well.

Wrong
**usb       <BLANK>**
It is not literal.

Right
**usb**

Please help me get my ups running properly.  I checked /var/lock and it's a directory.  What do I do now.

Aug  4 20:17:42 ubuntu apcupsd[4370]: Terminating due to configuration file errors. 
Aug  4 20:17:42 ubuntu apcupsd[4370]: Lock file read error. ERR=Is a directory 
Aug  4 20:17:42 ubuntu apcupsd[4370]: apcupsd error shutdown completed

Installed:
apcupsd        3.12.1-1
apcupsd-cgi   3.12.1-1
apcupsd-doc  3.12.1-1

Here is my configuration file.  And yes I have set it to IS Configured to =yes.  APC Back-UPS RS 1500

# UPSNAME xxx
#   Use this to give your UPS a name in log files and such. This
#   is particulary useful if you have multiple UPSes. This does not
#   set the EEPROM. It should be 8 characters or less.
Back-UPS

# usb       <BLANK>          Most new UPSes are USB.
#                            A blank DEVICE setting enables
#                            autodetection, which is th best choice
#                            for most installations.
UPSTYPE usb
DEVICE <BLANK>

# LOCKFILE <path to lockfile>
#   Path for device lock file.
LOCKFILE /var/lock

---

