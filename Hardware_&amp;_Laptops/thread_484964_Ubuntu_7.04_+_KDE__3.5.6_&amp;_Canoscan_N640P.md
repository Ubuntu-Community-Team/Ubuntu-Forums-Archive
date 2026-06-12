---
title: "Ubuntu 7.04 + KDE  3.5.6 &amp; Canoscan N640P"
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by Dave Coulstock on 2007-06-26
I have recently converted from SuSE 10.2 to Ubuntu and can only run XSane/Sane with the above scanner in root mode (not recommended).  When I run in normal user mode I get the message "no devices available".  The problem is to do with the permissions of the /dev/parport0 device file.  This is created at boot time with ownership root/lp and owner+group can read/write but others only read.  The scanner works in normal user mode if I change the ownership of parport0 to root/users or its permissions to others can read/write.  I have put a CHOWNcommand [chown root:users /dev/parport0] in the rc.local shell script which seems to work some time after boot up but not immediately.  
Can anyone explain this please?  Is this the correct place to action things at boot time?  I had a similar problem with SuSE 10.2 and overcame it by similar means.

---

