---
title: "battery problem with my laptop"
date: 2013-08-02
forum: Hardware
---

### Post by frank4 on 2013-08-02
hi i am new here and i don't know where to put my question so i pick here, sorry if it is the wrong place . well i have an acer aspire 5551 laptop and i duel boot it with windows 7 and ubuntu. on windows i don't have any problems with the battery or changing but when i am in ubuntu my laptop does not recognize when the changer is plug in. some times it will recognize for a few minutes but then it will stop suddenly. i think it must be ubuntu but i don't know what to do. thanks

---

### Post by GwL3eNC on 2013-08-02
Hi frank4,

dont know if it helps solving your problem. Energieevents are stored in the file

/var/log/syslog

Try 

cat /var/log/syslog | grep ACPI

and view the output. Evtl it's good to post it here.

---

