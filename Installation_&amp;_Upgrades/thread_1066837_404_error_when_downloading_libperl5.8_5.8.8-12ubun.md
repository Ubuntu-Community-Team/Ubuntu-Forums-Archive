---
title: "404 error when downloading libperl5.8_5.8.8-12ubuntu0.3_i386.deb"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by level7 on 2009-02-11
Hi all

I have a 8.04 LTS server installed and I am totally happy with it.

However, today I tried to install OpenLDAP by doing the following:
#sudo aptitude install slapd

Aptitude downloaded and installed some packages then but in the middle of downloading the dependencies it got a 404 error:

```

Err http://ch.archive.ubuntu.com hardy-updates/main libperl5.8 5.8.8-12ubuntu0.3
  404 Not Found
Err http://security.ubuntu.com hardy-security/main libperl5.8 5.8.8-12ubuntu0.3
  404 Not Found
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/perl/libperl5.8_5.8.8-12ubuntu0.3_i386.deb: 404 Not Found

```
The download and installation process then aborts.
I googled around but did not really find a solution or a reason why this libperl dependency is not available anymore, nor what I can do.

```

#sudo aptitude search slapd 
pi  slapd
```


Can you give me some hints, how I resolve this issue.
Or what can I do to resolve/change this dependency?

Many thanks and best regards

l7

---

### Post by Partyboi2 on 2009-02-11
Change your download server in Software Sources (System>Admin>Software Sources) on the first tab change the download server to something else.

---

### Post by level7 on 2009-02-12
Thanks for the reply.

Unfortunately, the change described, will not help. The file "libperl5.8_5.8.8-12ubuntu0.3_i386.deb" does not exist (anymore?) in the main archive. see [http://archive.ubuntu.com/ubuntu/pool/main/p/perl/]("http://archive.ubuntu.com/ubuntu/pool/main/p/perl/").
But there's a file available "libperl5.8_5.8.8-12ubuntu0.4_i386.deb" which might be used instead of the "old" one. But eventually, nobody has told this the "slapd" package maintainer.

Changing to another archive will not make this file available.

---

