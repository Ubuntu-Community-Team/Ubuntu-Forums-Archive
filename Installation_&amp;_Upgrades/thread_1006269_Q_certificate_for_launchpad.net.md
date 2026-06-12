---
title: "Q: certificate for launchpad.net"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by grkuntzmd on 2008-12-09
Does anyone know where I can get an "apt-get" certificate for launchpad.net. I added it as a software source to download the newest openoffice, but now apt-get warns me that the downloads cannot be authenticated (it does allow them though).

Thanks.

---

### Post by kiko-canonical on 2008-12-10
So I think you (or I) am missing some information on where exactly you're pulling the package from, but your message hints to me that you are pulling it from a Launchpad PPA: [https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

The short answer is that right now PPAs are unsigned so there's nothing you can do to avoid the unsigned repository warning. However, next week's Launchpad release will bring signed PPAs online and when that happens you will be able to import the PPA's key from the Ubuntu keyserver and add that to your keyring; the instructions will be posted but will probably use apt-key(1) or something similar.

---

