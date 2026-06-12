---
title: "Ubuntu Apt Won't Update Today"
date: 2005-11-24
forum: General Help
---

### Post by SuperMike on 2005-11-24
Occasionally I get a condition like this...

root@mypc:/etc/apt # apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
99% [Connecting to us.archive.ubuntu.com (216.165.129.138)]

...where Ubuntu won't update. If I wait a day, it will work. Is Ubuntu.com having issues today? Have they been notified? Anyone know a way to contact their domain admin (the proper way) and let them know that they have tech difficulty?

---

### Post by Xian on 2005-11-24
[QUOTE=SuperMike]
99% [Connecting to us.archive.ubuntu.com (216.165.129.138)]

...where Ubuntu won't update. If I wait a day, it will work. Is Ubuntu.com having issues today? Have they been notified? Anyone know a way to contact their domain admin (the proper way) and let them know that they have tech difficulty?[/QUOTE]
My experience with the US mirrors is not a good subject. I would edit your /etc/apt/sources.list and remove the 'us' prefix from that server(s), leaving just archive.ubuntu.com.

---

