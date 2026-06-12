---
title: "How to install DELL Wireless 1397 WLAN Mini Card"
date: 2011-02-14
forum: Hardware
---

### Post by JSNL on 2011-02-14
Hi I'm a new user in Ubuntu.
I need help installing my DELL Wireless 1397 WLAN Mini Card

---

### Post by mikewhatever on 2011-02-14
Hook up an ethernet cable, then check out System->Admin->Aditional-Drivers.

---

### Post by TBABill on 2011-02-14
I believe that card is a BCM4312 Broadcom card. If so, follow the steps already mentioned (make sure you have wired access for it to work). It uses the STA driver (also called the "wl", which is WL in lowercase) normally for best performance, but if necessary it can use the b43. However, b43 performance sometimes doesn't work at all and others have complained of it being slow and disconnecting often. I have a BCM4312 and with the b43 I could not get over about 4.2Mbps but with the STA got to my max of 6.82Mbps (the speed of my service).
 
Your mileage may vary, but I recommend the STA driver first if it offers both.

---

### Post by JSNL on 2011-02-14
Problem solved! Thanks for your help Mikewhatever and TBABill

---

### Post by mehradmbs on 2011-03-12
Hi dears,
im new user and begginer in ubuntu,
i want to install my wireless driver in ubuntu, i download it in *.tar.gz
please help me to install it, because my wlan doesn't work at all.
thanks a lot

---

### Post by mehradmbs on 2011-03-13
this forum is down!?

---

### Post by colin.p on 2011-03-13
the answer is three and four posts above yours. If you have the same broadcom card, then follow the directions. It should work, notice "should", as with the multitude of different computer configurations, you never know.

---

### Post by JSNL on 2011-03-13
> **mehradmbs said:**
> this forum is down!?

Use Mikewhatever instructions, it worked for my WLAN Card

---

### Post by nextlife7 on 2013-02-20
I reviewed this thread I tried the steps above and I am using 12.10 but I was unable to locate the drivers using the steps given. I am a newb so it could be totally me not doing something right. However I wanted to add these steps  if the steps already given didn't work you could also use the steps in the link below which was what I did. Once I ran the script it told me the version to use which I ran and it worked. 

[http://www.howopensource.com/2012/10/install-broadcom-b43-legacy-wireless-driver-in-ubuntu-12-10-12-04/](http://www.howopensource.com/2012/10/install-broadcom-b43-legacy-wireless-driver-in-ubuntu-12-10-12-04/)

---

