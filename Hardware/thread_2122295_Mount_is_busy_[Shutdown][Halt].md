---
title: "Mount is busy [Shutdown][Halt]"
date: 2013-03-04
forum: Hardware
---

### Post by aznboi on 2013-03-04
Hi guys, just installed Ubuntu 12.10 64 bit, however when I try to shutdown or reboot the computer I get this screen [attached pic]

any solutions or possible steps toward a solution? thanks!

---

### Post by aznboi on 2013-03-07
> **aznboi said:**
> Hi guys, just installed Ubuntu 12.10 64 bit, however when I try to shutdown or reboot the computer I get this screen [attached pic]

any solutions or possible steps toward a solution? thanks!

still having this issue every shutdown/reboot, any help would be great!

---

### Post by miraculix4094 on 2013-03-23
i had the same problem and found, that the dhclient is holding its lease file open for writing. In my opinion that behaviour is the bug, but couldn't solve it quickly. so i included the command  ```
/bin/fuser -kw /var/lib/dhcp/*
```  in file ```
/etc/init.d/umountroot
```  I'm aware that this is a dirty "solution". so please suggest a better one.

---

