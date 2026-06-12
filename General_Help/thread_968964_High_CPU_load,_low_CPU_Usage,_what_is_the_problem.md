---
title: "High CPU load, low CPU Usage, what is the problem?"
date: 2008-11-03
forum: General Help
---

### Post by BlackDex on 2008-11-03
Hello there,

I have a problem with a web-server.
It has a very high CPU load, but a very low CPU usage.
How is this posible, where do i look??

The server runs Apache with PHP, and a MySQL server is located on a different server in the local network.

Thx in advance.

---

### Post by flying_surprise on 2008-11-03
Hi,

I'm also interested in this. In some cases it may have to do with intensive hardware accessing, like disk reading/writing or networking. In my case it is not showing up until after several hours, then si is raising to ~20% and ksoftirqd is taking 100% cpu.

---

### Post by FrostyFlames on 2008-11-03
I suppose if you just want to see the usage and what is using it you could use "top" or "htop". As far as diagnosing what is actually eating your CPU up...donno.

---

### Post by Yellow Pasque on 2008-11-03
> It has a very high CPU load, but a very low CPU usage.
I'm not sure I understand. Is your CPU not throttling on high loads? How do you know it has "low usage"?

Some ?'s:
Are you using the server kernel? If you have a multi-core chip, is multi-core processing enabled in the BIOS? (I'm not sure if this applies to AMD CPU's, but I know a lot of Intel mobos have this option.)

---

