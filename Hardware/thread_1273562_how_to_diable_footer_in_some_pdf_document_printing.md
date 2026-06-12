---
title: "how to diable footer in some pdf document printing"
date: 2009-09-23
forum: Hardware
---

### Post by white_rule on 2009-09-23
Hi

i have HP LaserJet P1006 on my ubuntu box, and install HPLIP 3.9.8, printer driver version is : HP LaserJet P1006 Foomatic/foo2xqx
every thing is Ok, and my printer works properly, but i have a problem when print documents, when i want to print some document in PDF fromat, the footer below pages printed, it has a number like this 
in bottom left corner I have something like this --> 02536book.indd 30
in bottom centre I have a some picture like cible 
in bottom right side of page I have date and time like this --> 1/16/09 9:35:45 A 
in preview of printing i can see these footer, i think it depend on printer or cups settings but i cant find configuration file or another thing in HPLIP application.
how can i disable this footer ?

PS : on HP Device manager -> printer setting -> miscellaneous > set to no banner on pages 
My system info : Ubuntu 9.04 and kernel ver is 2.6.28-15-generic

thanks

---

### Post by white_rule on 2009-10-15
Hi all

I can fix this problem, it's wonderful...
This is the story: 

I setted the printing page setup to A4 the above problem occured, when I accidentally changed it to US letter size the problem solved, and now every thing work OK.

Regards,

---

