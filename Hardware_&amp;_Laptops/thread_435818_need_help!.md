---
title: "need help!"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by chunchengch on 2007-05-07
I found an article may be useful for installing webcam , but I experienced problem when tried to execute

**sudo ln - s /usr/src/linux-source-2.6.20 /usr/src/linux**

I can not find directory or file "linux" under /usr/src , in which there are only 3 directories and 1 file as follows :

chun@pa:/usr/src$ ls
linux-headers-2.6.20-15 linux-source-2.6.20
linux-headers-2.6.20-15-generic linux-source-2.6.20.tar.bz2

should anyone could help? thanks.

---

### Post by kidders on 2007-05-08
> **chunchengch said:**
> **sudo ln - s /usr/src/linux-source-2.6.20 /usr/src/linux**It looks as though you have a space between '-' and 's'.

Also, the symlink you are trying to create **_must_** point to the source of the kernel you are currently using. You should double-check that, if you're not 100% sure ... whatever you're compiling may not warn you if you symlink the wrong thing.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

