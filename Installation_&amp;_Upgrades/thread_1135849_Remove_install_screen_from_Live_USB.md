---
title: "Remove install screen from Live USB"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by max.goedjen on 2009-04-24
Hey guys,
I'm setting up my flash drive as a mobile workstation of sorts, and was wondering if there's any way to disable the initial screen that Ubuntu launches into when booting from the flash drive (select language, boot, install, etc)?

---

### Post by krul on 2009-07-25
Did you figure this out? I also like to know this....

---

### Post by Baffetto on 2010-11-19
Try removing Ubiquity which is the installation program. 
I tried on my Ubuntu 10.10 liveUSB and it worked.

```
sudo apt-get remove ubiquity
```

---

### Post by SteveM10 on 2012-01-17
> **Baffetto said:**
> Try removing Ubiquity which is the installation program. 
I tried on my Ubuntu 10.10 liveUSB and it worked.

```
sudo apt-get remove ubiquity
```


This worked for me with 10.04.3 as well. Thank you for the information.

---

### Post by jasonbd on 2012-07-18
Tried on 12.04 LTS. The remove process end up with some error and stop but manage to remove install page.

---

