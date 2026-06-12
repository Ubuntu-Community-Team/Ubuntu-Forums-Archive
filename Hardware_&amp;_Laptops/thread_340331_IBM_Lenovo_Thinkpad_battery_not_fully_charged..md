---
title: "IBM Lenovo Thinkpad battery not fully charged."
date: 2007-01-17
forum: Hardware &amp; Laptops
---

### Post by Captus on 2007-01-17
For those who has a laptop from Lenovo and has the problem that the battery doesn't get fully charged. 

I added this to my /etc/apt/sources.list:

```

deb http://www.oakcourt.dyndns.org/debian/ ./
deb-src http://www.oakcourt.dyndns.org/debian/ ./

```

Then: 
```
apt-get install tpsmapi-utils
```

Then i opened the file /etc/init.d/tpsmapi-utils
and changed 
```
START_CHARGE_THRESH_BAT0="40"
STOP_CHARGE_THRESH_BAT0="70"
```
to
```
START_CHARGE_THRESH_BAT0="40"
STOP_CHARGE_THRESH_BAT0="100"
```

At first this didn't help me, so i found a new BIOS at the [http://www.ibm.com]("http://www.ibm.com")site. For me that is:
* 15 Jan 2007
79ETC9WW (2.09) (T60 2007-FUG) Link: [http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-63027]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-63027")

I downloaded the "BIOS Bootable CD", and flashed the BIOS from there. 

Now my battery gets fully charged!!!

---

