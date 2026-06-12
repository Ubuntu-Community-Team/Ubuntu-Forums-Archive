---
title: "I want to blacklist my Bluetooth Module"
date: 2008-11-13
forum: Hardware
---

### Post by Rovdjur on 2008-11-13
Well, I have a Lenovo X300 and the bluetooth is always on and I want to prevent it from ever turning on in Ubuntu ever again. I don't use it and have no need for it. I have already done the menu>admin>services and uncheck bluetooth, but the little hardware light still comes on meaning that the module is, in fact, still on. The OS just won't start the services. How can I prevent it from turning on at all?

Please help.

Thanks!

---

### Post by Rovdjur on 2008-11-13
Bump?

---

### Post by cariboo on 2008-11-13
All you have to do is add the **bluetooth** module to /etc/modprobe.d/blacklist. To do that press Alt-F2 and type:

```
gksu gedit /etc/modprobe.d/blacklist
```

Create a comment about why you are blacklisting the the dirver, preface the comment with a #. Then add bluetooth to the list. Save the file and reboot.

Jim

---

### Post by Rovdjur on 2008-11-13
Well, I am rather new at linux, so how do I figure out the exact name of my bluetooth module (exactly what to type in the blacklist)?

Thanks :)

---

### Post by Rovdjur on 2008-11-13
Bump?

---

### Post by Rovdjur on 2008-11-14
?

---

