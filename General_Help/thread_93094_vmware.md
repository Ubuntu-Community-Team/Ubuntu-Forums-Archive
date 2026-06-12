---
title: "vmware"
date: 2005-11-21
forum: General Help
---

### Post by much better on 2005-11-21
i downloaded vmware and the player for linux but i don't know how to install it .. Any help will be appreciated

---

### Post by xavierh on 2005-11-21
[QUOTE=much better]i downloaded vmware and the player for linux but i don't know how to install it .. Any help will be appreciated[/QUOTE]

try this link
[https://wiki.ubuntu.com/VmWare]("https://wiki.ubuntu.com/VmWare")

I used it and it worked for me!!

---

### Post by suRoot on 2005-11-21
A lot of that is unnecessary for the player, at least on my box.

Install build-essentials

```
sudo apt-get install build-essentials
```

Install the player

```
cd /path/to/player/files
sudo ./vmware-install.pl
```

Hit enter 9 or so times to accept the defaults & then you are done.

The player compiled & inserted the modules perfectly on my system with GCC 4.  VMWare workstation, on the other hand, did require the steps detailed on that other page.

---

