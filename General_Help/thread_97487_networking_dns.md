---
title: "networking dns"
date: 2005-12-01
forum: General Help
---

### Post by davebradford on 2005-12-01
was thinkin on using ubuntu server a while ago but then i ran into a problem, becuase ubuntu server doesnt run a gui i found that i was unable to setup my network properly! i know how to get a static ip into place (/etc/networking/interfaces etc) but i need to enter a primary and secondary which is not entered in this conf. Any ideas? In the end i just had to run a gui as this is easily entered in the networking window, just like in windoze..

penny for the n00b?

---

### Post by suRoot on 2005-12-01
Add them to /etc/resolv.conf

```
nameserver x.x.x.x
nameserver x.x.x.x
```

---

### Post by jatos on 2005-12-01
BTW, with a server you may find webmin, apt-get install webmin, may be useful to you.

---

### Post by davebradford on 2005-12-01
so i would just make it
```

nameserver 1.2.3.4 (primary)
nameserver 1.2.3.5 (secondary)

```
that sound right?

---

### Post by suRoot on 2005-12-01
Yes, that's right.

---

### Post by davebradford on 2005-12-01
you say about webmin.. i did have that running but i can't get apache to work on it out of the box? how does webmin need to be configured to run apache2??

Dave

---

