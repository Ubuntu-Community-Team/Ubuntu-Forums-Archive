---
title: "Lexmark E240 printer problem"
date: 2007-01-14
forum: Hardware &amp; Laptops
---

### Post by neur0n on 2007-01-14
I recently tried to install a Lexmark E240 printer on my Ubuntu system. After downloading and installing the drivers everything seemed to work fine, but if I print a file I get nothing but alot of random characters (but the hardware's print test works fine). Also, even though I choose to print one paper only, I get many. 

Any suggestions?


/neur0n

---

### Post by EiriktheRed on 2007-02-03
I had the same problem - to me it looks like the driver produces failed Postscript output. I struggled with this for quite some time, and solved it by choosing a HP driver - specifically the *LaserJet Series PCL 6 CUPS*. It's included in the standard Dapper/Edgy install, just change it from System/Administration/Printing/Your Printer/Properties. Haven't tested it fully yet, but it seems fairly OK.

---

