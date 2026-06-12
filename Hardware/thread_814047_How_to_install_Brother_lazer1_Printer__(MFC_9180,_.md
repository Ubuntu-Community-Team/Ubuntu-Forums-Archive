---
title: "How to install Brother lazer1 Printer:  (MFC 9180, etc) on Ubuntu 8.04"
date: 2008-05-31
forum: Hardware
---

### Post by mia.king on 2008-05-31
Hi, my first post, hopes it helps someone and is not a duplicate.

I'm running Xubuntu 8.04, Dell Inspiron 6000, and I have a Brother MFC 9180 connected via USB.

(If you're using another printer - search "Brother" in synaptic. Check the list of supported printers under each of the CUPS or LPR options if you have a different printer.)


Don't [have to] plug in printer yet.

synaptic or apt-get the following 2 and its dependencies (if you can't find it, you need to add multiverse)
brother-cups-wrapper-laser1
brother-lpr-drivers-laser1



[Plug in printer, and it should auto-detect and bring up button for installing a new driver, click that, else...]
!Applications!Settings!Printing 
!Edit!New printer
Brother MFC-9180 USB #1
[Tick] Select printer from database, and choose: Brother
MFC-9180 for CUPS (should now appear after installing the above packages)
Just select new PPD unless you've got old settings

Change the paper type, and toner settings as per your usage in tab printer options.


Less frustration to all!
mia

---------------
comments:

My printer was automatically detected by Ubuntu 8.04 correctly, but no driver or the wrong driver (?Brother MFC-9100c) was installed. It printed gibberish only. 

Attempting to use the PPD file from my CD (winXP/addprinter) as per another suggestion - gave me no help . BroMF918.ppd gave errors only.


My small brain was unable to understand the instructions from other sites, but some comments:

?useful
[http://www.iclbiz.com/brothermfc/](http://www.iclbiz.com/brothermfc/)   

?claimed to be so easy but wasn't
[http://www.freesoftwaremagazine.com/articles/printing_ubuntu](http://www.freesoftwaremagazine.com/articles/printing_ubuntu)


?says lots of nothing (that I couldn't understand or didn't need to use) but sounded great
[https://wiki.ubuntu.com/BrotherDriverPackaging](https://wiki.ubuntu.com/BrotherDriverPackaging)
[http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html)
[http://ubuntuforums.org/showthread.php?t=105703&page=16](http://ubuntuforums.org/showthread.php?t=105703&page=16)
[http://packages.ubuntu.com/source/hardy/brother-lpr-drivers-laser1](http://packages.ubuntu.com/source/hardy/brother-lpr-drivers-laser1)

?Don't believe these (perhaps only in my context)
[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#143](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#143)
[http://ubuntuforums.org/archive/index.php/t-252922.html](http://ubuntuforums.org/archive/index.php/t-252922.html)
(don't worry about above post, the LPR and CUPS files installed by synaptic/apt-get are safe - won't damage your system)

---

### Post by mia.king on 2008-06-01
I take the above line back...

Installing the printer, has not affected my apt-get/synaptic but my WINE no longer works...

Prompt> winecfg
(how do you do screen dumps? And copy and paste from terminals?)


fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:winsock:WSASocketW Unsupported socket family -1!
fixme:ds:DsRoleGetPrimaryDomainInformation ((nil), 1, 0x33f040) stub
fixme:advapi:LsaOpenPolicy ((null),0x33efe8,0x00000001,0x33f004) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:profile:CloseProfileUserMapping (), stub!
fixme:advapi:ObjectOpenAuditAlarmW stub 
(L"Spooler",0x5c0150,L"Server",L"\\\\eyubuntu",0x13a270,0xbc,0x00000001,0x00000001,(nil),0,1,0x75bfb4fc)
fixme:advapi:ObjectCloseAuditAlarmW stub (L"Spooler",0x5c0150,0)
err:winspool:add_printer_driver Failed adding driver "wineps.drv" 
("Windows NT x86"): 1805
err:winspool:CUPS_LoadPrinters printer 'MFC-9180' not added by 
AddPrinterA (error 1797)
fixme:advapi:ObjectOpenAuditAlarmW stub 
(L"Spooler",0x5c0150,L"Server",L"\\\\eyubuntu",0x13a270,0xbc,0x00000001,0x00000001,(nil),0,1,0x75bfb4fc)
fixme:advapi:ObjectCloseAuditAlarmW stub (L"Spooler",0x5c0150,0)
err:winspool:add_printer_driver Failed adding driver "wineps.drv" 
("Windows NT x86"): 1805
fixme:winspool:AddPrinterW Can't create printer L"PDF"
err:winspool:CUPS_LoadPrinters printer 'PDF' not added by AddPrinterA 
(error 1801)
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} 
not registered


Seems that other people have the same error message, it sound like the solution was to delete the whole wine installation, esp. the .wine directory to clear all the settings and install again.

Is there another solution? Thanks.

---

