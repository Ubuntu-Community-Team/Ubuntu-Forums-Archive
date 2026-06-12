---
title: "Can't install Squid"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by clievers on 2009-05-08
Hi. I'm still running Feisty on my file server (please don't yell, I'll upgrade this summer hopefully). I was wanting to try Squid out to play w/ proxy server. So I've tried to install by running
```
sudo apt-get install squid
```
After saying yes to install and can't authenticate, it says:
```
Err http://archive.ubuntu.com feisty-security/main squid-common 2.6.5-4ubuntu2.2
  404 Not Found [IP: 91.189.88.140 80]
Err http://archive.ubuntu.com feisty-security/main squid 2.6.5-4ubuntu2.2
  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/s/squid/squid-common_2.6.5-4ubuntu2.2_all.deb 404 Not Found [IP: 91.189.88.140 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/s/squid/squid_2.6.5-4ubuntu2.2_i386.deb 404 Not Found [IP: 91.189.88.140 80]
```
I've seen this in the past for other packages too. How can I fix this? If I go to [http://archive.ubuntu.com/ubuntu/pool/main/s/squid/](http://archive.ubuntu.com/ubuntu/pool/main/s/squid/) there are a number of squid packages, but not the one in question in my repository. I'm not sure why my repository isn't reflecting the proper version. I've tried running the --fix-missing and the apt-get update.
Any advice?

Thanks

---

### Post by taurus on 2009-05-08
If you decide to use an expired release, then you need to modify your repos from whatever you have right now, archive.ubuntu.com, to old-releases.ubuntu.com.

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by clievers on 2009-05-08
You rock taurus. I updated as you suggested and I was able to install.
Thanks so much for your quick reply.

---

### Post by clievers on 2009-05-08
Oh, and I love your quote in your signature (windows and gates). That's awesome. lol.

---

