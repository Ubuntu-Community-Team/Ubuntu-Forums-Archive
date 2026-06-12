---
title: "Thinkpad R40: KPowersave &amp; edgy"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by xKevin on 2006-10-27
After upgrading to edgy, KPowersave won't manage the CPU speed. It worked fine before the upgrade so I'm guessing either something is different or I need to modify a setting. 

Any ideas? Need more info?6.10

---

### Post by Mac-Patxaran on 2006-10-27
Hello,

Same problem with my Acer Aspire 3003 WLMI. Help !

---

### Post by zba78 on 2006-10-28
Same problem on my Acer 1962. One workaround was to install **powernowd**. This does make the CPU frequency scaling work but it removes both powersaved and kpowersave packages.

---

### Post by Mac-Patxaran on 2006-10-29
Yep, I am currently running powernowd and, I think, kde-guidance-powermanager. This is what is provided with Edgy, but KPowersave (that worked on Dapper) is far more complete !

---

### Post by xKevin on 2006-10-30
Yup, I settled on that about 1 hour after my original post. Watching the battery of my laptop drain by the second was the deciding factor... ;)

---

### Post by piquadrat on 2006-10-30
BTW, typing "sudo /etc/init.d/powersaved restart" into a console gives back the frequency managment to kpowersave/powersaved on my laptop.

---

