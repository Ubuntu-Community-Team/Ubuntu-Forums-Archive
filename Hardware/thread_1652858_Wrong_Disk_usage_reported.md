---
title: "Wrong Disk usage reported"
date: 2010-12-25
forum: Hardware
---

### Post by Aztek on 2010-12-25
120GB hard drive. 90GB Windows 7 partition. The rest is an extended with swap and Ubuntu. I'm using about 20GB of the windows partition (verified with du), but Windows, Ubuntu, and GParted live CD all report the usage as 60GB.

I'm trying to reduce the size of the windows partition to around 30GB (I hardly ever use it) so I can install another distro.

Any ideas?

---

### Post by Aztek on 2010-12-26
bump

---

### Post by karthick87 on 2010-12-26
Boot using a live cd and use Gparted..If it is not there then install it
```
sudo apt-get install gparted
```

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Aztek on 2010-12-26
Thanks for the reply. Yeah I tried the GParted Live CD already and it also reports the usage as 60GBs.

---

### Post by karthick87 on 2010-12-26
Post the output of,
```
df -h
```

---

### Post by Aztek on 2010-12-26
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              17G  7.7G  8.3G  49% /
none                  1.3G  264K  1.3G   1% /dev
none                  1.3G  448K  1.3G   1% /dev/shm
none                  1.3G   92K  1.3G   1% /var/run
none                  1.3G     0  1.3G   0% /var/lock
/dev/sda2              80G   61G   19G  77% /media/8AE85D13E85CFEBF
```

/dev/sda2 is the one we're interested in. I managed to resize it to 80GB, but that's as small as GParted will let me make it.

---

### Post by Aztek on 2010-12-26
bump

---

