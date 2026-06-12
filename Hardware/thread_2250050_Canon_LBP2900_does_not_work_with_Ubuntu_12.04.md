---
title: "Canon LBP2900 does not work with Ubuntu 12.04"
date: 2014-10-26
forum: Hardware
---

### Post by cyb3r_sn4k3 on 2014-10-26
I've installed the CAPT drivers (V2.60) and have followed the instructions given [here]("https://help.ubuntu.com/community/CanonCaptDrv190") but still no luck. The CUPS jobs page just stays at ```
Sending data to printer.
```. Please help.

---

### Post by pdc on 2014-10-28
please tell us if you have 32bit; or 64bit

post #2 here [http://ubuntuforums.org/showthread.php?t=2076037&highlight=canon](http://ubuntuforums.org/showthread.php?t=2076037&highlight=canon) gives a how-to;

for a standard printer, one registers the printer (PPD) with the print spooler as the sole step after driver install; with the CAPT driver, one also registers the printer in the ccpd daemon setup file

__________________________

in the readme that Canon supplies with the 2.6 CAPT driver, they ask one to check that

> [COLOR="#0000FF"]libglade2[/COLOR] is installed; 

for 64bit they say > [COLOR="#0000FF"]ia32-libs libpopt0:i386[/COLOR] are needed

_______________________________

I confess that with a little familiarity of the CAPT install, that I don't find the instructions of [https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190) are the easiest to follow ...............

---

### Post by cyb3r_sn4k3 on 2014-10-29
I have a 32 bit and I tried following the instructions but here is no status message in the window :(

---

### Post by pdc on 2014-10-29
and you have[COLOR="#0000FF"] libglade2[/COLOR] installed? it is recommended also for the 32bit install; 

like you, we have a 12.04 32bit ubuntu and it does work with the LBP. 

____________________________________________________________

can you please paste what > [COLOR="#FF0000"]/usr/sbin/lpinfo -v[/COLOR] gives ..............it lists the printer listings on your computer ..........

If you used the UK/Europe version of CAPT 2.6, you would have referenced the ppd file > CNCUPSLBP2900CAPTK.ppd ?

_______________________

also what does > [COLOR="#FF0000"]dpkg -l | grep Canon[/COLOR] give please..........that asks for which CAPT drivers are installed .................

_______________________________________

in your last post; when you said >  I tried following the instructions ...............which instructions were they please?

---

