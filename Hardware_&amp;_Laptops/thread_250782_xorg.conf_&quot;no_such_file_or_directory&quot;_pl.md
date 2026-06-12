---
title: "xorg.conf &quot;no such file or directory&quot; plus no 1280x800 display"
date: 2006-09-04
forum: Hardware &amp; Laptops
---

### Post by TommyMann on 2006-09-04
I'm using Kubuntu on a Gateway 6510.

I'm brand spanking new to linux, as I just got it yesterday.

Well originally I was trying to figure out why I could only get 1280x768 after I noticed things weren't exactly circular. So I went to the forums and found a site that I have forgotten that explains how to fix your xorg.conf, but when I went to do that it gave me that error, so I tried another thread for resetting your xorg.conf, but that gave me an error about removing and controlling.

If I got could get a hand with this that would be awesome,

Tommy

---

### Post by Ziox on 2006-09-04
to rebuild xorg.conf file, enter this command:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by TommyMann on 2006-09-04
I tried that but I get this

debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process

---

### Post by TommyMann on 2006-09-04
and now I can't even get adept to open

---

### Post by TommyMann on 2006-09-04
I'm getting my rear handed to me by Kubuntu

---

### Post by TommyMann on 2006-09-04
Ok I restarted and got adept back

---

### Post by TommyMann on 2006-09-04
Ok I tried that and when it went to autodetect the monitor everything flipped out and I had to log back in

---

