---
title: "memory cache growing"
date: 2008-11-23
forum: General Help
---

### Post by kevil99 on 2008-11-23
can i clear this?
my memory cache keeps getting higher and higher 






[IMG]http://i140.photobucket.com/albums/r25/kevil99/Screenshot-5.png[/IMG]

---

### Post by spiderbatdad on 2008-11-23
```
free
```

```
sudo -i
snyc; echo 3 > /proc/sys/vm/drop_caches
```

```
free
``` This is only for use when, for some reason, linux doesnt make the cahce free available to other programs. Generally unused memory is used for caching, resulting in greater system performance, and cached memory is freely available to any program that needs it.

---

### Post by oldos2er on 2008-11-23
Looks normal to me. Are you experiencing any sluggishness?

---

### Post by kevil99 on 2008-11-23
no it was just really high. i assumed it was a problem


RESOLVED thx

---

