---
title: "&quot;dd&quot; stop to recover dvd"
date: 2012-01-02
forum: Hardware
---

### Post by miousername on 2012-01-02
Hi at all,
I've a camera with dvd-rw as memory and I've partially overwritten the initial part of this disk with 34 Mb of a new video...I now try to recover the last video but when i launch:

```
 
dd if=/dev/sr0 of=dd.iso 

```

the copy of my disk stop it after 34 Mb but ther are 1.4Gb of video in the  the disk that  I can't read it ..

Have you some advice for recover the whole disk??

Thanks in advance

---

### Post by fdrake on 2012-01-02
ciao!
poi dirci il risultato di questo commando:
```

df -h /dev/sr*

```

---

### Post by miousername on 2012-01-02
Il risultato è il seguente:

```

Filesystem            Size  Used Avail Use% Mounted on
none                  997M  288K  996M   1% /dev

```

---

