---
title: "Upgrade from Hoary"
date: 2005-11-25
forum: General Help
---

### Post by bockman on 2005-11-25
I tried to upgrade from hoary with 'apt-get dist-upgrade' and way on down the line this happened:
```
Selecting previously deselected package libhal-storage1.
Unpacking libhal-storage1 (from .../libhal-storage1_0.5.3-0ubuntu14_i386.deb) ...
Preparing to replace libcomerr2 1.35-8ubuntu2 (using .../libcomerr2_1.38-2ubuntu1_i386.deb) ...
Unpacking replacement libcomerr2 ...
Errors were encountered while processing:
 /var/cache/apt/archives/gvlc_0.8.4-svn20050920-3+hal0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
I tried 'apt-get -f dist-upgrade' and have repeated this a number of times, but it won't recover. How do I fix this?

---

### Post by rickmans on 2005-11-25
I did it the first time like you described in your post and I had the same issues. The second time I first used the update manager and after that I used synaptec. Strangly enough that had a better effect than doing an apt-get dist-upgrade.

---

### Post by bockman on 2005-11-25
I tried using Synaptic and got the same error.

---

### Post by bockman on 2005-11-25
I deleted the package gvlc and rebooted my computer after it was finished. It still looks really like Hoary and still uses the 2.6.10 kernel. Also, the xserver fails to start, and then crashes my computer (locks all input). Is there anyway to recover?

---

### Post by cdsboy on 2005-11-26
can you get to a terminal? if so just apt-get the old distro. that would be my guess.

---

