---
title: "Magtech card reader"
date: 2014-10-02
forum: Hardware
---

### Post by Albert_Boucher on 2014-10-02
I am using a proprietary Eterm terminal software for our Eclipse ERP system and we process  
 credit card payments through Eterm. Well all worked well while I was using Ubuntu 13.04  
 and now that I have upgraded to 14.04 when I swipe a credit card Eterm locks up solid and  
 I have to close out the program and restart it. Does any body have any ideas.

---

### Post by tgalati4 on 2014-10-03
Run the eterm software in a Terminal and see what errors pop up.

Check /var/log/syslog for errors.  Is the card reader a USB device?  Perhaps there is a bug with 14.04 with certain USB devices.

---

