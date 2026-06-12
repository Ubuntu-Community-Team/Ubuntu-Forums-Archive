---
title: "Weird Wireless"
date: 2008-12-30
forum: Hardware
---

### Post by Erus on 2008-12-30
Hello! I use Ubuntu all the time on my eee and on my desktop and love it, and its wireless is stable. Today I am setting up an older laptop for my dad to use. Interestingly my laptop can find and pick up wireless networks fairly well. Except mine. From time to time it will see my network, other times not. Even stranger still it refuses to connect to *any* network it sees. The laptop is a Toshiba P-25 S507 Satellite. Any suggestions? 

Thanks!

---

### Post by kev000 on 2008-12-31
I'm also experiencing some strange wireless issues.  I cannot connect to my home access point, but I can connect to my neighbor's.  After a while, all the APs disappear from the list all together except for my neighbor's AP (may be similar if not the same as the original poster).  All of the sudden, it won't even connect to my neighbor's or any wifi AP.

Both networkmanager-applet and iwlist ** scan show only the one access point.  My desktop shows 10.

lspci:
Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b

NOTE: when i reboot the laptop (IBM Thinkpad T40), I can see all the APs in my area.  After a while, they all disappear except for the one I'm connected to.

---

### Post by kev000 on 2009-01-05
Confirmed: Works perfect in hardy,

Intrepid = fail
Jaunty = fail

---

