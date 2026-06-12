---
title: "Saving upgrade files"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by grognut on 2009-01-09
Hi,

I want to upgrade a 6.06 lts sever to 8.04lts.
BUT I want to do the download outside tiscali FUP hours and then do the upgrade later. Is this possible??

Cheers

grognut

---

### Post by Tim Sharitt on 2009-01-09
Running apt-get ugrade with the -d option should allow you to download the packages and then update later.
```
sudo apt-get upgrade -d
```

---

### Post by grognut on 2009-01-09
Hi Tim,

Thank you for your reply but I realised that I asked the wrong question.
I should have asked can I do this with
 ```
sudo do-release-upgrade -m desktop
```
I've done it on one systen, it was 843Mb.

Cheers

Grognut

---

