---
title: "MP C2500 printer on ubuntu"
date: 2010-02-03
forum: Hardware
---

### Post by Quintus on 2010-02-03
First I posted this in the network section of this forums, since I'm trying to connect the printer in question over the network. But I  thought this might the correct place to post it.


I'm trying to install a printer (MP C2500). It didn't have a driver installed in ubuntu, so I downloaded Ricoh Aficio MP C2500 PXL. Now ubuntu believes that the printing is without problems, so I get no error messages, but I cannot print anything.


Regards and thanks in advance

Quintus

---

### Post by IcarusR on 2010-02-03
There is a driver for this in CUPS.
Open browser & enter the following...

[http://localhost:631/]("http://localhost:631/") 

From there you can add your printer.
If the web page does not appear make sure you have CUPS installed.

---

### Post by Quintus on 2010-02-03
Thanks. I don't my printer right here, but I'll do that tomorrow afternoon.

How do I check for -  and if necessary install - CUPS?

---

### Post by Quintus on 2010-02-04
CUPS is installed, and I installed the printer the way you said. But I get this message "client-error-document-format-not-supported", when I open "printers" under "administration" and click on "print self test-page."

By the way, the driver I used was "Ricoh-Aficio_MP_C2500_PXL.ppd"

---

### Post by IcarusR on 2010-02-04
Try using the one that CUPS provides...
CUPS+Gutenprint v5.2.0-rc1 (en)

---

### Post by Quintus on 2010-02-05
Thanks, but I tried that also. It didn't work.

---

### Post by IcarusR on 2010-02-07
Found this suggestion on another forum as a solution to your origional error. 

> This might be the one where you have to uncomment something in /etc/cups/mime.convs and /etc/cups/mime.types. It's the last few lines, saying
#
# Uncomment the following filter to allow printing of arbitrary files
# without the -oraw option.
#

#application/octet-stream        application/vnd.cups-raw 0 - 

Could also try setting the debug level of cups to a high level "LogLevel debug" in cupsd.conf, then restart cups ```
etc/init.d/cupsys restart
```
 and look at /var/log/cups/error_log while trying to print the file.
```
tail -f /var/log/cups/error_log

```

---

### Post by Quintus on 2010-02-09
Did it, and nothing happened... :(

---

