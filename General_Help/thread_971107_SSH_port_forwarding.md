---
title: "SSH port forwarding"
date: 2008-11-04
forum: General Help
---

### Post by eludlow on 2008-11-04
If I SSH map a port on one server to one on my local machine using:

```
ssh -L 3306:sqlserver:3306 -N user@sqlserver
```

I can then connect to the server from my LOCAL (let's say 192.168.1.2) machine by accessing 127.0.0.1.

Question is, can I then access it from ANOTHER machine on the network by using the local machine's IP, 192.168.1.2:3306 ?

Would this depend on allowed hosts in the mySQL DB users, or what?

Thanks,
Ed Ludlow

---

