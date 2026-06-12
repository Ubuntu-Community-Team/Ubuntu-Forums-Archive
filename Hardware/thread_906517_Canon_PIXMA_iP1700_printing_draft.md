---
title: "Canon PIXMA iP1700 printing draft"
date: 2008-08-31
forum: Hardware
---

### Post by fauzie on 2008-08-31
Hi, I finally get my printer, Canon PIXMA iP1700 to work. I used the driver from their website (rpm, converted by alien to deb). However I cannot find a way to print in draft mode. Is this even possible in linux? Any experience? I can't afford to print with best quality every single time.

---

### Post by fauzie on 2008-08-31
Nevermind, I found a solution here

[http://iwansetiawan.wordpress.com/2007/07/19/install-printer-canon-pixma-di-linux/](http://iwansetiawan.wordpress.com/2007/07/19/install-printer-canon-pixma-di-linux/)

edit this file : /usr/share/cups/model/canonip2200.ppd

Change this
*MaxMediaWidth: “612&#8243;
*MaxMediaHeight: “1656&#8243;
into
*MaxMediaWidth: “215&#8243;
*MaxMediaHeight: “584&#8243;

Also edit this
*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: “<</HWResolution[600 600]>>setpagedevice”
*CloseUI: *Resolution

into this
*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: “<</HWResolution[600 600]>>setpagedevice”
*Resolution 1200/1200 dpi: “<</HWResolution[1200 1200]>>setpagedevice”
*Resolution 2400/2400 dpi: “<</HWResolution[2400 2400]>>setpagedevice”
*CloseUI: *Resolution

And add the following lines
*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: “2&#8243;
*CNQuality 3/Normal: “3&#8243;
*CNQuality 4/Standard: “4&#8243;
*CNQuality 5/Economy: “5&#8243;
*CloseUI: *CNQuality

Save and restart CUPS
/etc/init.d/cupsys restart

reinstall the printer.

---

### Post by jtmedin on 2008-10-23
Ok i have an ip1700 also but am unable to figure out how you got the file '/usr/share/cups/model/canonip2200.ppd'. TIA

---

### Post by vanzandtj on 2009-01-25
The PPD comes in an RPM package in this tarball:

[http://software.canon-europe.com/files/soft24301/software/iP2200_Linux_260.tar.gz](http://software.canon-europe.com/files/soft24301/software/iP2200_Linux_260.tar.gz)

You can convert the RPMs to DEBs with "alien --to-deb --script *6.rpm"

---

