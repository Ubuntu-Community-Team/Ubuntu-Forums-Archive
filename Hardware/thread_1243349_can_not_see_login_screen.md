---
title: "can not see login screen"
date: 2009-08-18
forum: Hardware
---

### Post by vnrbhargav on 2009-08-18
hi

I'm using 9.04. Till yesterday all was fine now suddenly i could not see my login screen after the ubuntu loading screen. Only a blank screen is displayed. I dont know what i did ! I suspect this happend after marked something in Add/Remove programs for installation. Definitely this is not by compiz (b'se i removed compiz through rescue mode), Eventhough same screen flashes !

can any one plz help me!

Laptop model: HP DV5t

---

### Post by riazrahaman on 2009-08-18
press ctrl+alt+f1

login and give the command 

dmesg

If there is any problem you should see it there and also open the file /var/log/Xorg log files and check for any issues with x configuration.

---

### Post by vnrbhargav on 2009-08-18
i think the last program i installed is ATI Catalyst control centre !

plz tell me a command to uninstall it from root shell (through the recovery option)

THanx

---

### Post by vnrbhargav on 2009-08-18
I got the command here :

[http://ubuntuforums.org/showthread.php?t=1212683](http://ubuntuforums.org/showthread.php?t=1212683)

---

### Post by vnrbhargav on 2009-08-18
Everything fine now! :popcorn:

---

