---
title: "Laptop to Desktop Connection (Desktop to Server)"
date: 2008-11-09
forum: General Help
---

### Post by rothdavid on 2008-11-09
Hi:

I have a laptop with Ubuntu 8.10 desktop version and a tower running Ubuntu 8.10 server.  I want to connect to server using my laptop.  I used the VNC client but the server is sharing a much larger monitor with a much larger resolution.  It connects but I have to constantly scroll the window.

I tried using the RDP Client hoping it would connect using my laptop monitors resolution but it doesn't connect at all. 

Any advice on how I may connect to the server using a desktop gui from my laptop at a smaller resolution my laptop can handle?

Thanks
David

---

### Post by russlar on 2008-11-09
If this is server, it doesn't have a desktop gui, unless you installed it yourself. I'd use ssh with X forwarding, calling each GUI window you need, rather than showing the entire desktop.

---

