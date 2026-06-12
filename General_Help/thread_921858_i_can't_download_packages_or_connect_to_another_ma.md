---
title: "i can't download packages or connect to another machine through my command promp"
date: 2008-09-16
forum: General Help
---

### Post by shredder12 on 2008-09-16
Hey  i use hardy..and now a days i m having a weird problem with my command prompt..
whenever try to install something 
using apt-get it always says that unable to connect to the website..
and even when i try to connect to a server on my LAN using ssh it says that no possible route to the server could be found..though other machines could connect to it..
how do solve this problem??

---

### Post by cariboo on 2008-09-16
Check /etc/resolv.conf and make sure it is connecting to the correct dns server, and also make sure you are on the same subnet as the server eg:

```
your computer ip address: 192.168.1.100
server ip address: 192.168.0.200
```

These ip address are used as an example only. Make sure the third set of numbers are the same.

Jim

---

### Post by shredder12 on 2008-09-17
The  /etc/resolv.conf file has correct ips for dns servers..and i have my network settings set to roaming mode..
so the ip address, subnet and gateway get automatically assigned...and since i m using collg lan..
i have my local ip 172.*.*.* where as the server i m trying to connect to which is actually a lan server has ip 192.168.36.205
so i don't think that the ip thing is a problemm.
because it works for all the other guys..

---

