---
title: "Modem Issue-Ubuntu 6.06 on HP Pavillion ze5300 series"
date: 2006-07-10
forum: Hardware &amp; Laptops
---

### Post by pcflight on 2006-07-10
Hello,
I am trying to get my software modem working under Ubuntu 6.06.  The laptop is an HP Pavillion ze5300. I am using a Conexant Modem (Coming up as a ALi M5457 in Ubuntu, Conexant ACLink Modem in Windows). 
I have read the ModemHowto wiki and I narrowed it down to the fact that I need to use the smartlink drive. Part of my problem was getting slamr to load.  I was able to solve this by using ungrab-winmodem.  wvdialconf was able to detect the modem, but froze the system when it tried to dial.  The opensource driver by Alexandre Otto Strube will install, just not create the syslinks or the files in /dev.  I have a feeling the know bug for 6.06 may be the problem with the freeze, but the instructions are a little backwards (i.e you install the sl-modem-daemon in step 4, then a different version (older) in step  12).  
I am at a lose, I really want to get Ubuntu to work on this thing.](*,)

---

### Post by pcflight on 2006-07-11
I got the modem to work using the linuxant drive from [http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/)  Currently I am using the free one for 14.4k.  I may pay up the $20 for full 56k.  After about 8 hours of pain trying to get slmodemd working, this is well worth it.

---

