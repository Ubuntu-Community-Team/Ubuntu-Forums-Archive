---
title: "Xchat refuses to connect"
date: 2008-11-23
forum: General Help
---

### Post by Directorate on 2008-11-23
Hello,

I've been trying to use xchat for quite some time now, but for some reason it seems unable to connect.


This is what it tells me:

> * Looking up chat.us.freenode.net
* Connecting to chat.us.freenode.net (207.158.1.150) port 6667...

Pidgin and aMSN seem to work fine, so I can't get if it's a matter of ports or not.

Thank you for your help

---

### Post by Directorate on 2008-11-24
No one ?

---

### Post by silverglade00 on 2008-11-24
It is most likely the ports are being blocked. That is the case where I am. Try irc.ubuntu.com port 8001 and see if that works. That's what I have to do to get around the firewall.

---

### Post by Directorate on 2008-11-24
> **silverglade00 said:**
> It is most likely the ports are being blocked. That is the case where I am. Try irc.ubuntu.com port 8001 and see if that works. That's what I have to do to get around the firewall.

That's true. I use my college connection, and their IT department is understandably security paranoid.

When I tried connecting through the port you told me about I got a problem that I was getting with a few other servers that I tried which is quite confusing because it connects and won't log in.

> * Looking up irc.ubuntu.com
* Connecting to chat.freenode.net (207.158.1.150) port 8001...
* Connected. Now logging in...

Keeps trying to log-in but it won't. Is that a blocked port problem as well?

---

### Post by silverglade00 on 2008-11-24
It could be stuck on the identd service which runs on port 113 (going by my dusty cobwebbed recollection). If that is blocked, then you may have to investigate using a java irc client on a website somewhere.

---

