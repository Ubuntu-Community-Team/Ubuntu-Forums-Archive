---
title: "Network Upgrade 8.10 Error"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by ajude on 2009-01-06
Hi Admin,

Im new using Ubuntu. Version that I used now as below.
[I]DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
[/I]

But, there is an error during upgrade to 10.1 via network. Error message below:
[I]W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release)  Unable to find expected entry  multivers/source/Sources in Meta-index file (malformed Release file?)

, E:Some index files failed to download, they have been ignored, or old ones used instead.
 
[/I]

Please help. Thank you


Regards,
Ajude

---

### Post by abn91c on 2009-01-06
try changing repositories servers, like  to the main or US servers.

---

### Post by ajude on 2009-01-07
How to changing repositories servers, like to the main or US servers?

Thank you.



Regards,
ajude

---

### Post by zika on 2009-01-07
> **ajude said:**
> How to changing repositories servers, like to the main or US servers?
Thank you.
Regards,
ajude
System->Software_Resources->Download_from->Main_server

---

### Post by ajude on 2009-01-07
Thank you.


Regards,
ajude

---

### Post by ajude on 2009-01-07
Hi Admin,

There is an error exist even though i select from Main, US server, Tawain, Australlia, Thailand, Japan, and other country too. Error message still the same.

The error message below for last server location download i made.

"[I]Failed to fetch [http://ubuntu.indika.net.id/ubuntu/dists/hardy-security/Release](http://ubuntu.indika.net.id/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  multivers/source/Sources in Meta-index file (malformed Release file?)

Some index files failed to download, they have been ignored, or old ones used instead."[/I]

Please help.

Thank you.


Regards,
ajude

---

### Post by zika on 2009-01-08
You are using Hardy and You have Intrepid address in Your sources.lst? post Your /etc/apt/sources.list 
type in Terminal ```
cat /etc/apt/sources.list
```

---

### Post by ajude on 2009-01-08
Hi Zika and abn91c,

I manage to upgrade now. The problem cause from the Menu Software Sources.
I suppose to Checked the Source Code selection for Downloadable From The Internet.

Thank you for your help.


Regards,
ajude

:Ubuntu beginner

---

