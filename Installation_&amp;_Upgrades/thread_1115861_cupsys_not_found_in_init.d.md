---
title: "cupsys not found in init.d"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by dagarshali on 2009-04-04
Hi
I have ubuntu intrepid 8.10. i was trying to install a printer and was following some instructions given on a website to install canon pixma ip1700. 

one of the commands was sudo /etc/init.d/cupsys restart

but i got an error saying command not found. 

When i went /etc/init.d, all i could find was cups and not cupsys.

I then went to synaptic package manager to check if it has been installed to begin with and i could see that cupsys has been installed. 

What do I do?

Regards,
Vishwa

---

### Post by BigTA78 on 2009-04-06
Try **sudo /etc/init.d/cups restart**

---

