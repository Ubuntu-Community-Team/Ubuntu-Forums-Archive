---
title: "LDAP user resolving"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by hal_bg on 2009-08-04
Hi all
I have an issue with the LDAP client. 
I need my NFS server to be able to resolve users and groups from the LDAP but not to authenticate them. In other words need to be able to do 
'chown ldapuser:ldapgrpup somefile' and 'ls -l' to show usernames and groups instead of numbers. But I do not want those users to be authenticated on the NFS server. 
I have changed nsswith.conf and ldap.conf with no success. what I am missing? Please help! What I have to do?

10x in advance!

Hal

---

