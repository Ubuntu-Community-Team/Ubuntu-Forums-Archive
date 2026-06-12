---
title: "Change 'From' address when sending email"
date: 2008-08-14
forum: General Help
---

### Post by gekkos on 2008-08-14
Hi, How can I easily change 'rom' address when a script is sending an email. Otherwise it takes always the user@server address and I would like to have a real reply address.
Thanks

---

### Post by brian_p on 2008-08-14
> **gekkos said:**
> Hi, How can I easily change 'rom' address when a script is sending an email. Otherwise it takes always the user@server address and I would like to have a real reply address.
Thanks

Knowing the commands you are using would be a help but if mailx is involved:

```
man mail
```

and the -a option. Get back if that is unclear.

---

### Post by gekkos on 2008-08-14
Thanks I solved it already with sendmail

---

