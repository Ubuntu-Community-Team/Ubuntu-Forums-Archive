---
title: "Trying to print with authentication"
date: 2017-10-31
forum: Hardware
---

### Post by cdunivan on 2017-10-31
I'm trying to print to a Konica Minolta bizhub C658 in my office with authentication. We send a job to the printer, walk to it, log in using a keyboard, and then the document (supposedly) prints out. It works fine in Windows, but my desktop dual-boots with Ubuntu 16.04, where I do spend more than 90% of my time. I've already implemented the steps from this thread:

[https://ubuntuforums.org/showthread.php?t=2292528](https://ubuntuforums.org/showthread.php?t=2292528)

I went to the Konica Minolta website and downloaded the latest driver, KOC658UX.ppd, and added the line shown in bold below to the first few lines, clipped to show here:

> *PPD-Adobe: "4.3"
*FormatVersion: "4.3"
*LanguageVersion: English
*LanguageEncoding: ISOLatin1
*FileVersion: "90001.0006"
*% Linux Version


***cupsFilter:    "application/vnd.cups-postscript 0 minolta"**


*Manufacturer: "KONICA MINOLTA"
*ModelName: "KONICA MINOLTA C658SeriesPS/P"
*ShortNickName: "KONICA MINOLTA C658"
*NickName: "KONICA MINOLTA C658SeriesPS(P)"
*PCFileName: "KOC658UX.ppd"
*Product: "(KONICA MINOLTA C658)"
*PSVersion: "(3016.102) 1"


KOC658UX.km resides in /etc/cups/ppd, has permissions set to 755 and reads:

> ACCOUNT_NAME="_*myusername*_"
ACCOUNT_PASSWORD="_*mypassword*_"
ACCOUNT_COETYPE="0"


A file called minolta resides in /usr/lib/cups/filter and reads:

> #!/bin/bash


source /etc/cups/ppd/${PRINTER}.km


echo -en "\033%-12345X"
echo -en "@PJL JOB\015\012"
echo -en "@PJL SET KMUSERNAME = \"${ACCOUNT_NAME}\"\015\012"
echo -en "@PJL SET KMUSERKEY2 = \"${ACCOUNT_PASSWORD}\"\015\012"
echo -en "@PJL SET KMCOETYPE = ${ACCOUNT_COETYPE}\015\012"
echo -en "@PJL ENTER LANGUAGE = POSTSCRIPT\015\012"


cat -


echo -en "\004\033%-12345X\015\012@PJL EOJ\015\012"
echo -en "\033%-12345X"



And I restarted CUPS before printing a test page.

I can tell it's connecting, because in the properties window for the printer, the toner levels tab is showing the different levels, and when I log in to have it print my job, I can see it in the log. It's just deleted, with a login error. Any ideas?

---

