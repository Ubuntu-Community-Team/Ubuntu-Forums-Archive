---
title: "Get a driver version"
date: 2008-06-12
forum: Hardware
---

### Post by john.ennew on 2008-06-12
How do find out what driver name and version is loaded and being used for any particular piece of hardware? Is there a standard location for this information?

Specifically, I'd like to know what video driver the system is running on. I updated it but have no idea if the new version is running.

System is Ubuntu 8.04 64 bit with an Intel GM965 chipset (X3100 graphics core).

---

### Post by SlappyTheFish on 2008-06-23
Try:

sudo apt-get install sysinfo

---

### Post by john.ennew on 2008-07-02
Nice little app.  Doesn't give driver revisions though :(

---

### Post by starcannon on 2008-07-02
This should do it for you:

```
sudo lshw
```

```
lsmod
```

```
dmesg | grep some-device-here
```

```
modinfo some-module-name-here
```

---

