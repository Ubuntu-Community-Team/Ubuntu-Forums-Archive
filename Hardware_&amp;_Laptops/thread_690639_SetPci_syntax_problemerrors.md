---
title: "SetPci syntax problem/errors"
date: 2008-02-07
forum: Hardware &amp; Laptops
---

### Post by atlas95 on 2008-02-07
Hello,
I have find a workaround to get working my mmc reader on the m1330, a ricoh reader.
this fix is for a slackware normally, it seems to be a syntax error but I don't find.
If someone could help me I will be happy.

    * /sbin/setpci -s &#8216;03:01.0&#8242; 0xCA=0×57 (Write Enable)
    * /sbin/setpci -s &#8216;03:01.0&#8242; 0xCB=0×02 (MMC Disable)
    * /sbin/setpci -s &#8216;03:01.0&#8242; 0xCA=0×00 (Write Disable)

from [http://intr.overt.org/blog/?page_id=56](http://intr.overt.org/blog/?page_id=56)

the correct bus id is 3:01.1, but I have those error for the first command for example: 
 sudo setpci -s '03:01.1' 0xCA=0×57
setpci: Invalid value "0×57"

best regards

---

