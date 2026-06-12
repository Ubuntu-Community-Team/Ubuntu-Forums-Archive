---
title: "AMD radeon Graphic Driver"
date: 2012-12-05
forum: Hardware
---

### Post by Elshentenawy on 2012-12-05
hey every one 
I am trying to install my AMD graphic driver 
I downloaded the proper driver from hp official site it's jar file so I found in it a "LIB" folder
I tried to copy "lib" folder to the file system lib folder but I cannt keep saying you dont have permissions so what I have to do to install it right 
hope can any body help 
thanks

---

### Post by Yellow Pasque on 2012-12-05
The AMD driver should not be in a jar file. Please tell us what graphics card you have and what driver you're trying to install (link to it).
The following command will tell you wha GPU you have:
```
lspci | grep -i vga
```

---

