---
title: "Toshiba A135-S4477 &amp; 4GB RAM"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by wrpo on 2008-01-06
Hi,

I upgraded my Toshiba A135-S4477 laptop with 4GB RAM and I've seen posts telling that we need Ubuntu 64-bit edition to get the 4GB RAM full access (the 32-bit edition accesses ~3GB only).

Do I really need the 64-bit Ubuntu version? I'm concerned of 64bit driver issues with this laptop model. So, is it possible to have 4GB RAM access with the 32-bit edition?

I'd appreciate any replies!

Thanks!

---

### Post by Yellow Pasque on 2008-01-06
Related topic: [http://ubuntuforums.org/showthread.php?t=658586](http://ubuntuforums.org/showthread.php?t=658586)

Please run the following so we can see what hardware you have:
```
sudo update-pciids
sudo lspci
```

Most likely, everything will work just fine (and faster) in 64-bit. I would recommend upgrading to 64-bit when Hardy Heron comes out in April (unless you haven't installed Ubuntu or just got started with it; then do it now). You can post in the 64-bit forum and we will gladly help you make the transition (e.g. keeping your home folder and preferences)

---

