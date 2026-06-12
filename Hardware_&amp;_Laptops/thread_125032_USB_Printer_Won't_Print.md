---
title: "USB Printer Won't Print"
date: 2006-02-02
forum: Hardware &amp; Laptops
---

### Post by maxomai on 2006-02-02
Hey all. I've pretty much exhausted my resources and/or patience on this, and so I turn to you.

I have an HP DeskJet 845C that I'm trying to get to print from Kubuntu. I've followed [this procedure]("http://ubuntuforums.org/archive/index.php/t-75682.html") and it seemed to work swimmingly. However, it won't print a test page. Figuring that this might be a bug in the test page procedure, I completed the install procedure and tried printing a text document I'd written in Kate. The print job queued up instead of printing. On checking the IPP report I got this feedback:

> 
printer-state 0x5
printer-state-reasons paused
printer-state-message Unable to open USB device "usb://HP/DeskJet%20845C?serial=TH1771C64YSX": No such device

printer-is-accepting-jobs True
...
queued-job-count 1
printer-uri-supported ipp://cups-server:631/printers/hp845c
...
printer-name hp845c
...
printer-more-info ipp://cups-server:631/printers/hp845c
job-quota-period 0
job-k-limit 0
job-page-limit 0
job-sheets-default none none
device-uri usb://HP/DeskJet%20845C?serial=TH1771C64YSX
color-supported True
pages-per-minute 1
printer-make-and-model HP DeskJet 845C Foomatic/hpijs (recommended)


I tried shutting off the printer, deleting the printer from the system, powering down, turning on the printer, powering up and re-installing. This didn't fix the problem. Neither did a simple reboot.

So then -- what should I do, gang?

---

### Post by Jeffery Mewtamer on 2006-02-03
[http://hpinkjet.sourceforge.net/install.php#HPLIP](http://hpinkjet.sourceforge.net/install.php#HPLIP)

There's a good walkthough for installing HP printers. Its what I used to install mine and it worked like a charm. And while HP doesn't offically support HPLIP, I did find this though HP's website.

I hope this helps.

---

### Post by maxomai on 2006-02-07
So having tried the HOWTO provided by HP (linked kindly by Mr. Mewtamer), switched the printer around several USB ports, etc., I still get the same condition. It seems that nothing I do makes the printer connect to the USB port.

Again, it works perfectly well in Windows XP, so I suspect it's not a hardware or printer problem.

Could this be a problem with my USB drivers?

---

### Post by maxomai on 2006-02-10
Try this thread:

[http://ubuntuforums.org/showthread.php?t=126135](http://ubuntuforums.org/showthread.php?t=126135)

Anything more that I post on the problem will be in the above thread.

---

