---
title: "Internal Graphics ATI Xpress200"
date: 2005-05-17
forum: Hardware &amp; Laptops
---

### Post by griffith on 2005-05-17
Is there anyway to get the internal graphics card working on my MSI motherboard? It's a RS480 based on ATI's Xpress 200 chipset. If anyone has a solution to my problem please help.

---

### Post by nandhu on 2005-06-06
[QUOTE=griffith]Is there anyway to get the internal graphics card working on my MSI motherboard? It's a RS480 based on ATI's Xpress 200 chipset. If anyone has a solution to my problem please help.[/QUOTE]
 Hi, 

I've got the same problem. Though I've not tried. I just found out (literaly couple of hours before), that there is an ATI Driver for X200 series.
Go to this link. Who knows it might be of help. If it works for you, please post a line here and so we can also be benefitted. :)

[http://support.ati.com/ics/support/default.asp?deptID=894&ticketID=822344](http://support.ati.com/ics/support/default.asp?deptID=894&ticketID=822344)

Hope this helps. If not let me know, i can email you the driver.

---

### Post by Jiilik on 2005-06-30
In xorg.conf, under the 'ati' driver section, enter in Option "NoAccel" "true" and the ati drivers will work

---

