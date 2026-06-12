---
title: "Epson D120 Printer"
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by diw on 2007-11-13
The D120 printer is automatically set up in Gutsy using the Gups +Gutenprint 5.01 simplified driver which is used for the D88 epson printer.  The D120 isn't listed which is why it presumably default s to the D88.  However, the printer doesn't work properly with this driver, despite fiddling around with the many settings.

I went to the epson website to look for a linux driver and was eventually redirected to the avasys website who do the linux drivers.  Although separate drivers exist for Redhat, Suse, mandriva and a couple of others, Ubuntu isn't listed so I chose Debian.  But when I do this it only gives me a one binary which is pips-sc120-Redhat9-3.0-CLGE.tgz and one source pips-3.0-1.src.rpm.  Now I'm only a novice here but I didn't think RPM's were Debian?  If you think it is safe to install the binary how do I do this?

---

### Post by highvalley on 2007-11-23
Hi

I invested some hours and got the thing to run  

1)
Run the installer you can get from
[www.avasys.jp](www.avasys.jp)
The installer exits with an error.

2)
Add your printer in cups.
(define ppd) find it here: /usr/share/cups/model/eksc120.ppd

3)
Set cups to use raw-data
in /etc/cups/mime.types
and /etc/cups/mime.convs 
remove the '#' in the line #application/octet-stream 

4) 
Restart Cups 

5)
create a file /etc/pipsrc 
(The content can be found in /usr/local/EPAva/printers/sc120/pipsrc_sc120)
...otherwise copy this file to /etc and rename it.

6)
create /etc/ekpdrc 
(The content can be found in /usr/local/EPAva/printers/sc120/ekpdc_sc120)
Attention: Cange the URI to: /dev/usblp0

7)
sudo /usr/local/EPAva/spooler/lpr/lprsetup
sudo /usr/local/EPAva/spooler/cups/cupsetup

8)
start /usr/local/EPAva/core/ekpd 
(edit init.d to start ekpd automaticaly) 


... after that you can print a test-page, and out of openoffice.
You cannot print from gthumb, eog, evince, etc. don't ask me why.

But hey, the printer prints ...
Sorry for no more detailed description, but you will make it.

find a description in german here:
[http://www.igperau.at/phpBB2/viewtopic.php?p=1376](http://www.igperau.at/phpBB2/viewtopic.php?p=1376)

best regards

Mr. Highvalley

---

### Post by diw on 2007-11-27
Thank you for this - it must have taken you some considerable time but It is way too complicated for me.  I have had to move over to mandriva where I have found that the avasys driver works with a simple double click of the mouse, installs itself, sets itself up in the driver database and is there ready to be used by adding another printer.

---

### Post by airon on 2008-01-01
Hi,
with the last version of Gutenprint 5.1.5 (it's a development release of Gutenprint 5.1) also the d120 is automatically set up without any external drivers.
Find it here: [http://gimp-print.sourceforge.net/](http://gimp-print.sourceforge.net/)
Regards

---

### Post by pixdamix on 2008-01-06
How to make Gutenprint 5.1.6 packages for ubuntu:

[http://devlife.org/en/miscellaneous/14/epson-stylus-d120-under-debian-ubuntu-whatever.html](http://devlife.org/en/miscellaneous/14/epson-stylus-d120-under-debian-ubuntu-whatever.html)

---

