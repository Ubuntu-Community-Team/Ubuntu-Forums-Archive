---
title: "help! please!"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by BrandonD92 on 2007-11-24
hi, ive been trying to make my Linksys Wireless G notebook adapter v.3 work on my laptop. I have a Presario 2100 with Ubuntu 7,10. On the restriced Driver manager i can get chipset bxm43 working and by using 

   sudo gedit /etc/network/interfaces

and erasing everything except lo.
and then after i reset the system using

   sudo /etc/init.d/dbus restartsudo /etc/init.d/dbus restart

and it finds my wireless connection

**but** whenever i reset my computer and check my network configs my wireless connection disapears and i have to repeat at that over again
does any one know i can stop it from doing that??

pleaasee!

---

### Post by BrandonD92 on 2007-11-24
help! please!
hi, ive been trying to make my Linksys Wireless G notebook adapter v.3 work on my laptop. I have a Presario 2100 with Ubuntu 7,10. On the restriced Driver manager i can get chipset bxm43 working and by using

sudo gedit /etc/network/interfaces

and erasing everything except lo.
and then after i reset the system using

sudo /etc/init.d/dbus restartsudo /etc/init.d/dbus restart

and it finds my wireless connection

but whenever i reset my computer and check my network configs my wireless connection disapears and i have to repeat at that over again
does any one know i can stop it from doing that??

pleaasee!

---

### Post by ksousa on 2007-11-24
I'm still noob ... but i think is something with depmod -a and modprobe ...

---

