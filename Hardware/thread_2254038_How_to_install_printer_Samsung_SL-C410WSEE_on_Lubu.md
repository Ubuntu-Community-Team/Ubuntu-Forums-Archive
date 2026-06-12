---
title: "How to install printer Samsung SL-C410W/SEE on Lubuntu 14.04 LTS?"
date: 2014-11-24
forum: Hardware
---

### Post by bartek6 on 2014-11-24
Hello Everybody,

I need your help with installing my new printer Samsung SL-C410W/SEE known also as Samsung C410W. Printer is brand-new and already tested on Win7. From site [http://www.samsung.com/pl/support/model/SL-C410W/SEE](http://www.samsung.com/pl/support/model/SL-C410W/SEE) I've downloaded file called "[Print Driver]("http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=UNI_PL&CttFileID=5768596&CDCttType=DR&ModelType=N&ModelName=SL-C410W&VPath=DR/201407/20140710101538239/ULD_V1.00.27.04.tar.gz")" prepeared for Linux. Unfortuanatelu I've no experience with installing printer on lubuntu so I've decided to ask you form help. How can I install driver for this printer from this file?

---

### Post by Enigma12 on 2014-11-25
I am also running Lubuntu 14.04, but I am still fairly new to this Linux stuff, so maybe someone else will have a better approach. Here's my suggestions: 

1 - Have your printer turned on
2 - Click on the LXDE icon on the extreme bottom left
3 - Click on System Tools
4 - Click on Printers
5 - If your printer is not shown in list, click Add. 
6 - If your printer then shows up, just go through the rest of the installation. You may have to select the driver you downloaded if the printer isn't configured automatically. If the driver is either a deb or tar or gz, it may need to be unpacked (This is where my newbie status gets proven.) before that driver can be used. 
7 - If you get through all this and print a test page that is correct, you should be done. Hopefully. If this doesn't work, maybe someone else more knowledgeable than me will offer a better process.

---

### Post by bartek6 on 2014-11-25
Problem solved.

1) Download driver for printer from Samsung website
[http://www.samsung.com/pl/support/model/SL-C410W/SEE](http://www.samsung.com/pl/support/model/SL-C410W/SEE)

2) Open terminal
```
cd /home/user/.../uld (destination folder for unpacked file) 
```

```
 sudo ./install-printer.sh
``` and follow installer

3) Follow Wayne_Terrebonne (above) instructions

---

### Post by Scott_Paulson on 2015-10-25
This thread was helpful to get me started in the right direction.  I did have trouble, because I was trying to install the driver for a network printer (not physically connected to my linux machine).  It would appear to install properly, but then it would not print, and would keep giving a "cups" related error.  I finally succeeded when I downloaded an updated driver...I used: UnifiedLinuxDriver-1.00.27.tar.gz.  I downloaded and extracted that file.  Then, I used the sudo ./install-printer.sh command.  It properly identified the network printer and asked if I wanted the installation file to automatically configure the firewall.  I selected 'y' and everything installed correctly.  The printer printed the test page properly.

---

### Post by fractaldg on 2016-07-01
NOTE: When installing in Ubuntu 16.04, a message was received indicating that the filter driver (/usr/lib/cups/filter/rastertospl) was missing.

A quick 'locate rastertospl' gave "/opt/smfp-common/printer/bin/rastertospl", so the locations of the files appear to have changed or been misinterpreted by the Samsung installer and/or cups.

The solution is: sudo ln -s `locate --limit 1 rastertospl` /usr/lib/cups/filter/

---

