---
title: "setting up a HP ENVY 5642 all in one printer"
date: 2015-10-08
forum: Hardware
---

### Post by sequimbob on 2015-10-08
I am running a HP G7=2069wm Notebook PC with 6gb ram and Ubuntu 14.04 (64bit).  I am trying to set up a new HP ENVY 5642 all in one printer.  It is printing fine but can't get the scan to work.  It recognizes the printer but when I go to scan with simple scan or Xzane,  I get the error "NO SCANNER DETECTED:". I have searched Linux Forums, no references to HP ENVY 6542,
I went to [https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne) and followed the applicable steps on that page. results below
I tried hp-Setup  result - "error: No devices found on bus: usb"
I ran hp-check -r  result - "error: Unsupported model: ENVY_5640_series" (python-qt4 was installed prior to running hp-check -r)
I went to [http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html).  This says that HPLIP supports this printer and scanner. According to hplip.conf, I have HPLIP version 3.14.3, XSane, SimpleScan, Linux drivers, installed. I have run apt-get update and it tells me everything is good. 
Does anyone have any ideas.  This somewhat computer savvy guy is lost.

---

### Post by Tadaen_Sylvermane on 2015-11-03
You need 3.14.10 to be able to use it. However I will say that I am having no luck with this printer myself on Debian, even with the latest hplip installed. Can only see it from the cups web interface, and that doesn't enable scanning so imo this printer was a waste of money :/

---

