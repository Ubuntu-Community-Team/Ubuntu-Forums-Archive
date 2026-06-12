---
title: "FreeRadius: Domain Name"
date: 2006-01-07
forum: Installation &amp; Upgrades
---

### Post by InDenial on 2006-01-07
Hi all,

I am trying to get freeRadius working with my wireless network using WPA support. I am using the following page:

[link to setup freeradius server]("http://www.linuxjournal.com/article/8095")

I am at the point where I am going to create the server certificate. It warns me about filling in my 'Fully Qualified Domain Name'. 

I am just running an ubuntu "server" here in the network and I have no domain of some sort. On the other hand.. maybe I do but I am not aware of this. What would I enter as a Fully Qualified Domain Name?

---

### Post by Lambert on 2006-01-07
To find your fqdn on the server use this command.

```
hostname --fqdn
```

It's probably just localhost.localdomain

---

### Post by InDenial on 2006-01-07
Yep.. localhost.localdomain it is. thanks...

---

