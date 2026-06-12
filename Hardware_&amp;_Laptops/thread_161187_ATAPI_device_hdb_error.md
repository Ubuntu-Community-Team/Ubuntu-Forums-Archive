---
title: "ATAPI device hdb error"
date: 2006-04-16
forum: Hardware &amp; Laptops
---

### Post by crucian on 2006-04-16
Hello,

While troubleshooting a Samba printing problem I came upon these error messages in /var/log/messages. They are written to the log every two seconds and are making it impossible to troubleshoot my other problem. Can anyone lead me in the right direction to resolve this problem?

Apr 16 11:12:14 chy kernel: ATAPI device hdb:
Apr 16 11:12:14 chy kernel:   Error: (reserved) -- (Sense key=0x0a)
Apr 16 11:12:14 chy kernel:   (reserved error code) -- (asc=0x7a, ascq=0xff)
Apr 16 11:12:14 chy kernel:   The failed "Read Cd/Dvd Capacity" packet command was: 
Apr 16 11:12:14 chy kernel:   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "

Thanks in advance,

crucian

---

