---
title: "default ssh banner..."
date: 2005-11-03
forum: General Help
---

### Post by djlosch on 2005-11-03
> Linux io 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

how do i remove those?

the sshd_config file has no banner specified

---

### Post by maulattu on 2005-11-04
edit the file /etc/motd:
```

sudo nano -w /etc/motd

```

MOTD = Message Of The Day (i suppose ;) )

---

### Post by djlosch on 2005-11-04
yeah, motd = message of the day.

this worked... THANKS

---

