---
title: "Not always printing, depends on apps"
date: 2004-10-25
forum: Hardware &amp; Laptops
---

### Post by FrançoisObada on 2004-10-25
Hello,

I've succeed to install a remote printer (Canon BJC-2000 over Samba in a local network) in Ubuntu 4.10, but there are some printing issues remaining.

When I start printing a test page from Gnome's utility, or from another Gnome app (Gedit for example), everything works fine, jobs is immediately done.

But when I print a page from OpenOffice, I see my printer (BJC2000), but nothing seems to be sent to the printer, and Gnome Printers Panel doesn't tell me about any current job. Here is a sample of /var/log/cups/error_log :

```
I [25/Oct/2004:15:41:59 +0200] Adding start banner page "none" to job 24.
I [25/Oct/2004:15:41:59 +0200] Adding end banner page "none" to job 24.
I [25/Oct/2004:15:41:59 +0200] Job 24 queued on 'BJC-2000' by 'titoxx69'.
I [25/Oct/2004:15:41:59 +0200] Started filter /usr/lib/cups/filter/pstops (PID 5 619) for job 24.
I [25/Oct/2004:15:41:59 +0200] Started filter /usr/lib/cups/filter/foomatic-rip (PID 5620) for job 24.
I [25/Oct/2004:15:41:59 +0200] Started backend /usr/lib/cups/backend/smb (PID 56 21) for job 24.
E [25/Oct/2004:15:42:01 +0200] PID 5620 stopped with status 1!
I [25/Oct/2004:15:42:01 +0200] Hint: Try setting the LogLevel to "debug" to find  out more.

```

The worst is reached in Firefox/Thunderbird where my printer isn't listed at all ; I can just choose Postscript/default, which isn't the remote printer.

Here is the /etc/cups/printers.conf :

```
# Printer configuration file for CUPS v1.1.21rc1
# Written by cupsd on Mon Oct 25 15:36:28 2004
<DefaultPrinter BJC-2000>
Info BJC-2000
Location Neutron
DeviceURI smb://neutron/CanonBJC2000
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>
```

I don't understand why I encounter three different issues though my remote printer seems to be well installed (according to Gnome).

Thanks

---

### Post by calvinpriest on 2004-10-25
Hopefully someone out there can you give you real advice on this particular printer, but I will share my general opinion with you.

Older, cheap printers like the BJC 2000 (4 years is old for this type of printer) are rarely much fun to use in Linux.  Cheap old printers don't usually inspire volunteer developers to perfect a driver, and many users ultimately switch to higher quality, and/or newer printers, draining further interest in driver perfection.

There is a great site for printer research called linuxprinting.org.  They ranked the BJC2000 as two stars, saying it worked "mostly".  My experience has been that their rankings are fairly kind.  I wouldn't personally use a printer with Linux that they didn't rank at least a three.
[http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-BJC-2000](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-BJC-2000)  

They also have a "Suggested Printers" page which is helpful.  Some of the printers they recommend can be gotten cheaply used (Ebay's a good source).

Now, your current problem may have nothing to do with the quality of the drivers, but in any case, you might want to consider an upgrade.  My HP Laserjet 1100 works great over my network.

Calvin

---

