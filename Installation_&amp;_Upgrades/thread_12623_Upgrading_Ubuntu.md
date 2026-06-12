---
title: "Upgrading Ubuntu"
date: 2005-01-25
forum: Installation &amp; Upgrades
---

### Post by rbrugman on 2005-01-25
Hello,
I have Warty installed with a / partition and a /home partition.  I was wondering how I would be able to upgrade to "Horay Hedgehog" (when it's out) without losing my data.  Any advice would be helpful.

Robert

---

### Post by shmonkey on 2005-01-25
You would change all instances of warty to hoary in /etc/sources.list and then do 

```
sudo apt-get dist-upgrade
```

---

### Post by rbrugman on 2005-01-25
So I really don't even have to download the ISO's to upgrade to the latest version?  Will the kernel be upgraded as well?

Robert

---

### Post by ubuntu UsER on 2005-01-25
[QUOTE=rbrugman]So I really don't even have to download the ISO's to upgrade to the latest version?  Will the kernel be upgraded as well?

Robert[/QUOTE]

Yes, i made apt-get dist-upgrade and i had no problems with it.

---

### Post by farruinn on 2005-01-26
sudo apt-get dist-upgrade would do it, but I think that the safer way is to do sudo apt-get upgrade first, then the dist-upgrade.  AFAIK your /home should not be touched though.

~Nathan

---

