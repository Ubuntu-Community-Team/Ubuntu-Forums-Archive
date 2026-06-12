---
title: "HTTPS without SSL?"
date: 2008-11-10
forum: General Help
---

### Post by frmdstryr on 2008-11-10
Hi, I have a small website that runs on my desktop by apache2.  Is there a way that I can set it up so that it can be accessed by [https://***.com/](https://***.com/) instead of only [http://***.com/](http://***.com/) without having a SSL?  My teacher blocks http but always allows https so I'm looking for a way to use both. if it is at all possible.  Thanks.

---

### Post by Titan8990 on 2008-11-10
Sounds like you can just change your default apache port for non-ssl connections from 80 to 443. Most likely it is port 80 being blocked and not the http:// from the address header.

---

### Post by frmdstryr on 2008-11-10
My ISP is blocking port 80 so I use port 81. But it still is blocked.  After searching, I think I've found what I was looking for, self signed certificates, now I need to figure out how to set it up.  Thanks.

---

