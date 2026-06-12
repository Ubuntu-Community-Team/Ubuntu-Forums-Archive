---
title: "tmpfs /var/log/apt"
date: 2009-04-07
forum: Hardware
---

### Post by kozimodo on 2009-04-07
Hi,

Following [http://www.ubuntu-eee.com/wiki/index.php5?title=How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive](http://www.ubuntu-eee.com/wiki/index.php5?title=How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive), I added:

```
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/log tmpfs defaults,noatime,mode=0755 0 0 
tmpfs /var/log/apt tmpfs defaults,noatime 0 0
```
to my /etc/fstab but /var/log/apt does not mount. Is there some configuration option that I'm missing?  Will a "mkdir /var/log/apt" in rc.local do the same trick?

Thanks,
kozi

---

### Post by sdennie on 2009-04-07
Rather than trying to mount a /var/log/apt as tmpfs, instead just create it in rc.local (which gets run after /var/log is mounted).  Edit, /etc/rc.local and add the following to it:

```

mkdir /var/log/apt

```

That's what I use for what you are doing and it works fine.

---

### Post by kozimodo on 2009-04-08
Thanks.  That is what I had already done.  I guess I'm just puzzled since those fstab lines are suggested in numerous places so presumably it works on some installations.

---

### Post by sdennie on 2009-04-08
I found those instructions too and it inspired me to mount a bunch of stuff as tmpfs for power savings reasons.  However, as written, I don't think they can ever actually work because apt will always need /var/log/apt and it's doesn't seem to be keen on creating that directory when it doesn't exist.  I would almost consider that an apt bug actually.

---

### Post by kozimodo on 2009-04-16
So what else do you mount to tmpfs to save power?

Just curious since I'm building a digital picture frame from an old dell and it would be nice to keep power consumption to a minimum.

---

