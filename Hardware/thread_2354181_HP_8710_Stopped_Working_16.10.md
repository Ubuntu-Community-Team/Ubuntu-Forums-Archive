---
title: "HP 8710 Stopped Working 16.10"
date: 2017-02-28
forum: Hardware
---

### Post by yinzpitmaster on 2017-02-28
Two days ago the printer stopped accepting jobs. Error said the printer could not be found. Restarted the printer & computer and tried again. Still could not find the printer. So, I removed the printer from the system and tried to reinstall. When I searched for the printer it is not coming up.

Should I:
[LIST=1]
[*]Remove & reinstall ALL printing packages?
[*]Continue to try and locate the printer
[*]Something else you recommend.
[/LIST]
Thanks

---

### Post by pdc on 2017-02-28
I guess one can trouble-shoot by "frequency gambling": ie what you reckon happens mostest ....... or having a structured approach;

to their credit, Ubuntu offer a troubleshooting guide [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems) which is very structured: it may sound an awful chore but perhaps you work through that; as you go through it, useful things like ```
lsusb
``` lets you see if the printer is seen and your usb seems to work; and ```
lpinfo -v
``` asks for a verbose readout of what lpinfo (linux printing infor) sees ........

HP provide diagnostics that you can look at later 

this is the main page [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) and over on the right of this page you can click on troubleshooting things [http://hplipopensource.com/node/224](http://hplipopensource.com/node/224)

let us know how you get along

---

### Post by ajgreeny on 2017-02-28
You need hplip 3.16.5 for that OfficeJet Pro 8710 printer according to [http://hplipopensource.com/hplip-web/models/officejet/hp_officejet_pro_8710.html](http://hplipopensource.com/hplip-web/models/officejet/hp_officejet_pro_8710.html) but Ubuntu-16.04 has only 3.16.3 as its default version, and Ubuntu-16.10 has 3.16.7, so depending on your Ubuntu version you may not have the required version of hplip installed.  

However it is easy to get the newest version of hplip by using the download and install links on their site.
Download the **hplip-3.16.11.run** file from [http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html) 
Install instructions at [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

It may look complicated but it's not as the system does everything for you if you just follow those instructions to the letter.

---

