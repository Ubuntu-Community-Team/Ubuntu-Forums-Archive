---
title: "Buying a new laptop, system requirements to run Ubuntu super fast?"
date: 2015-01-13
forum: Hardware
---

### Post by Riemens on 2015-01-13
Hello everyone,

I know what the system requirements are, but what are the system requirements to run Ubuntu 14.04 really fast? e.g. starting Firefox taking < 0.3s.

Also, my 2 siblings own an Asus laptop (i7, 8GB RAM, 1 TB, Windows 7 / 8.1), what would it take to be faster than them when running on Ubuntu? (<- optional, they don't like Linux, so I would love to learn them a lesson :D )

No I don't want to run Lubuntu or Xubuntu, although I will check them.

Many Thanks!

---

### Post by kpatz on 2015-01-13
A fast SSD and plenty of RAM (8 GB is plenty).  Processor/RAM speed is secondary, and graphics speed is a factor if you're gaming or doing anything heavily graphical (fancy Compiz animations etc.).

---

### Post by leclerc65 on 2015-01-13
Avoid swapping
```

Add these lines into  /etc/sysctl.conf
#
# Sharply reduce swap inclination
vm.swappiness=1
# Improve cache management
vm.vfs_cache_pressure=50

```
Set these parameters in Firefox
```

browser.cache.disk.enable to false 
browser.cache.memory.enable to true 
browser.cache.memory.capacity -1 

```

---

