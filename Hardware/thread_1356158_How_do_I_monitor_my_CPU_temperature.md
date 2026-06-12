---
title: "How do I monitor my CPU temperature?"
date: 2009-12-15
forum: Hardware
---

### Post by DTHCND on 2009-12-15
How do I monitor my CPU temperature? I am currently have an AMD processor...

---

### Post by bp0 on 2009-12-15
Install lm-sensors:

```
sudo apt-get install lm-sensors
```

To detect what sensors are available:

```
sudo sensors-detect
```

When you want to see the temp:

```
sensors
```

---

### Post by nmaster on 2009-12-15
sudo apt-get install acpi

you can check the thermal info with "acpi -t".  check the man page for more stuff.

---

### Post by DTHCND on 2009-12-16
> **bp0 said:**
> Install lm-sensors:

```
sudo apt-get install lm-sensors
```To detect what sensors are available:

```
sudo sensors-detect
```When you want to see the temp:

```
sensors
```
I tried this but it keeps saying no sensors detected or something... But I can check on Windows... (Triple Boot system)

---

### Post by DTHCND on 2009-12-16
Lol I just Googled "Ubuntu no thermal sensors detected" and a couple of links came up saying Ubuntu 9.10 Karmic might have a bug... A few people say it worked fine on older versions and on Windows which seems to be similar to my situation...

---

