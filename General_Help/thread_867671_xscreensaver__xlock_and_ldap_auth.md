---
title: "xscreensaver / xlock and ldap auth"
date: 2008-07-23
forum: General Help
---

### Post by verschdl on 2008-07-23
Dear forum users,

I played around with ldap authentication and everything works just fine. But when I want to use xlock or xscreensaver it doesn't work.

My /etc/pam.d/xlock looks like this:
```
@include common-auth
```

My /etc/pam.d/common-auth looks like this:
```
auth    sufficient      pam_ldap.so 
auth    requisite       pam_unix.so nullok_secure
auth    optional        pam_smbpass.so migrate missingok

```

Perhaps someone of you can give me a hint, what I done wrong.

Regards,
Max

---

### Post by verschdl on 2008-07-28
bump...

---

### Post by peace09 on 2009-01-19
I have the same problem with Ubuntu 8.04 here, run xlock -mode blank it lock screen fine, but can not unlick it, always saying Invalid login

Seems nobody cares about it as they use gnome or kde lock ; for me I need to find a way to lock in icewm session thus very important. Googling around the net does not show much though.

Shoud we report a xlick Ubuntu bug?

---

