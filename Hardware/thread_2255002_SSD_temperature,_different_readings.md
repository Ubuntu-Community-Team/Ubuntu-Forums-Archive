---
title: "SSD temperature, different readings"
date: 2014-12-01
forum: Hardware
---

### Post by minuser on 2014-12-01
Ubuntu 14.04 LTS - 64 bit
I fount two different readings of my SSD temperature
hddtemp shows:
/dev/sda: SSD2SC240G1SA754D117-820                &#65533;: 36°C
gnome-disks reports 100 C/ 212 F
Who is right?

---

### Post by tgalati4 on 2014-12-01
Open a terminal:

```
sudo smartctl -a /dev/sda | grep Temperature
```

---

### Post by gordintoronto on 2014-12-02
hddtemp is right.

---

