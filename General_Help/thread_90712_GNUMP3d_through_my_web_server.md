---
title: "GNUMP3d through my web server"
date: 2005-11-15
forum: General Help
---

### Post by qwert231 on 2005-11-15
I can access my GNUMP3d feed through localhost, but not through the web. I have apache running, and my web address is [http://mark.arkaoss.com/](http://mark.arkaoss.com/)

I think I need to configure apache (version 2) to feed it, but I'm not sure where.

---

### Post by invalid on 2005-11-15
GNUMP3d runs independently from other servers, including apache webserver. Any configuration you do to this, will have nothing to do with the other (unless you are trying to use the same port, which will lead to problems).

If you can not access it beyond localhost, it sounds like you have something blocking the GNUMP3d port.. either a firewall, a router, and ISP, etc. Try checking those settings and see if you can add an exception for this service.

Cheers,
Cb

---

### Post by qwert231 on 2005-11-15
Sorry, before you came on I realized it was my router and fixed it. Thanks.

---

