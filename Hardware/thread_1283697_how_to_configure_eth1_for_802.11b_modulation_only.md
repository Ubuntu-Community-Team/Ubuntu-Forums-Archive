---
title: "how to configure eth1 for 802.11b modulation only"
date: 2009-10-05
forum: Hardware
---

### Post by vitreousity on 2009-10-05
Hi,  I have an Intel PRO/Wireless 2200BG card which ubuntu fully supports.  The problem is it doenst play nice with my older Netgear router when attempting to run at 802.11g.  It also has this problem in windows, but works fine when you configure it for B only. 

I believe what I need to do is this command:    

sudo iwconfig eth1 modu 11b  

but what that yields is: 

Error for wireless request "Set Modulation (8B2F) :    SET failed on device eth1 ; Operation not supported  

Does anyone know if this card can be configured to run as 802.11b only? 

Thanks,  Vit

---

### Post by vitreousity on 2009-10-06
bump

---

