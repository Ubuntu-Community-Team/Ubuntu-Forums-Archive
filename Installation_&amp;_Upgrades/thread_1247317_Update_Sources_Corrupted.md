---
title: "Update Sources Corrupted?"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by Patriot1776 on 2009-08-22
Okay, my brother, who is now running Hardy on his laptop got a message that a series of updates can't be authenticated.  Here's the message he gets when he clicks 'install updates' in the Update Manager:

```
You are about to install software that can't be authenticated! Doing this could allow a malicious individual to damage or take control of your system.
```

It tells him the following updates can't be authenticated:

```
linux-image-2.6.24-24-generic
libgnutls13
libcurl3
libcurl3-gnutls
pidgin-data
libpurple0
linux-headers-2.6.24-24
linux-headers-2.6.24-24generic
pidgin
```

The fact that kernel initrd image updates and header updates can't be authenticated is telling me that his update sources list has possibly been corrupted.  Anybody know anything about this and can offer a solution?

---

### Post by Partyboi2 on 2009-08-22
Hi, It looks like you need to add a gpg key, open a terminal and run
```
sudo apt-get update
``` to see which repo requires authentication.

---

