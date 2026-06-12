---
title: "[SOLVED] Virtual hosting in Apache"
date: 2008-07-22
forum: General Help
---

### Post by Deicist on 2008-07-22
Not sure if this is in the right place, but here goes:

I have a virtual host being served from my home folder (/home/username/Web/sitename.com) and it works fine from the local machine when I add the site into my hosts file.  However, it doesn't work from an external machine... I just get the default webroot (/var/www).  How do I get my Virtual host served externally?

edit: never mind, fixed it by actually reading through the forums :/

---

### Post by oerd on 2008-07-27
Would you kindly place a link to the thread that solved this problem?

Thanks!

---

### Post by jay019 on 2008-07-27
> **oerd said:**
> Would you kindly place a link to the thread that solved this problem?

Thanks!

And maybe mark the thread as solved :P

---

### Post by Deicist on 2008-07-27
> **oerd said:**
> Would you kindly place a link to the thread that solved this problem?

Thanks!

I can't remember the thread that gave me that 'Eureka!' moment, the problem was that the original tutorial I read about setting up virtual hosts suggested setting the Virtual host listen directive to 127.0.0.1:80 (for testing) and then once it was working on the local machine I forgot to set it back to * (to listen on any IP address).

---

