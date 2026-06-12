---
title: "ThinkPad running HOT"
date: 2008-06-27
forum: Hardware
---

### Post by 50words on 2008-06-27
ThinkPad T43:

```
cat /proc/acpi/ibm/thermal
temperatures:	91 57 40 67 41 -128 31 -128 61 55 59 -128 -128 -128 -128 -128
```

How can I figure out whether this is a hardware problem or a software problem?

---

### Post by damphoud on 2008-06-27
Does your thinkpad bios support thermal readings? You might be interested in:

[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

---

### Post by 50words on 2008-06-27
Didn't I already give the thermal readings? I already know it is running hot.

---

### Post by damphoud on 2008-06-27
Oh jeez, sorry, I thought you where trying to figure out if the readings where incorrect. You can go into power management (system -> preferences), and there is a setting where your cpu frequency will be set on load, instead of always max.  I'm on my desktop, and my laptop is not here, so I don't know the exact setting. If ubuntu is properly managing your cpu, then check hardware. You can take off the back panel of your thinkpad and see if your fan is dirty/dusty. Maybe there is something obstructing your fan outflow?

---

### Post by 50words on 2008-06-28
The fans is pretty clean, actually. I blew it out recently. I don't see anything related to CPU frequency or the fan in power management, though.

---

