---
title: "Acer TravelMate C110 - Bluetooth, working but"
date: 2009-02-18
forum: Hardware
---

### Post by appzattak on 2009-02-18
anyone know how to add this to start up so I don't have to run it each time I reboot my laptop to get bluetooth working???



sudo modprobe acerhk
echo "1" > /proc/driver/acerhk/blueled

---

### Post by appzattak on 2009-02-18
anyone?

---

### Post by appzattak on 2009-02-19
this site is so worthless when it comes to folks helping others.....

---

### Post by appzattak on 2009-02-20
????

---

### Post by appzattak on 2009-02-20
?

---

### Post by sharathpaps on 2009-02-20
@appzattak,
             a VERY probable reason why you are not getting an answer here is probably because of your third post in this thread. People who help others here do it without expecting anything in return. It takes some selflessness to help somebody just because you can. Hope you understand that.

Anyway, coming to your problem. I'm no expert user myself, but I know that its possible to add a program to the list of Start Up items from System>Preferences>Sessions>Startup Programs in Ubuntu 8.10 running gnome. Try adding your command there.

---

### Post by IQRules on 2009-02-20
Check this,

[http://ubuntuforums.org/showthread.php?t=1031730](http://ubuntuforums.org/showthread.php?t=1031730)

---

