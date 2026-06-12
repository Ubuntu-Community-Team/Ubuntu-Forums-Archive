---
title: "NETSTAT issue (probably an easy question)"
date: 2008-10-29
forum: General Help
---

### Post by Coldmiser487 on 2008-10-29
[porn](http://emo-porn.com)
[amateur porn](http://camrevenge.com)
[dubstep](http://n3k4.com)

---

### Post by maxhax on 2008-10-29
Well you can do this to see those without domain names.  

> netstat -an | grep ESTABLISHED

Since everything in Linux is supposed to be a file you can use the lsof(list open files).  If you want TCP or UDP there specify TCP or UDP instead of ESTABLISHED.  You'll have to run as root to see everything if you're ever looking for something specific...that's not necessary here though.

> lsof | grep ESTABLISHED

Here's another way to see what is going on.

> ss

One of these will hopefully get what you are looking for.

---

### Post by Coldmiser487 on 2008-10-30
> **maxhax said:**
> netstat -an | grep ESTABLISHED 

and then do a nslookup on the remote IP address.

OK, this will work, It's not elegant, but it gets the job done.

I was hoping to be able to do this with as little resources as possible so if anyone else has an idea I would be interested in hearing it.

Thanks maxhax!

---

