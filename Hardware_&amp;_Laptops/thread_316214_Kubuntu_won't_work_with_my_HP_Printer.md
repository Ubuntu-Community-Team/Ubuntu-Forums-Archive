---
title: "Kubuntu won't work with my HP Printer"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by steven8 on 2006-12-10
I wanted to give Kubuntu a whirl, because I've liked KDE in other distros.  I tried the Dapper version, because I've always had good luck with it.  But it fails to work with my HP printer.  In Ubuntu, with Gnome, it worked just fine, liveCD or install.  I was using the liveCD with Kubuntu.  Could that be the issue?  Has anyone else had this sort of problem with Kubuntu?

Sorry. . .I need to note that it recognizes my printer with no problem, but it gives a printer error, or failed to create error when trying to use it.

---

### Post by Jose Catre-Vandis on 2006-12-10
So exactly what printer?
What are the error messages?
What app are you trying to print from?
You says Kubuntu recognises printer, where and how? (e.g. from command line or GUI?)
Can you set it up as a printer in the GUI for printing? And are these settings the same as you got in Gnome
What options do you get when you try to print, is your printer the default printer?

---

### Post by steven8 on 2006-12-10
I have not been able to successfully add it as a printer yet.

When I go into the print manager and try to Add Printer, it finds it.  It's an HP PSC 1210.  The error is:

Unable to Locate the requested driver:

Unable to create the Foomatic driver [HP-PSC_1210,hpijs].  Either that driver does not exist, or you don't have the required permissions to perform that operation.

I clicked the Administrator Mode button, but it didn't make a difference.

---

### Post by Jose Catre-Vandis on 2006-12-10
This page might help?

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PSC_1210](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PSC_1210)

see if you can choose a generic multifunction HP printer driver?

is CUPS installed OK, and Foomatic (?) or try HPLIP ?

---

### Post by mk2supra on 2006-12-11
I support the HP AiO printers and there is a site made by HP for linux print drivers.

[http://hplip.sourceforge.net/supported_devices/inkjet_aio.html]("http://hplip.sourceforge.net/supported_devices/inkjet_aio.html")

That page there should get you somewhere. Shows the supported AiO list for "HPLIP".

We get the odd call from time to time but I wouldn't try because you'll probably get an Indian SP (no offense - language barrier sucks) and they'll want to charge you for support because you more than likely have an OOW product.

Here is the actual download page:
[http://hplip.sourceforge.net/downloads.html]("http://hplip.sourceforge.net/downloads.html")

Good Luck. I only wish I could dig up the Lexmark version of this site but I'd probably just rather get rid of the Lexmark I have because I hate it.

---

### Post by steven8 on 2006-12-11
My bad.  It wouldn't do it with the liveCD.  I installed it and it set up and printed just fine.  Sorry about that.  Thank you for all your help!!

---

### Post by Jose Catre-Vandis on 2006-12-11
> **steven8 said:**
> My bad.  It wouldn't do it with the liveCD.  I installed it and it set up and printed just fine.  Sorry about that.  Thank you for all your help!!

:) :) :)

---

