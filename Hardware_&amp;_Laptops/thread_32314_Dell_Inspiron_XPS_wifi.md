---
title: "Dell Inspiron XPS wifi"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by Mathew on 2005-05-07
I believe I posted this in another support thread already, if I did
I apologize for the duplicate post. (Really life is just crazy some
times... :) 

Here is what I am facing.  I have a dell inspiron xps with the integrated
broadcom 570x series nic.  I also have the dell 1450 mini-pc nic installed 
as well (I believe it is a 4390 broadcom chipset 802.11 a/b/g).

Device manager makes notice of both cards.  The integrated card is
working fine.  When I go into terminal and do a lspci I get the following 
output:

0000:02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 0 3)

so it is being listed.  I was told I could use ndiswrapper to convert my .inf files from the driver cd to correct this issue.  This is where I could use some help please.

Thanks

---

### Post by leviathon on 2005-05-07
Look at this thread...
[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=ndiswrapper](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=ndiswrapper)

---

