---
title: "Identifying the graphics card"
date: 2015-11-15
forum: Hardware
---

### Post by UncleMonty on 2015-11-15
I am running a machine with ubuntu 14.04. How do I go about identifying the graphics card? Do I need to look through the laptop manual or can I access this info via terminal or anything like that?

---

### Post by Vladlenin5000 on 2015-11-15
System Settings > Details

Otherwise, doing *lspci* should be enough to get that information.

---

### Post by sammiev on 2015-11-15
Hi UncleMonty,

[This]("https://askubuntu.com/questions/31618/how-can-i-find-my-hardware-details") should help you. :)

---

### Post by Bucky Ball on 2015-11-15
```
sudo lshw -C video
```

... will also work. That will also give you the driver you are currently using (nouveau?). 

If you have a workable desktop and no screen/graphics problems with the open-source driver, then maybe you don't need the proprietary driver. Presuming you are online, have you done an update and looked in 'Additional Drivers'? That might be all you need to do ...

---

