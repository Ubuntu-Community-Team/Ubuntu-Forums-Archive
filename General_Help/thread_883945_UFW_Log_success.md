---
title: "UFW Log success?"
date: 2008-08-08
forum: General Help
---

### Post by kblancha82 on 2008-08-08
Hi All,

I am using UFW as a firewall and it successfully logs rejected connections. Is it possible to have it log successful connections?

Thanks,
Kyle

---

### Post by brian_p on 2008-08-08
> **kblancha82 said:**
> Hi All,

I am using UFW as a firewall and it successfully logs rejected connections. Is it possible to have it log successful connections?


I thought it logged everything. Is that not the case?

---

### Post by kblancha82 on 2008-08-08
I seem to only be getting failures in /var/log/messages. Is there another place to look?

---

### Post by brian_p on 2008-08-08
> **kblancha82 said:**
> I seem to only be getting failures in /var/log/messages. Is there another place to look?

/var/log/syslog and /var/log/kern.log, but I think they will contain duplicates of what's in /var/log/messages.

---

