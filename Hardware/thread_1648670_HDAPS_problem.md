---
title: "HDAPS problem"
date: 2010-12-19
forum: Hardware
---

### Post by pedi0022003 on 2010-12-19
when I run the application in terminal i get this error : 
Could not find a suitable interface
I'm using ubuntu 10.10 on my lenovo thinkpad sl500c.

---

### Post by pedi0022003 on 2010-12-19
really?!no one?!
this might help : i get this when i run hdapsd :
```
Sun Dec 19 19:51:13 2010: Starting hdapsd
Sun Dec 19 19:51:13 2010: WARNING: You did not supply any devices to protect, trying autodetection.
Sun Dec 19 19:51:13 2010: Adding autodetected device: sda
Sun Dec 19 19:51:13 2010: Could not find a suitable interface

```
i really appreciate any kind of help.

---

### Post by adeeriswan on 2010-12-25
I got same problem as [pedi0022003]("http://ubuntu-virginia.ubuntuforums.org/member.php?u=1202924") had

Any solution for this?

---

### Post by spamalam on 2010-12-27
```

[x201t /]$ sudo service hdapsd stop
[x201t /]$ sudo service hdapsd start
Mon Dec 27 22:07:08 2010: Starting hdapsd
Mon Dec 27 22:07:08 2010: Could not find a suitable interface

```

Seems to be the same, I've got an x201t

---

