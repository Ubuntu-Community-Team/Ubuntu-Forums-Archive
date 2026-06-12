---
title: "Detect Hardware After Install"
date: 2011-07-25
forum: Hardware
---

### Post by repease on 2011-07-25
Does anyone know of a way to detect new hardware after the system has been fully installed and is running?  I really don't want to have to re-install just for a new USB wireless network adapter to work.

Any suggestions??

---

### Post by jramshu on 2011-07-26
You could plug it in, open terminal, and type this to see if it's being recognized.
```
lsusb
```
If it is and doesn't work, go from there to get the appropriate drivers. Sometimes it's better to plug it in and then turn on the machine to see if it "just works." If it doesn't, I'm sure it can be solved on here.

---

