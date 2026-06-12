---
title: "Running HP Printer on Ubuntu 12.04"
date: 2013-09-07
forum: Hardware
---

### Post by dudethatserin on 2013-09-07
Hello,

I currently have a basic HP printer that I wanted to make sure would run just fine when I go about installing Ubuntu 12.04.

I have the installation disc and everything. Are there any printers you guys know about that aren't good with linux?

Please help! & Thanks!

---

### Post by scbingham on 2013-09-07
Do some research. Try looking at this for starters:

[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

---

### Post by dudethatserin on 2013-09-07
Thanks!

---

### Post by ajgreeny on 2013-09-07
And here is the hplip site to look for the HP printer by model name and number.
[http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)

---

### Post by buzzingrobot on 2013-09-07
Here's how I install my HP printer, a p1102w.  It needs an HP driver that is not installed or available from Ubuntu. (Ubuntu's printer setup will often seem to set up the printer.  But, without the driver, it won't work.)

Install "hplip" and "hplip toolbox". (E.g., search for them in Software Center.)  

Click on the icon for "hplip toolbox" to run it. You'll see several installation options.  Select one depending on how your printer is connected.

The driver needs to be installed with root provileges, so you will be asked for your password.  You will be asked to accept a Terms&Condition agreement.  When the download completes, click through to setup and test your printer.

This is thesame driver that's available for your printer from hpopensource.com.

I always open "Printers" in settings to double check that the printer is there, and to set it as the default.

---

### Post by dudethatserin on 2013-09-07
Thanks!

---

