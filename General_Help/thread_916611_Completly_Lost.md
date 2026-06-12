---
title: "Completly Lost"
date: 2008-09-11
forum: General Help
---

### Post by ilovelinux33467 on 2008-09-11
I am trying to connect ubuntu to a Windows 2000 AD Domain with likewise. I have followed the instructions [here]("http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/") but this is what is comes up with: 

```
Joining to AD Domain:   andrewit.local
With Computer DNS Name: andrewremotesvr.andrewit.local

administrator@ANDREWIT.LOCAL's password: 
[2008/09/11 19:18:55,  0] utils/net_ads.c:ads_startup_int(493)
  ads_connect: No logon servers
Failed to contact DC when trying to synchronize local system clock!
None of the domain controllers listed in DNS could be contacted, or there are no DCs listed in DNS.

Error: Unable to join domain [code 0x0008000e]

Creating the computer account in Active Directory failed. Common causes are a
bad administrator password, a bad OU name, or an existing computer account but
not modificiation permissions.

```

Any Help? I am really desperate to get this working

---

### Post by ilovelinux33467 on 2008-09-11
bump

---

### Post by overdrank on 2008-09-11
> **ilovelinux33467 said:**
> bump

Please do not bump your thread so frequently. :)

---

### Post by mb_webguy on 2008-09-11
I don't really know if this has anything to do with your problem, but [according to this]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/ServerType.html#id2553159") it looks like you need to set Samba's authentication mode to ADS in order to join an Active Directory domain.

---

