---
title: "Error opening ATI Control Center"
date: 2011-01-20
forum: Hardware
---

### Post by doktoreas on 2011-01-20
Hello everybody,
I have an error trying to open the ATI Control Center with 10.10:

```
sudo amdxdg-su -c amdcccle
amdxdg-su: no graphical method available for invoking 'amdcccle' as 'root'
```

My device:
```
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68e1
```

It's a fresh new install and not an upgrade from 10.04.

Thx
Luca

---

### Post by sooeta on 2011-07-27
Found a solution here: [http://forums.fedoraforum.org/showthread.php?t=262068](http://forums.fedoraforum.org/showthread.php?t=262068)

Just type "su - -c amdcccle" in shell. Worked for me.

---

