---
title: "Barricade 7004 print server problem??"
date: 2005-09-26
forum: Hardware &amp; Laptops
---

### Post by Pirámide on 2005-09-26
Dear friends:

I need information about how to configure Ubuntu in order to use the print server incorporated in the SMC Barricade 7004 router. This router is working with static IPs.

I tried some configurations using ipp/lpd (as said in Fedora, Suse and Mandrake forums), but I can't get it work.

Thanks for your help,

Pirámide

---

### Post by gimili on 2007-12-03
This works for me 

lpd://192.168.0.13/lpt1

and my smc 7004 with an hp1100 hooked up.

Change ip address to the ip of your smc of course.

I had trouble until I found out I needed the lpt1 at the end.

---

