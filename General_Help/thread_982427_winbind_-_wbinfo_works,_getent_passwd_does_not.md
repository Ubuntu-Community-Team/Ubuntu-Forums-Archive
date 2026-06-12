---
title: "winbind - wbinfo works, getent passwd does not"
date: 2008-11-14
forum: General Help
---

### Post by bannerman9 on 2008-11-14
wbinfo -u and wbinfo -g return the expected list of users and groups:

```
**wbinfo -u**
NB\administrator
NB\jon
NB\billy
NB\will

```

But **getent passwd** and **getent groups** return only the local users and groups. What could I have done wrong? I have done the Google, many times very hard.

```
**nsswitch.conf**
passwd:         winbind compat ;lwidentity
group:          winbind compat
shadow:         winbind compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

```

```
**smb.conf**
[global]

security = ADS
netbios name = NAME
realm = DOMAIN.LOCAL
password server = x.x.x.x (my Windows 2003 server, domain controller)
workgroup = DOMAIN
idmap uid = 10000-20000
idmap gid = 10000-20000
wins support = no
wins server = x.x.x.x (my Windows 2003 server, domain controller)

```

---

