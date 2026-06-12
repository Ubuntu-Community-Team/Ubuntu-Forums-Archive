---
title: "hard disk temperature problem"
date: 2010-02-12
forum: Hardware
---

### Post by bhuvi on 2010-02-12
i have a lenovo g550 laptop with a 320gb western digital hard drive ,i dual boot between ubuntu 9.10 and vista.in vista hard drive seems to stays cooler even if there is a lot of disk usage but in ubuntu hard disk gets hotter even if its idle. average temperature of my hard disk in vista stays around 44 deg C , but it ubuntu it averages around 51 deg C.is there any way i could keep my drive cooler in ubuntu.

---

### Post by dabl on 2010-02-12
How about your case fan(s)?  I doubt the hard drive itself is generating any different amount of heat, but fan control seems to be an issue where Windows and Linux have different capabilities and different results. Maybe you can lower the threshold and/or enable the case fans to come on sooner.

---

### Post by bhuvi on 2010-02-13
no,i read my hard disk's temperature from the smartctl utility and as it is a laptop i can feel the difference in temperature and it is really hotter in ubuntu ,it seems about 7 deg C.

---

### Post by bhuvi on 2010-03-10
i have reported a bug on this [https://bugs.launchpad.net/ubuntu/+bug/521295](https://bugs.launchpad.net/ubuntu/+bug/521295) 


from what i have looked so far i can come to the conclusion that only western digital hard drives are affected by the load cycle count and temperature problem.

---

### Post by tgalati4 on 2010-03-10
apt-cache search tpfan

---

