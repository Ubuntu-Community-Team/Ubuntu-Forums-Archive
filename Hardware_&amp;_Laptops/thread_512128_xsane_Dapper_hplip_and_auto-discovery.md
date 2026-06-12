---
title: "xsane Dapper hplip and auto-discovery"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by igoddard on 2007-07-28
If I invoke xsane from the command line and pass it a URI for the scanner on a laserjet 3020 on a hetdirect it will find the scanner & work.  If I just run xsane or gimp or any app that uses xsane it can't find the scanner.

HP toolbox also comes up with a message saying it can't find anything connected, to install in CUPS (done & working) and enable queue for auto-discovery.

Enable for auto-discovery?  Where?  I've crawled over every likely-looking app & not found such a facility.

I've come across a blog saying that Ubuntu broke it in the name of security and giving instructions to link in the snmp back end.  Done that, cups web interface now autodiscovers printer.  Nothing else does.

So what else do I have to fix before this kit works like it did under Fed7 before F7 shipped an update that irretrievably broke the wireless (another story)?

Ian

The solution is here: [https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)

It involves hacking a cups config file by hand.  This really should not be required - the GUI config should be sufficient.

---

