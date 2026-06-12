---
title: "Koala in macbook 1,1"
date: 2009-11-06
forum: Hardware
---

### Post by kazin on 2009-11-06
Hey Guys!

First time posting here asking some help.
Normally I always found the answers here, but after a lot of searchs I've failed finding this answer.

Well, after the installation the Karmic Koala in my MacBook 1,1 the first thing I notice is that my wi-fi is gone!
Doesn't work anywmore! And WI-FI worked fine in the 8.10 and 9.04.

So, anyone can help me?

Btw: Apologize my english, i'm a little rusty.

---

### Post by dranorter on 2009-11-07
Hi, I have the same problem. When I run "lspci | grep 802", I get nothing, so the system doesn't think I have a wireless card! Is this true for you?

---

### Post by dranorter on 2009-11-07
OK, I did a few things and then restarted my computer and it was working. I think the one than fixed it was running ```
sudo aptitude install bcmwl-kernel-source
```.

The other thing I did was comment out a line in /etc/modprobe.d/blacklist-ath_pci.conf, but I don't think that was important since it wasn't the line people had mentioned being important.

---

### Post by dranorter on 2009-11-07
OK I take it back! It was totally the line in /etc/modprobe.d/blacklist-ath_pci.conf.

---

