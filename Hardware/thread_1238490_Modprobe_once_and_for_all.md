---
title: "Modprobe once and for all"
date: 2009-08-12
forum: Hardware
---

### Post by motapa on 2009-08-12
I have an evdo card. Every time I want to connect to the Internet, I have to modeprobe the device. How can I modeprobe once and for all, so that I can use it straight away?:confused:

---

### Post by motapa on 2009-08-13
People! Any help here. You are reading my post but not responding. Have I posted a thread in the wrong category. Why aren't you helping?

---

### Post by egglestn on 2009-08-13
I think the following will work

BACKUP ANY FILES YOU CHANGE BEFORE YOU ALTER THEM
so
sudo cp  /etc/modules.conf /etc/modules.old

sudo gedit /etc/modules.conf

at the end add the line
modprode /path to my module/mymodule

save 
exit
restart

HTH

---

